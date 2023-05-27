# [关于Cargo.toml和Cargo.lock](https://course.rs/cargo/guide/cargo-toml-lock.html)

作用不同，但都是为了版本管理，例如本项目依赖于其他github项目，在toml中可以使用rev去管理：
```toml
[dependencies]
regex = { git = "https://github.com/rust-lang/regex.git", rev = "9f9f693" }
```

然而每个依赖都需要手动管理，非常不方便，如果不加的话，每次构建都是最新的，很容易出现版本不兼容问题。

Cargo.lock可以自动完成版本管理，第一次构建拉取最新的提交，之后就锁定rev，可以使用手动更新到最新。
```bash
cargo update            # update all dependencies
cargo update -p regex   # only update regex
```