LineageOS Pie (16.X) for the J6LTE
=====================================

Current Status
--------------

Untested.

Download
--------

You can grab some links from the XDA thread (will soon be available) or just join us at Telegram in the [Prebuilts Delivery Channel](https://t.me/romdelivery) or the [Dev support and off-topic group](https://t.me/somefeak) (previously SomeFeaK group).

Build Instructions
------------------

#### Automatic compilation

Download the script

	wget -q https://raw.githubusercontent.com/FacuM/shellscripts/master/android/buildrom/examples/los_j6lte.sh -O ~/los_j6lte.sh

Edit the variables at the top to your liking

	vi ~/los_j6lte.sh   or   nano ~/los_j6lte.sh

![Variables to edit](https://i.imgur.com/6gqS7sn.png)

Then begin the build, syncing source and just building what you need.

	. ~/los_j6lte.sh

If you want to remove the old source, you can run it like this.

	. ~/los_j6lte.sh reset

Or you can just clean the old compilation and build it all again.

	. ~/los_j6lte.sh clobber

#### Manual compilation

Create a build directory

	mkdir -p los
	cd los

Initialize your local repository using the LOS trees:

	repo init -u git://github.com/LineageOS/android.git -b lineage-16.0

Now move your magic wand
	
	mkdir -p .repo/local_manifests
	wget -O .repo/local_manifests/j6lte.xml https://raw.githubusercontent.com/j6lte-development/android/lineage-16.0/j6lte.xml

Do this everytime before every sync for tracking changes.

Then to sync up:

     repo sync  --force-sync --force-broken --current-branch --no-tags --no-clone-bundle --optimized-fetch --prune -j$(nproc --all)

Do this everything after sync for applying patches.	

Now start the build...

	. build/envsetup.sh 
	lunch los_j6lte-userdebug
	brunch j6lte   or   mka otapackage

Please see the [LineageOS WIKI](https://wiki.lineageos.org/) for further information.

Resources
---------

- Understanding bash sourcing: [How to detect if a script is being sourced - Stack Overflow](https://stackoverflow.com/questions/2683279/how-to-detect-if-a-script-is-being-sourced)
