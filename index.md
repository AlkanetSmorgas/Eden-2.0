
# Tutorials
[Add Tools](https://alkanetsmorgas.github.io/Eden-2.0/#add-to-tools)


### Add to tools

![Enviroment Eden2.0](https://i.imgur.com/cGKJeg9.jpg)
```markdown
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
			class toggleGrass
			{
				
				class TitleX: ctrlStatic
				{
					text="Toggle Grass";
					style=2;
					shadow=0;
					colorBackground[]={0.76999998,0.18000001,0.1,1};
				};
				class ValueX: ctrlCheckboxToolbar
				{
					strings[]={"grass"};
					values[]={0};
					onChange="_this call AlkFrameWork_3DEN_Toolbar_fnc_toggleGrass;";
				};
				
			};
			
			
		};
	};
};	

```

