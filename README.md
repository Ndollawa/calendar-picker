# Nuxt.js Calendar Picker

This project is a simple calendar picker built using **Nuxt.js**. It allows users to select a **start date** and an **end date**, with shortcuts for common date ranges such as **"Next 7 Days"**, **"Next 15 Days"**, **"Next 30 Days"**, **"Next 1 Month"**, and **"Next 3 Months"**.

## Features

- Select a **start date** and an **end date** using date inputs.
- Shortcuts for common date ranges:
  - **Next 7 Days**
  - **Next 15 Days**
  - **Next 30 Days**
  - **Next 1 Month**
  - **Next 3 Months**

## Demo

You can view the deployed application [here](#).  
*(Replace the `#` with the actual deployment URL)*

## Getting Started

### Prerequisites

Ensure you have the following installed:
- Node.js (v16+ recommended)
- npm or yarn

### Installation

#### 1. Clone the repository:
   ```bash
   git clone https://github.com/Ndollawa/calendar-picker.git
   cd calendar-picker
```

 ### Getting Started
#### Prerequisites
Ensure you have the following installed:

Node.js (v16+ recommended)
npm or yarn
Installation
Clone the repository:

``` bash
git clone https://github.com/yourusername/calendar-picker.git
cd calendar-picker
```
Install the dependencies:

``` bash
npm install
```
#### Running the Development Server
To start the development server:

``` bash
npm run dev
```
The application will be available at http://localhost:3000.

#### Building for Production
To build the project for production:

``` bash
npm run build
npm run start
```
Running Tests
To run unit tests:

``` bash
npm run test
```
#### Deployment
This project can be easily deployed to platforms like Vercel or Netlify.

For Vercel deployment:

Install the Vercel CLI:

``` bash
npm i -g vercel
```
#### Deploy:

``` bash
vercel
```
For Netlify deployment:

Install the Netlify CLI:

``` bash
npm i -g netlify-cli
```
Deploy:

``` bash
netlify deploy
```
### Technologies Used
Nuxt.js: Framework for building Vue.js applications.
Vue 3 Composition API: For reactivity and state management.
date-fns: For date manipulation and formatting.
Unit Testing
Unit tests are implemented using Jest. The test suite covers the following:

Date selection.
Shortcut functionality (e.g., "Next 7 Days", "Next 1 month").
Contributing
Feel free to submit issues or pull requests. Contributions are welcome!

License
This project is licensed under the MIT License.