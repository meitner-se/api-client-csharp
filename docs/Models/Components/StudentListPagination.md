# StudentListPagination

Pagination information


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Offset`                                                     | *long*                                                       | :heavy_check_mark:                                           | Number of items to skip from the beginning of the result set | 0                                                            |
| `Limit`                                                      | *long*                                                       | :heavy_check_mark:                                           | Maximum number of items to return in the result set          | 1                                                            |
| `Total`                                                      | *long*                                                       | :heavy_check_mark:                                           | Total number of items available for pagination               | 100                                                          |