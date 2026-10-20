# Week 1 Reflection — Marc Louis-Charles

## 1. Topics I Chose

I chose **UX Design, Accessibility, and Security** because I think all three are important when building software that people and businesses can rely on.

UX is about making sure the application is easy to use and makes sense to the person using it. Accessibility is important because everyone should be able to use the software, including people with disabilities. Security was another priority because businesses need to know their systems and customer information are protected.

I wanted to focus on areas that would help me build better applications, not just applications that work.

## 2. What Makes a Good Skill Document

One thing I learned this week is that a good skill document needs to be clear and specific. It's not enough to give Claude a bunch of information. You have to explain when the skill should be used and what steps it should follow.

I found that having a checklist makes the skill more useful because it gives Claude something practical to follow. I also wanted the skills to be based on actual industry standards rather than just general recommendations.

## 3. How I Approached It

I started by setting up my development environment. I installed Git, cloned my GitHub repository, and got everything organized so I could work on the project from different computers.

From there, I spent time learning how Claude skills work and how to structure the files properly. Once I had a better understanding, I created three skills focused on UX, Accessibility, and Security.

I used standards like WCAG 2.2 Level AA, the OWASP Top 10:2025, and Nielsen's usability heuristics to guide the content. I also created a `CLAUDE.md` file to help make sure Claude applies these skills during development.

After everything was set up, I pushed my changes to GitHub and moved on to testing.

## 4. How I Ensured Quality

I wanted to make sure the skills actually worked instead of just assuming they would.

I tested them using a fresh Claude agent and a login form that had several intentional problems. The goal was to see whether Claude would recognize issues related to security, accessibility, and UX.

The first test didn't go as planned. Claude wasn't automatically loading the skills because of how I had organized the folders. I had to figure out what was causing the issue, make changes to the folder structure, and test everything again.

The second test worked. Claude loaded all three skills and identified problems with the login form, including security vulnerabilities and accessibility issues.

**My biggest takeaway from this week** is that writing instructions for an AI agent is only part of the process. You also have to test them and make sure they're working the way you intended. I learned quite a bit from troubleshooting the first failed test, and it gave me a better understanding of how Claude skills work.

I'm looking forward to building on what I learned as I continue through the residency.
