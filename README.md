# Source Indexed pdb Files

These pdb files link to the original source from the projects hosted on sites like GitHub, BitBucket, or Google Project Hosting. Hopefully CodePlex will support raw files too soon. Please [vote for this issue](https://codeplex.codeplex.com/workitem/26806)!

The future goal is to get projects doing this automatically in their builds. I have more details [on my blog](http://blog.ctaggart.com/search/label/pdb). I'll add some of my favorites here as examples.

## How to Use these pdb Files

### File Copy

Symbol loading will need to be a topic of another blog post...  
A simple way is to copy the specific pdb to the same folder as the dll. I'd like it if the nuget packages distributed source indexed .pdb files like this.
  
### Using a Symbol Server

Tools > Options > Debugging > Symbols

#### Network 

Clone this repo to a network folder, then add the folder in the dialog using a **UNC path**: \\\\network\path 

### Web Server

If you have a local web server that serves files, just clone this repo to a folder it serves.

### Local Hack

I haven't figured out why this sometimes works and sometimes doesn't yet. The hack is use a UNC path to your a folder on your computer. For example, if you cloned it to C:\pdb\ctaggart, map it as \\\\localhost\c$\pdb\ctaggart. Visual Studio will then think it is a network share, "download" them, and put them in your cache as needed. This was working, but isn't for me now on a different network. Feedback would be appreciated.

## pdb Files in this Repo Match these dll Files

* Autofac 3.0.2 from [their website](https://code.google.com/p/autofac/)  
Autofac.dll, 5163A86D time date stamp Tue Apr 09 00:34:37 2013, {D864089A-F405-4AC3-8A57-5550C13670FC}, 1  
This was mapped as https and ReSharper's navigate to doesn't work. I'm going to log a bug.
Debug into works just fine. I'm running Visual Studio 2012.
* Autofac 3.0.2 from NuGet
Autofac.dll, 5162A61D time date stamp Mon Apr 08 06:12:29 2013, {D77905B6-7A50-4613-8298-AF1CC87D57D5}, 1  
This was mapped as http and ReSharper's navigate does work.

## Technical Details

Each .dll built gets a timestamp, a guid, and another number. These values can be seen using using dumpbin. On my computer, dumpbin is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\VC\bin.  
```dumpbin /headers Autofac.dll```  
The .pdb must match guid and number.