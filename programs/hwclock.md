# Update System/Harmware Clock

    sudo hwclock --set --date "02 Nov 2019 13:37"
    sudo hwclock --hctosys

NOTE: There might be a better way to do this depening on the system (or even just in general). I used this method given that I did not have a network time sync domain running on my system at the time, so I needed to update the hardware clock manually.
