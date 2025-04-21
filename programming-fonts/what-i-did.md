# Programming Fonts
## Finding my favourite fonts
1. Choose my favourite fonts from [Programming Fonts](https://www.programmingfonts.org) and [Nerd Fonts](https://www.nerdfonts.com/) and added them to a list

2. Chose my first favourite font to try: [The TeX Gyre Cursor](https://www.gust.org.pl/projects/e-foundry/tex-gyre)

3. converted [The TeX Gyre Cursor](https://www.gust.org.pl/projects/e-foundry/tex-gyre) to a Nerd Font using [Nerd Fonts's](https://www.nerdfonts.com/) [font-patcher](https://github.com/ryanoasis/nerd-fonts/?tab=readme-ov-file#font-patcher) python script.
```bash
fontforge -script font-patcher --complete --outputdir 'DESTINATION_PATh' 'FONT_PATH' 
```

4. Added the converted font to MacOS Font Book (built in MacOS App) under a Nerd Fonts collection

6. I downloaded several other fonts and eventually settled with [GeistMono](https://www.nerdfonts.com/font-downloads) for my terminal

## Converting fonts to be a Nerd Font so they have all the symbols you need:
1. Choose a font that you want to convert into a Nerd Font. The first font I tried this with was [The TeX Gyre Cursor](https://www.gust.org.pl/projects/e-foundry/tex-gyre)

2. Then I converted [The TeX Gyre Cursor](https://www.gust.org.pl/projects/e-foundry/tex-gyre) to a Nerd Font using Nerd Fonts's [font-patcher](https://github.com/ryanoasis/nerd-fonts/?tab=readme-ov-file#font-patcher) python script.

```bash
fontforge -script font-patcher --complete --outputdir 'DESTINATION_PATh' 'FONT_PATH' 
```

3. Finally I added the converted font to MacOS Font Book (built in MacOS App) under a Nerd Fonts collection

