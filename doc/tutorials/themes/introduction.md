# Introduction to Themes

General information
---------------------

Playnite's user interface is implemented using Windows Presentation Framework (WPF) and the UI definition is done using [XAML](https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/xaml-overview-wpf) files. Custom Playnite themes are implemented using [standard template and styling](https://docs.microsoft.com/en-us/dotnet/framework/wpf/controls/styling-and-templating) support that WPF provides, therefore any tutorial that apply to styling or editing in WPF, also applies to Playnite.

Fullscreen and Desktop modes
---------------------

Playnite offers two separate modes of operation. Standard `Desktop` mode designed for keyboard and mouse, and `Fullscreen` mode designed to be controlled with gamepad. These two modes are implemented completely separately and therefore themes are also completely separate.

Learning resources
---------------------

Recommended WPF resources:
* https://docs.microsoft.com/en-us/dotnet/framework/wpf/advanced/xaml-overview-wpf
* https://www.wpftutorial.net/GettingStarted.html
* https://www.tutorialspoint.com/wpf/

> [!NOTE]
> There's currently a very active community around theme/extension development on our [Discord server](https://discord.gg/hSFvmN6). We highly recommend joining if you plan on developing add-ons for Playnite!

Creating Playnite themes
---------------------

> [!WARNING] 
> Do not edit built-in default themes. Always create a new copy of theme files (ideally using the Toolbox utility) and edit those. Broken edits to default theme files could lead to Playnite being unable to start.

> [!WARNING] 
> Please read the documentation carefully, especially the section about [distribution and theme updates](distributionAndUpdates.md). Not updating your theme regularly could cause issues to users of the theme. For example, newly added features might become unusable - or in the worst case scenario - the theme might not load at all in newer versions of Playnite.

There are generally two approaches to theme creation in Playnite.

1. **[Manually editing](manualEditing.md)** XAML files using any text editor.

2. **[Using Blend/Visual Studio](usingBlend.md)** designer.

Option #1 requires no installation of any additional applications, and themes can be generally created even using Notepad. However this approach has major disadvantages:
* You get no live preview of changes your are making.
* Playnite needs to be restarted every time a change is made to the theme files.
* There's no autocompletion or error checking for XAML syntax.

Option #2 requires installation of [Visual Studio IDE](https://visualstudio.microsoft.com/), Community edition is free to download and includes [Blend](https://docs.microsoft.com/en-us/visualstudio/designers/creating-a-ui-by-using-blend-for-visual-studio?view=vs-2019) editor. This approach takes some time to set up, but offers all advantages manual editing lacks: like live preview, autocompletion of XAML properties, visual editor etc. 

**Using Blend editor is the recommended option.**

> [!WARNING] 
> Theme installation and update always replaces the entire theme directory completely; meaning any files that are not part of the installation package will be lost during the installation process! If your theme includes some custom functionality requiring users replacing/adding files to the theme's directory, make sure they're aware that those changes will be lost after an update!

Integrating with plugins
---------------------

Plugins can provide custom UI elements to be integrated into a theme. See [extension integration page](extensionIntegration.md) for more details.

Theme files and directories
---------------------

This section explains contents and purpose of specific theme files.

| Directory/File | Description |
| -- | -- |
| DefaultControls | Styles for standard (built-in WPF) controls; like button, checkbox etc. |
| DerivedStyles | Styles for standard (built-in WPF) controls; like button, checkbox etc., used for specific cases. For example, Play button, list item for Grid view etc. |
| CustomControls | Styles for custom Playnite controls. |
| Views | Styles for library views and panels. |
| Common.xaml | Base styles inherited by other theme styles. |
| Constants.xaml | Colors, brushes, sizes and other constants used by theme styles. |
| Media.xaml | Various icons, texts and image specifications used by theme styles.  |
