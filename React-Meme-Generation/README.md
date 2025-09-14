# React Meme Generator

This is a simple and fun meme generator application built with React. It allows users to create their own memes by adding custom top and bottom text to a randomly generated meme image fetched from the [Imgflip API](https://imgflip.com/api).

This project was created as a learning exercise to practice fundamental React concepts, particularly the `useState` and `useEffect` hooks.



## Features

*   Displays a random meme template on page load.
*   Input fields to customize the top and bottom text of the meme.
*   A button to fetch a new random meme image from the API.
*   Live preview of the text on the meme image as you type.

## Core Concepts Implemented

This project serves as a practical example for the following React hooks:

### `useState`

The `useState` hook is used to manage the state of the meme object. This object holds the `topText`, `bottomText`, and the URL of the current `image`.

```javascript
const [meme, setMeme] = useState({
    topText: "One does not simply",
    bottomText: "Walk into Mordor",
    image: "http://i.imgflip.com/1bij.jpg"
})
```

It is also used to store the array of all meme templates fetched from the API:

```javascript
const [allMemes, setAllMemes] = useState([])
```

### `useEffect`

The `useEffect` hook is used to perform a side effect: fetching data from an external API. The hook is configured to run only once when the `Main` component is first rendered, thanks to the empty dependency array `[]`.

```javascript
useEffect(() => {
    fetch("https://api.imgflip.com/get_memes")
        .then(res => res.json())
        .then(data => setAllMemes(data.data.memes))
}, [])
```

### Event Handling

*   **`getMemeImage()`**: This function is triggered by the "Get a new meme image" button's `onClick` event. It randomly selects a new meme from the `allMemes` state and updates the `image` property of the `meme` state.
*   **`handleChange()`**: This function handles the `onChange` event for both text inputs. It uses the `name` attribute of the input to dynamically update the corresponding property (`topText` or `bottomText`) in the `meme` state.

## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

*   Node.js and npm (or yarn/pnpm) installed on your machine.

### Installation & Setup

1.  Clone the repository:
    ```sh
    git clone https://github.com/your-username/React-Meme-Generation.git
    ```
2.  Navigate into the project directory:
    ```sh
    cd React-Meme-Generation
    ```
3.  Install NPM packages:
    ```sh
    npm install
    ```
4.  Run the development server:
    ```sh
    npm run dev
    ```

The application will be available at `http://localhost:5173/`.

