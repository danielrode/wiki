
# Set screen resolution and refresh rate

	swaymsg -t get_outputs  # Get list of available outputs and options

	swaymsg output OUTPUT mode MODE  # Set desired mode (resolution and refresh rate)

	swaymsg output HDMI-A-1 mode 1920x1080@29.970Hz  # Example

# Set screen resolution

	swaymsg output OUTPUT res RESOLUTION

	swaymsg output HDMI-A-1 res 1920x1080  # Example

# Allow touchpad while typing

	swaymsg input TOUCH_PAD_ID dwt disabled

