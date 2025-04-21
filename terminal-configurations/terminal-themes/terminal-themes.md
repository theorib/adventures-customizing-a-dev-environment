# Terminal Themes

Making the terminal visually pleasant and informative is a big thing for me since I am a very visual person.

I have tried a few themes in the past, having used [Powerlevel10k](https://github.com/romkatv/powerlevel10k) for a while with [Oh My ZSH!](https://ohmyz.sh) but I didn't find it  easy to use or customise and found that getting it to work in the first place was quite a hassle.

Enter April 2025 when I discovered [Starship](https://starship.rs)!

## Starship

While [Starship](https://starship.rs) is not strictly limited to *Oh My ZSH!* (you don't even need to use ZSH as a shell) it is actually a pleasure to setup and customize due to its polished developer experience. Much easier than Powerlevel10k.

### Installing Starship

I chose to Install most of my development packages using [Homebrew](https://brew.sh) on my mac. In their own words, Homebrew is *"The Missing Package Manager for macOS (or Linux)"* and I find myself gravitating towards it whenever there is some package that I need to install in my system.

You can find different installation instructions on [Starship's website](https://starship.rs) if you have different needs but this is the quick and easy way on a Mac:

1. Install a [Nerd Font](https://www.nerdfonts.com) in your computer.
    I chose the [GeistMono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.3.0/GeistMono.zip).

2. Setup your Terminal app and VS Code to use a Nerd Font (so they can display all the icons).
...

3. Install Starship using homebrew:
    ```bash
    brew install starship
    ```

4. For ZSH, Add the following lines to the end of your `.zshrc` file. You should find your `.zshrc` file at the root of your current user folder (`~/.zshrc`).
    ```bash
    # Activate Starship
    eval "$(starship init zsh)"
    ```
    
5. Restart your terminal session or `source` your `.zshrc` file to activate the changes.
    ```bash
    source ~/.zshrc
    ```
Voilà, Starship should be up and running.

### Add a Starship Preset

Next up you may want to start with a [Starship preset](https://starship.rs/presets/). I chose [Gruvbox Rainbow Preset](https://starship.rs/presets/gruvbox-rainbow#gruvbox-rainbow-preset) as a starting point.

In your terminal run the following command:
```bash
starship preset gruvbox-rainbow -o ~/.config/starship.toml
```

### Customize your Starship Preset
 Before I started doing this, I added a VS Code extension to [help edit](https://marketplace.visualstudio.com/items/?itemName=tamasfe.even-better-toml) .toml files. You may skip this step as it's not necessary.

 After that, I opened my Starship config file and started making changes following the excellent [docs](https://starship.rs/config/). By default it will be installed in your user folder at `~/.config/starship.toml`.

 There were a few things I wanted to do:
 - I wanted to display the current Python Virtual Environment (venv) if one was active.
 - I wanted the time to be displayed in hours minutes and seconds.
 - I wanted an icon to reflect which Shell environment I was currently in if switching from ZSH to Bash or Fish.

 I achieved all of these following the steps below.

 **Note: you may not be able to preview the icons contained in the code below if you see them on GitHub or most markdown editors.**
You may instead see an empty space or a generic square icon in their place, however, when you copy and paste the code to your Starship configuration file the icons should be copied and work correctly provided you installed and configured a Nerd Font to work with your terminal.

#### Customizing the `[python]` settings to display the current active python Virtual Environment (venv)
This was achieved by adding `( $virtualenv )` next to the `$version` variable in the `format` property.
```toml
[python]
symbol = ""
style = "bg:color_blue"
format = '[[ $symbol( $version ( $virtualenv )) ](fg:color_fg0 bg:color_blue)]($style)'
```

#### Change the `[time]` settings so my terminal clock looks like `17:39:13`
This is achieved by using the `"%T` pattern for the `time_format` property:
```toml
[time]
disabled = false
time_format = "%T"
style = "bg:color_bg1"
format = '[[  $time ](fg:color_fg0 bg:color_bg1)]($style)'
```

#### Add the `shell` module to show an indicator for the currently used shell 
This was achieved in two steps. I first created a `[shell]` module in the configuration file with icons for `Fish`, `ZSH`, `Bash` and `Powershell`.

```toml
[shell]
fish_indicator = '󰈺 '
zsh_indicator = ' '
bash_indicator = ' '
powershell_indicator = ' '
unknown_indicator = 'mystery shell'
format = '[[ $indicator ](fg:#83a598 bg:color_bg3)]($style)'
style = "bg:color_bg3"
disabled = false
```

I then inserted the `$shell` module into the main `format` property of the configuration file. I chose to put it together with the preset's `$docker_context` and `$conda` modules and had the foreground and background style colours above to match these:

```toml
format = """
[](color_orange)\
$os\
$username\
[](bg:color_yellow fg:color_orange)\
$directory\
[](fg:color_yellow bg:color_aqua)\
$git_branch\
$git_status\
[](fg:color_aqua bg:color_blue)\
$c\
$rust\
$golang\
$nodejs\
$php\
$java\
$kotlin\
$haskell\
$python\
[](fg:color_blue bg:color_bg3)\
$shell\
$docker_context\
$conda\
[](fg:color_bg3 bg:color_bg1)\
$time\
[ ](fg:color_bg1)\
$line_break$character"""
```
#### Don't forget to restart your terminal or `source` your `.zshrc` file!
To activate the changes you've just made, `source` your `.zshrc` or restart your terminal session:
```bash
source ~/.zshrc
```

## How I got here?
I discovered Starship after I found out that the [Powerlevel10k](https://github.com/romkatv/powerlevel10k) project wasn't in active development anymore. I had a few bugs that I wanted to iron out and instead of trying to fic them I just googled `Powerlevel10k alternative` and stumbled upon Starship.