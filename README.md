# Ex05 Image Carousel
## Date:05/11/2025
### NAME : Swathi S
### REG NO : 212223040220

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
import { useState, useEffect } from "react";
import "./App.css";
import sun from "./sun.jpeg";
import moon from "./moon.jpg";
import earth from "./earth.jpg";

function App() {
  const images = [
    { src: sun, alt: "Sun" },
    { src: moon, alt: "Moon" },
    { src: earth, alt: "Earth" },
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentIndex((prev) => (prev + 1) % images.length);
    }, 3000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="carousel">
        <h1>   Solar Carousel 🌞🌙🌍</h1>
      <div className="image-container">
        <img
          src={images[currentIndex].src}
          alt={images[currentIndex].alt}
          className="fade"
        />
      </div>
      <div className="dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
}

export default App;

```

App.css

```
/* Center everything on the page */
.carousel {
  background-color: #001f3f;
  color: white;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center; /* vertical center */
  align-items: center; /* horizontal center */
  text-align: center;
  overflow: hidden;
  margin: 0;
}

/* Title styling */
.carousel h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  font-weight: bold;
}

/* Image box styling */
.image-container {
  width: 400px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 0 30px rgba(255, 255, 255, 0.3);
}

/* Image fit and animation */
.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 20px;
  transition: opacity 1s ease-in-out;
}

/* Dot controls */
.dots {
  margin-top: 20px;
}

.dot {
  height: 12px;
  width: 12px;
  margin: 0 5px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  cursor: pointer;
  transition: background-color 0.3s;
}

.dot.active {
  background-color: white;
}

.fade {
  animation: fadeEffect 1s ease-in-out;
}

@keyframes fadeEffect {
  from {
    opacity: 0.5;
  }
  to {
    opacity: 1;
  }
}

/* Remove unwanted scroll bars or padding */
body, html {
  margin: 0;
  padding: 0;
  overflow: hidden;
}

```


## OUTPUT

<img width="1141" height="643" alt="image" src="https://github.com/user-attachments/assets/d15ae8a7-a03c-43fd-afdd-7e45694701f7" />

<img width="1144" height="643" alt="image" src="https://github.com/user-attachments/assets/abc25713-67ae-47ea-bcf7-19e5b89d5dd7" />

<img width="1141" height="644" alt="image" src="https://github.com/user-attachments/assets/06dd8be7-9848-40a1-a0b3-add265fc6f8b" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
