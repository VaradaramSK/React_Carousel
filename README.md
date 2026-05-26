# Ex05 Image Carousel
## Date: 26-05-2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
App.jsx
```
// App.js

import { useState } from "react";
import "./App.css";

function App() {
  const images = [
    "https://picsum.photos/id/1015/600/400",
    "https://picsum.photos/id/1016/600/400",
    "https://picsum.photos/id/1018/600/400",
    "https://picsum.photos/id/1020/600/400",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prevIndex) =>
      prevIndex === images.length - 1 ? 0 : prevIndex + 1
    );
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) =>
      prevIndex === 0 ? images.length - 1 : prevIndex - 1
    );
  };

  return (
    <div className="carousel">
      <h1>Image Carousel</h1>

      <img src={images[currentIndex]} alt="carousel" />

      <div className="buttons">
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage}>Next</button>
      </div>
    </div>
  );
}

export default App;
```

App.css
```
/* App.css */

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f2f2f2;

  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.carousel {
  text-align: center;
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.2);
}

.carousel img {
  width: 600px;
  height: 400px;
  object-fit: cover;
  border-radius: 10px;
}

.buttons {
  margin-top: 15px;
}

button {
  padding: 10px 18px;
  margin: 0 10px;
  border: none;
  background: #333;
  color: white;
  border-radius: 6px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background: orange;
}
```
## OUTPUT
<img width="1110" height="808" alt="image" src="https://github.com/user-attachments/assets/6a8e58b7-8964-4c77-b38d-f4a103643218" />
<img width="1106" height="812" alt="image" src="https://github.com/user-attachments/assets/a0c3efcf-a4be-4a72-9f92-d5d4b32c6ab1" />
<img width="1100" height="820" alt="image" src="https://github.com/user-attachments/assets/b0356832-201c-4082-88bd-ef9dc8033214" />




## RESULT
The program for creating Image Carousel using React is executed successfully.
