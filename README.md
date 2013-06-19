#source indexed pdb files

These pdb files link to the original source from the projects hosted on sites like GitHub, BitBucket, or Google Project Hosting. Hopefully CodePlex will support raw files too soon. Please [vote for this issue](https://codeplex.codeplex.com/workitem/26806)!

The future goal is to get projects doing this automatically in their builds. I have more details [on my blog](http://blog.ctaggart.com/search/label/pdb). I'll add some of my favorites here as examples.

## how to use these pdb files

To use these pdb files, clone this repo to a folder, then add the folder in Tools > Options > Debugging > Symbols using a **UNC path**. For example if you cloned it to C:\pdb\ctaggart, map it as \\\\localhost\c$\pdb\ctaggart. Visual Studio will then think it is a network share, "download" them, and put them in your cache as needed.

## pdb files in this repo match these dll files

* Autofac 3.0.2 from [their website](https://code.google.com/p/autofac/)  
Autofac.dll, 5163A86D time date stamp Tue Apr 09 00:34:37 2013, {D864089A-F405-4AC3-8A57-5550C13670FC}, 1

## technical details

Each .dll built gets a timestamp, a guid, and another number. These values can be seen using using dumpbin. On my computer, dumpbin is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\bin.  
```dumpbin /headers Autofac.dll```  
The .pdb must match guid and number.