1. The Compiler (The easy part)
On macOS, you don't need to hunt for libclang headers. Just make sure you have the Xcode Command Line Tools installed. Open your Mac terminal and run:

Bash
xcode-select --install
This gives you cc and clang natively.

2. The tree-sitter-cli (The better part)
You won't have the "GLIBC version too old" error on a Mac because macOS doesn't use GLIBC (it uses Libc). You can install the CLI easily using Homebrew or Cargo.

The Homebrew way (Easiest):

Bash
brew install tree-sitter
The Cargo way (If you're a Rust fan):

Bash
cargo install tree-sitter-cli
3. Your Config is Portable!
Since you used require('nvim-treesitter.install').compilers = { 'cc', 'gcc' } in the config we wrote, it will work perfectly on the Mac. macOS will see cc and map it to Apple Clang automatically.

One "Gotcha" to watch for on Mac
If you use an M1/M2/M3 (Apple Silicon) Mac, occasionally the parsers will try to compile for the wrong architecture if your terminal is running under Rosetta (Intel emulation).

The Fix: Make sure your terminal (iTerm2, Alacritty, or Kitty) is running natively. You can check by running arch in the terminal; it should say arm64.

Summary for your Macbook:
Install Homebrew (if you haven't).

Run brew install tree-sitter.

Copy your new init.lua over.

Run :TSUpdate and you're done. No apt, no libclang errors, no headaches.