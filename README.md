# wiresponge

*wiresponge* is a GameBoy Color emulation library designed
to run on virtually anything, including bare metal systems.

## Cool, but why?
Standard emulators are often made with a few assumptions about the OS,
available libraries and memory size.

On the other hand, *wiresponge*, doesn't assume anything, which makes it
**extremely** portable.
It provides a complete GameBoy Color emulator, and only expects you
to describe how it should fetch ROM data, how inputs are mapped,
and how it should communicate with video and audio output devices. This is done
cleanly using Rust's trait system.

Obviously, it was also meant to run on extremely limited hardware,
so it **is** "blazingly ~~fast~~ efficient" as the kool kids say.

## Requirements
Still, there's a bare minimum of computing power necessary to run
it:
- todo, I haven't yet tested that properly

Those metrics are computed using the assembly code produced for various
targets. The only definitive metrics are memory related ones, since this does
not vary from system to system.

## Usage
The (almost) sole exposed struct is `Gbc`. It defines two functions:
```rust
/// Creates a GameBoy Color emulator using the given devices
fn new(
    rom: &dyn Memory,
    input: &dyn InputDevice,
    audio: &mut dyn AudioDevice, 
    video: &mut dyn VideoDevice,
) -> Gbc {
    ...
}
/// Runs a single, complete fetch/decode/execute cycle
fn step_once(&mut self) {
    ...
}
```
Note that this is subject to change slightly until version 1.0, but the core 
idea will stay the same

As you can see, it makes extensive use of Rust's traits to grant
a lot of freedom in the implementation. This means that although I'd
truly like to, I can't help you when it comes to implementing the
rest: it depends on what you want to run a GameBoy emulator on.

## Hall of fame
This is a pre-created section, but I'd like to showcase implementations
using this library. It's a pretty cool embedded programming project, trust me!

(this is obviously empty for now tho, the lib is not working)
