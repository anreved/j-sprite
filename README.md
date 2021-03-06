# j-sprite

j-Sprite is a Java based program that will sprite images together and generate the css to display those images. It can:

- take a list of files or a directory (with optional regular expression filename filter)
- recursively search sub-folders (with option to look in hidden folders)
- generate the css styles in a new file, or append to an existing css stylesheet
- generate a test HTML file showing all of the "sprited" images.

#### Command Line Options
To run j-Sprite, you must first type 
```java 
java -jar jsprite.jar
```
followed by any paramters.

Shortcut|Full|Description|Default Value
--------|----|------|-----------|-------------
-u|--usage|the full help list (i.e., this information)|

#### Directory Options
Shortcut|Full|Description|Default Value
--------|----|-----------|-------------
-l|--files|comma separated list of files to sprite|
-d|--dir|directory containing images to sprite|
-g|--regex|regular expression used to filter file names (used with -d flag only)|
-r|--recurse|if flag is present, the program will look in subdirectories for other image files|
-n|--hidden|include hidden subdirectories (used with -r flag only)|

#### Sprite Options

Shortcut|Full|Description|Default Value
--------|----|------|-----------|-------------
-o|--output|the output file	sprite.png|
-f|--format|the output format (e.g, png, jpeg, etc.)|PNG
-p|--padding|the number of pixels to skip between images|0

#### CSS Options
Shortcut|Full|Description|Default Value
--------|----|-----------|-------------
-c|--css|if flag is present, CSS will NOT be print|	
-e|--prefix|an optional prefix for the css class name|	
-t|--postfix|an optional postfix for the css class name|	
-s|--separator|the character used to separate prefix/postfix from classname (and to replace spaces in filenames)|- (dash)
-a|--appendTo|if specified, will append the css styles to this file, instead of creating a new one|	
-x|--extra|extra CSS style(s) to be added (should be a quoted string or valid CSS styles)|	
-i|--inline|experimental use data URI scheme (as defined in RFC 2397) for inline images, instead of normal urls|	
-P|--imgPrefix|an optional URL for the CSS background attribute that will prefix the output name (from the -o option)|	
-U|--imgUrl|an optional URL for the CSS background attribute (the -o and -P flags will be ignored if this is specified)|	
-I|--important|if flag is present, "!important" flag will NOT be used for the background-position property|	

#### HTML Options
Shortcut|Full|Description|Default Value
--------|----|-----------|-------------
-h|--html|generate a sample html file for the sprite|

#### Parameter Examples
Below are parameter examples and their meaning. For full usage examples, scroll down further.

Flag / Value|Meaning
--------------|----
-f "image1.png, image2.jpeg, image3.gif"|sprite image1.png, image2.jpeg, and image3.gif
-d .|select all images in the current directory
-d . -r|select all images in the current directory, search subdirectories
-d . -r -n|select all images in the current directory, search subdirectories (even if hidden)
-d c:\icons|select all images in the c:\icons directory
-d c:\icons -g "^[a-m].*\.png$"|select all images in the c:\icons directory that start with the letters a through m and end in .png
-o mysprite.png|output the sprite to a file called mysprite.png
-e icon|add "icon" before each classname (e.g. icon-add, icon-save)
-e icon -t|sprite	add "icon" before and "sprite" after each classname (e.g., icon-add-sprite, icon-save-sprite)
-e icon -s|add "icon" before each classname and separate with underscore (e.g., icon_add, icon_save)
-a c:\mystyle.css|append the generated css to the file c:\mystyle.css
-x "padding-left: 20px;"|add the specified styles to every generated css class
-h|generate a sample html file demonstrating every generated css class
-o mysprite.png -P http://myurl.com/resources|Output the sprite as mysprite.png, and use http://myurl.com/resources/mysprite.png as the background-url property in the css file
-U http://myurl.com/resources/sprt.png|Use http://myurl.com/resources/sprt.png as the background-url property in the css file
