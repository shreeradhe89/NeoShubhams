// NeoShubhams - Ultra Premium Website (Next.js + Tailwind + GSAP + AI Chatbot + Payment + Welcome Animation)

import { useEffect, useState } from "react";
import { gsap } from "gsap";
import Link from "next/link";

export default function Home() {
  const [messages, setMessages] = useState([]);
  const [input, setInput] = useState("");

  useEffect(() => {
    gsap.from(".fade-in", { opacity: 0, y: 50, duration: 1, ease: "power2.out" });
    gsap.from(".welcome", { opacity: 0, scale: 0.8, duration: 1.5, ease: "elastic.out(1, 0.3)" });
  }, []);

  const sendMessage = () => {
    if (!input.trim()) return;
    setMessages([...messages, { text: input, type: "user" }]);
    setInput("");

    setTimeout(() => {
      setMessages((prev) => [...prev, { text: "I am NeoBot 🤖, How can I assist you?", type: "bot" }]);
    }, 1000);
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-black via-gray-900 to-black text-white flex flex-col items-center justify-center space-y-6 p-6">
      {/* Welcome Animation */}
      <div className="welcome text-4xl font-extrabold bg-gradient-to-r from-green-400 to-blue-500 text-transparent bg-clip-text">
        Welcome to NeoShubhams 🚀
      </div>
      
      <h1 className="text-7xl font-extrabold fade-in bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-purple-600">🚀 NeoShubhams</h1>
      <p className="mt-4 text-xl fade-in text-gray-300 text-center max-w-3xl">
        The most advanced, ultra-premium, and futuristic video editing portfolio. Get high-end video edits with seamless creativity.
      </p>
      
      {/* Demo Video Editing Showcase */}
      <div className="fade-in mt-6 w-full max-w-4xl">
        <video className="rounded-lg shadow-lg border-2 border-blue-500 hover:shadow-blue-500 transition-all duration-300" controls>
          <source src="/demo-edit.mp4" type="video/mp4" />
          Your browser does not support the video tag.
        </video>
      </div>
      
      {/* AI Chatbot */}
      <div className="fade-in mt-10 bg-gray-800 p-6 rounded-xl shadow-lg w-full max-w-md">
        <h3 className="text-xl font-bold text-blue-400">Chat with NeoBot 🤖</h3>
        <div className="mt-4 h-40 overflow-y-auto bg-gray-900 p-4 rounded-lg">
          {messages.map((msg, index) => (
            <div key={index} className={`mb-2 p-2 rounded-lg ${msg.type === "user" ? "bg-blue-500 text-white text-right" : "bg-gray-700 text-gray-200 text-left"}`}>
              {msg.text}
            </div>
          ))}
        </div>
        <div className="mt-4 flex">
          <input 
            type="text" 
            className="flex-1 p-2 bg-gray-700 text-white rounded-l-lg outline-none" 
            placeholder="Ask me anything..." 
            value={input} 
            onChange={(e) => setInput(e.target.value)}
          />
          <button onClick={sendMessage} className="px-4 bg-blue-500 hover:bg-blue-600 text-white rounded-r-lg">Send</button>
        </div>
      </div>
      
      {/* Payment Section */}
      <div className="fade-in mt-10 text-center bg-gray-800 p-6 rounded-xl shadow-lg w-full max-w-md">
        <h3 className="text-xl font-bold text-green-400">Make a Payment 💳</h3>
        <p className="text-gray-400 mt-2">Secure your premium video editing service now.</p>
        <a href="/payment" className="mt-4 inline-block bg-green-500 hover:bg-green-600 text-white py-2 px-6 rounded-lg text-lg font-semibold transition-all">Pay Now</a>
      </div>
      
      {/* Contact Section */}
      <div className="fade-in mt-10 text-center">
        <h2 className="text-3xl font-bold">Need High-End Video Editing?</h2>
        <p className="text-gray-400 mt-2">Contact me for premium video editing services.</p>
        <a href="mailto:shubhamshah8859@gmail.com" className="mt-4 inline-block bg-blue-500 hover:bg-blue-600 text-white py-2 px-6 rounded-lg text-lg font-semibold transition-all">Get in Touch</a>
      </div>
      
      {/* Navigation */}
      <div className="fade-in mt-6 flex space-x-6">
        <Link href="/portfolio" className="text-gray-300 hover:text-blue-400 transition-all">Portfolio</Link>
        <Link href="/about" className="text-gray-300 hover:text-purple-400 transition-all">About</Link>
        <Link href="/contact" className="text-gray-300 hover:text-pink-400 transition-all">Contact</Link>
      </div>
    </div>
  );
}
