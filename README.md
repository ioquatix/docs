# Docs

Docs is a format agnostic read-only index for documentation, designed for efficient symbolic lookup. It is a simple, fast, and flexible way to index documentation for use by a language server. It can process source code in multiple languages, and can be used to index documentation in multiple formats, including RDoc, YARD, and other popular formats.

## Installation

```shell
$ gem install docs
```

## Usage

Every package which is supported by docs should export it's own index of symbols. There are specific documentation tools which support creating these indexes.

### RDoc Integration

Use `docs-rdoc` to generate an index for a RDoc project.

```shell
bake docs:rdoc:index
```

### YARD Integration

Use `docs-yard` to generate an index for a YARD project.

```shell
bake docs:yard:index
```

### Decode Integration

Use `docs-decode` to generate an index for a Decode project.

```shell
bake docs:decode:index
```

### Indexing

index = Docs::Index.current # builds an index for this gem, and all loaded gems and native Ruby version.

index["Array#push"] -> {
	...
}

gem = Docs::Index.for_gem("async") gems/async-.../docs.json

index.each_symbol(...) {|symbol, metadata|
	metadata.description
	metadata.type_
}
