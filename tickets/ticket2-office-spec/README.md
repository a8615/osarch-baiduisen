# Ticket 2 — Office hardware specification

## 1. What was asked
Quote from Director: "We are opening the second office and need four computers - accountant, sales, web developer, designer. Budget 3,000,000 tenge for everything. Everyone says we should just buy the same four machines, is that right? Make sure they last a few years. Monitors included."

## 2. What was actually needed
The Director assumed we should buy four identical machines "to keep it simple." This assumption is wrong. 
Different roles have completely different workloads. Buying identical machines means overpaying for components some people don't use (e.g., a GPU for an accountant) and under-powering those who need it (e.g., RAM for a sales manager). 
What the request left out is the specific daily load: a sales manager running 40 Chrome tabs will crash on 8GB RAM. If I could ask the requester, I would ask: "What exact software and file sizes does the designer use?" Instead, I assumed standard heavy loads for those roles and allocated the budget dynamically.

## 3. What I did
I designed four custom builds tailored to specific bottlenecks within the 3,000,000 KZT budget (including monitors and licensed Windows 11). All prices were researched on Kaspi.kz on 2026-11-14.
*   Accountant: Focus on single-core speed for Excel. (Intel i5, 16GB RAM, no GPU).
*   Sales: Focus on massive RAM for browser tabs and video calls. (Intel i5, 32GB RAM).
*   Developer: Focus on multi-core performance and memory for builds. (B760M Motherboard, 32GB RAM).
*   Designer: Focus on GPU rendering and color accuracy. (RTX 3060, 27" 2K Monitor).

## 4. Evidence
*   budget.csv contains the exact components, models, prices in KZT, vendor URLs, and the date (2026-11-14).
*   vendor-quotes/ contains actual screenshots from Kaspi.kz proving these prices are real for the Kazakhstan market.
*   pcpartpicker-links.md contains links verifying component compatibility.

## 5. What I would do differently
If I had more time or budget, I would negotiate directly with local vendors to buy all four machines in bulk to secure a corporate discount. Also, I wish I could have asked the sales manager to track their exact RAM usage for a week before buying, rather than assuming 32GB is enough based on the 30-40 tabs estimate. If the budget allowed, I would immediately upgrade the designer's RAM from 16GB to 32GB to prevent future swapping.
If I had more time or budget, I would negotiate directly with local vendors to buy all four machines in bulk to secure a corporate discount. Also, I wish I could have asked the sales manager to track their exact RAM usage for a week before buying, rather than assuming 32GB is enough based on the 30-40 tabs estimate. If the budget allowed, I would immediately upgrade the designer's RAM from 16GB to 32GB to prevent future swapping.
