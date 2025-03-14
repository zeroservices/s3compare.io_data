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

## Performance Benchmarks
- Built using warp and a python wrapper
- Benchmarks are run from a client with 8 CPU cores, 32Gb RAM, 10GigE
- Benchmark client is < 5ms network latency away from s3 endpoint

- Benchmarks run per field:
  - perf_get_ops_16: warp get @ concurrency 16, 1KiB files (warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_get_1KB_16 --obj.size 1KB --objects 100000 --tls) => throughput in obj/s
  - perf_put_ops_16: warp put @ concurrency 16, 1KiB files (warp put --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_put_1KB_16 --obj.size 1KB --tls) => throughput in obj/s
  - perf_list_ops_16: warp list @ concurrency 16, 1KiB files (warp list --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_list_1KB_16 --obj.size 1KB --objects 100000 --tls) => throughput in obj/s
  - perf_del_ops_16: warp delete @ concurrency 16, 1KiB files (warp delete --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_delete_1KB_16 --obj.size 1KB --objects 100000 --tls) => throughput in obj/s
  - perf_get_100mb_16: warp get @ concurrency 16, 100MiB files (warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_get_100MB_16 --obj.size 100MB --objects 250 --tls) => througput in Mbps
  - perf_get_4000mb_1: warp get @ concurrency 1, 4000MiB files (warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 1 --benchdata benchmark_results/s3.example.org_get_4000MB_1 --obj.size 4000KB --objects 1 --tls) => throughput in Mbps
  - perf_put_100mb_16: warp put @ concurrency 16, 100MiB files (warp put --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_put_100MB_16 --obj.size 100MB --tls)
