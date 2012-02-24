## Usage ##
You can pass either the .app or the .dSYM file to the script.  

    symbolication yourapp.app.dSYM yourapp.crash > symbolicated.crash

or

    symbolication yourapp.app yourapp.crash > symbolicated.crash 

__NOTE:__ Symbolication will only symbolicate symbols native to your app.  The xcode tools should be used to symbolicate the Apple symbols (or you can not-symbolicate them, often where an app crashed in your code is more relevant to debugging).

__WARNING:__ When looking for a .dSYM, gdb does not care about the file name. If a non-matching .dSYM file is in the same directory, gdb may try and use it and provide inaccurate results. Double check your results and that you are using the right dSYM file.

__WARNING:__ Symblocation only supports iOS based crash logs due to the use of the iOS version of gdb.  With some simple tweaks, symbolication of all crash logs should be possible.

If you pass the .dSYM the matching .app file '''MUST''' be in the same directory for any symbols to be parsed. 

If you pass the .app you can still parse some symbols if you don't have the .dSYM file.  However, gdb will look for a .dSYM file in the same directory as the .app and if it finds it you will get the same results as if you passed the .dSYM.  

The script will output the symbolicated log file which can then be redirected to a new file or viewed in the console.