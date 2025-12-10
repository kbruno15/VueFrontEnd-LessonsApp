# VueFrontEnd-LessonsApp

Front-end for the **After School Lessons** coursework app for CST3144.  
This single-page application is built with **Vue.js** and connects to a separate Express + MongoDB backend.

---

## Live demo

- **Front-end (GitHub Pages)**  
  https://kbruno15.github.io/VueFrontEnd-LessonsApp

- **Back-end API (Render)**  
  https://lessons-backend-46m7.onrender.com

The front-end calls the backend API using `fetch` and JSON.

---

## Main features

- List of after school lessons loaded from the backend `/lessons` endpoint.
- **Search-as-you-type** using the `/search` endpoint (subject, location, price, spaces).
- **Sorting controls**:
  - Sort by subject, location, price, or availability (spaces).
  - Ascending / descending order.
- **Shopping cart**:
  - Add lessons to the cart (with quantity).
  - Remove items from the cart.
  - Cart badge shows total quantity.
  - Cart summary shows total items and total price.
- **Availability tracking**:
  - Spaces decrease when adding to cart.
  - Spaces increase again when removing from cart.
- **Checkout form**:
  - Name validation (letters and spaces only).
  - Phone validation (digits only).
  - Disabled checkout button until the form is valid.
- **Order submission**:
  - Sends POST request to `/orders`.
  - Sends PUT requests to `/lessons/:id` to update spaces.
  - Success and error banners shown to the user.
- **Lesson images**:
  - Each lesson document in MongoDB can contain an `image` field (e.g. `"math.png"`).
  - Images are served by the backend from `/images/<filename>` and displayed in the cards and cart.

---

## Technology used

- **Vue.js 2** (CDN, no build tools)
- **HTML5 + CSS3**
- **Fetch API** for AJAX calls (JSON only)
- Backend:
  - Node.js + Express
  - MongoDB Atlas (connected via the Express backend)

---

## How the front-end talks to the back-end

In `index.html` there is a single base URL:

```js
var API_BASE = 'https://lessons-backend-46m7.onrender.com';

All requests are made with fetch:

GET API_BASE + '/lessons' – load all lessons.

GET API_BASE + '/search?q=...' – filtered search.

POST API_BASE + '/orders' – create an order.

PUT API_BASE + '/lessons/:id' – update space for each lesson.

GET API_BASE + '/images/<filename>' – load lesson icon images.

All requests send / receive JSON except for the image route.
Running the front-end locally

Clone the repository:

git clone https://github.com/kbruno15/VueFrontEnd-LessonsApp.git
cd VueFrontEnd-LessonsApp


Make sure the backend is running and reachable
(either locally on http://localhost:3000 or on Render).

If you want to use a local backend during development, change:

var API_BASE = 'https://lessons-backend-46m7.onrender.com';


to

var API_BASE = 'http://localhost:3000';


Open index.html in a browser (for example using the VS Code Live Server
extension or a simple static server).

File structure
VueFrontEnd-LessonsApp/
├─ index.html   # Single-page Vue application
├─ style.css    # Styling for lessons list, cart and layout
└─ README.md

Coursework notes

The app satisfies the requirements for:

Vue.js front-end rendering a list of lessons.

Sorting, searching and filtering.

Shopping cart and checkout.

Validation of user input.

Communication with a back-end using AJAX and JSON.

Front-end is deployed on GitHub Pages and uses the Render back-end API.