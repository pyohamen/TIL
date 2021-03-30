# Git\_ignore

## How to use gitignore

### 1. `cd` into your projects root directory

### 2. Create `.gitignore` file

```text
$ touch .gitignore
```

## 3. Write it down using `.gitignore` patterns

ex\)

- 

* To ignore all files ending in `.log`

  ```text
  $ echo '*.log' >> .gitignore
  ```

* To ignore any file names that contain `.log`

  ```text
  $ echo '*.log*' >> .gitignore
  ```

* To ignore all files in a specific path

  ```text
  $ echo 'directory' >> .gitignore
  $ echo '/directory/directory/*' >> .gitignore
  ```

