---
sidebar_position: 1
---

# Introduction


## What is Schedify?
Schedify is like an alarm clock for servers. Set a task, pick a time, and we’ll send a webhook notification to your server exactly when needed!

## Use case

#### ⏳ Order Expiry (E-commerce & Food Delivery)
If an order isn’t paid or confirmed in time, it should expire automatically. Instead of manually tracking this, Schedify handles it!

🔹 Example:

- A customer places an order but doesn’t pay.
- You schedule a 15-minute task in Schedify.
- If unpaid, Schedify sends a webhook to your app to expire the order.

✅ No manual tracking—just automatic order handling!

#### 🏦 Subscription Renewals & Reminders
Need to remind users before their subscription renews? Schedify makes it easy!

🔹 Example:

- A user's subscription is about to end in 3 days.
- You schedule a task with Schedify to send a reminder.
- At the exact time, Schedify triggers a webhook to notify your app.
- Your app emails or messages the user.

✅ No missed reminders, no extra effort!

#### 🎟 Event Notifications
Want to send reminders for upcoming events, webinars, or appointments? Let Schedify handle it.

🔹 Example:

- A webinar starts at 5 PM tomorrow.
- You schedule a task with Schedify to notify users 1 hour before.
- Schedify sends a webhook, and your app sends a notification.

✅ Keep users engaged without manual scheduling!

#### 🚀 Delayed Workflows & Automated Actions
Need to delay an action in your system? Use Schedify instead of building complex delay logic.

🔹 Example:

- A new user signs up but doesn’t complete their profile.
- You schedule a 24-hour follow-up task with Schedify.
- If they haven’t updated their profile, Schedify triggers a webhook to remind them.

✅ Perfect for onboarding, follow-ups, and more!

## Features


| **Feature**                   | **Description**                                            |
|--------------------------------|------------------------------------------------------------|
| 📝 Custom JSON Payload & Scheduling | Define the exact payload and schedule for each webhook execution. |
| 🔒 Webhook Authentication      | Webhooks are secure with HMAC signature.                  |
| 🔗 Flexible API Integration    | Simple REST API for seamless integration with your application. |
