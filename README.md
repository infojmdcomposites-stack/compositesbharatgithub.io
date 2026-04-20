# compositesbharatgithub.io
import { useState, useEffect } from 'react';
import { motion } from 'framer-motion';
import Navbar from './components/Navbar';
import Hero from './components/Hero';
import Products from './components/Products';
import Processes from './components/Processes';
import Contact from './components/Contact';
import Footer from './components/Footer';

function App() {
  const [scrolled, setScrolled] = useState(false);

  useEffect(() => {
    const handleScroll = () => {
      setScrolled(window.scrollY > 50);
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  return (
    <div className="min-h-screen bg-neutral-950 text-white selection:bg-orange-500 selection:text-white">
      {/* Background Pattern */}
      <div className="fixed inset-0 z-0 opacity-20 pointer-events-none">
        <div className="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/carbon-fibre.png')]"></div>
      </div>

      <Navbar scrolled={scrolled} />
      
      <main className="relative z-10">
        <Hero />
        
        <section id="products" className="py-24">
          <div className="container mx-auto px-4">
            <motion.div 
              initial={{ opacity: 0, y: 20 }}
              whileInView={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.6 }}
              viewport={{ once: true }}
              className="text-center mb-16"
            >
              <h2 className="text-4xl md:text-5xl font-bold mb-4">Advanced Materials</h2>
              <div className="w-24 h-1 bg-orange-500 mx-auto"></div>
              <p className="mt-6 text-neutral-400 max-w-2xl mx-auto text-lg font-light">
                Discover our range of high-performance fibers and resins engineered for extreme performance and durability.
              </p>
            </motion.div>
            <Products />
          </div>
        </section>

        <Processes />

        <section id="applications" className="py-24 bg-neutral-900/50">
          <div className="container mx-auto px-4">
            <motion.div 
              initial={{ opacity: 0, y: 20 }}
              whileInView={{ opacity: 1, y: 0 }}
              transition={{ duration: 0.6 }}
              viewport={{ once: true }}
              className="text-center mb-16"
            >
              <h2 className="text-4xl md:text-5xl font-bold mb-4">Our Applications</h2>
              <div className="w-24 h-1 bg-orange-500 mx-auto"></div>
            </motion.div>
            
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
              <ApplicationCard 
                title="Drones & UAVs" 
                image="/drone_body.jpg"
                description="Ultra-lightweight drone frames and structures for enhanced flight time and stability."
              />
              <ApplicationCard 
                title="Automotive Parts" 
                image="/automotive_parts.jpg"
                description="High-strength components for performance vehicles, including spoilers and body panels."
              />
              <ApplicationCard 
                title="Industrial Tubes" 
                image="/carbon_fiber_tubes.jpg"
                description="Precision-engineered round and square tubes for various industrial structural needs."
              />
            </div>
          </div>
        </section>

        <Contact />
      </main>

      <Footer />
    </div>
  );
}

const ApplicationCard = ({ title, image, description }: { title: string, image: string, description: string }) => (
  <motion.div 
    whileHover={{ y: -10 }}
    initial={{ opacity: 0, y: 20 }}
    whileInView={{ opacity: 1, y: 0 }}
    transition={{ duration: 0.5 }}
    viewport={{ once: true }}
    className="group relative overflow-hidden rounded-3xl bg-neutral-800 border border-neutral-700"
  >
    <div className="h-64 overflow-hidden">
      <img 
        src={image} 
        alt={title} 
        className="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
      />
      <div className="absolute inset-0 bg-gradient-to-t from-neutral-900 via-transparent to-transparent opacity-60"></div>
    </div>
    <div className="p-8">
      <h3 className="text-2xl font-bold mb-3 group-hover:text-orange-500 transition-colors">{title}</h3>
      <p className="text-neutral-400 text-sm leading-relaxed mb-4">
        {description}
      </p>
      <div className="w-10 h-1 bg-orange-600 group-hover:w-20 transition-all duration-300"></div>
    </div>
  </motion.div>
);

export default App;
