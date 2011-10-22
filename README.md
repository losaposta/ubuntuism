Ubuntuism is a demo template developed to explore rapid template development for the Joomla! CMS. Ubuntuism is built with a modified version of Construct5, a unified HTML5 version of the Construct Template Development Framework from http://construct-framework.com

See http://betweenbrain.github.com/ubuntuism for the introductory presentation.

#To Get Started With Construct#
The Construct Template Development Framework is a code based solution with the goal of streamlining the process of creating one-of-a-kind Joomla! templates while not limiting your creative abilities. To get started with this demo version of Construct, <a href="https://github.com/betweenbrain/ubuntuism/zipball/master">Download</a> and install the template as you would any extension. Once installed, set *Ubuntuism* as your default template and start creating your unique look by adding your unique styles to the demo.css style sheet. Learn more about developing custom templates with Construct by visiting http://construct-framework.com

#Step By Step Guide To Creating Ubuntuism#
For this exploration, we will recreating the Ubuntu 11.04 classic desktop experience as a Joomla template.

1. Start with a clean installation of Joomla, preferably the latest version, with sample data installed.
2. Install the *Ubuntuism* demo template.
3. Set *Ubuntuism* as the default template in Joomla's template manager.
4. Open */templates/ubuntuism/demo.css* in your favorite editor and begin adding the custom styles for this template:

	Define the background image (already installed in the images directory for you)
	<pre>
	html {
    	background-image: url('../images/wallpaper.jpg');
    	background-position: 50% 50%;
    	background-repeat:no-repeat;
    	background-attachment:fixed;
	}</pre>

	Set the body width to 90.5em and give it some larger top and bottom margins
	<pre>
	body {
    	max-width:90.5em;
    	margin:50px auto;
    }</pre>

    Go ahead and add a dark aubergine background, with an opacity of .8
    <pre>
    body {
    	max-width:90.5em;
    	margin:50px auto;
    	background: rgba(44, 0, 30,.8);
    }</pre>

    Set the body font to 'Ubuntu' (we'll add this font later), and set the font color to white
    <pre>
    body {
    	max-width:90.5em;
    	margin:50px auto;
    	background: rgba(44, 0, 30,.8);
    	font-family: 'Ubuntu', sans-serif;
    	color:#fff;
    }</pre>

	Give the body a border, some nice rounded corners and a drop shadow:
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

	Let's give the primary header a nice grey gradient background and rounded corners to match the body
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

	Since Construct gives the primary header gutter a default margin of 10px, we need to override that style to line it
	up with the body. We'll add some padding while we are at it.
	 <pre>
	 #header .gutter {
		padding:.5em 0 0 .5em;
		margin:0 1em .5em 0;
	}</pre>

	Once again, we will override Construct's default style, this time for the logo. Note that we are setting the text-indent to auto so that the text can be displayed instead of an image.
	<pre>
	#logo {
		font-size: 1em;
		padding:.2em;
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

	Let's customize the color and decoration of the anchors tags
	<pre>
	a, a:link, a:visited, a:focus, a:active {
		color:#DD4814;
		text-decoration: none;
	}
	a:hover {
    	text-decoration: underline;
	}</pre>

5. We will now customize the look of the breadcrumbs, so let's first create a breadcrumbs module in Joomla, assign it to the "breadcrumbs" position. Set Show "You are here" to No.

6. While we're at it, let's go ahead and change the module position assignment of the Main Menu module from *position-7* to *nav*. Set the module assignment to *On All Pages*.

7. As you preview the site, we can see that the breadcrumbs are not where we want them, so we will now override the default layout of the template. This is done by either editing the template's root index.php file or by creating an <a href="http://construct-framework.com/intermediate/extended-template-overrides">extended template override</a>, something unique to Construct.
	* For this demo, the extended template override has already been installed to *templates/ubuntuism/layouts/index.php*.
	* The layout override capability was created to allow you to create custom layouts, if you don't like the default one, and to still be able to upgrade the template without loosing your customizations.

8. Open *templates/ubuntuism/layouts/index.php* in your favorite editor and move the following lines of code (175-177) to directly after the logo on line 103.
	<pre>
	&lt;?php if ($this->countModules('breadcrumbs')) : ?&gt;
		&lt;jdoc:include type="module" name="breadcrumbs" />
	&lt;?php endif; ?&gt;</pre>

9. While we are editing the layout override of the template, let's remove the in-page links by deleting the following lines of code (113-124)
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

10. We'll also move the main navigation, lines 167-171, to the final portion of the primary header, so that it now begins at line 121
   <pre>
	&tl;?php if ($this->countModules('nav')) : ?&gt;
		&lt;nav id="nav" class="clear clearfix"&gt;
			&lt;jdoc:include type="modules" name="nav" style="raw" /&gt;
		&lt;/nav&gt;<!-- end nav-->
	&tl;?php endif; ?&gt;</pre>

11. Let's go ahead and load that custom font, courtesy of Google web Fonts. To do so, simply add the following code to the first block of php code of layouts/index.php:
	<pre>$doc->addStyleSheet('http://fonts.googleapis.com/css?family=Ubuntu');</pre>

12. Let's get back to writing some more CSS, this time to style the main navigation. First, let's add some vertical spacing, borders and *float to fix*
	<pre>
	#nav {
		margin:5px 0 0 0;
		border-top:1px solid #454545;
		border-bottom:1px solid #333;
		float:left;
		width:100%;
	}</pre>

13. Next, we'll add a bit of padding, color and font styles to the menu items
	<pre>
	#nav ul.menu li a,
	#nav ul.menu li span.separator {
		padding:2px 6px;
		color:#fff;
		font-weight:normal;
		font-size:1.2em;
		line-height:1.4em;
	}</pre>

14. Let's go ahead and add some style to our parent menu items
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

15. Let's not forget the children
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

16. The close, minimize and maximize buttons can be simulated with the style sheet switcher and the addition of two style sheets.
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

17. Go ahead and move the follow code (166-122), to just before the logo on line 106
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

18. The final touch is to add the following css to your custom style sheet to bring the simulated buttons to life
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