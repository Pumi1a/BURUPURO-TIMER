[日本語版 README はこちら](https://github.com/Pumi1a/BURUPURO-TIMER/blob/main/README.md)
# BURUPURO-TIMER

## Introduction
I have created a Discord Bot that notifies you of the day and night switch timings in BLUE PROTOCOL (hereinafter, "BURUPURO"). If you play BURUPURO, you'll understand why I wanted to create this. In BURUPURO, there are Named Bosses that spawn only during the day or night. And the day and night change every 25 minutes. However, when you are on a mission or exploring freely, it's hard to know whether it's day or night. Also, I think there are some people (like myself) who would be working on other tasks and then launch BURUPURO for a Named Boss that spawns at night. For this reason, I have created a bot that notifies you of the day and night switch timings.

## Points to note
Please report any errors to the developer via [Twitter](https://twitter.com/Pumi1a) or [github](https://github.com/Pumi1a/BURUPURO-TIMER). I have tried to verify under various conditions, but as I am a beginner in Python, there may be bugs. I apologize for any inconvenience.Bugs that I am aware of at this point are described towards the end. If it doesn't work properly, try resetting by executing the `/reset_server` command.

The hosting service used is "Railway". It has a memory of 8GB and a CPU of 8 cores. I don't think it's a particularly demanding bot, but it might become unstable. Please refer to [this](https://qiita.com/Pumila/items/29f26fb349d5592046ae) for information about "Railway".

## Installation method
**Note: Only those with server admin rights can install the Bot.**

Please click [here](https://discord.com/api/oauth2/authorize?client_id=1127823303369834578&permissions=3072&scope=bot%20applications.commands), log in, select the server you want to install on, click [Yes], and then press Authenticate. Complete the installation by checking the robot confirmation screen.If you no longer need it, I would appreciate it if you could ban it to reduce the server load.

## How to use
**Note: Although the server information is updated every 5 minutes, depending on the timing of the slash command execution, the bot may not behave as expected.** For instance, you might get notifications to the default destination even after you have changed the notification channel, or you may get notifications even after you have turned them off. Please understand that these are issues due to the program's specifications.

**Furthermore, the bot will not post anything if the base time is not set.**

**When redeploying the Bot, I ask that you please reset the configuration. Because preparing the database is cumbersome, I do not save the settings for each server in the database. Please understand（If there are many requests, I will consider introducing a database.）.**

### Description of Each Slash Command
Here I will explain each slash command of the bot.Please try the slash command again if you encounter the following error when executing it.

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ad29da08-18cc-0377-f841-a0c0b9fa2655.png)

#### Changing the Notification Channel
You can change the channel to which notifications are sent. By default, it is set to the system message channel.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_channel` from the command list.
2. Enter the name of the channel you want notifications to go to, and execute the command.
3. If you choose a channel where the bot does not have permission to post or a channel that is not a text channel, you will receive a warning like this: Warning: `No permission to post in the channel {new_channel.name}.`, `{new_channel.name} is not a text channel.`.
4. You will receive a message from the Bot saying `Set channel to {new_channel_name}.`.

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/935ca7eb-0d9e-f222-600e-b67538ad1402.png)

#### Setting the Base Time

You can set the timing for the day-night switch. Since each server may have different switch timings, or they may shift due to maintenance, it is not set automatically. The user is required to enter the timing of the day-night switch. There is no problem whether the time you input is in the past or the future.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_day_base_time` or `/set_night_base_time` from the command list. With `set_day_base_time`, you can set the timing when it becomes daytime, and it will also set the nighttime for you. On the other hand, `set_night_base_time` allows you to set the timing when it becomes nighttime, and it will also set the daytime for you.
2. Select the command that suits you, enter the time, and execute the command.
3. You will receive a message from the bot saying `Day base time set to: {hour}:{minute}. Night base time set to: {hour}:{minute}.`

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

#### Resetting to Default Settings
You can reset various settings back to their defaults. Please try using this when you're having trouble posting.

1. Enter "/", click on the Blue Pro Timer icon, and from the command list, select and execute `/reset_server`.
2. You will receive a message from the Bot saying `Server configuration has been reset. Default post channel set to {channel.name}.`

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/53e9d72e-0ac3-9a23-ccf0-4996e17a3f02.png)

## Known bugs at present
I am posting at 25-minute intervals, but it seems that after a day passes, the timing of the day-night switch shifts by a few minutes. This could be due to the day-night switch not being exactly 25 minutes, or due to the server's time shifting due to maintenance or other circumstances. I will investigate this issue, but it would be helpful if you could provide me with any information.


## Features planned for implementation at the current stage
* A feature to prepare a database, eliminating the need to reconfigure every time you redeploy.

## Finally
BURUPURO is so much fun!!! But Orochi's "Stream of Life" hardly ever appears (damn it!!!). I carefully selected 11 Orochi... For that, I set a timer every 50 minutes while doing other tasks, but I thought it could be automated with a bot, so I created one. Please give it a try.

To help cover the server maintenance costs, any donations from those who enjoy this bot would be greatly appreciated.

[Amazon Gift Card Recipient: yskl6695@gmail.com]

https://www.amazon.co.jp/dp/B004N3APGO

[PayPal]

https://www.paypal.com/paypalme/IrsPumila

Please send your opinions, impressions, requests, error reports, etc., to my [Twitter](https://twitter.com/Pumi1a).
