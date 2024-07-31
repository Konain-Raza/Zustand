# Zustand 🌟

Zustand is a simple, fast, and small state management library for React. It offers a minimalistic API for managing global state, making it easy to integrate and use in your projects. 🚀

## Why Zustand? 🤔

- **Simplicity**: Easy-to-understand API with no boilerplate. 🧩
- **Performance**: Fast and optimized for high performance. ⚡
- **Flexibility**: Seamless integration with React and other libraries. 🎯
- **No Boilerplate**: Skip actions, reducers, and manual component connections. 🚫

## Key Functions and Concepts 🛠️

### `create` 🏗️

The `create` function from Zustand is used to create a store. A store is where your application's global state is managed. You define your state and actions inside this function.

**Syntax**:

```javascript
import create from 'zustand';

const useStore = create((set) => ({
  // Initial state and actions go here
}));
```

**Example**:

```javascript
// store.js
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

export default useStore;
```

### `set` 🔄

The `set` function is used to update the state within the store. It accepts a function that receives the current state and returns the new state.

**Syntax**:

```javascript
set((state) => ({
  // Return new state here
}));
```

**Example**:

```javascript
// Increment count
increment: () => set((state) => ({ count: state.count + 1 })),
```

### `get` 🔍

The `get` function allows you to access the current state of the store. It can be useful for reading the state inside actions.

**Syntax**:

```javascript
get()
```

**Example**:

```javascript
// Fetch current state
const currentState = get();
```

### `subscribe` 📰

The `subscribe` function allows you to listen for changes in the store. You can use it to trigger side effects when the state changes.

**Syntax**:

```javascript
const unsubscribe = useStore.subscribe(
  (state) => state.someProperty,
  (someProperty) => {
    // Handle state change
  }
);
```

**Example**:

```javascript
const unsubscribe = useStore.subscribe(
  (state) => state.count,
  (count) => {
    console.log('Count changed:', count);
  }
);
```

### `persist` 📦

The `persist` middleware helps save the store's state to local storage, so it persists across page reloads.

**Syntax**:

```javascript
import { persist } from 'zustand/middleware';

const useStore = create(persist(
  (set) => ({
    // State and actions here
  }),
  { name: 'store-name' } // Key for local storage
));
```

**Example**:

```javascript
// store.js
import create from 'zustand';
import { persist } from 'zustand/middleware';

const useStore = create(persist(
  (set) => ({
    count: 0,
    increment: () => set((state) => ({ count: state.count + 1 })),
    decrement: () => set((state) => ({ count: state.count - 1 })),
  }),
  { name: 'counter-storage' } // Name for local storage
));

export default useStore;
```

## Getting Started 📦

### 1. Install Zustand

Add Zustand to your project using npm or yarn:

```bash
npm install zustand
# or
yarn add zustand
```

### 2. Create a Store 🏗️

Define your store with initial state and actions.

```javascript
// store.js
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

export default useStore;
```

### 3. Use the Store in Components 🔄

Access and modify state within your components.

```javascript
// Counter.js
import React from 'react';
import useStore from './store';

const Counter = () => {
  const { count, increment, decrement } = useStore();

  return (
    <div>
      <h1>Count: {count} 🧮</h1>
      <button onClick={increment}>Increment ➕</button>
      <button onClick={decrement}>Decrement ➖</button>
    </div>
  );
};

export default Counter;
```

### 4. Integrate into Your App 🌐

Use your components in the main application.

```javascript
// App.js
import React from 'react';
import Counter from './Counter';

const App = () => (
  <div>
    <h1>Welcome to Zustand Example! 🎉</h1>
    <Counter />
  </div>
);

export default App;
```

## Advanced Usage 🚀

### Asynchronous State Management 🕒

Handle async operations like fetching data:

```javascript
// store.js
import create from 'zustand';

const useStore = create((set) => ({
  data: null,
  loading: false,
  fetchData: async () => {
    set({ loading: true });
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    set({ data, loading: false });
  },
}));

export default useStore;
```

### Middleware 🔧

Add middleware for features like logging or persisting state:

```javascript
// store.js
import create from 'zustand';
import { persist } from 'zustand/middleware';

const useStore = create(persist(
  (set) => ({
    count: 0,
    increment: () => set((state) => ({ count: state.count + 1 })),
    decrement: () => set((state) => ({ count: state.count - 1 })),
  }),
  { name: 'counter-storage' } // Key for local storage
));

export default useStore;
```

## Practice Project: Task Tracker 🗂️

Build a Task Tracker application to practice Zustand:

1. **Create a Task Store**: Manage tasks with properties like title, description, and completion status.
2. **Add Task Functionality**: Implement actions to add, remove, and toggle tasks.
3. **Display Tasks**: Create components to list tasks, add new ones, and mark them as complete.
4. **Persist Tasks**: Use Zustand's `persist` middleware to save tasks across sessions.

**Example Features**:
- Add new tasks ✍️
- Toggle task completion ✅
- Delete tasks ❌
- Filter tasks (All, Completed, Incomplete) 🔍

This project will give you hands-on experience with Zustand and build a practical application using its state management features.

Happy coding with Zustand! If you have any questions, feel free to ask. 😊
