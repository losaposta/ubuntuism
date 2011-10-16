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
	<pre>
	html {
    	background-image: url('../images/wallpaper.jpg');
    	background-position: 50% 50%;
    	background-repeat:no-repeat;
    	background-attachment:fixed;
	}</pre>

	b. Set the body width to 90.5em and give it some larger top and bottom margins:
	<pre>
	body {
    	max-width:90.5em;
    	margin:50px auto;
    }</pre>

    c. Go ahead and add a dark aubergine background, with an opacity of .8
    <pre>
    body {
    	max-width:90.5em;
    	margin:50px auto;
    	background: rgba(44, 0, 30,.8);
    }</pre>

    d. Set the bod font to 'Ubuntu' (we'll add this font later), and set the font color to white
    <pre>
    body {
    	max-width:90.5em;
    	margin:50px auto;
    	background: rgba(44, 0, 30,.8);
    	font-family: 'Ubuntu', sans-serif;
    	color:#fff;
    }</pre>

	e. Give the body a border, some nice rounded corners and a drop shadow:
	 <pre>
	body {
    	max-width:90.5em;
    	margin:50px auto;
    	background: rgba(44, 0, 30,.8);
    	font-family: 'Ubuntu', sans-serif;
    	border:2px solid #333;
    	-moz-border-radius: 12px 12px 0 0;
		-webkit-border-radius: 12px 12px 0 0;
		border-radius: 12px 12px 0 0;
		-moz-background-clip: padding;
		webkit-background-clip: padding-box;
		background-clip: padding-box;
		-moz-box-shadow: 0px 0px 36px #000;
		-webkit-box-shadow:  0px 0px 36px #000;
		box-shadow: 0px 0px 36px #000;
	}</pre>

	f. Let's give the primary header a nice grey gradient background and rounded corners to match the body
	<pre>
	#header {
		background:#333;
		font-weight:bold;
		width:100%;
		-moz-border-radius: 12px 12px 0 0;
		-webkit-border-radius: 12px 12px 0 0;
		border-radius: 12px 12px 0 0;
		-moz-background-clip: padding;
		webkit-background-clip: padding-box;
		background-clip: padding-box;
		background-color: #454545;
		background-image: -webkit-gradient(linear, left top, left bottom, from(#666666), to(#333333));
		background-image: -webkit-linear-gradient(top, #666666, #333333);
		background-image:    -moz-linear-gradient(top, #666666, #333333);
		background-image:     -ms-linear-gradient(top, #666666, #333333);
		background-image:      -o-linear-gradient(top, #666666, #333333);
		background-image:         linear-gradient(top, #666666, #333333);
		filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#666666', EndColorStr='#333333');
	}</pre>

	g. Since Construct gives the primary header gutter a default of 10px, we need to override that style to line it
	up with the body. We'll add some padding while we are at it.
	 <pre>
	 #header .gutter {
		padding:.5em 0 0 .5em;
		margin:0 1em .5em 0;
	}</pre>

	h. Once again, we will override Construct's default style, this time for the logo
	<pre>
	#logo a:link,
	#logo a:visited,
	#logo a:hover,
	.breadcrumbs a {
		background:none;
		width:auto;
		height:auto;
		text-indent:0;
		font-family: 'Ubuntu', sans-serif;
		color:#fff;
		font-weight:bold;
	}</pre>

	 Let's customize the color and behavior of the anchors tags
	<pre>
	a, a:link, a:visited, a:focus, a:active {
		color:#DD4814;
		text-decoration: none;
	}
	a:hover {
    	text-decoration: underline;
	}</pre>

	g. 