---
tags:
  - pecha-kucha
  - horde
---

![[horde-build-system.webp]]

notes: Horde is a CI/CD system built by Epic specifically for Unreal Engine. They've been using it to build Fortnite for years now, and recently released it into General Availability for Unreal Engine 5.5

---
# Horde

A build system for Unreal Engine

notes: Most of my time at GDC this year was spent attending lectures talking about how and why you use Horde on-prem and in the cloud.

---

# Horde

A build system for Unreal Engine...but *why*

notes: Building games is hard, and while general-purpose tools like Jetbrains's TeamCity and CDF's Jenkins can be configured and tweaked and hacked and *managed* to do whatever it is you want to do, it'd be nice if your tool had some idea what your work flow was supposed to be

---
# Features

- Build Automation using BuildGraph
- Orchestrator for Unreal Build Accelerator
- Test Automation
- Device Manager for mobile devices and devkits
- Built-in UnrealGameSync Metadata Server

notes: ...and thus springs Horde. Working with a system that knows what an Unreal Game's build looks like means it can make smarter decisions about how to manage those builds. Plus, there's a lot of tools that have been floating in the periphery -- bits of utilities like the UnrealGameSync Metadata Server that Horde can absorb and handle itself.

---
# Build with BuildGraph

Just like with RunUAT

notes: Horde speaks BuildGraph, so any projects using a BuildGraph can be built by Horde without any additional configuration. This includes *automatically* parallelizing work and omitting build steps where nothing has changed. So long as the BuildGraph has the DAG well-defined, Horde can assign as many agents to it as it needs to run optimally

---
# Unreal Build Accelerator

Incredibuild, but smarter

notes: In fact, those compute resources don't need to sit idle waiting for a build. Unreal Build Accelerator allows a developer testing a feature to compile on their workstation and leverage build resources to speed up compile times opportunistically. This isn't new to Horde, but you can leverage your existing user database in Horde to power up Unreal Build Accelerator with Horde's agent clusters (AKA the spare machines on your build rack) to run CPU-heavy loads on those remote machines and ship back the compilation results

---
# Test with Gauntlet

You mean games can have tests too?

notes: Though this was *not* something I saw a lot of talk about at GDC, one of the features that I'm excited for is the ability to use Epic's Gauntlet Automation Framework to run automated tests on the build machines *or on device*. Each CI build can kick off a suite of tests on a set of QA devices plugged into the build farm and give a report when those tests fail and in what circumstances, saving valuable QA time smoking daily builds

---
# Device Manager

"Who's got the iPhone 15 Pro Max again?"

notes: along with build agents, you can give a fleet of QA devices to Horde to manage. As mentioned in the last slide, test automation can automatically reserve available devices to make sure no two builds are stepping on each others' toes.

---

# UGS Metadata Server

Desktop notifications when you break the build

notes: another existing Unreal tool being absorbed by Horde is the UGS Metadata Server, which adds power to UnrealGameSync by allowing users to mark changes as "Good" or "Bad," showing which users are synced to which changes, and surfacing build results via direct integration with Horde CI. This allows UGS to notify you directly on your desktop if you check something in which breaks the build.

---

# Non-Unreal Builds?

An incomplete solution

notes: The glaring problem with Horde is that it doesn't handle any of the non-Unreal builds. So your C# backend services, your Java web apps, and your Terraform deployment calls are all non-starters in Horde. BuildGraph can begin to fill the gap here by allowing you to "Spawn" external executables and wait for them to finish, but we're back to configuring and tweaking and hacking to get that to work. A complete solution on a project likely uses Horde *in addition* to old mainstays like Jenkins, Teamcity, or Git-powered solutions like Github Actions for a full-throated CI/CD system.

---

# Questions?

---

## References:

Horde  
https://dev.epicgames.com/documentation/en-us/unreal-engine/horde-in-unreal-engine

BuildGraph  
https://dev.epicgames.com/documentation/en-us/unreal-engine/buildgraph-script-tasks-reference-for-unreal-engine

PW Horde server (still WIP)  
https://horde.dev.pipeworks.com

