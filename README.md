Angular directive to create a responsive steps section

Warnings:

The labels are positioned absolutely, so make sure they're not overflowing onto the div below.	Adding some padding to the bottom of the container fixes it. (I didn't add it because it depends on the size of font you're using).

Make sure you set position relative or absolute on my-steps or the bar will behave weird.


Usage:

"sequential" being defined means that the circles behind the active one also remain active. 
"bar" being defined means that you'll get a bar connecting the circles
"clickable" enables the user to change steps by clicking on the label or circle. May be useful.

	<my-steps active-step="{{ ctrl.activeStep }}" sequential bar clickable> // {{ctrl.activeStep}} can be any variable you want. The first step will have number 1, not 0.
		<div> // call this whatever you'd like but needs to be here
			<step><span>Step 1</span></step>
			<step><span>Step 2</span></step>
			<step><span>Step 3</span></step>
			<step><span>Step 4</span></step>
		</div>
	</my-steps>


CSS RULES---------------------

MANDATORY --------------------

		my-steps{
			position:relative;
		}

		.circles{
			display:flex;
			justify-content:space-between;
			position:relative;
		}

		.circle{
			background:#EEE; // optional
			z-index:2;
			position:relative;
		}

		.bar{
			background:#EEE; // optional 
			z-index:1; // leave this
		}

		
	//Whatever color you put in here will be the color of labels that aren't active
	step{
		padding-top:10px; // optional
		color:#DDD; //optional
	}

	//Self explanatory
	step.active{
		color:#444; // optional
	}

	//This will help keep consistency
	step span{
		white-space: nowrap; //optional
	}

	//This defines the styles on the circle filling, when it's the current step (active)
	//If you don't want filling just delete these rules
	.circle.active:before{
		content:'';
		position:absolute;
		top:5px;
		left:5px;
		bottom:5px;
		right:5px;
		border-radius:50%;
		z-index:3;
	}

	//Other bar styling must be defined in the config part of the directive (near top)
	.bar-fill{ 
		transition:all 200ms ease-in-out; //optional
	}