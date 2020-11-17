"now"

tests/test_quiescent.rs
15:        let start = Instant::now();
19:        let end = Instant::now();

benchmarks/stress2/src/main.rs
305:    let now = std::time::Instant::now();
342:    let time = now.elapsed().as_secs() as usize;
359:        std::thread::current().name().unwrap_or("unknown").to_owned()

src/flusher.rs
66:        let before = std::time::Instant::now();

src/debug_delay.rs
74:        thread::yield_now();

src/threadpool.rs
49:        let cutoff = Instant::now() + duration;

src/metrics.rs
46:    static START: Lazy<Instant, fn() -> Instant> = Lazy::new(Instant::now);

src/config.rs
452:        let now = SystemTime::now()
464:        let salt = (pid << 16) + now + seed;

src/pagecache/mod.rs
1004:            let time_now =
1005:                SystemTime::now().duration_since(UNIX_EPOCH).unwrap();
1008:            let fail_seed = std::cmp::max(3, time_now.as_nanos() as u32 % 128);
1172:            let time_now =
1173:                SystemTime::now().duration_since(UNIX_EPOCH).unwrap();
1176:            let fail_seed = std::cmp::max(3, time_now.as_nanos() as u32 % 128);
2142:        let stable_lsn_now: Lsn = self.log.stable_offset();
2160:                        std::thread::yield_now();
2171:                    std::thread::yield_now();
2177:            stable_lsn: Some(stable_lsn_now),

"time"

benchmarks/stress2/src/main.rs
144:        thread::sleep(std::time::Duration::from_secs(1));
305:    let now = std::time::Instant::now();
329:            thread::sleep(std::time::Duration::from_millis(50));
333:        thread::sleep(std::time::Duration::from_secs(args.duration));
342:    let time = now.elapsed().as_secs() as usize;
347:        time,
348:        (ops * 1_000) / (time * 1_000)

src/debug_delay.rs
12:    use std::time::Duration;

src/threadpool.rs
7:    time::{Duration, Instant},
46:    fn recv_timeout(&self, duration: Duration) -> Option<Work> {
55:            if res.timed_out() {
103:        let task_res = QUEUE.recv_timeout(wait_limit);

src/metrics.rs
7:use std::time::{Duration, Instant};
37:            let u = uptime();
45:pub(crate) fn uptime() -> Duration {
65:    /// The time delta from ctor to dtor is recorded in `histo`.

src/config.rs
446:        use std::time::SystemTime;

src/pagecache/iobuf.rs
1003:                let timeout = iobufs
1005:                    .wait_for(&mut waiter, std::time::Duration::from_secs(30));
1006:                if timeout.timed_out() {

src/pagecache/mod.rs
998:            use std::time::{SystemTime, UNIX_EPOCH};
1004:            let time_now =
1008:            let fail_seed = std::cmp::max(3, time_now.as_nanos() as u32 % 128);
1166:            use std::time::{SystemTime, UNIX_EPOCH};
1172:            let time_now =
1176:            let fail_seed = std::cmp::max(3, time_now.as_nanos() as u32 % 128);

tests/test_crash_recovery.rs
8:use std::time::Duration;
127:        let runtime = rand::thread_rng().gen_range(0, 60);
128:        thread::sleep(Duration::from_millis(runtime));

src/flusher.rs
2:use std::time::Duration;
66:        let before = std::time::Instant::now();

tests/test_quiescent.rs
5:use std::time::{Duration, Instant};
10:fn test_quiescent_cpu_time() {
21:        let (user_cpu_time, system_cpu_time) = unsafe {
30:            (resource_usage.ru_utime, resource_usage.ru_stime)
34:            user_cpu_time.tv_sec as f64 + user_cpu_time.tv_usec as f64 * 1e-6;
35:        let system_cpu_seconds = system_cpu_time.tv_sec as f64
36:            + system_cpu_time.tv_usec as f64 * 1e-6;
37:        let real_time_elapsed = end.duration_since(start);
44:                real_time_elapsed.as_secs_f64(),
