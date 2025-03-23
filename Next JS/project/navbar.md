
```
"use client";
import { useState } from "react";
import Image from "next/image";
import { FiMenu, FiX } from "react-icons/fi";
import CustomeLink from "../../components/UI/CustomeLink";

const Navbar = () => {
  const [menuOpen, setMenuOpen] = useState(false);

  return (
    <nav className="bg-white shadow-md">
      <div className="max-w-container mx-auto py-4 px-4 flex justify-between items-center">
        {/* Logo Section */}
        <Image src="/images/logo.png" width={120} height={50} alt="Logo" />

        {/* Desktop Menu */}
        <div className="hidden md:flex gap-x-8">
          <CustomeLink path="/">Home</CustomeLink>
          <CustomeLink path="/amr">Find Doctor</CustomeLink>
          <CustomeLink path="/find-hospital">Find Hospital</CustomeLink>
          <CustomeLink path="/find-ambulance">Find Ambulance</CustomeLink>
        </div>

        {/* Login Button */}
        <button className="hidden md:block border border-[#04518c] px-4 py-2 rounded-md text-[#04518c] hover:bg-[#04518c] hover:text-white transition">
          Login
        </button>

        {/* Mobile Menu Button */}
        <button className="md:hidden" onClick={() => setMenuOpen(!menuOpen)}>
          {menuOpen ? <FiX size={28} /> : <FiMenu size={28} />}
        </button>
      </div>

      {/* Mobile Menu */}
      {menuOpen && (
        <div className="md:hidden flex flex-col items-center gap-4 py-4 bg-gray-100">
          <CustomeLink path="/">Home</CustomeLink>
          <CustomeLink path="/amr">Find Doctor</CustomeLink>
          <CustomeLink path="/find-hospital">Find Hospital</CustomeLink>
          <CustomeLink path="/find-ambulance">Find Ambulance</CustomeLink>
          <button className="border border-[#04518c] px-4 py-2 rounded-md text-[#04518c] hover:bg-[#04518c] hover:text-white transition">
            Login
          </button>
        </div>
      )}
    </nav>
  );
};

export default Navbar;

```