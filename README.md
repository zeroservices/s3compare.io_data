# s3compare.io CSV data
This repo provides the data for [s3compare.io](https://www.s3compare.io).\
Feel free to update/add providers by forking and opening a pull-request.

## Rating Mechanism
- 5-star scale (5 is best, 1 is worst)

- Factors considered:
  - Monthly storage cost ($/TB/Mo)
  - Outbound transfer cost (Out/TB)
  - Write operation cost ($/1K Write)
  - Read operation cost ($/1K Read)

- Each factor rated from 1 to 5 stars based on cost

- Overall rating:
  - Average of factor ratings
  - Weighted towards storage and outbound transfer costs

- Fair Use penalty:
  - Subtract 1.5 stars for providers with strict fair use policies

- Final rating rounded to nearest full star
