# Usage of Typescript in React

In this chapter, we will give you how to use Typescript in React.



## Type-Definitions Cheatsheet



### `React.Component<Props, State>`

Type representing a class component
```tsx
class MyComponent extends React.Component<Props, State> { ...
```

### `React.FC<Props>` | `React.FunctionComponent<Props>`

Type representing a functional component
```tsx
const MyComponent: React.FC<Props> = ...
```

### `React.ComponentType<Props>`

Type representing union of (React.FC<Props> | React.Component<Props>) - used in HOC
```tsx
const withState = <P extends WrappedComponentProps>( WrappedComponent:React.ComponentType<P>) => { ...
```

### `React.ComponentProps<typeof XXX>`

Gets Props type of a specified component XXX (WARNING: does not work with statically declared default props and generic props)
```tsx
type MyComponentProps = React.ComponentProps<typeof MyComponent>;
```

### `React.ReactElement` | `JSX.Element`

Type representing a concept of React Element - representation of a native DOM component (e.g. `<div />`), or a user-defined composite component (e.g. `<MyComponent />`)
```tsx
const elementOnly: React.ReactElement = <div /> || <MyComponent />;
```

### `React.ReactNode`

Type representing any possible type of React node (basically ReactElement (including Fragments and Portals) + primitive JS types)
```tsx
const elementOrPrimitive: React.ReactNode = 'string' || 0 || false || null || undefined || <div /> || <MyComponent />;
const Component = ({ children: React.ReactNode }) => ...
```

### `React.CSSProperties`

Type representing style object in JSX - for css-in-js styles
```tsx
const styles: React.CSSProperties = { flexDirection: 'row', ...
const element = <div style={styles} ...
```

### `React.HTMLProps<HTMLXXXElement>`

Type representing Props of specified HTML Element - for extending HTML Elements
```tsx
const Input: React.FC<Props & React.HTMLProps<HTMLInputElement>> = props => { ... }

<Input about={...} accept={...} alt={...} ... />
```

### `React.ReactEventHandler<HTMLXXXElement>`

Type representing generic event handler - for declaring event handlers
```tsx
const handleChange: React.ReactEventHandler<HTMLInputElement> = (ev) => { ... } 

<input onChange={handleChange} ... />
```

### `React.XXXEvent<HTMLXXXElement>`

Type representing more specific event. Some common event examples: `ChangeEvent, FormEvent, FocusEvent, KeyboardEvent, MouseEvent, DragEvent, PointerEvent, WheelEvent, TouchEvent`.
```tsx
const handleChange = (ev: React.MouseEvent<HTMLDivElement>) => { ... }

<div onMouseMove={handleChange} ... />
```

In code above `React.MouseEvent<HTMLDivElement>` is type of mouse event, and this event happened on `HTMLDivElement`