### If you're looking for AnthemInsider's Anthem Countdown bot, then you have come to the right place!

First of all - the bot has two major launch modes:
- Flag defined behaviour
- Interactive setup

If you're unsure about how to use the flags to set up the bot, or if you simply need a bit of help while setting up the bot the first time, you can launch it using `java -jar timer_bot.jar --interactive` (or -i for short), which will launch the bot in an interactive setup mode. The bot will guide you through the setup step by step, asking you for every setting it needs along the way. Once you finish the setup, it will also generate a run command for you, that you can use to launch the bot with the settings you defined during this process!

If you don't need the interactive setup, feel free to read the parts below and figure out how to do it on your own :P

--------

# Flags:
- --help [flags] | -h [flags]
  * Shows the help screen for the specified flags. If [flags] is empty, the entire help screen will be shown.
- --token \<token\>
  * Defines the bot-token that discord needs for the bot to log in. You get this from your [discord developer portal](https://discordapp.com/developers/applications/).
  * Mutually exclusive with `token_env`
  * Default: N/A
- --token_env
  * Tells the bot that the token is in an environmental variable called `token`
  * Mutually exclusive with `token_env`
  * Default: N/A
- --file <path> | -f <path>
  * Used to redefine where the bot will save its data. The files inside the folder will be `messages.dat` and `channels.dat`. Make sure the bot has rw- permissions for the files in question!
  * Default: `./settings/`
- --refresh <time> | -r <time>
  * Used to redefine the refresh interval of the bot in seconds. Faster intervals will mean the message will stay up to date faster, but every time the bot edits the message it will flicker a bit.
  * Default: 30 seconds.
- --messages <amount> | -m <amount>
  * Used to define a message-requirement before non-whitelisted people can run the countdown command again.
  * Default: 100 messages
- --style [VDER] | -s [VDER]
  * Used to tell the bot what the timer message should look like. The bot will add the corresponding countdown in the order specified in the flag. It will add countdowns multiple times if they are in the flag multiple times! 
    - (V)IP Demo 
    - Open (D)emo 
    - (E)arly Access 
    - (R)elease 
  * Default: VDR
- --interactive | -i
  * Launches the bot in interactive mode, as described above.
  * **Mutually exclusive with all other flags!**
- --whitelist <id>[,id,id,id] | -w <id>[,id,id,id]
  * Allows to define a list of group ids that have override permissions for the bot. Useful if you have a mod/admin group on your discord that you want to give permissions to manage the bot to.
  * The discord server owner is whitelisted by default and cannot be removed from the whitelist.
  * Default: N/A
- --cmd_prefix <prefix> | -c <prefix>
  * Used to define a prefix in front of the `countdown` command. Useful if you have multiple bots interfering with each other!
  * Default: !

-----

# Commands:

- @\<bot\> timer
  * Sets the active channel to the current one
  * No command prefix
  * Resets the message limit counter
  * Ignores message limit (as it's a whitelist only command)
  * Force updates the message and pulls it to the bottom of the channel
  * Whitelist only
  
- !countdown
  * Can only be run in the active channel (see `@<bot> timer` command)
  * Respects the prefix
  * Resets the message limit counter if ran successfully
  * Respects message limit (if user is whitelisted, this limit will be ignored)
  * Force updates the message and pulls it to the bottom of the channel
  * Can be run by anyone
 
