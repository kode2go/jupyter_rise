# jupyter_rise

Installed on Miniconda:

Location:

```
C:\Users\...\AppData\Local\miniconda3\share\jupyter\nbextensions\rise
```

# Increase size of cell font and line height

in main.css

```
.rise-enabled .reveal pre {
  transition-property: all;
  transition-duration: 0.2s;
  transition-timing-function: ease;
  font-size: 150%; /* Adjust font size */
  line-height: 1.5; /* Adjust line spacing */
  width: 100%;
  box-shadow: 0px 0px 0px rgba(0, 0, 0, 0);
  overflow: hidden;
}
```

# Add a logo

in main.js

```
 /* load_jupyter_extension */
	function setup() {
	  // load css first
	  $('<link/>')
		.attr({
		  rel: "stylesheet",
		  href: require.toUrl("./main.css"),
		  id: 'maincss',
		})
		.appendTo('head');

	  configLoaded()
		//      .then(showConfig)
		.then(registerJupyterActions)
		.then(addButtonsAndShortcuts)
		.then(autoLaunch)
		.then(() => {
		  // Add global logo to the slides
		  var logo = $('<div class="logo"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c0/Skillshare_logo_2020.svg/320px-Skillshare_logo_2020.svg.png" alt="Logo" width="100"></div>');
		  $('body').append(logo);

		  // Apply CSS to position the logo
		  var logoStyle = `
			.logo {
			  position: absolute;
			  top: 20px;
			  right: 20px;
			  z-index: 9999;
			}
		  `;
		  var styleSheet = document.createElement("style");
		  styleSheet.type = "text/css";
		  styleSheet.innerText = logoStyle;
		  document.head.appendChild(styleSheet);
		});
	}

	setup.load_ipython_extension = setup;
	setup.load_jupyter_extension = setup;

	return setup;
```
