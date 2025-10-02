# HTML Code for a Blur Background
## Copy in a Measure and Insert in HTML Content (Lite) Custom Visual
### Code
```html
<style>
  .blur-background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    backdrop-filter: blur(6px);
    -webkit-backdrop-filter: blur(6px); 
    background: rgba(255, 255, 255, 0.3); /* frosted-glass effect */
    border-radius: 0px; /* optional */
  }
</style>

<div class='blur-background'></div>
```
> Insert this code as a string ("") in a Measure

### Alternative via UDF
#### Define the Function
```dax
DEFINE
	FUNCTION background_html_blur = (
		// opacity between 0 and 1
		opacity:decimal,
		// corner radius in px
		corner_radius:int64
	)
	=>
	
	"
	<style>
	.blur-background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		backdrop-filter: blur(6px);
		-webkit-backdrop-filter: blur(6px); 
		background: rgba(255, 255, 255, "&opacity&"); /* frosted-glass effect */
		border-radius: "&corner_radius&"px; /* optional */
	}
	</style>

	<div class='blur-background'></div>
	"
```
#### Call the function
Call the function in a measure
```sql
background_example = 
// background with 50% opacity and rounded corners at 50px
background_html_blur(0.5, 50)
```
