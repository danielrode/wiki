
# KEYBINGINS

- v   Open buffer contents in text editor [^1]
- s   Write buffer to file


# FOOTNOTES

[^1]: Ensuring 'v' works

	Your ~/.profile must have several variables set for the 'v' key to work 
	correctly:

		export LESSEDIT="%E < %f"
		export VISUAL=hx
		export EDITOR="$VISUAL"

	I am not sure whether just VISUAL or EDITOR need to be set, or both,
	but I do know that less needs to know to use helix as its editor to 
	send the buffer contents to.
