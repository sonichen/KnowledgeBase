[crates.io](https://crates.io/)

> 注意：发布包到 `crates.io` 后，特定的版本无法被覆盖，要发布就必须使用新的版本号，代码也无法被删除!

## 首次登录

用github登录

打开AccountSettings-->API TokenS, 生成token。并且用token在终端登录

```shell
cargo login [token]
```

可能遇到报错

```shell
error: crates-io is replaced with non-remote-registry source registry `tuna`;
include `--registry crates-io` to use crates.io
```

加上`--registry crates-io` 再次执行即可

```shell
cargo login [token]  --registry crates-io
```

## 发布包之前

`crates.io` 上的**包名遵循先到先得**的方式：一旦你想要的包名已经被使用，那么你就得换一个不同的包名。

在发布之前，**确保** `Cargo.toml` 中以下字段已经被设置:

- [license 或 license-file](https://course.rs/cargo/reference/manifest.html#license和license-file)
- [description](https://course.rs/cargo/reference/manifest.html#description)
- [homepage](https://course.rs/cargo/reference/manifest.html#homepage)
- [documentation](https://course.rs/cargo/reference/manifest.html#documentation)
- [repository](https://course.rs/cargo/reference/manifest.html#repository)
- [readme](https://course.rs/cargo/reference/manifest.html#readme)

## 打包

确保代码没有 warning 或错误

```
cargo publish --dry-run
```

在 `target/package` 目录下观察生成的 `.crate` 文件。

检查其中包含的文件:

```
cargo package --list
```

当打包时，Cargo 会自动根据版本控制系统的配置来忽略指定的文件，例如 `.gitignore`。除此之外，你还可以通过 [`exclude`](https://course.rs/cargo/reference/manifest.html#exclude和include) 来排除指定的文件:

```toml
[package]
# ...
exclude = [
    "public/assets/*",
    "videos/*",
]
```

如果想要显式地将某些文件包含其中，可以使用 `include`，但是需要注意的是，这个 key 一旦设置，那 `exclude` 就将失效：

```toml
[package]
# ...
include = [
    "**/*.rs",
    "Cargo.toml",
]
```

## 上传

```
cargo publish
```

## 管理 crates.io 上的包

无法删除版本

`yank` 能做到的就是让其它人不能再使用这个版本作为依赖，但是现存的依赖依然可以继续工作。

```
cargo yank --vers 1.0.1
cargo yank --vers 1.0.1 --undo
```

## Reference

https://course.rs/cargo/reference/publishing-on-crates.io.html