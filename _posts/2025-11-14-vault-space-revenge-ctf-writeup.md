---
layout: post
author: M0hmedGamal (gem0x00)
categories: [CTF, Web]
tags: [CTF-Solutions] 
---
# Vault Space Revenge

At first I Search for the flag where can I find it so I can put a plan to arrive to it So let's see the target:\\

<figure><img src="https://1287051708-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaS4i8I28DZfShW081NU8%2Fuploads%2F0dOOchD0ZOVNzvy0XWLz%2Fimage.png?alt=media&#x26;token=b0e9ad97-e6de-48f1-905d-371afed8031d" alt=""><figcaption></figcaption></figure>

So , the flag is in the dashboard in the admin account.

So Think about it and search in the source code :

There is an `api_handler.php` endpoint this endpoint take the param and action inputs :\\

<figure><img src="https://1287051708-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaS4i8I28DZfShW081NU8%2Fuploads%2FPiN59imWWJ7jznJtcjcA%2Fimage.png?alt=media&#x26;token=e29c9198-cfde-477f-9101-e20c800bc595" alt=""><figcaption></figcaption></figure>

Okay I tried to look in the `functions.php` to see what can I do :\\

<figure><img src="https://1287051708-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaS4i8I28DZfShW081NU8%2Fuploads%2FE1vhUgNC1MQJL0b3z7Tr%2Fimage.png?alt=media&#x26;token=11e3b8ed-d553-4e19-87e4-ac8563b6b2e2" alt=""><figcaption></figcaption></figure>

I found the function named `check_user_credentials` and thought can I use it to get the password of the admin account but How can I get the username of the admin account so went to see the forgot password functionality to see  what is the username of the admin account when I tried the admin it let me to input the 4 digit number when I typed any other name it tells me this is not a registered user so the username of the admin account is admin So , I will use this function to get the admin account password.

<figure><img src="https://1287051708-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaS4i8I28DZfShW081NU8%2Fuploads%2FQFOlm4OfCwXRq33pbMsZ%2Fimage.png?alt=media&#x26;token=c762a6a9-4037-4495-9fa0-b67acac46bbb" alt=""><figcaption></figcaption></figure>

&#x20;When I tried at the first time I got this but when I Just tried test as a password I got that :

<figure><img src="https://1287051708-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaS4i8I28DZfShW081NU8%2Fuploads%2FuhLZjnJ7fh20BAkleTfs%2Fimage.png?alt=media&#x26;token=ae18f2ef-fcac-4e13-a9c7-3c1f45ea9bb3" alt=""><figcaption></figcaption></figure>

It was a strange behaviour for me so I decided to test it for the admin account credentials :

<figure><img src="https://1287051708-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FaS4i8I28DZfShW081NU8%2Fuploads%2FiEFWNJiqKAqImjYraII7%2Fimage.png?alt=media&#x26;token=62e8fe24-17ba-4970-a2bf-da6d3249daff" alt=""><figcaption></figcaption></figure>

It worked and I got the flag ...

