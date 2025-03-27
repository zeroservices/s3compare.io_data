# s3compare.io CSV data
This repo provides the data for [s3compare.io](https://www.s3compare.io).\
Feel free to update/add providers by forking and opening a pull-request.

## Performance Benchmarks
- Built using warp and a python wrapper
- Benchmarks are run from a client with 8 CPU cores, 32Gb RAM, 10GigE
- Benchmark client is < 5ms network latency away from s3 endpoint

###Benchmarks run per field
| Benchmark | Operation | Concurrency | Object Size | Result | Command |
|-----------|-----------|-------------|-------------|--------|---------|
| perf_get_100mb_16 | GET | 16 | 100 MiB | Mbps | `warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_get_100MB_16 --obj.size 100MB --objects 250 --tls` |
| perf_get_4000mb_1 | GET | 1 | 4000 MiB | Mbps | `warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 1 --benchdata benchmark_results/s3.example.org_get_4000MB_1 --obj.size 4000KB --objects 1 --tls` |
| perf_put_100mb_16 | PUT | 16 | 100 MiB | Mbps | `warp put --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_put_100MB_16 --obj.size 100MB --tls` |
| perf_get_ops_16 | GET | 16 | 1 KiB | obj/s | `warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_get_1KB_16 --obj.size 1KB --objects 100000 --tls` |
| perf_put_ops_16 | PUT | 16 | 1 KiB | obj/s | `warp put --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_put_1KB_16 --obj.size 1KB --tls` |
| perf_list_ops_16 | LIST | 16 | 1 KiB | obj/s | `warp list --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_list_1KB_16 --obj.size 1KB --objects 100000 --tls` |
| perf_del_ops_16 | DELETE | 16 | 1 KiB | obj/s | `warp delete --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 16 --benchdata benchmark_results/s3.example.org_delete_1KB_16 --obj.size 1KB --objects 100000 --tls` |
| perf_get_ops_150 | GET | 150 | 1 KiB | obj/s | `warp get --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 150 --benchdata benchmark_results/s3.example.org_get_1KB_150 --obj.size 1KB --objects 100000 --tls` |
| perf_put_ops_150 | PUT | 150 | 1 KiB | obj/s | `warp put --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 150 --benchdata benchmark_results/s3.example.org_put_1KB_150 --obj.size 1KB --tls` |
| perf_list_ops_150 | LIST | 150 | 1 KiB | obj/s | `warp list --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 150 --benchdata benchmark_results/s3.example.org_list_1KB_150 --obj.size 1KB --objects 100000 --tls` |
| perf_del_ops_150 | DELETE | 150 | 1 KiB | obj/s | `warp delete --host s3.example.org:443 --access-key abc --secret-key def --bucket benchmark --duration 5m --concurrent 150 --benchdata benchmark_results/s3.example.org_delete_1KB_150 --obj.size 1KB --objects 100000 --tls` |
