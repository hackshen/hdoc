```javascript
import React, {useState, useEffect} from 'react';
function App() {
    const [count, setCount] = useState(1)

    useEffect(() => {
        const handleResize = () => {
            console.log(`count is ${count}`)
        }
        window.addEventListener('resize', handleResize)
        return () => window.removeEventListener('resize', handleResize)
    },[null]);

    return (
        <div className="App">
            <button onClick={() => setCount(count + 1)}>+</button>
            <h1>{count}</h1>
        </div>
    );
}
export  default App
```
