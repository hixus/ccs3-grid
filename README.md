ccs3-grid
=========

Simplistic CSS3-grid with only two classes .row and .col (really it's that simple!).

##Why new grid

I like grids but don't like the idea where I need to put different classes, depending on how many columns I need (col1, col2, col3, etc.). 

My grid needs to only know what is a row (.row) and what is a column (.col). The magic is in the :nth-last-of-type() selector.

```	div.col:nth-last-of-type(1) {width: 100%;}```
```	div.col:nth-last-of-type(2), div.col:nth-last-of-type(2) + div.col {width: 50%;}```
```	
div.col:nth-last-of-type(3), 
div.col:nth-last-of-type(3) + div.col,
div.col:nth-last-of-type(3) + div.col + div.col {width: 33.3333%;}
```

##How to use

You create a row by making a div with class row. Inside a row you can divide your content with class col divs. For example this makes one row with three columns:

```
<div class="row">
	<div class="col"> ... </div>
	<div class="col"> ... </div>
	<div class="col"> ... </div>
</div>
```

You can also put rows inside columns and there fore create as many subcolumns as needed. This creates a row with 2 colums where first column is nested with row with 2 columns.

```
<div class="row">
	<div class="col">
		<div class="row">
			<div class="col"> ... </div>
			<div class="col"> ... </div>
		</div>
	</div>
	<div class="col"> ... </div>
</div>
```

##How about that crappy old IE8?

Crappy old IE8 needs little javascript to get this working. This adds usual col1, col2, col3 classes.

``` 
$(document).ready(function(){
	$('div.row').each(function() {
		var $cols = $(this).find('> div.col');
		$cols.addClass('col' + $cols.length);
	});
});
```

##I'm insane and need 48 columns. How can I do this?

I haven't had a need for more than 3 columns, so I did not bother to create more than 3. If you don't want to nest rows inside columns you can always extend the idea.

This selects a column if its the only one inside a row:
```
div.col:nth-last-of-type(1)
```

This selects first column from row with two columns:
```
div.col:nth-last-of-type(2)
```

This one selects the second column from row with two columns:
```
div.col:nth-last-of-type(2) + div.col
```

#Licence
I'm not sure if a couple lines of code can have any copyrights but then again it's way more than rounded corners in Apple's products. So for your peace of mind I grant you the license to use this code how ever you want without any demands from my self. 