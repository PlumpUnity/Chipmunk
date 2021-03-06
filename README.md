Chipmunk
========

Chipmunk is a set of WPF attached behaviors that provide attached properties.
Simply add a reference to the Chipmunk.dll and specify properties all via XAML.
You need neither write any code-behind nor make a reference to the Expression Blend SDK.

<img src="https://raw.githubusercontent.com/wiki/chitoku-k/Chipmunk/preview.win7.png" alt="Sample" width="732">

<img src="https://raw.githubusercontent.com/wiki/chitoku-k/Chipmunk/preview.win10.png" alt="Sample" width="689">

## Features

### Window Behavior
- Completely full control of System Menu
  - Enables or disables the minimize button, maximize button, help button, and close button independently with one another
  - Automatically processes Window Message if needed.
- Hides an icon on the caption bar (title bar)
- Enables DWM (Desktop Window Manager) Aero Composition
  - Applies extended window frame settings if supported
  - Makes a specified area window-draggable through XAML
  - Supports automatic enable/disable the feature when DWM is turned on/off


### TextBox Behavior
- Provides a property of numeric validation of System.Windows.Controls.TextBox
- Just specify whatever value available: Integer, decimal, negatives and/or combinations with each other


### PasswordBox Behavior
- Provides a bindable PasswordBox.Password property to help MVVM


### NumericUpDown Control
- A control that has buttons to increase or decrease values of the text box



## Usage

### WindowBehavior
```xaml
<Window xmlns:cm="clr-namespace:Chipmunk;assembly=Chipmunk"
        cm:WindowBehavior.DwmComposition="-1,0,0,0,White"
        cm:WindowBehavior.IsIconVisible="False"
        cm:WindowBehavior.IsMinimizeButtonEnabled="True"
        cm:WindowBehavior.IsMaximizeButtonEnabled="False"
        cm:WindowBehavior.IsHelpButtonEnabled="False"
        cm:WindowBehavior.IsCloseButtonEnabled="True"
        cm:WindowBehavior.IsControlButtonVisible="False"
        cm:WindowBehavior.NonClientArea="{Binding ElementName=Window}"
        Name="Window" />
```

- IsIconVisible (bool)
  - Shows or hides the icon on windows  
    This value cannot be changed after the window is initialized
- IsMinimizeButtonEnabled (bool)
- IsMaximizeButtonEnabled (bool)
- IsHelpButtonEnabled (bool)
- IsCloseButtonEnabled (bool)
- IsControlButtonVisible (bool)
  - Enables or disables the system menu on windows
- DwmComposition (Chipmunk.DwmCompositionOption)
  - Sets the DWM Aero Composition settings  
    Values are [Left],[Top],[Right],[Bottom],[BackgroundColor]
- NonClientArea (Window)
  - Sets a window-draggable area  
    In XAML, you can use binding to the window


### TextBoxBehavior
```xaml
<TextBox xmlns:cm="clr-namespace:Chipmunk;assembly=Chipmunk"
         cm:TextBoxBehavior.ValidationType="Negative,Decimal" />
```

- ValidationType (Chipmunk.TextBoxValidationType)
  - Sets an automatic validation to the TextBox  
    You can make combinations delimitted by ',' with following values:
    - Integer
    - Decimal
    - Negative


### PasswordBoxBehavior
```xaml
<PasswordBox xmlns:cm="clr-namespace:Chipmunk;assembly=Chipmunk"
             cm:PasswordBoxBehavior.BindsPassword="True"
             cm:PasswordBoxBehavior.Password="{Binding Password}" />
```

- BindsPassword (bool)
  - Sets whether to bind Password property
- Password (string)
  - Sets binding to the Password propery
  - Specify Mode property of the binding to TwoWay (default)


### NumericUpDown
```xaml
<cm:NumericUpDown LargeChange="0.1" Minimum="0" Maximum="100" />
```

(Properties of System.Windows.Controls.Primitives.RangeBase are available)
