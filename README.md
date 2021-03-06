# RYFloatingInput
A flexible text field control of "Float Label Pattern" following mvvm pattern written in Swift.

[![CI Status](http://img.shields.io/travis/eebolue/RYFloatingInput.svg?style=flat)](https://travis-ci.org/eebolue/RYFloatingInput)
[![Version](https://img.shields.io/cocoapods/v/RYFloatingInput.svg?style=flat)](http://cocoapods.org/pods/RYFloatingInput)
[![License](https://img.shields.io/cocoapods/l/RYFloatingInput.svg?style=flat)](http://cocoapods.org/pods/RYFloatingInput)
[![Platform](https://img.shields.io/cocoapods/p/RYFloatingInput.svg?style=flat)](http://cocoapods.org/pods/RYFloatingInput)

![](./Screenshots/Showcase.gif)

## Features
- Float label pattern
- Customization support: theme, color, icon
- Text input inpection and callback
- mvvm pattern

## Installation
#### CocoaPods
Available on CocoaPods. Simply add the following to your project Podfile, and you're good to go.

```ruby
pod 'RYFloatingInput'
```

## Getting Started
#### Setup from InterfaceBuilder
1. Drag a UIView instance into your UIViewController/UIView
2. Change class type of the UIView to `RYFloatingInput`.
2. Link to the IBOutlet instance of your UIViewController/UIView.

#### Setup Programmitacally
Create an `RYFloatingInput` instance and add to superview
```swift
let floatingInput = RYFloatingInput(frame: frame)
self.view.addSubview(floatingInput)
```

## Usage
* [Setting Builder](#setting_builder)
* [Input Text Validation](#text_validation)
* [Theme & Color Customization](#theme_customization)
* [Icon / Placeholder / Secure Text](#other)

<a id='setting_builder'></a>
### Setting Builder
`RYFloatingInputSetting` is required for `RYFloatingInput` to work properly, which concise all the settings and customizations together into one single builder function. Here are the steps:
1. Initialize `RYFloatingInputSetting` instance by using `RYFloatingInputSetting.Builder`
2. Add features & customizations
3. setup `RYFloatingInput` by created `RYFloatingInputSetting` instance

Example:
```swift
let setting = RYFloatingInputSetting.Builder.instance()
.theme(.dark)
.iconImage(UIImage(named: "image_name")!)
.placeholer("I AM PLACEHOLDER")
.secure(true)
.build()

floatingInput.setup(setting: setting)
```

<a id='text_validation'></a>
### Input Text Validation
Setting up text validation is totally painless in `RYFloatingInput` by simply adding `.maxLength` or `.inputType` implementation in setting builder and it's done. You can also customize warning message along with a callback event triggered at any invalid input occurrence. Complex delegation is not needed.

2 options for input Type validation:
- `.number` - only accept numeric input.
- `.regex(pattern: String)` - check input text with regular expression you want.

Example:
```swift
RYFloatingInputSetting.Builder.instance()
.theme(.standard)
.maxLength(8, onViolated: (message: "Exceed max length", callback: {
print("Exceed max length")
}))
.inputType(.number, onViolated: (message: "Invalid input, number only", callback: {
print("Invalid input, number only")
}))
.build()
```
<a id='theme_customization'></a>
### Color & Theme Customization
**Color Customization** is implemented for almost every component in `RYFloatingInput`, such as background, divider, placeholer, divider, warning label, and input cursor.
Here are the color customization options provided:

```swift
RYFloatingInputSetting.Builder.instance()
.backgroundColor(.clear)
.textColor(.darkText)
.placeholderColor(.lightGray)
.dividerColor(.lightGray)
.cursorColor(.blue)
.accentColor(.cyan)
.warningColor(.red)
.build()
```

Normally, divider and floating label are displayed as accent color while highlighted, and will turn into warning color once invalid text input has entered.

![](./Screenshots/WarningTransition_dark.gif)

**Theme** is a easier way to customize colors which covers all color options described above. 3 theme options are definded in `RYFloatingInput.Theme`:
- `.standard` - default
- `.light`
- `.dark`

```swift
RYFloatingInputSetting.Builder.instance()
.theme(.light)
.build()
```
Please note that if theme and color customization, e.g. textColor, are both setup in builder, the text color from theme will be ignored.

<a id='other'></a>
### Icon / Placeholder / Secure Text
Setting input icon, placeholder, secure text options.

```swift
RYFloatingInputSetting.Builder.instance()
.iconImage(UIImage(named: "image_name")!)
.placeholer("I AM PLACEHOLDER")
.secure(true)
.build()
```

## TODO
- [ ]   Support customized font
- [ ]   Multiple text validation conditions
- [ ]   Activity indicator & asyncronous task completion event

## Built with
[RxSwift](https://github.com/ReactiveX/RxSwift) - Reactive Programming in Swift


## License
RYFloatingInput is available under the MIT license. See the LICENSE file for more info.


## Author
Ray ChengJui YU - eebolue@gmail.com


