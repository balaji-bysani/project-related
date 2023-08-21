import React, { useState, useEffect } from 'react';
import './App.css'; // Import your CSS file

function App() {
  const [isMobile, setIsMobile] = useState(false);

  // Check the device width and update the state
  const checkScreenWidth = () => {
    setIsMobile(window.innerWidth <= 768); // You can adjust the breakpoint as needed
  };

  useEffect(() => {
    // Initial check
    checkScreenWidth();

    // Attach event listener to window resize
    window.addEventListener('resize', checkScreenWidth);

    // Cleanup
    return () => {
      window.removeEventListener('resize', checkScreenWidth);
    };
  }, []);

  return (
    <div className={`container ${isMobile ? 'mobile' : 'desktop'}`}>
      {/* Render sidebar or navbar based on isMobile */}
      {isMobile ? (
        <nav className="navbar">
          {/* Navbar content */}
        </nav>
      ) : (
        <aside className="sidebar">
          {/* Sidebar content */}
        </aside>
      )}

      <main className="content">
        {/* Main content */}
      </main>
    </div>
  );
}

export default App;
