---
layout: post
author: M0hmedGamal (gem0x00)
categories: [CTF, Web]
tags: [CTF-Solutions] 

---
# Boxbin 
Hey! How are you?

Lately, I’ve been really obsessed with CTFs, so I was searching through archived competitions and came across one called Snake CTF. It looked great, so I downloaded the challenges, hosted them locally on my machine, and started hacking away.

Alright—let’s dive in!

When I first explored the website, it looked like this:

I started using the website and it looked like that :
<img width="1258" height="774" alt="image" src="https://github.com/user-attachments/assets/ad151750-4058-4213-acb7-10fd1a201656" />

<img width="1172" height="681" alt="image" src="https://github.com/user-attachments/assets/6aa41111-51d8-40df-ae2e-897a8d9d3497" />

The website has different user roles—regular users, admins, moderators, and possibly others.

What caught my eye right away was that the site uses GraphQL, so I knew I’d want to analyze it closely. But before diving into that, I decided to look for the flag in the source code first—just to get a sense of what my actual goal should be in this CTF.

I found the flag inside the seed.mjs file (part of the challenge’s provided files). It’s hidden inside a post that’s marked as “hidden.”

So, here’s the plan:
<img width="608" height="190" alt="image" src="https://github.com/user-attachments/assets/8d344f09-5963-4fce-8b1e-f6aa51dcff04" />

First, I registered a new user and checked what information GraphQL would reveal.
To explore the schema, I ran an introspection query using INQL in Burp Suite:
<img width="688" height="650" alt="image" src="https://github.com/user-attachments/assets/b006130a-9a88-43e3-9f61-2849df21b524" />

I discovered several interesting mutations and queries, including these notable mutations:

- adminUserUpgrade
- hidePosts
- purchaseUpgrade
- updateSettings

While navigating the website, I also noticed something important: the `/settings` endpoint isn’t accessible to regular users—only privileged roles (like admins or moderators) seem to have access to it.
<img width="951" height="319" alt="image" src="https://github.com/user-attachments/assets/32e665ac-43b8-4d29-a417-91c51e8caf0f" />

So, it’s clear: I need to become an admin to access the restricted functionality.
But the question is—how can I escalate my privileges and gain admin access?

<img width="1121" height="533" alt="image" src="https://github.com/user-attachments/assets/47c0cdd2-b335-4bc2-973a-07788566461f" />

My goal is to set "isAdmin": true in a request—but how?
Before diving into privilege escalation, though, let’s check if there’s a shortcut to the flag: the hidden posts.
<img width="1115" height="599" alt="image" src="https://github.com/user-attachments/assets/dde06517-8649-4619-a011-4e4c33c9a515" />
Didn't work so let's see the adminUserUpgrade :
<img width="1165" height="556" alt="image" src="https://github.com/user-attachments/assets/7e547f4f-2ff5-4d9b-9634-d4dea553c921" />
It is done!
let's see the `/settings` endpoint 
<img width="860" height="521" alt="image" src="https://github.com/user-attachments/assets/7df31fd3-3b59-431c-a7a2-6024190bb0f7" />
It worked so let's see the request :
<img width="1090" height="406" alt="image" src="https://github.com/user-attachments/assets/4f97c164-dc37-4c6f-89a2-41240e7b6775" />
What if we added "isAdmin": true
<img width="1137" height="401" alt="image" src="https://github.com/user-attachments/assets/9b6fe514-ddcd-40d8-9e9a-ea22c6d24bfb" />
updated so navigate the website :
<img width="1266" height="866" alt="image" src="https://github.com/user-attachments/assets/2722d9fb-5e20-42a0-9038-fb2d9a8f759e" />
let's see the hidden posts :
And I found the flag in the `/upload/0a089636-6dbe-4c9c-9ea2-68bce2352d8e` endpoint.

<img width="1035" height="357" alt="image" src="https://github.com/user-attachments/assets/8c2ed0d0-d053-4db3-b60d-bed84455d193" />
After retrieving the flag, I did some further investigation. I created a new account with no privileges and realized that—surprisingly—I could become an admin without going through all those steps. In fact, it was as simple as:
<img width="1146" height="403" alt="image" src="https://github.com/user-attachments/assets/9c1d31c4-3517-4ddd-b085-fcfe03a1567a" />
I tried it with the new user—and just like that, the challenge was solved effortlessly.
Turns out, this was a much simpler alternative approach.
