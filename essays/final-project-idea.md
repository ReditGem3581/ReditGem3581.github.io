---
layout: essay
type: essay
title: "Final Project Idea: Tithr"
date: 2025-11-04
labels:
  - Software Engineering
  - Nextjs
  - Faith-Based App
  - Financial Planning
---

# 🌿 Tithr: A Faith-Based Financial Budgeting App for UH Students

## Overview

### The Problem
Many UH Mānoa students struggle to manage their finances wisely—balancing tuition, part-time work, rent, and social life often leads to anxiety about money. For Christian students, financial management isn’t only practical but *spiritual*—stewardship and tithing are acts of faith and discipline. However, most budgeting tools ignore this perspective, focusing solely on material spending and wealth growth rather than spiritual balance and generosity.

### The Solution
**Tithr** helps UH students honor God through wise, intentional stewardship. It’s a **faith-based budgeting app** that organizes income into categories based on biblical financial principles:
1. **Tithe** (10%) — giving back to God first.
2. **Needs** (50%) — essentials like food, rent, and tuition.
3. **Savings** (20%)— planning for the future.
4. **Wants** (20%)— life’s enjoyments handled responsibly.

All percentages are just example percentages.

Tithr helps users **customize categories and percentages** to reflect their personal convictions, track expenses, and view how faithfully they’ve maintained their priorities. Every time they log in, they’re greeted with a **random Bible verse** reminding them of God’s provision and wisdom in financial stewardship.

---

## Key Features

### Core Functionality
- **User authentication and profiles** (NextAuth.js or Firebase)
- **Customizable budget categories and percentages** (must total 100%)
- **Income logging** that automatically distributes funds to each category
- **Transaction tracking** — purchases automatically reduce from the correct category
- **Transfer between categories** (e.g., move unspent “wants” to “savings”)
- **Monthly summary dashboard** with charts showing spending and giving ratios
- **Randomized daily Bible verse API** (using an open source API like BibleAPI.co or Scripture API)

### “Special Sauce” (Personalization)
Each user’s account includes:
- Their **unique budget configuration**
- Their **income/spending history**
- **Faith metrics** — e.g., how consistently they tithe or save
This makes the app’s experience individualized and spiritually meaningful.

### UI and Visual Design
- Clean **Bootstrap 5 dashboard**
- Soft, minimalist color scheme (greens and neutrals)
- Tabs: *Home (Verse + Balance Overview)*, *Transactions*, *Budget Setup*, *Reports*, *Profile*
- Encouraging verse at the top (“Honor the Lord with your wealth…” — Proverbs 3:9)

---

## Mockup Page Ideas
1. **Login Page** – simple faith-based welcome, logo “Tithr”, Bible verse footer.  
2. **Dashboard** – pie chart (Tithe / Needs / Savings / Wants), balance summary, daily verse.  
3. **Add Income / Transaction** – form with amount, source, and category.  
4. **Customize Categories** – sliders to allocate percentages.  
5. **Reports Page** – charts of monthly giving/spending.  
6. **Profile Settings** – user email, church affiliation (optional), dark/light theme toggle.

---

## Use Case Scenarios
1. *Kaleo, a UH Mānoa student and Inspire Church member,* logs in after payday. He enters his $800 paycheck, and Tithr automatically allocates:
   - $80 to Tithe  
   - $400 to Needs  
   - $160 to Savings  
   - $160 to Wants  
   He sees a verse: *“The generous will prosper; those who refresh others will themselves be refreshed.” (Proverbs 11:25)*  

2. *A week later,* Kaleo logs a $15 Starbucks purchase — Tithr deducts it from “Wants” and updates the pie chart.

3. *At the end of the month,* Kaleo views his report, realizing he saved 20% more than usual and tithed every week.

---

## Beyond the Basics
- **Integration with local UH life:** budgeting presets for “UH Expenses” (books, parking, dining).
- **Encouragement section:** show streaks for consistent tithing or savings goals.
- **Optional community feature:** (future scope) “Church Partners” page linking to UH ministries like Inspire Movement or BCM.
- **AI suggestion feature:** analyze past spending patterns and recommend adjustments (stretch goal).
- **Spiritual focus:** dynamic verse generator and journaling tab for prayer notes about stewardship.

---

## Authors
Written collaboratively by **Adones Morales**, ICS 314 Fall 2025, inspired by personal involvement with Inspire Church and a passion for integrating faith with technology.

---

## Criteria Satisfaction

| Criterion | Fulfillment |
|------------|-------------|
| **Uses Next.js + React + Bootstrap 5** | Fully integrated front end and routing |
| **Hosted on GitHub / Vercel** | Public deployment for evaluation |
| **Individual state** | Personalized finance data + spiritual metrics |
| **Local community focus** | Designed for UH students and the Inspire Church community |
| **Demonstrates full-stack and standards** | Code linting (Airbnb TS), form validation, and dynamic components |
| **Beyond the basics** | API integration, customizable categories, data visualization |
