# Convert animations from choregraphe to android studio

We have created a draft script to convert animation.xar into animation.qianim.

You can download it [here](anim_convert.zip)

** /!\ Note that this tool comes as-is with no support /!\ **

### Usage
The HowToConvert is explained in the README, then you have to copy past the .qianim files in the raw directory of your project.

When using those animations on real robot, an error can appear, *Optional parameter has a null value*.

In order to solve this problem, you have to modify one value of the animation with the animation editor in Android Studio, save it. Then put the original value back and save it.

There are additional values in the .qianim, that's why you have to save the new anim with android studio.

Note : The output directory has to be created before starting the script.

If the animation doesn't work and give the following error log :
<pre>
09-24 14:32:47.120 6645-6698/com.softbankrobotics.qisdktutorials E/SignalManager: Unexpected exception
    java.lang.reflect.InvocationTargetException
        at java.lang.reflect.Method.invoke(Native Method)
     Caused by: java.lang.RuntimeException: com.aldebaran.qi.QiException: Attempted to access the value of an uninitialized optional object.
</pre>

The problem come from a missing information that is mandatory in .qianim and not present in the .xar which has been converted.

Workaround :
To make it work, in android studio, open the animation in the editor, modify a position a little bit, save it then it will work (when saving it inside android studio, the missing information is added).

/!\ If it is not the case, please add a Stand position Frame at the beginning of the animation after the conversion with the animation editor in android studio.