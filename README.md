# React-native
react-xd-assignment/
├── src/
│   ├── assets/
│   ├── components/
│   │   └── MobileContainer.jsx
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── PageTwo.jsx
│   ├── routes/
│   │   └── AppRoutes.jsx
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── public/
├── tailwind.config.js
├── postcss.config.js
├── package.json
└── README.md

npm create vite@latest react-xd-assignment -- --template react
cd react-xd-assignment
npm install

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

export default {
  content: ["./index.html", "./src/**/*.{js,jsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};

@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  @apply bg-gray-100;
}

const MobileContainer = ({ children }) => {
  return (
    <div className="min-h-screen flex items-center justify-center">
      <div className="w-[375px] min-h-[812px] bg-white shadow-xl rounded-xl overflow-hidden">
        {children}
      </div>
    </div>
  );
};

export default MobileContainer;

npm install react-router-dom

import { Routes, Route } from "react-router-dom";
import Home from "../pages/Home";
import PageTwo from "../pages/PageTwo";

const AppRoutes = () => {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/page-two" element={<PageTwo />} />
    </Routes>
  );
};

export default AppRoutes;

import { useNavigate } from "react-router-dom";
import MobileContainer from "../components/MobileContainer";

const Home = () => {
  const navigate = useNavigate();

  return (
    <MobileContainer>
      <div className="p-6 flex flex-col h-full">
        <h1 className="text-2xl font-bold mb-4">Home Screen</h1>

        <p className="text-gray-600 mb-6">
          Pixel-perfect UI based on Adobe XD design.
        </p>

        <button
          onClick={() => navigate("/page-two")}
          className="mt-auto bg-black text-white py-3 rounded-lg"
        >
          Go to Next Page
        </button>
      </div>
    </MobileContainer>
  );
};

export default Home;

import { useNavigate } from "react-router-dom";
import MobileContainer from "../components/MobileContainer";

const PageTwo = () => {
  const navigate = useNavigate();

  return (
    <MobileContainer>
      <div className="p-6 flex flex-col h-full">
        <h1 className="text-2xl font-bold mb-4">Second Screen</h1>

        <button
          onClick={() => navigate("/")}
          className="mt-auto bg-gray-200 py-3 rounded-lg"
        >
          Back
        </button>
      </div>
    </MobileContainer>
  );
};

export default PageTwo;

import AppRoutes from "./routes/AppRoutes";

function App() {
  return <AppRoutes />;
}

export default App;

import React from "react";
import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);

npm run dev

git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/react-xd-assignment.git
git push -u origin main
