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
	#logo {
		font-size: 1em;
		padding-right:.25em;
	}
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
	}
	#logo a:after {
    	content:": /"
	}</pre>

	i. Let's customize the color and behavior of the anchors tags
	<pre>
	a, a:link, a:visited, a:focus, a:active {
		color:#DD4814;
		text-decoration: none;
	}
	a:hover {
    	text-decoration: underline;
	}</pre>

7. We will now customize the look of the breadcrumbs, so let's first create a breadcrumbs module in Joomla, assign it to the "breadrumbs" position. Set Show "You are here" to No.

8. As you can see, the breadcrumbs are not where we want them, so we will now override the default layout of the template. This is done by either editing the template's root index.php file or by creating an extended template override, something unique to Construct.
	* Open the installation package and copy the <b>layouts/index.php</b> file to the <b>layouts</b> directory of your
	template.
	* We created the layout override capability to allow for you to be able to create custom layouts and to be able to later upgrade the template without loosing your customizations.

9. Open this file ( layouts/index.php ) in your editor and cut/paste lines 175-177 to directly after the logo on line 103.
	<pre>
	&lt;? php if ($this->countModules('breadcrumbs')) : ?>
		&lt;jdoc:include type="module" name="breadcrumbs" />
	&lt;? php endif; ?></pre>

10. While we are editing the layout of the template, let's remove the in-page links by deleting lines  113-124
	<pre>
	&lt;nav&gt;
		&lt;ul id="access"&gt;
		  &lt;li&gt;Jump to:&lt;/li&gt;
		  &lt;li&gt;<a href="&lt;? php $url->setFragment('content'); echo $url->toString();?>" class="to-content">Content</a>&lt;/li&gt;
		  &lt;? php if ($this->countModules('nav')) : ?>
			&lt;li&gt;<a href="&lt;? php $url->setFragment('nav'); echo $url->toString();?>" class="to-nav">Navigation</a>&lt;/li&gt;
		  &lt;? php endif; ?>
		  &lt;? php if ($contentBelowCount) : ?>
			&lt;li&gt;<a href="&lt;? php $url->setFragment('additional'); echo $url->toString();?>" class="to-additional">Additional Information</a></li>
		  &lt;? php endif; ?>
		&lt;/ul&gt;
	&lt;/nav&gt;</pre>

11. We'll also move the main navigation to 