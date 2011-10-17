A template developed to demonstrate rapid template development for the Joomla! CMS. It is a modified version of Construct5, a unified / HTML5 version of the Construct Template Development Framework from http://construct-framework.com

Please see http://betweenbrain.github.com/ubuntuism for the introductory presentation.

#How to use this framework#
The Construct Template Development Framework is a code based solution with the goal of streamlining the process of creating one-of-a-kind Joomla! templates, while not limiting your ability to add every bit of your creativity. To get started, install Construct like you would any Joomla extension. Then add a new style sheet to the CSS directory of Construct and select that style sheet in the template's settings from within template manager of Joomla.

#Step by step#
For the workshop, we will recreating the Ubuntu 11.04 classic desktop experience as a Joomla template.

1. Start with a clean installation of Joomla, preferably 1.7, with sample data installed.
2. <a href="https://github.com/betweenbrain/ubuntuism/zipball/master">Download</a> the master branch zip and
install it as you would any extension.
3. Set *ubuntuism* as the default template in Joomla's template manager.
4. Create a blank styles sheet, named whatever you'd like, within the CSS directory of the *ubuntuism* template (i.e. var/www/joomla/templates/ubuntuism/css ).
5. Open *ubuntuism* in Template Manager: Styles (in Joomla 1.7) and select the name of the style sheet that you just
created in the Custom Style Sheet drop-down. While we're in there, under the Layout parameter section, select Off next to Use CSS Sticky Footer. Click Save & Close.
6. Open the style sheet that you just created in your favorite editor and begin adding the custom styles for this template:

	a. Set the background image (available within the images directory of the installer file that you downloaded,
	or at https://github.com/betweenbrain/ubuntuism/raw/master/images/wallpaper.jpg) :
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

7. We will now customize the look of the breadcrumbs, so let's first create a breadcrumbs module in Joomla, assign it to the "breadcrumbs" position. Set Show "You are here" to No.

8. While we're at it, let's go ahead and change the module position assignment of the Main Menu module from *position-7* to *nav*. Set the module assignment to *On All Pages*.

9. As you can see, the breadcrumbs are not where we want them, so we will now override the default layout of the template. This is done by either editing the template's root index.php file or by creating an extended template override, something unique to Construct.
	* Open the installation package and copy the <b>layouts/index.php</b> file to the <b>layouts</b> directory of your
	template.
	* We created the layout override capability to allow for you to be able to create custom layouts and to be able to later upgrade the template without loosing your customizations.

10. Open this file ( layouts/index.php ) in your editor and cut/paste lines 175-177 to directly after the logo on line 103.
	<pre>
	&lt;?php if ($this->countModules('breadcrumbs')) : ?&gt;
		&lt;jdoc:include type="module" name="breadcrumbs" />
	&lt;?php endif; ?&gt;</pre>

11. While we are editing the layout of the template, let's remove the in-page links by deleting lines  113-124
	<pre>
	&lt;nav&gt;
		&lt;ul id="access"&gt;
		  &lt;li&gt;Jump to:&lt;/li&gt;
		  &lt;li&gt;&lt;a href="&lt;?php $url->setFragment('content'); echo $url->toString();?&gt;" class="to-content"&gt;Content&lt;/a&gt;&lt;/li&gt;
		  &lt;?php if ($this->countModules('nav')) : ?&gt;
			&lt;li&gt;&lt;a href="&lt;?php $url->setFragment('nav'); echo $url->toString();?&gt;" class="to-nav"&gt;Navigation&lt;/a&gt;&lt;/li&gt;
		  &lt;?php endif; ?&gt;
		  &lt;?php if ($contentBelowCount) : ?&gt;
			&lt;li&gt;&lt;a href="&lt;?php $url->setFragment('additional'); echo $url->toString();?&gt;" class="to-additional"&gt;Additional Information&lt;/a&gt;&lt;/li&gt
		  &lt;?php endif; ?&gt;
		&lt;/ul&gt;
	&lt;/nav&gt;</pre>

12. We'll also move the main navigation, lines 167-171, to the final portion of the primary header, so that it now begins at line 121
   <pre>
	&tl;?php if ($this->countModules('nav')) : ?&gt;
		&lt;nav id="nav" class="clear clearfix"&gt;
			&lt;jdoc:include type="modules" name="nav" style="raw" /&gt;
		&lt;/nav&gt;<!-- end nav-->
	&tl;?php endif; ?&gt;</pre>

13. Let's go ahead and load that custom font, courtesy of Google web Fonts. To do so, simply add the following code to the first block of php code of layouts/index.php:
	<pre>$doc->addStyleSheet('http://fonts.googleapis.com/css?family=Ubuntu');</pre>

14. Let's get back to writing some more CSS, this time to style the main navigation. First, let's add some vertical spacing, borders and *float to fix*
	<pre>
	#nav {
		margin:5px 0 0 0;
		border-top:1px solid #454545;
		border-bottom:1px solid #333;
		float:left;
		width:100%;
	}</pre>

