# StartupWebPages

The goal of this very simple script is to open a set of web pages at Mac startup time with the default browser. So far, I have not found any other solution that would allow me to open web pages only once on startup, with a browser which was not Safari (if you save the links as .webloc and set them into the Login Items sections).

## Usage

To start enjoying the HUGE benefits of the script, perform the following steps:

1. Rename the `YOUR_IDENTIFIER.plist` file to your own reversed domain, such as `me.diiaablo.startup_web_pages.plist`;
2. Open the plist file and modify the sections with your own parameters:
    - `SERVICE_LABEL_NAME`: the name the service will use in the management console;
    - `ERROR_FILE_PATH`: the path of the file containing the stderr output. Recommended to set something like _/tmp/startup_web_pages.err_;
    - `OUTPUT_FILE_PATH`: the path of the file containing the stdout output. Recommended to set something like _/tmp/startup_web_pages.out_;
    - `PATH_TO_SCRIPT`: the path where the script will be saved in the filesystem.
3. Copy/move the plist file to `~/Library/LaunchAgents`;
4. Modify `websites.txt` to contain the list of websites you would like to open at startup time. Use one line for each URL;
5. Run `sudo launchctl load YOUR_IDENTIFIER.plist` where `YOUR_IDENTIFIER` is the identifier chosen at point 1.

That's it, you can now enjoy your Twitter feed at Mac startup instead of opening it at every browser launch! If you need to update the list of websites to open, just update `websites.txt`.