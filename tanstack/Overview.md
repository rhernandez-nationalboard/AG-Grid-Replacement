#### Overview
1. Define a model
2. Define columns
3. Use table plugin
4. Render using plugin

##### Example Code
```
// define mode
type LogInAttempts = {
  email: string;
  date: string;
  ip: string
}


// Define columns
const columnHelper = createColumnHelper<LogInAttempts>();
const columns = [
  columnHelper.accessor('email', {
    cell: info => info.getValue(),
    footer: info => info.column.id,
  }),
  columnHelper.accessor('date', {
    cell: info => info.getValue(),
    footer: info => info.column.id,
  }),
    columnHelper.accessor('ip', {
    cell: info => info.getValue(),
    footer: info => info.column.id,
  })
];

// Render table
export const LoginTable = () => {
  const [data, setData] = useState<LoginAttempts[]>([]);
  const table = useReactTable({ columns, data, getCoreRowModel: getCoreRowModel(), });

  // load data
  useEffect(() => {
    setData([
      { email: '', date: '', ip: ''},
    ])
  }, []);

  // render table
  return (<div>
    <table>
      <thead>
        {table.getHeaderGroups().map((headerGroups) => (
          <tr key={headerGroups.id}>
            {headerGroups.headers.map((header) => (
              <th key={header.id}>
                {header.isPlaceholder
                  ? null
                  : flexRender(header.column.columnDef.header, header.getContext())}
              </th>
            ))}
          </tr>
        ))}
      </thead>
      <tbody>
        {table.getRowModel().rows.map((row) => (
          <tr key={row.id}>
            {row.getVisibleCells().map((cell) => (
              <td key={cell.id}>
                {flexRender(cell.column.columnDef.cell, cell.getContext())}
              </td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  </div>)
}
```