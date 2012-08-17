multiSuggest
============

jQuery plugin for categorized input suggestions.

Example:
```
	// Input element.
	var $input = $( '#exampleInput' );
	// Multi Suggest configuration.
	var options = {
		'parent': $input.parent(),
		'prefix': 'example-multi',

		// Build suggestion groups in order.
		'suggestions': function( params ) {
			// Generic params object.
			var example = params.example,
				example2 = params.example2,
				query = params.query;
				groups = {
					// Set 1
					query: {
						label: 'Query',
						items: [query],
						itemClass: 'query-class'
					},
					// Set 2
					exampleGroup: {
						label: 'Example 1',
						items: example,
						itemClass: 'example-class'
					},
					// Set 3
					exampleGroup2: {
						label: 'Example 2',
						items: example2,
						itemClass: 'example-class'
					}
				};
			// Return the groups object.
			return groups;
		},
		// Called on succesfull input.
		'input': function( callback ) {
			var query = $input.val();
			// Example params object.
			var params = {
					query: query,
					example: ['example item 1', 'example item 2', 'example item 3', 'example item 4'],
					example2: ['example item 5', 'example item 6']
			};
			// Build with params.
			callback( params );
		}
	};

	// Setup
	$input.multiSuggest( options );
```
