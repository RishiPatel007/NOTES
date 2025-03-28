## path.basename()

- **Purpose**: Returns the last portion of a path
- **Examples**:

```javascript
path.basename('/users/docs/file.txt')     // 'file.txt'
path.basename('/users/docs/file.txt', '.txt')   // 'file'
```

## path.dirname()

- **Purpose**: Returns directory name of a path
- **Examples**:

```javascript
path.dirname('/users/docs/file.txt')      // '/users/docs'
```

## path.extname()

- **Purpose**: Returns extension name of a path
- **Examples**:

```javascript
path.extname('/users/docs/file.txt') //.txt
```

## path.join()

- **Purpose**: Joins path segments using platform-specific separator
- **Examples**:

```javascript
path.join('/foo', 'bar', 'baz/asdf', 'quux', '..')  // '/foo/bar/baz/asdf'
```

## path.parse()

- **Purpose**: Returns an object with path components
- **Examples**:

```javascript
path.parse('/users/docs/file.txt')
/* Returns:
{
  root: '/',
  dir: '/users/docs',
  base: 'file.txt',
  ext: '.txt',
  name: 'file'
}
*/
```