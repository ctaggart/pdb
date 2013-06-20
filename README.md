# Source Indexed pdb Files

These pdb files link to the original source from the projects hosted on sites like GitHub, BitBucket, or Google Project Hosting. Hopefully CodePlex will support raw files too soon. Please [vote for this issue](https://codeplex.codeplex.com/workitem/26806)!

The future goal is to get projects doing this automatically in their builds. I have more details [on my blog](http://blog.ctaggart.com/search/label/pdb). I'll add some of my favorites here as examples.

## How to Use these pdb Files

Clone this repository to a folder and add the folder in Visual Studio > Tools > Options > Debugging > Symbols. The "pingme.txt" file is what is checked to see if it is a symbol server. Network folders and UNC paths also work.

## pdb Files in this Repo Match these dll Files

* Autofac 3.0.2 from [their website](https://code.google.com/p/autofac/)  
Autofac.dll, 2013-04-09T05:34:37Z, {D864089A-F405-4AC3-8A57-5550C13670FC}, 1 
This was mapped as https and ReSharper's navigate to doesn't work. I'm going to log a bug.
Debug into works just fine. I'm running Visual Studio 2012.
* Autofac 3.0.2 from NuGet
Autofac.dll, 5162A61D time date stamp Mon Apr 08 06:12:29 2013, {D77905B6-7A50-4613-8298-AF1CC87D57D5}, 1  
This was mapped as http and ReSharper's navigate does work.

## Technical Details

Each dll built gets a timestamp, a guid, and age. The pdb must match the guid and age. The age is the number of times the linker processes it during a compilation, usually 1 or 2. The source server folder structure uses a concatenation of the guid and age. These values can be seen using dumpbin. On my computer, dumpbin is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\bin.  
```dumpbin /headers Autofac.dll```

If you are using **ReSharper**, it's source navigation support isn't working with **https**. It works with http. I've [logged a bug](http://youtrack.jetbrains.com/issue/RSRP-371569) and they've marked it as critical. I'd prefer all the source indexing to be https rather than http, so hopefully they can fix this soon.