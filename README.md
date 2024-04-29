# zeromq_ios_libraries

Forked from crccunningham's original repository that contained these scripts.
Changes were made to fix issues related to this post.
https://github.com/zeromq/libzmq/issues/4679

Changes made
* enabled bitcode in libsodium compilation for armv7 and armv7s architectures
* modified configure.ac for zmq to enable curve on libzmq 4.3.5
* added precompiled static libraries for use on iOS
WARNING: I had to make a change to the way czmq is downloaded, it is now cloned directly instead of downloading a released version.
So for future users, it may be necessary to revert back to an earlier commit on the czmq repo in build.sh. The commands for this have
already been added and are commented out right now. If you are needing to revert, try going back to the latest and greatest for czmq as of 4/29/2024


code to compile the zeromq, czmq, and libsodium statically for ios

# why does this exist?

i was trying to use zeromq for an ios project and i couldn't find an easy way to do it so i modified some scripts i found to generate the libraries i needed. 

# how does it work?

you run `build.sh` and it will download version of zmq, czmq, and libsodium (the versions are defined at the top of build.sh). then it will call each of the subscripts: libzmq.sh, libczmq.sh, and libsodium.sh. when they finish you'll have a `dist` folder which contains all of the libraries. 

# random note

when using these on ios you might need to explicitly link libc++. 
