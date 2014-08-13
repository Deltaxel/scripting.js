# About
scripting.js is a project that permit you to use JavaScipt code in your projects
for generating other code like c, c++, c#, etc.

How to use code:

`<-js
     // Put your code here
js->`

Compatible with node.js modules.

You can check 'scripting.js\common\context.js' to see witch functions are implemented in execution context.

# Install
First install node.js.
Then create a new project or keep an existing project.

Use the setup for extract files in your project folder.
Open a terminal and go to your download directory.
Then use the command above and remplace 'your_project_folder' by the path of your project.
`node ./setup_node_win.js install your_project_folder`

## Visual Studio 2013
### Auto-update
Close Visual Studio.

We are going to patch your .vcxproj file.
**Warning !** Do not path a .vcxproj that is already patched, that might create unknown behavior.
First go in your project folder with a terminal and use:
`node ./scripting.js/tools/vs2013/patch.js ./yourProject.vcxproj`
Don't forget to replace 'yourProject.vcxproj' by the name of your .vcxproj file.

This step has edited your .vcxproj file and added a pre-build event.
Now each time you're going to build your project, your.vcxproj will be analysed.
If there is new files, your .vcxproj will be edited.
That will create an error but don't be afraid, reload the project and build again.

Each file now generate a '.generated' file.
That the final code without JavaScript.

### Manually
The manual setup must be done for each file who contain JavaScipt code.

Open the property panel of your file.
In 'Configuration Properties->General', set 'Item Type' to 'Custom Build Tool'.
Apply changes.
Now in 'Configuration Properties->Custom Build Tool->General' set this values:

  'Command Line':
`node .\scripting.js\common\scripting.js .\%(Filename)%(Extension) .\%(Filename).generated%(Extension)`

  'Description':
`Generating %(Filename).generated%(Extension) from %(Filename)%(Extension)`

  'Outputs':
`%(Filename).generated%(Extension)`

Now your file will generate a .generated file that you must add the project.

## Makefile
Coming soon
