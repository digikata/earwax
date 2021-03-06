[crates.io]: https://crates.io/crates/earwax
[docs.rs]: https://docs.rs/earwax

[![crates.io](https://img.shields.io/crates/v/earwax.svg)][crates.io]
[![docs.rs](https://docs.rs/earwax/badge.svg)][docs.rs]

Audio decoding library based on ffmpeg 2.8. The purpose of this library is
to provide a safe and simple way of converting any audio input to raw PCM data.

## Dependencies

From ffmpeg 2.8, the required libraries are `libavcodec`, `libavformat`, and `libavdevice`.

## Usage

```rust
extern crate earwax;

use earwax::Earwax;

fn main() {
    let mut earwax = Earwax::new("[URL]").unwrap();
    while let Some(chunk) = earwax.spit() {
        // Do something with chunk.data, an array of raw pcm data.
        println!("Time: {}", chunk.time.seconds()); // or chunk.time.pts().
    }
}
```

Check the [documentation][docs.rs] for a detailed reference.

## TODO

* Add error handling to the `spit` function.
