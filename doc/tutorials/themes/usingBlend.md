# Creating themes using Blend editor

Installing Blend
---------------------

Blend is part of the [Visual Studio IDE](https://visualstudio.microsoft.com/), available for free with the Community Edition. Visual Studio comes with lots of components you might not be interested in; for theme development all you need is the `.NET Desktop development` workload.

> [!WARNING] 
> The latest Visual Studio **2022** is currently not supported (live previews will not work)! Use the [2019 or 2017 version](https://visualstudio.microsoft.com/vs/older-downloads/) instead.

Creating a new theme
---------------------
[Open the command prompt](https://www.windows-commandline.com/how-to-open-command-prompt/) and [navigate](https://www.windows-commandline.com/command-prompt-change-directory/) to Playnite's installation folder. To create a new theme, you need to run the `Toolbox.exe` utility using these arguments:

```cmd
Toolbox.exe new desktoptheme|fullscreentheme <ThemeName>
```

For example, to create a new desktop theme with "Super Clear Modern as the name:

```cmd
Toolbox.exe new desktoptheme "Super Clear Modern"
```

This will create a new folder containing all files needed for the theme to be edited in Blend. If the theme creation is successful, the Explorer window will open using your new theme folder. DO NOT move the theme's folder - designer in Blend will not work properly unless the theme is opened from the initial location Toolbox used to create it!

> [!NOTE] 
> If Playnite was installed into a folder with no write access enabled by default, some issues might occur using the aforementioned examples - some folders need you to have elevated privileges (folders like `c:\Program Files`). In those cases you will need to run the command prompt and Blend using admin privileges. However, a better approach would be to use a different install location.

Editing a theme
---------------------

To edit a theme in Blend, open the `Theme.sln` file from the theme's directory.

> [!NOTE] 
> Just opening `.sln` file will usually open Visual Studio instead of Blend. While you can use Visual Studio to edit the theme as well, it lacks many features making editing easier; like live preview for templates and styles. To open `.sln` files in Blend, right-click on the file, select `Open with` and select the `Blend for Visual Studio` option.

> [!WARNING] 
> Due to the way Playnite resolves theme files' paths (like images), it is necessary to open a theme sln file via the file itself. If you open Blend first and use that to open the theme sln, some parts of the live preview might not work properly. This will be fixed in future Playnite updates.

As a first thing after creating a new theme, open the `theme.yaml` file and change the manifest fields (if you need to) - you will probably need to change Author at least. For more information about the available manifest fields, see the [manifest file page](manifestFile.md).

Files
---------------------

Themes consists of several `.xaml` files. Each view, panel or specific control usually has their own xaml file. Commonly used resources like colors and brushes affecting all controls are generally defined in `Constants.xaml`.

Live preview
---------------------

To open the live preview (design view):

#### 1) Open the appropriate style (xaml) file

Not all files can be previewed in the design view; some only contains constants like colors, brushes etc. - `Constants.xaml` is the best example of this. If you want to see a preview of these resources, open the resources window (View -> Resources window) and expand the appropriate file.

#### 2) Open the design view panel

Toggle design view using the `Design` tab button. It is highly recommended to keep the XAML text view open as well, since it's faster for making changes. To have both views open at once, you can split the editor using the buttons on the bottom right part of the editor (offering both horizontal and vertical split.

![image](images/designSwitch.png)

#### 3) Select style to preview

Since a single xaml file might contain multiple styles for multiple views/controls, you need to select the prefered style to preview first. To do so, select the line in a text editor starting with `<Style TargetType=...`.

#### 4) Activate the preview

On the design panel, click on the `Style` dropdown and select `Edit Template`, and then `Edit Current`. This will load the preview for the style selected in the previous step.

![image](images/templateEdit.png)

#### 5) Enjoy

Now a preview for the specific view/control should appear. If not all resources are being displayed properly in the view (for example missing or incorrect colors and brushes are used), see the troubleshooting section.

![image](images/designExample.png)

Troubleshooting
---------------------

### Fonts, colors and other resources are not applied

When opening the style's design view for the first time, sometimes the referenced resources may load incorrectly (like fonts, colors etc). This is a Blend issue and can be easily fixed by editing any part of the style, which will force the design view to reload. Switching to a different file tab and back also sometimes resolves this.

### Updating the ThemeFile markup doesn't update in a preview

Specifically declare the `RelativePath` property if this happens:
```xml 
<Image Source="{ThemeFile RelativePath='Images/applogo.png'}" />
```
...instead of just:
```xml 
<Image Source="{ThemeFile 'Images/applogo.png'}" />
```

### Design view is not working

This happens if the theme is opened from an incorrect directory. As mentioned above, the theme's .sln file must be opened from the directory where Toolbox created it. Moving it to a different directory will cause issues!

Testing changes
---------------------
 
To test a theme in Playnite, just start the application and change the prefered theme in the application settings. No additional steps should be needed for Playnite to load the theme.

Packaging theme for distribution
---------------------

See the [Distribution and Updates](distributionAndUpdates.md) page for more details.

> [!WARNING] 
> Please pay special attention to the section about updating themes, to make sure your custom theme always works with the latest Playnite version.
