## autottylogin
un-attended configuration of a linux host to automatically log in on the console
 
By default the linux sound system (pipewire or pulseaudio) is run in a per-user basis. The audio process is stared only when a user is logged in.
So for a headless setup you need something to be logged in for audio to work. There is a (unsupported) global mode but it's not recommended so this is the workaround
