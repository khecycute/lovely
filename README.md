import { useEffect, useState } from "react";
import './App.css';

function App() {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts")
      .then((response) => response.json())
      .then((data) => {
        setPosts(data);
      })
      .catch((error) => console.error("Error fetching posts:", error));
  }, []);

  return (
    <div className="p-4">
      <h1 className="text-4xl font-bold mb-6">Posts</h1>
      
      <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        {posts.map((post) => (
          <div 
            key={post.id} 
            className="border p-4 rounded-lg shadow-md bg-white flex flex-col gap-2"
          >
            <h2 className="text-xl font-semibold capitalize">{post.title}</h2>
            <p className="text-gray-700">{post.body}</p>
          </div>
        ))}
      </div>
    </div>
  );
}

export default App;
