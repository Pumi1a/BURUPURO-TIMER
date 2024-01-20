[日本語版 README はこちら](https://github.com/Pumi1a/BURUPURO-TIMER/blob/main/README-ja.md)
# BURUPURO-TIMER

## Introduction
I have created a Discord Bot that notifies you of the day and night switch timings in BLUE PROTOCOL (hereinafter, "BURUPURO"). If you play BURUPURO, you'll understand why I wanted to create this. In BURUPURO, there are Named Bosses that spawn only during the day or night. And the day and night change every 25 minutes. However, when you are on a mission or exploring freely, it's hard to know whether it's day or night. Also, I think there are some people (like myself) who would be working on other tasks and then launch BURUPURO for a Named Boss that spawns at night. For this reason, I have created a bot that notifies you of the day and night switch timings.

## Points to note
For feature improvement requests or bug reports, please use the /send_message_to_developer command. I generally don't check X (former Twitter) so I won't notice messages there. I have tried to verify under various conditions, but as I am a beginner in Python, there may be bugs. I apologize for any inconvenience.Bugs that I am aware of at this point are described towards the end. If it doesn't work properly, try resetting by executing the `/reset_server` command.

The hosting service used is "Railway". It has a memory of 8GB and a CPU of 8 cores. I don't think it's a particularly demanding bot, but it might become unstable. Please refer to [this](https://qiita.com/Pumila/items/29f26fb349d5592046ae) for information about "Railway".

## Installation method
**Note: Only those with server admin rights can install the Bot.**

Please click [here](https://discord.com/api/oauth2/authorize?client_id=1127823303369834578&permissions=3072&scope=bot%20applications.commands), log in, select the server you want to install on, click [Yes], and then press Authenticate. Complete the installation by checking the robot confirmation screen.If you no longer need it, I would appreciate it if you could ban it to reduce the server load.

## How to use
**Note: Although the server information is updated every 5 minutes, depending on the timing of the slash command execution, the bot may not behave as expected.** For instance, you might get notifications to the default destination even after you have changed the notification channel, or you may get notifications even after you have turned them off. Please understand that these are issues due to the program's specifications.

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

#### Starting Notifications
You can set whether to notify the timing of day and night. The default value is `False`.

1. Type "/" and click on the Blue Pro Timer icon, then select `/set_posting` from the command list.
2. You will have the options [True, False]. Choose `True` if you want to enable notifications, and `False` if you want to stop them.
3. You will receive a message from the bot saying `Set posting to {new_value}.`

![screenshot2024-01-19 08.42.49.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/33d04e75-3f90-bf2b-2da4-863fd5fbfb36.png)

#### Choose to Notify Either Day or Night, or Both
There may be people who only want to be notified during the day or night (for example, if you have a named event only at night, you only need to be notified at night). Therefore, you can choose to notify both day and night, or just one. The default setting is to notify both.
1. Type "/" and click on the Blue Pro Timer icon, then select `/set_state` from the command list.
2. You will have the options [Day, Night, Both]. If you only want to be notified at night, select `Night`, if you only want to be notified during the day, select `Day`. If you decide you want to be notified both times, select `Both`.
3. You will receive a message from the bot saying `State set to: {state}.`

![4.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/ddcd4da3-2486-7e55-2cad-58b22a1ac6ce.png)

#### Changing the Timing of Notifications to Minutes Before Day/Night Transition
Even if you are notified exactly at day or night, you may not have time to launch the game and take down the named. So, you can change the notification method to "It will be Day/Night in X minutes". The default value is 0.

1. Type "/" and click on the Blue Pro Timer icon, then select `/notify_in_advance` from the command list.
2. Next, enter in minutes how far in advance you want to be notified and execute the command.
3. You will receive a message from the bot saying `Will now notify {minutes_before} minutes in advance.`

![5.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/b6d3089b-17d2-da45-29e8-a064da134e43.png)

#### Posting Notifications at Both Day/Night Time and Minutes Before
When you set to notify minutes before day/night in the previous item, you can also post notifications at the time of day/night change. The default value is False.

1. Type "/" and click on the BlurPro Timer icon, then select /set_dual_notification from the list of commands.
2. You should see options like [True, False]. Choose True if you want notifications for both, and False if you don’t.
3. A message from the Bot will appear saying Set dual_notification to {new_value}.

#### Notifying Raid Times
You can notify when a raid is happening. The default value is False.

1. Type "/" and click on the BlurPro Timer icon, then select /set_raid_posting from the list of commands.
2. You should see options like [True, False]. Choose True to enable notifications and False to stop them.
3. A message from the Bot will appear saying Set raid_posting to {new_value}.

#### Changing the Timing of Raid Notifications to Minutes Before
You can change the method of raid notification to “raid starts in X minutes.” The default value is 0.

1. Type "/" and click on the BlurPro Timer icon, then select /notify_in_advance_for_raid from the list of commands.
2. Enter how many minutes in advance you want to be notified and execute.
3. A message from the Bot will appear saying Will now notify {minutes_before} minutes in advance for raid.

#### Deleting Regular Posts
You can backtrack and delete the Bot's day/night notifications.

1. Type "/" and click on the BlurPro Timer icon, then select /clear_posts from the list of commands and execute.
2. Enter how far back you want to delete and execute. The limit is 500, but please enter a smaller number to avoid API limitations.
3. A message from the Bot will appear saying Deleting bot's periodic posts...
4. Once the deletion is complete, the Bot will send a message Deleted {deleted_count} bot's periodic posts. depending on the number of posts deleted.
5. Messages from items 3 and 4 will be automatically deleted.

#### Displaying Server Settings
You can display the current settings of the server.

1. Type "/" and click on the BlurPro Timer icon, then select /check_config from the list of commands and execute.
2. A message like the following will come from the Bot.

#### Reporting Feature Improvements or Bugs to the Developer
You can report feature improvement requests or bugs to me. I don’t usually check X (former Twitter), so using this method is appreciated. Of course, if there's a high number of prank uses, usage restriction penalties will be applied to the Bot.

1. Type "/" and click on the BlurPro Timer icon, then select /send_message_to_develope from the list of commands and execute.
2. Enter the content you want to report and execute.
3. A message from the Bot will appear saying Message sent to the bot's developer.

#### Resetting to Default Settings
You can reset various settings back to their defaults. Please try using this when you're having trouble posting.

1. Enter "/", click on the Blue Pro Timer icon, and from the command list, select and execute `/reset_server`.
2. You will receive a message from the Bot saying `Server configuration has been reset. Default post channel set to {channel.name}.`

![キャプチャ.PNG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1115291/53e9d72e-0ac3-9a23-ccf0-4996e17a3f02.png)

## Known bugs at present

## Features planned for implementation at the current stage

## Finally
BURUPURO is so much fun!!! But Orochi's "Stream of Life" hardly ever appears (damn it!!!). I carefully selected 11 Orochi... For that, I set a timer every 50 minutes while doing other tasks, but I thought it could be automated with a bot, so I created one. Please give it a try.

To help cover the server maintenance costs, any donations from those who enjoy this bot would be greatly appreciated.

[Amazon Gift Card Recipient: yskl6695@gmail.com]

https://www.amazon.co.jp/dp/B004N3APGO

[PayPal]

https://www.paypal.com/paypalme/IrsPumila

Please send your opinions, impressions, requests, error reports, etc., to my [Twitter](https://twitter.com/Pumi1a).
