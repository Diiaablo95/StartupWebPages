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

## If you use Google Chrome

If your default browser is Google Chrome, the script will work fine. The only detail is that Google Chrome will open such tabs with the last used user. If you want to open the pages always with the same user, there are a few additional steps involved.

1. Navigate to `~/Library/Application Support/Google/Chrome`. Each user will have its own folder named `Profile N`, where N is an integer number. You can understand which account is which from the info enclosed within the folder, especially the avatar image which can be found in `Accounts/Avatar Images`, if any.

2. After identifying the designated profile that will be used, change the actual script to: `/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome $(< <PATH_TO_SCRIPT_DIRECTORY>/websites.txt) --args --profile-directory="Profile N"`

**Et voilà!**
