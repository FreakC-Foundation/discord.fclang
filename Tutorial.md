Before reading the tutorial, please check out the original [discord.bat](https://github.com/mininmobile/discord.bat)

## Step 1: Install and setup
Clone this repo and create a file called `init.fclang`.

## Step 2: Start coding
Open the file you've created, then type in this code:

	function[] config
		:: Bot's configuration goes here
	endfunc[]

	function[] commands
		:: Bot's commands' processing goes here
	endfunc[]

## Step 3: Config
Have a look at the `config` function, it will holds all the bot's infos, somewhat like this:

	function[] config
		var[] bot.token=Bot's token goes here
		var[] bot.prefix=Prefix goes here
	endfunc[]

We need to create 2 variables, which are `bot.token` for holding your bot's token and `bot.prefix` to define the bot's prefix

## Step 4: Commands
It would suck if your bot can't do anything, so let's create a command inside the `commands` function.

Now, let's create a simple **ping pong** bot:

	function[] commands
		if[] %1 NEQ "" call[] :%~1 2>nul
		quit[] /b

		label[] ping
		call[] s.bat sendMessage "pong"
		goto[] :eof
	endfunc[]

Now, don't smash the screen, I'll explain how the codes work.

The first line is just an if statement to check if the first parameter, which is the command itself is empty or not. If it's not empty, then goto the label `ping`. After that, we will just call `s.bat` and pass in two arguments: `sendMessage` and `pong`. `sendMessage` basically informs that the bot wants to send a message, and the message is `pong`. `goto[] :eof` basically exits the function safely.

You can also DM the author of the message by simply using:

	call[] s.bat dmAuthor "message goes here"

## Step 5: Boot up the bot
Open cmd/powershell or your trusty command prompt variations and type this in:

	freakc BuildBot

It basically compiles BuildBot and open the bot.

That's it (I don't know all the things from [discord.bat](https://github.com/mininmobile/discord.bat), so probably check it out to know more informations).

## Get message
If you want to collect the messages, then in `config`, add `var[] events.message.notification=true`

## Example
There's already a `init.fclang` file which comes with the repo, so you can compile `BuildBot.fclang` and try the bot now!