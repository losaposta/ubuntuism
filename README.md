This template will be used as part of the Joomla Dev Day 2011 Rapid Template Development workshop. It is a modified version of Construct5-Pro beta 2, a unified HTML5 template development framework from http://construct-framework.com

Please see http://betweenbrain.github.com/jdaynyc2011 for the introductory presentation to this workshop.

#How to use this framework#
The Construct Template Development Framework is a code based solution with the goal of streamlining the process of creating one-of-a-kind Joomla! templates, while not limiting your ability to add every bit of your creativity. To get started, install Construct like you would any Joomla extension. Then add a new style sheet to the CSS directory of Construct and select that style sheet in the template's settings from within template manager of Joomla.

#Step by step#
For the workshop, we will recreating the Ubuntu 11.04 classic desktop experience as a Joomla template.

1. Start with a clean installation of Joomla, preferably 1.7, with sample data installed.
2. <a href="https://github.com/betweenbrain/jdaynyc2011/zipball/master">Download</a> the master branch zip and
install it as you would any extension.
3. Set jdaynyc2011 as the default template in Joomla's template manager.
4. Create a blank styles sheet, named whatever you'd like, within the CSS directory of the jdaynyc2011 template (i.e.
 var/www/joomla/templates/jdaynyc2011/css ).
5. Open jdaynyc2011 in Template Manager: Styles (in Joomla 1.7) and select the name of the style sheet that you just
created in the Custom Style Sheet drop-down and click save.
6. Open the style sheet that you just created in your favorite editor and begin adding the custom styles for this
template:

	a. Set the background image (available within the images directory of the installer file that you downloaded,
	or at https://github.com/betweenbrain/jdaynyc2011/raw/master/images/wallpaper.jpg) :
	<pre>html {
    	background-image: url('../images/wallpaper.jpg');
    	background-position: 50% 50%;
    	background-repeat:no-repeat;
    	background-attachment:fixed;
	}</pre>

