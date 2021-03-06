# ng2-breadcrumb
This component generates a breadcrumb trail, as you navigate to child routes using the @angular/router. It interprets the browser URL of a navigate request, 
in the same way the component router does to match a path to a specific component, to build up a hierarchy of available parent/child routes for that destination.

So given a navigation request to a url '/comp1/comp2/comp3', a breadcrumb trail with 3 levels will be generated. Each level includes all the elements from the previous 
level along with the next child. Thus the above url request will result in the following 3 levels being generated: '/comp1', '/comp1/comp2', '/comp1/comp2/comp3'.

Theres a breadcrumbService that allows you to add friendly names for each of your app's available routes. This friendly name will show up in the breadcrumb trail 
for each matching level, otherwise it will show the full url fragment.

Below is an example of how to use the breadcrumbService, to give friendly names to the 3 levels availbe in the example app.

	constructor(private breadcrumbService: BreadcrumbService) {
		breadcrumbService.addFriendlyNameForRoute('/comp1', 'Comp 1');
		breadcrumbService.addFriendlyNameForRoute('/comp1/comp2', 'Comp 2');
		breadcrumbService.addFriendlyNameForRoute('/comp1/comp2/comp3', 'Comp 3');
	}

For a live example see: http://plnkr.co/BO2ruqRzNeu5BsZqCYtW

## Dependencies
Requires bootstrap.css (v 3.x.x) for styling of some elements (although the component is fully functional without it).

## Install
Install the module via npm:

    npm install ng2-breadcrumb --save

## Usage
Import the BreadcrumbService and make it available as a global provider when you bootstrap your app:

	import {BreadcrumbService} from 'ng2-breadcrumb/ng2-breadcrumb';

	bootstrap(App, [
		BreadcrumbService
	])

Import both the BreadcrumbComponent & BreadcrumbService into your component and update its directive list:

	import {BreadcrumbComponent, BreadcrumbService} from 'ng2-breadcrumb/ng2-breadcrumb';

	@Component({
		directives: [BreadcrumbComponent]
	})
	class Component {
		...
	}
	
Inject the BreadcrumbService via the component's constructor, so you can add friendly names for each of your apps routes:

	constructor(private breadcrumbService: BreadcrumbService) {
		breadcrumbService.addFriendlyNameForRoute('/home', 'Home Sweet Home');
	}

Place the breadcrumb selector in your component's html where you added your router-outlet:

	<breadcrumb></breadcrumb>
	<router-outlet></router-outlet>
    
## Build
To compile the project locally just run the default gulp task (ensure you have gulp install globally to do this):

    gulp
