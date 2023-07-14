# BURUPURO-TIMER

## Introduction
I have created a Discord Bot that notifies you of the day and night switch timings in BLUE PROTOCOL (hereinafter, "BURUPURO"). If you play BURUPURO, you'll understand why I wanted to create this. In BURUPURO, there are Named Bosses that spawn only during the day or night. And the day and night change every 25 minutes. However, when you are on a mission or exploring freely, it's hard to know whether it's day or night. Also, I think there are some people (like myself) who would be working on other tasks and then launch BURUPURO for a Named Boss that spawns at night. For this reason, I have created a bot that notifies you of the day and night switch timings.

## Points to note
If there are any errors or strange behaviors, please notify the developer via [Twitter](https://twitter.com/Pumi1a). The hosting service used is "Railway". It has a memory of 8GB and a CPU of 8 cores. I don't think it's a particularly demanding bot, but it might become unstable. More information about "Railway" is summarized in the following article:

https://qiita.com/Pumila/items/29f26fb349d5592046ae

## Installation method
**Note: Only those with server admin rights can install the Bot.**
Please click [here](), log in, select the server you want to install on, click [Yes], and then press Authenticate. Complete the installation by checking the robot confirmation screen.If you no longer need it, I would appreciate it if you could ban it to reduce the server load.

## How to use
**Note: Although the server information is updated every 5 minutes, depending on the timing of the slash command execution, the bot may not behave as expected.** For instance, you might get notifications to the default destination even after you have changed the notification channel, or you may get notifications even after you have turned them off. Please understand that these are issues due to the program's specifications.
**Furthermore, the bot will not post anything if the base time is not set.**

### Description of Each Slash Command
Here we will explain each slash command of the bot.

#### Changing the Notification Channel
You can change the channel to which notifications are sent. By default, it is set to the system message channel. To save the trouble of setting up a database, channels are managed by their ID. To get the channel ID, go to [User Settings], select [Advanced Settings], and check Developer Mode.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_channel` from the command list.
2. Right-click on the channel where you want to send the notifications, select [Copy Channel ID] at the bottom, paste it, and execute the command.
3. You will receive a message from the bot saying `Set channel to {new_channel_id}.`

![1.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/8ab601e4-d986-7b5f-b298-29acbef7e80c.png)

#### Setting the Base Time

You can set the timing for the day-night switch. Since each server may have different switch timings, or they may shift due to maintenance, it is not set automatically. The user is required to enter the timing of the day-night switch. It is fine to enter a time in the past.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_day_base_time` or `/set_night_base_time` from the command list. With `set_day_base_time`, you can set the timing when it becomes daytime, and it will also set the nighttime for you. On the other hand, `set_night_base_time` allows you to set the timing when it becomes nighttime, and it will also set the daytime for you.
2. Select the command that suits you, enter the time, and execute the command.
3. You will receive a message from the bot saying `Day base time set to: {hour}:{minute}. The night base time is set to: {hour}:{minute}.`

<img width=300 src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/4f06aa25-460a-ab9b-57ae-0737c6dc347c.png"><img width=300 src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/19d8706b-3d62-82a5-fb77-f165967f85b8.png">

#### Choose to Notify Either Day or Night, or Both
There may be people who only want to be notified during the day or night (for example, if you have a named event only at night, you only need to be notified at night). Therefore, you can choose to notify both day and night, or just one. The default setting is to notify both.
1. Type "/" and click on the Blue Pro Timer icon, then select `/set_state` from the command list.
2. You will have the options [Day, Night, Both]. If you only want to be notified at night, select `Night`, if you only want to be notified during the day, select `Day`. If you decide you want to be notified both times, select `Both`.
3. You will receive a message from the bot saying `State set to: {state}.`

![4.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ddcd4da3-2486-7e55-2cad-58b22a1ac6ce.png)

#### Changing the Notification Timing to "It will be Day/Night in X Minutes"
Even if you are notified exactly at day or night, you may not have time to launch the game and take down the named. So, you can change the notification method to "It will be Day/Night in X minutes". The default value is 0.

1. Type "/" and click on the Blue Pro Timer icon, then select `/notify_in_advance` from the command list.
2. Next, enter in minutes how far in advance you want to be notified and execute the command.
3. You will receive a message from the bot saying `Will now notify {minutes_before} minutes in advance.`

![5.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/b6d3089b-17d2-da45-29e8-a064da134e43.png)

#### Choose to Always Notify
You can set whether or not to always notify the day/night timing. The default value is `True`.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_persistent_posting` from the command list.
2. You will have the options [True, False]. If you don't want to be notified all the time, select `False`.
3. You will receive a message from the bot saying `Set persistent_posting to {new_value}.`

![6.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ee389fe1-6d6e-bb89-a848-eedc968c8ff2.png)

#### Choose to Temporarily Notify
You can set whether to temporarily notify the day/night timing. The default value is `False`.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_temporary_posting` from the command list.
2. You will have the options [True, False]. If you want to be notified temporarily, select `True`, if you no longer need to be notified, select `False`.
3. You will receive a message from the bot saying `Set temporary_posting to {new_value}.`

![7.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/d849bba8-72d0-b2d9-7097-5b46116d6eb0.png)

This function is covered by `/set_persistent_posting`, but I created it just in case. You can use either one.

## Finally
BURUPURO is so much fun!!! But Orochi's "Stream of Life" hardly ever appears (damn it!!!). I carefully selected 11 Orochi... For that, I set a timer every 50 minutes while doing other tasks, but I thought it could be automated with a bot, so I created one. Please give it a try.

To help cover the server maintenance costs, any donations from those who enjoy this bot would be greatly appreciated.

[Amazon Gift Card Recipient: yskl6695@gmail.com]

https://www.amazon.co.jp/dp/B004N3APGO

[PayPal]
Coming soon

Please send your opinions, impressions, requests, error reports, etc., to my [Twitter](https://twitter.com/Pumi1a).
