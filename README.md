# React JS Practice 1

> This project is a practice of building Responsive website using React Javascript and TailwindCSS.

## Installations & Setups

1. Create React project: `npx create-react-app react_practice1`
2. Install Tailwind CSS
   - `npm install -D tailwindcss postcss autoprefixer`
   - `npx tailwindcss init -p`
   - Add "./src/\*_/_.{js,jsx,ts,tsx}", on tailwind.config.js file
   - Add tailwind directives to index.css
3. Install react-icons: `npm install react-icons --save`

## Major features:

- Responsive Navbar
- Hero section with text animation
- Hover effect cards modals
- Footer

---

### Step 1: Responsive Navigation bar

In this project, to make responsive navigation bar, first, made Navbar.jsx file inside of components folder and `export default Navbar`. At Navbar.jsx, I made two different `<div>` tags: one for mobile version and the other for bigger screen version. I am not yet familiar with TailwindCSS responsive design so, it might look very hardcoding.

**Goals of responsive navbar are below:**

1.  As soon as the screen reaches mobile size, the expanded navbar on top disappears and menu icon shows up and vise versa.
2.  If user clicks the menu icon, the mobile version navbar will be smoothly in-and-out.

To achieve goal #2, I made a `<div>` to put react-icon and then use jsx condition statement.

```jsx
<div onClick={handleNav} className="block md:hidden">
  {!nav ? <AiOutlineClose size={20} /> : <AiOutlineMenu size={20} />}
</div>
```

To make click transition for menu icon, I used `useState()` and made `handleNav` function to change its state.

```jsx
let [nav, setNav] = useState(false);
const handleNav = () => {
  setNav(!nav); //Change nav state to opposite state
};
```

For mobile version's navbar, use tailwindcss to adjust its size, fixed on left, and **ease-in-out**, **duration-500** allows to make soomth transition.

```jsx
<div
  className={
    !nav
      ? "fixed left-0 top-0 h-full w-[60%] border-r border-r-gray-900 bg-[#000300] ease-in-out duration-500"
      : "fixed left-[-100%]"
  }
>
  <h1 className="w-full text-3xl font-bold text-[#00df9a] m-5">BLANK.</h1>
  <ul className="uppercase p-4">
    <li className="p-4 border-b border-gray-600">Home</li>
    <li className="p-4 border-b border-gray-600">Company</li>
    <li className="p-4 border-b border-gray-600">Resources</li>
    <li className="p-4 border-b border-gray-600">About</li>
    <li className="p-4">Contact</li>
  </ul>
</div>
```

To achieve goal #1, simply use tailwindcss to make it hidden below of 'md' breakpoint and display:flex above md breakpoint.

```jsx
<ul className="hidden md:flex">
  <li className="p-4">Home</li>
  <li className="p-4">Company</li>
  <li className="p-4">Resources</li>
  <li className="p-4">About</li>
  <li className="p-4">Contact</li>
</ul>
```

**[Navbar bugs/questions]**

1.  Assumming let window as half size of monitor and click the menu icon to open side navbar menu. Here is a problem: if I enlarge a window to full size, the side navbar is still remain and horizontally expanded-navbar on top is also shown together.
2.  I had to make brandlogo two times: one for web version, and the other for mobile version. I am not sure whether it's the only way or not. Q) Is there any other simpler way?

### Step 2: Hero section

### Step 3 : Footer

### References:

1.  [Tailwind CSS](https://tailwindcss.com/docs/guides/create-react-app)
2.  [Youtube tutorial](https://www.youtube.com/watch?v=ZU-drSVodBw)
