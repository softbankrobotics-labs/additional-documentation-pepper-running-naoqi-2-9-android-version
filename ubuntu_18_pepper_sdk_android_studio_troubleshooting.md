# Ubuntu 18  Pepper SDK  Android Studio troubleshooting

You might face difficulties running the Pepper emulator on Android Studio under Ubuntu 18.04. Here is how to solve them. Tested OK with API 5.

### 1. Make sure your user is in the kvm group.

You need to first install this:
<pre>
sudo apt install qemu-kvm
</pre>
To check the ownership of /dev/kvm use:
<pre>
ls -al /dev/kvm
</pre>
The user was root, the group kvm. To check which users are in the kvm group, use
<pre>
grep kvm /etc/group
</pre>
This returned
<pre>
kvm:x:some_number:
</pre>
on my system: as there is nothing rightwards of the final " : ", there are no users in the kvm group.

To add the user yourname to the kvm group, you could use
<pre>
sudo adduser yourname kvm
</pre>
which adds the user to the group, and check once again with _grep kvm /etc/group_.

You might want to log out and back in (or restart) for the permissions to take effect.

### 2. Relink the correct libraries

Add the repo and install the missing lib:
<pre>
echo "deb http://security.ubuntu.com/ubuntu xenial-security main" | sudo tee --append /etc/apt/sources.list
sudo apt-get update
sudo apt-get install libicu55
</pre>

Navigate to your lib folder:
<pre>
cd /home/$USER/.local/share/Softbank Robotics/RobotSDK/API 5/tools/lib
</pre>
Back up the old libraries:
<pre>
mv libz.so.1 libz.so.1.bak
mv libicui18n.so.55 libicui18n.so.55.bak
</pre>
And relink the system's ones:
<pre>
ln -s /usr/lib/x86_64-linux-gnu/libz.so libz.so.1
ln -s /usr/lib/x86_64-linux-gnu/libicui18n.so.55 libicui18n.so.55
</pre>

### 3. Restart Android Studio

You should now be able to start the Pepper emulator!