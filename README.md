# Flight Finder - Single Page Responsive Application

This is a Single Page Responsive Application built using **Vue.js**. The application allows users to select a source and destination, view available flights, and filter them based on flight duration.

## Features

1. **Dropdown Selection**: 
   - Select source and destination from dropdown menus populated with JSON data.
   - Prevent selecting the same city for both source and destination. If attempted, an error message is displayed.

2. **Flight Information Display**:
   - Displays all available airlines, departure, and arrival times based on selected source and destination.

3. **Dynamic Filtering**:
   - Users can filter flights by duration in ascending order.

4. **Responsive Design**:
   - Works seamlessly on desktop and mobile devices.

## Setup Instructions

### Prerequisites
- Node.js (>= 14.x)
- npm (>= 6.x) or yarn (>= 1.x)

### Installation

1. Clone the repository:
   ```bash
   git clone [git@github.com:diwakarjhadj/flight-app-vue.git](git@github.com:diwakarjhadj/flight-app-vue.git)
   cd flight-finder
   ```

2. Install dependencies:
   ```bash
   npm install
   ```
   or, if using yarn:
   ```bash
   yarn install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```
   or:
   ```bash
   yarn dev
   ```

4. Open your browser and navigate to:
   ```
   http://localhost:5173/
   ```

### Build for Production
To create a production build, run:
```bash
npm run build
```
or:
```bash
yarn build
```
The build will be available in the `dist` folder.

### Linting
To lint and fix code issues, run:
```bash
npm run lint
```
or:
```bash
yarn lint
```

## JSON Data

The application uses JSON data to populate source and destination dropdowns and display flight information. Ensure the JSON data is placed in the `src/data` folder and imported in the application.

Example JSON format:
```json
[
  {
    "id": "fc704c16fd79",
    "company": "US Airlines",
    "duration": 590,
    "segment": [
      {
        "departureTime": "2023-10-10T21:30-03:00",
        "arrivalTime": "2023-10-11T06:20-04:00",
        "origin": "Sao Paulo",
        "destination": "New York"
      }
    ]
  }
]
```

## Project Structure

```
flight-finder/
├── public/              # Static assets
├── src/
│   ├── assets/          # Images, stylesheets, etc.
│   ├── components/      # Vue components (e.g., FlightApp.vue)
│   ├── data/            # JSON data
│   ├── views/           # Main views
│   ├── App.vue          # Root Vue file
│   ├── main.js          # Application entry point
│   └── router.js        # Application routes
├── .eslintrc.js         # Linting configuration
├── package.json         # Project dependencies and scripts
└── README.md            # Project documentation
```

## Features Walkthrough

1. **Dropdowns**:
   - The dropdowns dynamically populate the list of available cities from the JSON data.
   - If the source and destination are the same, an error message is displayed.

2. **Flight Cards**:
   - Displays airline details, including duration, departure, and arrival times.
   - Flights can be sorted by duration.

3. **Error Handling**:
   - Alerts users when the same city is selected as both source and destination.

4. **Responsive Design**:
   - Optimized for viewing on both desktop and mobile devices.

## Deployment
To deploy the app:
1. Build the project using `npm run build` or `yarn build`.
2. Deploy the contents of the `dist` folder to your hosting provider (e.g., Netlify, Vercel, GitHub Pages).

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- [Vue.js Documentation](https://vuejs.org/)
- [Vite - Next Generation Frontend Tooling](https://vitejs.dev/)

---

### Author
**Diwakar Jha**

Feel free to fork and contribute to this project!
