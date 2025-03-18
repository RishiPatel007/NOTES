## Stepping Commands

- **Purpose**: Control execution flow during debugging
- **Examples**:

```javascript
cont, c     // Continue execution
next, n     // Step next
step, s     // Step in
out, o      // Step out
pause       // Pause running code
```

## Breakpoint Commands

- **Purpose**: Set and clear breakpoints during debugging
- **Examples**:

```javascript
setBreakpoint(), sb()                           // Set breakpoint on current line
setBreakpoint(line), sb(line)                   // Set breakpoint on specific line
setBreakpoint('fn()'), sb('fn()')               // Set breakpoint on first statement in function's body
setBreakpoint('script.js', 1), sb('script.js', 1) // Set breakpoint on first line of script.js
```

## Conditional Breakpoints

- **Purpose**: Set breakpoints that only trigger when a condition is met
- **Examples**:

```javascript
setBreakpoint('script.js', 1, 'num < 4')        // Break on line 1 only when num < 4 is true
```

## Clearing Breakpoints

- **Purpose**: Remove previously set breakpoints
- **Examples**:

```javascript
clearBreakpoint('script.js', 1), cb('script.js', 1) // Clear breakpoint in script.js on line 1
```