15. Next, we'll add a bit of padding, color and font styles to the menu items
	<pre>
	#nav ul.menu li a,
	#nav ul.menu li span.separator {
		padding:2px 6px;
		color:#fff;
		font-weight:normal;
		font-size:1.2em;
		line-height:1.4em;
	}</pre>

16. Let's go ahead and add some style to our parent menu items
	<pre>
	#nav ul.menu li.parent:hover {
		background-color: #666666;
		background-image: -webkit-gradient(linear, left top, left bottom, from(#666666), to(#454545)); /* Saf4+, Chrome */
		background-image: -webkit-linear-gradient(top, #666666, #454545); /* Chrome 10+, Saf5.1+ */
		background-image:    -moz-linear-gradient(top, #666666, #454545); /* FF3.6 */
		background-image:     -ms-linear-gradient(top, #666666, #454545); /* IE10 */
		background-image:      -o-linear-gradient(top, #666666, #454545); /* Opera 11.10+ */
		background-image:         linear-gradient(top, #666666, #454545);
		filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#666666', EndColorStr='#454545');
		-moz-border-radius: 6px 6px 0 0;
		-webkit-border-radius: 6px 6px 0 0;
		border-radius: 6px 6px 0 0;
		-moz-background-clip: padding;
		webkit-background-clip: padding-box;
		background-clip: padding-box;
	}</pre>

17. Let's not forget the children
	<pre>
	#nav ul.menu ul {
		background-color: #454545;
		-moz-border-radius: 0 6px 6px 6px;
		-webkit-border-radius: 0 6px 6px 6px;
		border-radius: 0 6px 6px 6px;
		-moz-background-clip: padding;
		webkit-background-clip: padding-box;
		background-clip: padding-box;
	}</pre>

18. The close, minimize and maximize buttons can be simulated with the style sheet switcher and the addition of two style sheets.
	NOTE: We will leave the Layout Aid parameter set to Hide, as this also loads the style sheet switcher, but with a different set of style sheets.

	We start be adding manually enabling the style sheet switcher, and loading of two custom stylesheets, by adding the following code to our custom layout ( layouts/index.php ).
	<pre>
	$doc->addCustomTag('&lt;link rel="alternate stylesheet" href="'.$template.'/css/close.css" type="text/css" media="screen" title="close" /&gt;');
	$doc->addCustomTag('&lt;link rel="alternate stylesheet" href="'.$template.'/css/minimize.css" type="text/css" media="screen" title="minimize" /&gt;');
	$doc->addScript($template.'/js/styleswitch.js')</pre>

	These two style sheets need to be created, and added to the css directory of your template.

	close.css needs to only contain <pre>
	body {
    	display:none;
	}</pre>

	minimize.css needs to only contain <pre>
	body {
		margin-top:55%;
		height:35px;
		overflow:hidden;
	}</pre>
	Adjust either to suit your personal tastes.

19. Go ahead and move the follow code (lines 166-122), to just before the logo on line 106
	<pre>
	&tl;?php if ($enableSwitcher) : ?&gt;
		&lt;ul id="style-switch"&gt;
			&lt;li&gt;&lt;a href="#" onclick="setActiveStyleSheet('wireframe'); return false;" title="Wireframe"&gt;Wireframe&lt;/a&gt;&lt;/li&gt;
			&lt;li&gt;&lt;a href="#" onclick="setActiveStyleSheet('diagnostic'); return false;" title="Diagnostic"&gt;Diagnostic Mode&lt;/a&gt;&lt;/li&gt;
			&lt;li&gt;&lt;a href="#" onclick="setActiveStyleSheet('normal'); return false;" title="Normal"&gt;Normal Mode&lt;/a&gt;&lt;/li&gt;
		&lt;/ul&gt;
	&tl;?php endif; ?&gt;</pre>

	And change them to:
	<pre>
	&lt;ul id="style-switch"&gt;
		&lt;li class="close"&gt;&lt;a href="#" onclick="setActiveStyleSheet('close'); return false;" title="close"&gt;x&lt;/a&gt;&lt;/li&gt;
		&lt;li class="minimize"&gt;&lt;a href="#" onclick="setActiveStyleSheet('minimize'); return false;" title="minimize"&gt;&#95;&lt;/a&gt;&lt;/li&gt;
		&lt;li class="restore"&gt;&lt;a href="#" onclick="setActiveStyleSheet('restore'); return false;" title="restore"&gt;&#91;&#93;&lt;/a&gt;&lt;/li&gt;
	&lt;/ul&gt;</pre>

20. The final touch is to add the following css to your custom style sheet to bring the similated buttons to life
	<pre>
	#style-switch {
		float: left;
		clear: none;
		background:#333333;
		-moz-border-radius: 10px;
		-webkit-border-radius: 10px;
		border-radius: 10px;
		padding:4px 2px 4px 6px;
		margin: 0 5px 0 0;
	}
	#style-switch li {
		padding: 0;
		-moz-border-radius: 10px;
		-webkit-border-radius: 10px;
		border-radius: 10px;
		height: 16px;
		width: 16px;
		float: left;
		margin-right:5px;
		-moz-box-shadow: 1px 1px 6px #888;
		-webkit-box-shadow:  1px 1px 6px #888;
		box-shadow: 1px 1px 6px #000;
	}
	#style-switch a {
		color:#333;
		display:block;
		line-height:1em;
		text-shadow: 0px 0px 1px #666;
	}
	#style-switch .close {
		background: #DD4814;
	}
	#style-switch .close a {
		padding: 1px 0 0 4px;
	}
	#style-switch .minimize,
	#style-switch .restore {
		background: -webkit-gradient(linear, left top, left bottom, from(#333333), to(#888888));
		background: -moz-linear-gradient(top, #333333, #888888);
	}
	#style-switch .minimize a {
		padding: 0 0 0 5px;
		font-size:1em;
		line-height:.5em;
	}
	#style-switch .restore a {
		padding: 1px 0 0 4px;
		font-size:.8em
	}
	#style-switch li:hover {
	  background-color: #999999;
	  background-image: -webkit-gradient(linear, left top, left bottom, from(#999999), to(#666666));
	  background-image: -webkit-linear-gradient(top, #999999, #666666);
	  background-image:    -moz-linear-gradient(top, #999999, #666666);
	  background-image:     -ms-linear-gradient(top, #999999, #666666);
	  background-image:      -o-linear-gradient(top, #999999, #666666);
	  background-image:         linear-gradient(top, #999999, #666666);
	  filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#999999', EndColorStr='#666666');
	}</pre>