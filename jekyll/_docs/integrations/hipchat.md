---
layout: classic-docs
title: HipChat
categories: [integrations]
description: HipChat
---

This guide will help you automate posting Airbrake errors to
[HipChat](http://www.hipchat.com)! You will need an **auth token** and to pick a
**Room name** that you want to receive Airbrake error notifications in.

## Create a HipChat auth token for Airbrake
First you will need to [create a HipChat V1 API auth token](https://www.hipchat.com/admin/api).
The new token's type should be be `Notification`

![hipchat new token](/docs/assets/img/docs/integrations/hipchat_new_token.png)

## Room Name
You can see your room names in hipchat with this link
[https://www.hipchat.com/rooms/ids](https://www.hipchat.com/rooms/ids).

## Configure the HipChat integration
Fill in the HipChat integration's fields with your **Api auth token** and
**Room name**, then Save. The **Test integration** link is a helpful way to check that your configuration will work when a new Airbrake error occurs.

![hipchat settings](/docs/assets/img/docs/integrations/hipchat_settings.png)
