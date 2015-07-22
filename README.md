## Author: Devon Ash
## Maintainer: noobaca2@gmail.com

Language tools found here:
http://www.speech.cs.cmu.edu/tools/lmtool.html

This package contains the speech commands that the Talos robot accepts as a ROS service.

To launch the listener:
    roslaunch talos_audio listener.launch

To launch the recognizer: 
    roslaunch talos_audio recognizer.launch

To see what commands are accepted by the robot, open the file speech_commands.corpus:

    roscd talos_audio
    cd speech_dictionaries/simple_speech
    cat speech_commands.corpus

To generate new commands, follow the tutorial at http://www.speech.cs.cmu.edu/tools/lmtool.html and replace the existing files inside the talos_audio ROS package.

Usage:

The listener should be brought up first and then the recognizer after. The listener 
listens to commands and then the recognizer program produces something when a command is detected.

the /say service, if called, will tell the robot what to say. For example, calling /say like:

    rosservice call /say 'hi'

will output 'hi' from the speakers.

Calling the service /listen_for_all will tell the robot to be conscious for all of the dictionary words until it hears one of those words, upon which 
it will put whatever word it heard on the recognizer/output topic. 

Example:

    rosservice call listen_for_all devon ok

The recognizer/start function is called which waits until either 'devon' or 'ok' is heard. when it is heard, the word is then outputted to recognizer/output and recognizer/stop is called.

This should handle all of the voice recognition needed for Talos.







