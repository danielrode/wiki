
# Installing fonts on Linux

Move font files to: ~/.local/share/fonts
Then run the following to rengenerate system font cache

	fc-cache -f -v

Then run the following to regenerate ConTeXt font cache

	export OSFONTDIR=$HOME/.fonts:/usr/share/fonts:$HOME/.local/share/fonts
	"$DCV_HOME_OPT"/context/tex/texmf-linux-64/bin/mtxrun --generate
	"$DCV_HOME_OPT"/context/tex/texmf-linux-64/bin/mtxrun --script font --reload

# List/search installed fonts

	fc-list | fzf

# Show which font file will be used for a given font string

  fc-match <FONT STRING>

# List/search installed fonts for use in ConTeXt

	"$DCV_HOME_OPT"/context/tex/texmf-linux-64/bin/mtxrun --script fonts --list --all | fzf --header-lines=1

See ConTeXt's website for more details: https://wiki.contextgarden.net/Use_the_fonts_you_want
