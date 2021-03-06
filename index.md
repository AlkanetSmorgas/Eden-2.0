
# Tutorials
[Tools](https://alkanetsmorgas.github.io/Eden-2.0/#add-a-tool-to-the-menu)


## Add a tool to the menu
### Basic Structure
All tools need to be specifed in the class Display3DENALK_Tools.<br/>
They need to belong to a Category class. <br/> 
The category class then need to have a Attributes class where all your tools can be added.
```markdown
class Display3DENALK_Tools {
	class Category {

		displayName="Category";
		class Attributes
		{
			//Your tools.
		};
	};
};
```
### Tool structure
All tools need to be surrounded by a class. <br/>
All classes inside will be treated like a control. <br/> 
You are free to add whatever controls you want but we recomend to only use a text control and a value control.  
```markdown
class Time
{

	class TitleX: ctrlStatic
	{
		text="Set Time:";
		tooltip="Set current time.";
		style=2;
		shadow=0;
		colorBackground[]={0.76999998,0.18000001,0.1,1};
	};
	class ValueX: ctrlCombo
	{

		text="0";		
		font="EtelkaMonospacePro";
		sizeEx="3.875 * (1 / (getResolution select 3)) * pixelGrid * 0.5";
		onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_setTimeDay;";
		values[]={"Midday","Dusk","Midnight","Dawn"};
	};


};
```
### Settings
You can also add settings to your tools. You specify it in the category.<br/>
**type** - For now, only Edit is working.<br/>
**value** - the default value to use.<br/>
**valueType** - Number = convert to number.<br/>
**saveTo** - variabel in missionnamespace to save the data to.
```markdown
class Modifiers {
	class Attributes{
		......
	};
	class Settings {
		class RotationSpeed {
			type = "Edit";
			name="Rotation Speed";
			value = "10";
			valueType = "Number";
			saveTo ="AlkFrameWork_3DEN_rotateMouseWheel_Speed";
		};
	};
};
```
### onChange
When ever the control is clicked or changed. Data stored in _this variabel.<br/>
Accepted controls: _this<br/>
**Button**: [_control].<br/>
**Editbox**:[_control,_text].<br/>
**Slider**: [_control,_sliderValue]<br/>
**Combo, Listbox** [_control,_text,_value]<br/>
**Toolbox**: [_control,_value]<br/>
**Checkbox**: [_control,_value,_isChecked]<br/>
```markdown
onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_setTimeDay;";
```
### Checkbox
**Strings[]** - Is required for checbkox.<br/>
**values[]** - The value returned in _this. Only number.
```markdown
class ValueX: ctrlCheckboxToolbar
{
	strings[]={"showLayers"};
	values[]={0};
	onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_showLayers;";
};
```
### Button
**text** - Text displayed on the button.
```markdown
class ValueX: ctrlButton
{
	text="Open";
	onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_configInfo;";
};
```
### Combo
**values[]** - The values to display and returned in _this. Only strings.
```markdown
class ValueX: ctrlCombo
{
	values[]={"Midday","Dusk","Midnight","Dawn"};
	onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_setTimeDay;";
};
```


### Example
Here is an example on how the Set time tool is added.

![Enviroment Eden2.0](https://i.imgur.com/cGKJeg9.jpg)

```markdown
class ctrlStatic;
class ctrlCombo;
class Display3DENALK_Tools {
	class Environment {     
		
		displayName="Environment";
		class Attributes
		{
			class Time
			{
				
				class TitleX: ctrlStatic
				{
					text="Set Time:";
					tooltip="Set current time.";
					style=2;
					shadow=0;
					colorBackground[]={0.76999998,0.18000001,0.1,1};
				};
				class ValueX: ctrlCombo
				{
					
					text="0";		
					font="EtelkaMonospacePro";
					sizeEx="3.875 * (1 / (getResolution select 3)) * pixelGrid * 0.5";
					onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_setTimeDay;";
					values[]={"Midday","Dusk","Midnight","Dawn"};
				};
				
				
			};
		};
	};
};	

```
