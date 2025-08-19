# Ecoweb
npm i @vercel/analytics
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/yourusername/yourrepo.git
git push -u origin main
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { motion } from "framer-motion";

export default function Home() {
  const [form, setForm] = useState({ name: "", email: "", message: "" });

  const handleChange = (e) => {
    setForm({ ...form, [e.target.name]: e.target.value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert("Message sent! We will contact you soon.");
    setForm({ name: "", email: "", message: "" });
  };

  return (
    <div className="min-h-screen bg-green-50 text-gray-800">
      {/* Hero Section */}
      <section className="text-center py-20 bg-green-600 text-white">
        <motion.h1
          initial={{ opacity: 0, y: -20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.6 }}
          className="text-4xl font-bold mb-4"
        >
          KodeMamas EcoWeb 🌍
        </motion.h1>
        <p className="text-lg max-w-xl mx-auto">
          Founded by <strong>Nokwazi Nobuhle Xaba</strong>, EcoWeb empowers recycling companies, green startups, and eco-projects with affordable websites and digital branding.
        </p>
        <Button className="mt-6 bg-white text-green-700 hover:bg-green-100">
          Get a Quote
        </Button>
      </section>

      {/* Services Section */}
      <section className="py-16 px-6 grid md:grid-cols-3 gap-6 max-w-6xl mx-auto">
        {[
          {
            title: "Starter Websites",
            desc: "Affordable 3–5 page websites tailored for eco-businesses.",
            price: "From R2,500",
          },
          {
            title: "Eco E-commerce",
            desc: "Online stores to sell recycled and sustainable products.",
            price: "From R5,000",
          },
          {
            title: "Branding & Maintenance",
            desc: "Logos, social media branding, and monthly website updates.",
            price: "R800 – R1,200 p/m",
          },
        ].map((service, i) => (
          <Card
            key={i}
            className="rounded-2xl shadow-md hover:shadow-lg transition"
          >
            <CardContent className="p-6">
              <h3 className="text-xl font-semibold mb-2">{service.title}</h3>
              <p className="text-gray-600 mb-2">{service.desc}</p>
              <p className="font-bold text-green-700">{service.price}</p>
            </CardContent>
          </Card>
        ))}
      </section>

      {/* React Playground Section */}
      <section className="py-16 px-6 bg-white max-w-4xl mx-auto rounded-2xl shadow-md my-12">
        <h2 className="text-2xl font-bold text-center mb-6">Try React Code Live!</h2>
        <div className="flex justify-center">
          <iframe
            src="https://codesandbox.io/embed/new?codemirror=1"
            style={{
              width: "100%",
              minHeight: "500px",
              border: "0",
              borderRadius: "8px",
              overflow: "hidden",
            }}
            title="React Live Editor"
            allow="accelerometer; ambient-light-sensor; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; payment; usb; vr; xr-spatial-tracking"
            sandbox="allow-forms allow-modals allow-popups allow-presentation allow-same-origin allow-scripts"
          />
        </div>
        <p className="text-center text-sm text-gray-400 mt-4">
          Powered by <a href="https://codesandbox.io/" className="underline" target="_blank" rel="noopener noreferrer">CodeSandbox</a>
        </p>
      </section>

      {/* Contact Form */}
      <section className="py-20 px-6 bg-white max-w-4xl mx-auto rounded-2xl shadow-md">
        <h2 className="text-2xl font-bold text-center mb-6">Contact Us</h2>
        <form onSubmit={handleSubmit} className="grid gap-4">
          <Input
            name="name"
            placeholder="Your Name"
            value={form.name}
            onChange={handleChange}
            required
          />
          <Input
            name="email"
            type="email"
            placeholder="Your Email"
            value={form.email}
            onChange={handleChange}
            required
          />
          <Textarea
            name="message"
            placeholder="Your Message"
            value={form.message}
            onChange={handleChange}
            required
          />
          <Button type="submit" className="bg-green-600 hover:bg-green-700">
            Send Message
          </Button>
        </form>
      </section>

      {/* Footer */}
      <footer className="text-center py-6 mt-10 bg-green-100 text-gray-600">
        © {new Date().getFullYear()} KodeMamas EcoWeb | Built by Nokwazi Nobuhle Xaba for a Greener Digital Future.
      </footer>
    </div>
  );
}
