# v-ada

This is an implementation of V in Ada, written by Peter Lambert, (c) 2025.

This product is distributed under "The V Public License" ("VPL"), see 
LICENSE.txt.

Simply put, V is a system to check the veracity of signatures for a set of 
patches, and then apply the patches in the correct order.

The program expects to find V patch files (diff files with timestamps replaced
with file hashes, file name ending in .vpatch) in a directory, specified by the 
-p PATCH_DIR argument. Likewise, a directory for the seals (detached signatures,
with file names ending in .sig) should be stored in a directory specified by
-s SEAL_DIR argument. Public keys of the patch signers should be present in a
WoT directory specified by the -w WOT_DIR argument.

Note: Since the program only takes files with the correct file extension for 
each file type, it is possible to store all the files together in one folder.

This implementation is fairly bare-bones; it is the user's responsibility to
choose the patches to include - any patches present in the indicated directory
will be applied.

Main file is v.adb, supporting files include lists.ads/adb, str.ads/adb, and 
sys.ads/adb.


Build:
(in folder v-ada)
gprbuild


Run:

bin/v [-p PATCHES] [-s SEALS] [-w WOT] [+v] TARGET_DIR

 -p PATCHES : Set the directory that holds the patches. Default is "patches".
 -s SEALS   : Set the directory that holds the seals. Default is "seals"
 -w WOT     : Set the directory that holds the WoT public keys. 
              Default is "wot".
 +v         : Turn on verbose mode.
 TARGET_DIR : Directory on which to apply patches. Directory will be created
              if it is not already present. Default is "v_out".
