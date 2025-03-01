
# DataTables component for Vue 3

This library provides a Vue 3 component for [DataTables.net](https://datatables.net) to be used inside a Vue application.

To install:

```
npm install --save datatables.net-vue
```

This will automatically install DataTables as a dependency. Other DataTables extensions can also be installed in your application - see below.

In your Vue component you can then:

```js
import DataTable from 'datatables.net-vue'
```

Which makes a `DataTable` component available. It provides the following parameters:

* `columns` - Define the columns array used for [DataTables initialisation](https://datatables.net/reference/option/#datatables%20-%20columns)
* `data` - [Data array for DataTables](https://datatables.net/reference/option/data). This is _optional_ and if you are using Ajax to load the DataTable data is not required.
* `ajax` - [Ajax option for DataTables](https://datatables.net/reference/option/ajax) - to load data for the table over Ajax.
* `class` - Class name to assign to the `table` tag
* `options` - The [DataTables options](https://datatables.net/reference/option) for the table. Note that this can include `columns`, `data` and `ajax` - if they are provided by one of the properties from above that will override a matching option given here.


### Templates

The `DataTable` component provides a single slot that can be used to define the HTML for the table structure - i.e. the `thead` and `tfoot`:

```html
<DataTable :data="[[1,2], [3,4]]" class="display">
	<thead>
		<tr>
			<th>A</th>
			<th>B</th>
		</tr>
	</thead>
</DataTable>
```

**IMPORTANT** You should not use a Vue `for` in the template to display the HTML for the table body! Doing so will cause a conflict between DataTables and Vue both trying to control the same DOM elements. Allow DataTables to build the HTML for the rows.


## Extensions

DataTables provides [a wide range of extensions](https://datatables.net/extensions/index) that singificantly expands its abilities. Extensions can be imported from npm and then registered with DataTables through it's `use()` method - e.g.:

```js
import DataTable from 'datatables.net-vue'
import Select from 'datatables.net-select';

DataTable.use(Select);
```


## Styling

The Vue component for DataTables doesn't include any styling by default. We provide support for a number of different styling libraries, and you will need to install those that you require and for any additional extensions you require.

For example, to use Bootstrap 5 styling, you would install the `-bs5` packages for DataTables:

```
npm install datatables.net-bs5
npm install datatables.net-select-bs5
```

And in your Vue application's CSS (assuming your are using Vite or some other builder which can resolve the `style` property for npm packages):

```css
@import 'datatables.net-dt';
@import 'datatables.net-select-dt';
```
