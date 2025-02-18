import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';
import { useState } from 'react';

function App() {
  return (
    <Router>
      <div className="min-h-screen bg-gray-100">
        <Navbar />
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/destinations" element={<Destinations />} />
          <Route path="/book" element={<Booking />} />
        </Routes>
        <Footer />
      </div>
    </Router>
  );
}

function Navbar() {
  return (
    <nav className="bg-blue-600 text-white p-4 flex justify-between">
      <h1 className="text-xl font-bold">Arat Na Travel</h1>
      <div>
        <Link className="mx-2" to="/">Home</Link>
        <Link className="mx-2" to="/destinations">Destinations</Link>
        <Link className="mx-2" to="/book">Book</Link>
      </div>
    </nav>
  );
}

function Home() {
  return (
    <div className="text-center p-10">
      <h2 className="text-3xl font-bold">Discover the World with Arat Na Travel</h2>
      <p className="text-gray-600 mt-4">Explore the best travel destinations.</p>
      <Link to="/destinations" className="mt-4 inline-block bg-blue-600 text-white px-4 py-2 rounded-lg">View Destinations</Link>
    </div>
  );
}

function Destinations() {
  const places = [
    { name: "Boracay", image: "https://source.unsplash.com/400x300/?beach" },
    { name: "Baguio", image: "https://source.unsplash.com/400x300/?mountain" },
    { name: "Palawan", image: "https://source.unsplash.com/400x300/?island" },
  ];

  return (
    <div className="p-10 grid grid-cols-1 md:grid-cols-3 gap-4">
      {places.map((place, index) => (
        <div key={index} className="bg-white p-4 rounded-lg shadow-lg">
          <img src={place.image} alt={place.name} className="w-full h-48 object-cover rounded-md" />
          <h3 className="text-xl font-bold mt-2">{place.name}</h3>
        </div>
      ))}
    </div>
  );
}

function Booking() {
  const [name, setName] = useState("");
  const [destination, setDestination] = useState("");
  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Booking confirmed for ${name} to ${destination}`);
  };

  return (
    <div className="p-10">
      <h2 className="text-2xl font-bold">Book Your Trip</h2>
      <form onSubmit={handleSubmit} className="mt-4">
        <input className="border p-2 w-full" type="text" placeholder="Your Name" value={name} onChange={(e) => setName(e.target.value)} required />
        <input className="border p-2 w-full mt-2" type="text" placeholder="Destination" value={destination} onChange={(e) => setDestination(e.target.value)} required />
        <button className="bg-blue-600 text-white px-4 py-2 mt-2 rounded-lg">Book Now</button>
      </form>
    </div>
  );
}

function Footer() {
  return (
    <footer className="bg-blue-600 text-white text-center p-4 mt-10">
      &copy; 2025 Arat Na Travel. All Rights Reserved.
    </footer>
  );
}

export default App;

