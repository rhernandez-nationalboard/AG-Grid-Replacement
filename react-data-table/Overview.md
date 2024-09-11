#### Overview
1. Define columns
2. Populate data

#### Code
```
import DataTable from 'react-data-table-component';

// define columns
const columns = [
	{
		name: 'Title',
		selector: row => row.title,
	},
	{
		name: 'Year',
		selector: row => row.year,
	},
];

// set data
const data = [
  	{
		id: 1,
		title: 'Beetlejuice',
		year: '1988',
	},
	{
		id: 2,
		title: 'Ghostbusters',
		year: '1984',
	},
]

// render component
function MyComponent() {
	return (
		<DataTable
			columns={columns}
			data={data}
		/>
	);
};
```