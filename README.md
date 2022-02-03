# ChiaTempAutodel

I just got annoyed with the way my temp drive was filling up when plotting got interrupted, so I decided to make this little bash script to clean everything up while not affecting currently running plots.

### How's it work?

The script grabs searches for keywords/expressions in the plot managers log files. Note this has only been tested with the original chia-plotter, I'll try to adapt it for [madmAx](https://github.com/madMAx43v3r/chia-plotter) as well. 
It will then grab the plot's ID, the PID it's being plotted on and the corresponding temp directory.
Now there are three ways the script could continue:

1) If the script finds an indication that the plot has been completed ("Summary" in the log), it will look for tmp files and delete them. This feature may be obsolete because the files are moved rather than copied, however, still not bad to make sure everything is gone.

2) If the script can't confirm a plot has been finished, it looks up the PID to see if plotting is still in progress. If not, the tmp files will be deleted as plotting probably got interrupted and can (as of now) not be resumed.

3) If the plot has not been completed and PID exists, script will do nothing.

Additionally, you can have the logs for either failed plots, completed plots or both removed.


# Usage:

`sh autodelete.sh [-f] [-c] [-h] LOGDIR`

`-f: Remove plotter logs of failed plots`

`-c: Remove plotter logs of completed plots`

`-h: Display help`

`LOGDIR: Directory with chia plotter logs, user will be prompted if not passed` 




Obviously, this file only works on Linux. 

Please forgive any mistakes/non-compliances in the script, I'm still a noob when it comes to bash scripting :) 
Feel free to use, modify and extend.

