---
layout: post
title:  "Secure Scope"
date:   2024-01-21 09:29:20 +0700
categories: vuln_scan
---

# Secure Scope | A College Project That Taught Me Vulnerability Intelligence

Back in 2023, during my college days, I built a small security project called **Secure Scope**.

The idea came from a simple question:

> If I can identify the technologies running on a website, can I automatically check whether they're vulnerable?

At the time, I was spending a lot of time learning web security, reconnaissance, and vulnerability assessment. Whenever I came across a website running an old CMS or framework version, I'd manually search for CVEs, exploit references, and public disclosures. After doing that repeatedly, I thought it would be fun to automate the process.

So I built Secure Scope.

Given a website, the application would identify the technologies being used, determine their versions whenever possible, and then compare those versions against publicly known vulnerabilities and exploit references.

For example, if a website was running an outdated WordPress version, the platform could automatically look for known security issues and public exploit information associated with that specific release.

Looking back, the project was fairly simple, but it was one of the first times I combined reconnaissance, version fingerprinting, vulnerability intelligence, and automation into a single workflow.

< InsertScreenshot > HomepageUI >

## How It Worked

The workflow was intentionally straightforward.

A user would enter a target URL, and the backend would begin collecting information about the technologies running behind the site.

To identify technologies, I integrated the WhatRuns API. This allowed the application to detect things like:

* CMS platforms
* JavaScript libraries
* Frontend frameworks
* Analytics services
* Third-party technologies

Once the technologies were identified, the application attempted to determine version information whenever it was exposed.

After that came the interesting part.

The detected versions were compared against publicly available vulnerability information to see whether any known security issues existed for those specific releases.

For vulnerability matching, I used `searchsploit`, which provided an easy way to query public exploit database entries and correlate them with detected versions.

While the logic wasn't particularly advanced, it gave me a practical understanding of how vulnerability intelligence systems work behind the scenes.

< InsertScreenshot > Dashboard >

## Tech Stack

The project was built using a fairly lightweight stack:

* Flask
* HTML
* CSS
* JavaScript
* Tailwind CSS
* WhatRuns API
* Searchsploit

Nothing fancy.

Most of the effort went into connecting the different pieces together and making the results easy to understand through a simple dashboard.

At the time, I was more interested in learning how APIs, backend services, command-line tools, and frontend interfaces could work together than building something production-ready.

## Vulnerability Analysis Flow

The overall process looked something like this:

1. Enter a target website
2. Detect technologies being used
3. Extract version information where possible
4. Compare versions against known vulnerabilities
5. Display the findings through a dashboard

The results were presented visually so that vulnerable components could be identified quickly.

If a vulnerable version was detected, the dashboard would highlight it and provide related exploit references. If no known public vulnerabilities were found, the component would simply be marked as safe based on the available intelligence.

< Insert Screenshot > Version Detection & Vulnerability Scanner >

## Results

One of the more interesting parts of building Secure Scope was testing it against different websites and seeing how often outdated software appeared in the wild.

Some sites were fully up to date and produced clean results.

< InsertScreenshot > SafeWebsiteResult >

Others exposed older versions of frameworks or CMS platforms that had publicly documented security issues.

< InsertScreenshot > UnsafeWebsiteResult >

In cases where public exploit information existed, Secure Scope could also surface matching entries from Exploit-DB through `searchsploit`.

< InsertScreenshot > ExploitDBResult >

## Looking Back

Today, the implementation feels pretty basic compared to the projects I work on now.

But Secure Scope taught me a lot.

It was one of the first projects where I moved beyond simply reading about vulnerabilities and started building tooling around them. Through this project, I learned about technology fingerprinting, version detection, vulnerability correlation, exploit intelligence, API integration, and basic security automation.

What started as a college-side project ended up pushing me deeper into security research, tooling development, and eventually vulnerability management itself.

And honestly, that's probably why I still remember this project years later.
