# Building Java Projects with zb

Use zb to build Java 21+ projects without external dependencies.

## When to Use

All three conditions must apply:

- Java project with exactly one `void main()` entry point
- No Maven/Gradle dependencies required
- Single-module application

## Build Command

Run from the project root:

```bash
java -jar ~/bin/zb.jar
```

Or with shell wrapper:

```bash
zb.sh
```

CLI arguments override `.zb` configuration:

```bash
java -jar ~/bin/zb.jar [source-dir] [classes-dir] [jar-dir] [jar-filename]
```

## Source Detection

zb auto-detects sources in this order:

1. `src/main/java`
2. `src/`
3. Current directory

All `.java` files in the source directory are compiled together in a single pass.

## Output

Executable JAR: `zbo/app.jar`

## Configuration

A `.zb` file is auto-generated in the project root on first run with these defaults:

```properties
sources.dir=<discovered by zb>
resources.dir=<discovered by zb>
classes.dir=<temp.dir>
jar.dir=zbo/
jar.file.name=app.jar
```

- `<discovered by zb>` — zb uses its auto-detection logic
- `<temp.dir>` — zb creates a temporary directory for compilation and deletes it after the JAR is built

## Resources

Only `META-INF/services` files from the resources directory are included in the JAR.

## Verification

Run the built JAR:

```bash
java -jar zbo/app.jar
```
