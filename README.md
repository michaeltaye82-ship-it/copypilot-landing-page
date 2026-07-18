# copypilot-landing-page
Modern SaaS landing page built with Next.js and Tailwind CSS.
saas-landing/
├── app/
│   ├── components/
│   │   ├── Navbar.tsx
│   │   ├── Hero.tsx
│   │   ├── Features.tsx
│   │   ├── Pricing.tsx
│   │   ├── Testimonials.tsx
│   │   ├── FAQ.tsx
│   │   ├── CTA.tsx
│   │   └── Footer.tsx
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── public/
├── next.config.ts
├── next-env.d.ts
├── tailwind.config.ts
├── tsconfig.json
├── postcss.config.js
├── package.json
├── .gitignore
└── README.md
{
  "name": "saas-landing",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "next": "15.1.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "framer-motion": "^11.15.0",
    "lucide-react": "^0.468.0"
  },
  "devDependencies": {
    "@types/node": "^22.10.0",
    "@types/react": "^19.0.0",
    "@types/react-dom": "^19.0.0",
    "typescript": "^5.7.0",
    "tailwindcss": "^3.4.0",
    "postcss": "^8.4.0",
    "autoprefixer": "^10.4.0"
  }
}
{
  "compilerOptions": {
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [{ "name": "next" }],
    "paths": { "@/*": ["./*"] },
    "target": "ES2017"
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
},
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  output: "export",
  images: {
    unoptimized: true,
  },
};

export default nextConfig;
import type { Config } from "tailwindcss";

const config: Config = {
  darkMode: "class",
  content: [
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {
      colors: {
        background: "#0a0a0f",
        surface: "#111118",
        "surface-light": "#1a1a24",
        "surface-hover": "#222230",
        border: "#1e1e2e",
        "border-light": "#2a2a3c",
        foreground: "#f0f0f5",
        muted: "#8a8a9a",
        primary: "#6366f1",
        "primary-hover": "#4f46e5",
        "primary-glow": "rgba(99, 102, 241, 0.15)",
        secondary: "#22d3ee",
        accent: "#a78bfa",
        success: "#34d399",
        warning: "#fbbf24",
      },
      fontFamily: {
        sans: ["Inter", "system-ui", "sans-serif"],
      },
      animation: {
        "gradient-x": "gradient-x 8s ease infinite",
        "float": "float 6s ease-in-out infinite",
        "pulse-slow": "pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite",
        "shimmer": "shimmer 2s linear infinite",
      },
      keyframes: {
        "gradient-x": {
          "0%, 100%": { backgroundPosition: "0% 50%" },
          "50%": { backgroundPosition: "100% 50%" },
        },
        float: {
          "0%, 100%": { transform: "translateY(0px)" },
          "50%": { transform: "translateY(-20px)" },
        },
        shimmer: {
          "0%": { backgroundPosition: "-200% 0" },
          "100%": { backgroundPosition: "200% 0" },
        },
      },
      backgroundImage: {
        "gradient-radial": "radial-gradient(var(--tw-gradient-stops))",
        "hero-glow":
          "radial-gradient(ellipse 80% 60% at 50% -20%, rgba(99,102,241,0.15), transparent)",
      },
    },
  },
  plugins: [],
};

export default config;
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};
import type { Metadata } from "next";
import "./globals.css";

export const metadata: Metadata = {
  title: "Nexus — Build Faster with AI-Powered Analytics",
  description:
    "Nexus is the all-in-one platform for modern teams. Ship faster, analyze smarter, and scale effortlessly with AI-powered insights.",
  keywords: [
    "SaaS",
    "analytics",
    "AI",
    "dashboard",
    "data visualization",
    "business intelligence",
  ],
  authors: [{ name: "Nexus" }],
  creator: "Nexus",
  metadataBase: new URL("https://nexus.dev"),
  openGraph: {
    type: "website",
    locale: "en_US",
    url: "https://nexus.dev",
    siteName: "Nexus",
    title: "Nexus — Build Faster with AI-Powered Analytics",
    description:
      "The all-in-one platform for modern teams. Ship faster, analyze smarter, and scale effortlessly.",
    images: [
      {
        url: "/og-image.jpg",
        width: 1200,
        height: 630,
        alt: "Nexus Dashboard Preview",
      },
    ],
  },
  twitter: {
    card: "summary_large_image",
    title: "Nexus — Build Faster with AI-Powered Analytics",
    description:
      "The all-in-one platform for modern teams. Ship faster, analyze smarter, and scale effortlessly.",
    images: ["/og-image.jpg"],
    creator: "@nexus",
  },
  robots: {
    index: true,
    follow: true,
    googleBot: {
      index: true,
      follow: true,
      "max-video-preview": -1,
      "max-image-preview": "large",
      "max-snippet": -1,
    },
  },
  icons: {
    icon: "/favicon.ico",
    shortcut: "/favicon-16x16.png",
    apple: "/apple-touch-icon.png",
  },
  manifest: "/site.webmanifest",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="en" className="dark">
      <body className="antialiased">{children}</body>
    </html>
  );
}
@tailwind base;
@tailwind components;
@tailwind utilities;

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');

@layer base {
  :root {
    --background: #0a0a0f;
    --surface: #111118;
    --surface-light: #1a1a24;
    --foreground: #f0f0f5;
    --muted: #8a8a9a;
    --border: #1e1e2e;
    --primary: #6366f1;
  }

  * {
    @apply border-border;
  }

  html {
    scroll-behavior: smooth;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  body {
    @apply bg-background text-foreground font-sans;
    background-color: #0a0a0f;
    overflow-x: hidden;
  }

  ::selection {
    background-color: rgba(99, 102, 241, 0.3);
    color: #f0f0f5;
  }

  ::-webkit-scrollbar {
    width: 8px;
  }

  ::-webkit-scrollbar-track {
    background: #0a0a0f;
  }

  ::-webkit-scrollbar-thumb {
    background: #2a2a3c;
    border-radius: 4px;
  }

  ::-webkit-scrollbar-thumb:hover {
    background: #3a3a50;
  }
}

@layer utilities {
  .text-gradient {
    @apply bg-clip-text text-transparent bg-gradient-to-r from-primary via-accent to-secondary;
  }

  .glass {
    @apply bg-surface/80 backdrop-blur-xl border border-border/50;
  }

  .glow-primary {
    box-shadow: 0 0 40px rgba(99, 102, 241, 0.15), 0 0 80px rgba(99, 102, 241, 0.05);
  }

  .glow-secondary {
    box-shadow: 0 0 40px rgba(34, 211, 238, 0.1), 0 0 80px rgba(34, 211, 238, 0.05);
  }
}
import Navbar from "./components/Navbar";
import Hero from "./components/Hero";
import Features from "./components/Features";
import Pricing from "./components/Pricing";
import Testimonials from "./components/Testimonials";
import FAQ from "./components/FAQ";
import CTA from "./components/CTA";
import Footer from "./components/Footer";

export default function Home() {
  return (
    <main className="relative min-h-screen bg-background">
      <Navbar />
      <Hero />
      <Features />
      <Pricing />
      <Testimonials />
      <FAQ />
      <CTA />
      <Footer />
    </main>
  );
}
"use client";

import { useState, useEffect } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { Menu, X, Zap } from "lucide-react";

const navLinks = [
  { label: "Features", href: "#features" },
  { label: "Pricing", href: "#pricing" },
  { label: "Testimonials", href: "#testimonials" },
  { label: "FAQ", href: "#faq" },
];

export default function Navbar() {
  const [scrolled, setScrolled] = useState(false);
  const [mobileOpen, setMobileOpen] = useState(false);

  useEffect(() => {
    const handleScroll = () => setScrolled(window.scrollY > 20);
    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  }, []);

  return (
    <motion.header
      initial={{ y: -100 }}
      animate={{ y: 0 }}
      transition={{ duration: 0.6, ease: "easeOut" }}
      className={`fixed top-0 left-0 right-0 z-50 transition-all duration-300 ${
        scrolled
          ? "bg-background/80 backdrop-blur-xl border-b border-border/50"
          : "bg-transparent"
      }`}
    >
      <nav className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div className="flex items-center justify-between h-16 sm:h-20">
          <a href="#" className="flex items-center gap-2 group">
            <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-primary to-accent flex items-center justify-center group-hover:shadow-lg group-hover:shadow-primary/20 transition-shadow">
              <Zap className="w-4 h-4 text-white" />
            </div>
            <span className="text-lg font-bold tracking-tight text-foreground">
              Nexus
            </span>
          </a>

          <div className="hidden md:flex items-center gap-1">
            {navLinks.map((link) => (
              <a
                key={link.label}
                href={link.href}
                className="px-4 py-2 text-sm font-medium text-muted hover:text-foreground transition-colors rounded-lg hover:bg-surface-light"
              >
                {link.label}
              </a>
            ))}
          </div>

          <div className="hidden md:flex items-center gap-3">
            <a
              href="#"
              className="px-4 py-2 text-sm font-medium text-muted hover:text-foreground transition-colors"
            >
              Sign in
            </a>
            <a
              href="#pricing"
              className="px-4 py-2 text-sm font-semibold text-white bg-primary hover:bg-primary-hover rounded-lg transition-all hover:shadow-lg hover:shadow-primary/25"
            >
              Get Started
            </a>
          </div>

          <button
            onClick={() => setMobileOpen(!mobileOpen)}
            className="md:hidden p-2 text-muted hover:text-foreground transition-colors"
          >
            {mobileOpen ? <X className="w-5 h-5" /> : <Menu className="w-5 h-5" />}
          </button>
        </div>
      </nav>

      <AnimatePresence>
        {mobileOpen && (
          <motion.div
            initial={{ opacity: 0, height: 0 }}
            animate={{ opacity: 1, height: "auto" }}
            exit={{ opacity: 0, height: 0 }}
            transition={{ duration: 0.3 }}
            className="md:hidden bg-background/95 backdrop-blur-xl border-b border-border/50 overflow-hidden"
          >
            <div className="px-4 py-4 space-y-1">
              {navLinks.map((link) => (
                <a
                  key={link.label}
                  href={link.href}
                  onClick={() => setMobileOpen(false)}
                  className="block px-4 py-3 text-sm font-medium text-muted hover:text-foreground hover:bg-surface-light rounded-lg transition-colors"
                >
                  {link.label}
                </a>
              ))}
              <div className="pt-3 flex flex-col gap-2">
                <a
                  href="#"
                  className="px-4 py-2.5 text-sm font-medium text-center text-muted hover:text-foreground border border-border rounded-lg transition-colors"
                >
                  Sign in
                </a>
                <a
                  href="#pricing"
                  onClick={() => setMobileOpen(false)}
                  className="px-4 py-2.5 text-sm font-semibold text-center text-white bg-primary hover:bg-primary-hover rounded-lg transition-colors"
                >
                  Get Started
                </a>
              </div>
            </div>
          </motion.div>
        )}
      </AnimatePresence>
    </motion.header>
  );
}
"use client";

import { motion } from "framer-motion";
import { ArrowRight, Play, Sparkles } from "lucide-react";

export default function Hero() {
  return (
    <section className="relative min-h-screen flex items-center justify-center overflow-hidden pt-20">
      <div className="absolute inset-0 bg-hero-glow pointer-events-none" />
      <div className="absolute top-1/4 left-1/4 w-96 h-96 bg-primary/10 rounded-full blur-[128px] pointer-events-none" />
      <div className="absolute bottom-1/4 right-1/4 w-96 h-96 bg-accent/10 rounded-full blur-[128px] pointer-events-none" />
      <div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-secondary/5 rounded-full blur-[150px] pointer-events-none" />

      <div
        className="absolute inset-0 opacity-[0.03]"
        style={{
          backgroundImage:
            "linear-gradient(rgba(255,255,255,0.1) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.1) 1px, transparent 1px)",
          backgroundSize: "60px 60px",
        }}
      />

      <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <motion.div
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.5 }}
          className="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-surface-light border border-border-light mb-8"
        >
          <Sparkles className="w-3.5 h-3.5 text-secondary" />
          <span className="text-xs font-medium text-muted">
            Now with AI-powered insights
          </span>
        </motion.div>

        <motion.h1
          initial={{ opacity: 0, y: 30 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.6, delay: 0.1 }}
          className="text-4xl sm:text-5xl md:text-7xl font-bold tracking-tight leading-[1.1] mb-6"
        >
          Build{" "}
          <span className="text-gradient">faster</span>
          <br />
          with intelligent
          <br />
          analytics
        </motion.h1>

        <motion.p
          initial={{ opacity: 0, y: 30 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.6, delay: 0.2 }}
          className="max-w-2xl mx-auto text-base sm:text-lg text-muted leading-relaxed mb-10"
        >
          Nexus gives your team the power to ship products faster, understand
          users deeper, and make data-driven decisions with confidence. All in
          one beautiful platform.
        </motion.p>

        <motion.div
          initial={{ opacity: 0, y: 30 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 0.6, delay: 0.3 }}
          className="flex flex-col sm:flex-row items-center justify-center gap-4 mb-16"
        >
          <a
            href="#pricing"
            className="group flex items-center gap-2 px-8 py-3.5 bg-primary hover:bg-primary-hover text-white font-semibold rounded-xl transition-all hover:shadow-xl hover:shadow-primary/25"
          >
            Start Free Trial
            <ArrowRight className="w-4 h-4 group-hover:translate-x-1 transition-transform" />
          </a>
          <a
            href="#features"
            className="flex items-center gap-2 px-8 py-3.5 bg-surface-light hover:bg-surface-hover text-foreground font-semibold rounded-xl border border-border-light transition-all hover:border-border"
          >
            <Play className="w-4 h-4" />
            Watch Demo
          </a>
        </motion.div>

        <motion.div
          initial={{ opacity: 0, y: 60, scale: 0.95 }}
          animate={{ opacity: 1, y: 0, scale: 1 }}
          transition={{ duration: 0.8, delay: 0.5 }}
          className="relative max-w-5xl mx-auto"
        >
          <div className="relative rounded-2xl overflow-hidden border border-border-light bg-surface/50 backdrop-blur-sm glow-primary">
            <div className="flex items-center gap-2 px-4 py-3 border-b border-border/50 bg-surface-light/50">
              <div className="flex gap-1.5">
                <div className="w-3 h-3 rounded-full bg-red-500/80" />
                <div className="w-3 h-3 rounded-full bg-yellow-500/80" />
                <div className="w-3 h-3 rounded-full bg-green-500/80" />
              </div>
              <div className="flex-1 mx-4">
                <div className="max-w-md mx-auto h-6 rounded-md bg-background/60 flex items-center px-3">
                  <span className="text-[10px] text-muted/60">app.nexus.dev/dashboard</span>
                </div>
              </div>
            </div>

            <div className="p-6 sm:p-8">
              <div className="grid grid-cols-2 sm:grid-cols-4 gap-3 sm:gap-4 mb-6">
                {[
                  { label: "Total Users", value: "24,592", change: "+12.5%", positive: true },
                  { label: "Revenue", value: "$84.2K", change: "+8.2%", positive: true },
                  { label: "Conversion", value: "3.24%", change: "+0.4%", positive: true },
                  { label: "Churn Rate", value: "2.1%", change: "-0.3%", positive: true },
                ].map((stat) => (
                  <div
                    key={stat.label}
                    className="p-3 sm:p-4 rounded-xl bg-surface-light/60 border border-border/30"
                  >
                    <p className="text-[10px] sm:text-xs text-muted mb-1">{stat.label}</p>
                    <p className="text-lg sm:text-xl font-bold text-foreground">{stat.value}</p>
                    <p className="text-[10px] sm:text-xs text-success mt-0.5">{stat.change}</p>
                  </div>
                ))}
              </div>

              <div className="grid grid-cols-1 lg:grid-cols-3 gap-4">
                <div className="lg:col-span-2 p-4 sm:p-5 rounded-xl bg-surface-light/60 border border-border/30">
                  <div className="flex items-center justify-between mb-4">
                    <p className="text-xs sm:text-sm font-medium text-foreground">Revenue Overview</p>
                    <div className="flex gap-2">
                      <span className="px-2 py-0.5 text-[10px] rounded bg-primary/20 text-primary">Monthly</span>
                    </div>
                  </div>
                  <svg viewBox="0 0 400 120" className="w-full h-24 sm:h-32">
                    <defs>
                      <linearGradient id="chartGrad" x1="0" y1="0" x2="0" y2="1">
                        <stop offset="0%" stopColor="#6366f1" stopOpacity="0.3" />
                        <stop offset="100%" stopColor="#6366f1" stopOpacity="0" />
                      </linearGradient>
                    </defs>
                    <path
                      d="M0,100 Q40,80 80,85 T160,60 T240,50 T320,30 T400,20 L400,120 L0,120 Z"
                      fill="url(#chartGrad)"
                    />
                    <path
                      d="M0,100 Q40,80 80,85 T160,60 T240,50 T320,30 T400,20"
                      fill="none"
                      stroke="#6366f1"
                      strokeWidth="2"
                    />
                    <circle cx="320" cy="30" r="4" fill="#6366f1" />
                    <circle cx="320" cy="30" r="8" fill="#6366f1" opacity="0.2" />
                  </svg>
                </div>
                <div className="p-4 sm:p-5 rounded-xl bg-surface-light/60 border border-border/30">
                  <p className="text-xs sm:text-sm font-medium text-foreground mb-4">Traffic Sources</p>
                  <div className="space-y-3">
                    {[
                      { label: "Direct", pct: 45, color: "#6366f1" },
                      { label: "Organic", pct: 30, color: "#22d3ee" },
                      { label: "Referral", pct: 15, color: "#a78bfa" },
                      { label: "Social", pct: 10, color: "#34d399" },
                    ].map((item) => (
                      <div key={item.label}>
                        <div className="flex justify-between text-[10px] sm:text-xs text-muted mb-1">
                          <span>{item.label}</span>
                          <span>{item.pct}%</span>
                        </div>
                        <div className="h-1.5 rounded-full bg-background/60 overflow-hidden">
                          <div
                            className="h-full rounded-full transition-all"
                            style={{ width: `${item.pct}%`, backgroundColor: item.color }}
                          />
                        </div>
                      </div>
                    ))}
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div className="absolute -bottom-4 left-1/2 -translate-x-1/2 w-[90%] h-8 bg-primary/10 blur-xl rounded-full" />
        </motion.div>
      </div>
    </section>
  );
}
"use client";

import { motion } from "framer-motion";
import { Check, Sparkles } from "lucide-react";

const plans = [
  {
    name: "Starter",
    description: "Perfect for individuals and small projects getting started.",
    price: "$0",
    period: "/month",
    badge: null,
    features: [
      "Up to 3 team members",
      "10,000 events/month",
      "7-day data retention",
      "Basic analytics dashboard",
      "Email support",
      "1 project",
      "Community access",
    ],
    cta: "Get Started Free",
    ctaStyle: "outline",
    popular: false,
  },
  {
    name: "Pro",
    description: "For growing teams that need advanced analytics and collaboration.",
    price: "$49",
    period: "/month",
    badge: "Most Popular",
    features: [
      "Up to 20 team members",
      "500,000 events/month",
      "1-year data retention",
      "Advanced analytics & AI insights",
      "Priority email & chat support",
      "Unlimited projects",
      "Custom dashboards",
      "API access",
      "SSO authentication",
      "Slack integration",
    ],
    cta: "Start Pro Trial",
    ctaStyle: "primary",
    popular: true,
  },
  {
    name: "Enterprise",
    description: "Custom solutions for large organizations with advanced needs.",
    price: "Custom",
    period: "",
    badge: null,
    features: [
      "Unlimited team members",
      "Unlimited events",
      "Unlimited data retention",
      "Dedicated AI model training",
      "24/7 phone & email support",
      "Unlimited projects",
      "Custom dashboards & reports",
      "Full API & webhook access",
      "Advanced SSO & SAML",
      "Custom integrations",
      "SLA guarantee",
      "Dedicated success manager",
    ],
    cta: "Contact Sales",
    ctaStyle: "outline",
    popular: false,
  },
];

const containerVariants = {
  hidden: {},
  visible: {
    transition: { staggerChildren: 0.12 },
  },
};

const cardVariants = {
  hidden: { opacity: 0, y: 40 },
  visible: {
    opacity: 1,
    y: 0,
    transition: { duration: 0.6, ease: "easeOut" },
  },
};

export default function Pricing() {
  return (
    <section id="pricing" className="relative py-24 sm:py-32">
      <div className="absolute inset-0 bg-gradient-to-b from-transparent via-primary/[0.02] to-transparent pointer-events-none" />

      <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <motion.div
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true, margin: "-100px" }}
          transition={{ duration: 0.6 }}
          className="text-center mb-16 sm:mb-20"
        >
          <span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-secondary bg-secondary/10 rounded-full mb-4 border border-secondary/20">
            Pricing
          </span>
          <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
            Simple, transparent{" "}
            <span className="text-gradient">pricing</span>
          </h2>
          <p className="max-w-2xl mx-auto text-base sm:text-lg text-muted">
            Start free, scale as you grow. No hidden fees, no surprises.
          </p>
        </motion.div>

        <motion.div
          variants={containerVariants}
          initial="hidden"
          whileInView="visible"
          viewport={{ once: true, margin: "-50px" }}
          className="grid grid-cols-1 md:grid-cols-3 gap-6 lg:gap-8"
        >
          {plans.map((plan) => (
            <motion.div
              key={plan.name}
              variants={cardVariants}
              className={`relative flex flex-col rounded-2xl p-6 sm:p-8 transition-all duration-300 ${
                plan.popular
                  ? "bg-surface-light border-2 border-primary/50 shadow-2xl shadow-primary/10 scale-[1.02] md:scale-105"
                  : "bg-surface-light/40 border border-border hover:border-border-light"
              }`}
            >
              {plan.badge && (
                <div className="absolute -top-4 left-1/2 -translate-x-1/2">
                  <div className="flex items-center gap-1.5 px-4 py-1.5 bg-gradient-to-r from-primary to-accent text-white text-xs font-semibold rounded-full shadow-lg shadow-primary/25">
                    <Sparkles className="w-3 h-3" />
                    {plan.badge}
                  </div>
                </div>
              )}

              <div className="mb-6">
                <h3 className="text-lg font-semibold text-foreground mb-1">
                  {plan.name}
                </h3>
                <p className="text-sm text-muted">{plan.description}</p>
              </div>

              <div className="mb-6">
                <span className="text-4xl sm:text-5xl font-bold text-foreground tracking-tight">
                  {plan.price}
                </span>
                <span className="text-muted text-sm">{plan.period}</span>
              </div>

              <a
                href="#"
                className={`w-full py-3 px-4 rounded-xl text-sm font-semibold text-center transition-all mb-8 ${
                  plan.popular
                    ? "bg-primary hover:bg-primary-hover text-white shadow-lg shadow-primary/25 hover:shadow-xl hover:shadow-primary/30"
                    : "bg-surface hover:bg-surface-hover text-foreground border border-border hover:border-border-light"
                }`}
              >
                {plan.cta}
              </a>

              <div className="flex-1">
                <p className="text-xs font-semibold text-muted uppercase tracking-wider mb-4">
                  What's included
                </p>
                <ul className="space-y-3">
                  {plan.features.map((feature) => (
                    <li key={feature} className="flex items-start gap-3">
                      <div
                        className={`mt-0.5 w-4 h-4 rounded-full flex items-center justify-center flex-shrink-0 ${
                          plan.popular
                            ? "bg-primary/20 text-primary"
                            : "bg-surface-hover text-muted"
                        }`}
                      >
                        <Check className="w-2.5 h-2.5" />
                      </div>
                      <span className="text-sm text-muted">{feature}</span>
                    </li>
                  ))}
                </ul>
              </div>
            </motion.div>
          ))}
        </motion.div>
      </div>
    </section>
  );
}
"use client";

import { motion } from "framer-motion";
import { Star, Quote } from "lucide-react";

const testimonials = [
  {
    name: "Sarah Chen",
    role: "CTO at VercelFlow",
    avatar: "SC",
    content:
      "Nexus transformed how we understand our users. The AI insights surfaced patterns we never knew existed. Our conversion rate jumped 34% in the first quarter.",
    rating: 5,
  },
  {
    name: "Marcus Johnson",
    role: "Head of Product at StripeScale",
    avatar: "MJ",
    content:
      "The real-time dashboards are incredibly fast. We went from waiting hours for reports to seeing data update instantly. It changed how our team makes decisions.",
    rating: 5,
  },
  {
    name: "Elena Rodriguez",
    role: "VP Engineering at CloudNine",
    avatar: "ER",
    content:
      "We evaluated 12 analytics platforms. Nexus was the only one that combined power with elegance. The team adopted it in days, not months.",
    rating: 5,
  },
  {
    name: "David Park",
    role: "Founder at DataPulse",
    avatar: "DP",
    content:
      "The API is beautifully designed. We integrated Nexus into our entire stack in under a week. Documentation is world-class and support is genuinely helpful.",
    rating: 5,
  },
  {
    name: "Aisha Patel",
    role: "Director of Analytics at FinTrack",
    avatar: "AP",
    content:
      "Enterprise security was non-negotiable for us. Nexus exceeded every requirement and the SSO setup was seamless. Our security team loves it.",
    rating: 5,
  },
  {
    name: "James Wilson",
    role: "CEO at GrowthLab",
    avatar: "JW",
    content:
      "We replaced three separate tools with Nexus. The ROI was immediate. Less context switching, cleaner data, and our team is actually excited to open the dashboard.",
    rating: 5,
  },
];

const containerVariants = {
  hidden: {},
  visible: {
    transition: { staggerChildren: 0.1 },
  },
};

const itemVariants = {
  hidden: { opacity: 0, y: 30 },
  visible: {
    opacity: 1,
    y: 0,
    transition: { duration: 0.5, ease: "easeOut" },
  },
};

export default function Testimonials() {
  return (
    <section id="testimonials" className="relative py-24 sm:py-32">
      <div className="absolute inset-0 bg-gradient-to-b from-transparent via-accent/[0.02] to-transparent pointer-events-none" />

      <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <motion.div
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true, margin: "-100px" }}
          transition={{ duration: 0.6 }}
          className="text-center mb-16 sm:mb-20"
        >
          <span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-accent bg-accent/10 rounded-full mb-4 border border-accent/20">
            Testimonials
          </span>
          <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
            Loved by{" "}
            <span className="text-gradient">thousands</span> of teams
          </h2>
          <p className="max-w-2xl mx-auto text-base sm:text-lg text-muted">
            See what industry leaders say about their experience with Nexus.
          </p>
        </motion.div>

        <motion.div
          variants={containerVariants}
          initial="hidden"
          whileInView="visible"
          viewport={{ once: true, margin: "-50px" }}
          className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6"
        >
          {testimonials.map((t, i) => (
            <motion.div
              key={t.name}
              variants={itemVariants}
              className={`group relative p-6 rounded-2xl bg-surface-light/40 border border-border hover:border-border-light transition-all duration-300 hover:-translate-y-1 ${
                i === 0 || i === 3 ? "lg:row-span-1" : ""
              }`}
            >
              <Quote className="w-8 h-8 text-primary/20 mb-4" />

              <div className="flex gap-1 mb-4">
                {Array.from({ length: t.rating }).map((_, j) => (
                  <Star
                    key={j}
                    className="w-4 h-4 fill-warning text-warning"
                  />
                ))}
              </div>

              <p className="text-sm sm:text-base text-foreground/90 leading-relaxed mb-6">
                &ldquo;{t.content}&rdquo;
              </p>

              <div className="flex items-center gap-3">
                <div className="w-10 h-10 rounded-full bg-gradient-to-br from-primary to-accent flex items-center justify-center text-white text-xs font-bold">
                  {t.avatar}
                </div>
                <div>
                  <p className="text-sm font-semibold text-foreground">
                    {t.name}
                  </p>
                  <p className="text-xs text-muted">{t.role}</p>
                </div>
              </div>
            </motion.div>
          ))}
        </motion.div>
      </div>
    </section>
  );
}
"use client";

import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { ChevronDown } from "lucide-react";

const faqs = [
  {
    question: "How does the free trial work?",
    answer:
      "You get full access to all Pro features for 14 days, no credit card required. After the trial, you can choose to upgrade or continue with our free Starter plan. Your data stays intact either way.",
  },
  {
    question: "Can I switch plans at any time?",
    answer:
      "Absolutely. You can upgrade, downgrade, or cancel your plan at any time from your billing dashboard. Prorated credits are applied automatically when you upgrade mid-cycle.",
  },
  {
    question: "Is my data secure?",
    answer:
      "Security is our top priority. We are SOC 2 Type II certified, use AES-256 encryption at rest and TLS 1.3 in transit. Your data is never sold, shared, or used to train AI models without explicit consent.",
  },
  {
    question: "Do you offer refunds?",
    answer:
      "Yes, we offer a 30-day money-back guarantee on all paid plans. If Nexus is not the right fit for your team, contact support within 30 days for a full refund, no questions asked.",
  },
  {
    question: "What integrations are supported?",
    answer:
      "We support 200+ integrations including Slack, Salesforce, Stripe, Segment, HubSpot, Zendesk, GitHub, Jira, and more. We also offer a robust REST API and webhooks for custom integrations.",
  },
  {
    question: "How does the AI insights feature work?",
    answer:
      "Our AI analyzes your data patterns to detect anomalies, predict trends, and surface actionable recommendations. All processing happens in real-time using models trained specifically for analytics workloads.",
  },
  {
    question: "Do you offer onboarding support?",
    answer:
      "Every Pro and Enterprise plan includes onboarding support. Enterprise customers get a dedicated success manager who will help migrate your data, set up dashboards, and train your team.",
  },
  {
    question: "What happens if I exceed my event limit?",
    answer:
      "We never drop your data. If you exceed your plan limit, we will notify you and give you a grace period to upgrade. Events are still collected and you can access them once you adjust your plan.",
  },
];

export default function FAQ() {
  const [openIndex, setOpenIndex] = useState<number | null>(0);

  return (
    <section id="faq" className="relative py-24 sm:py-32">
      <div className="relative z-10 max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
        <motion.div
          initial={{ opacity: 0, y: 20 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true, margin: "-100px" }}
          transition={{ duration: 0.6 }}
          className="text-center mb-16 sm:mb-20"
        >
          <span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-primary bg-primary/10 rounded-full mb-4 border border-primary/20">
            FAQ
          </span>
          <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
            Frequently asked{" "}
            <span className="text-gradient">questions</span>
          </h2>
          <p className="text-base sm:text-lg text-muted">
            Everything you need to know about Nexus.
          </p>
        </motion.div>

        <motion.div
          initial={{ opacity: 0 }}
          whileInView={{ opacity: 1 }}
          viewport={{ once: true, margin: "-50px" }}
          transition={{ duration: 0.6 }}
          className="space-y-3"
        >
          {faqs.map((faq, index) => (
            <div
              key={index}
              className={`rounded-xl border transition-all duration-300 ${
                openIndex === index
                  ? "bg-surface-light border-border-light"
                  : "bg-surface-light/30 border-border hover:border-border-light"
              }`}
            >
              <button
                onClick={() =>
                  setOpenIndex(openIndex === index ? null : index)
                }
                className="w-full flex items-center justify-between p-5 sm:p-6 text-left"
              >
                <span className="text-sm sm:text-base font-medium text-foreground pr-4">
                  {faq.question}
                </span>
                <motion.div
                  animate={{ rotate: openIndex === index ? 180 : 0 }}
                  transition={{ duration: 0.2 }}
                  className="flex-shrink-0"
                >
                  <ChevronDown className="w-5 h-5 text-muted" />
                </motion.div>
              </button>

              <AnimatePresence initial={false}>
                {openIndex === index && (
                  <motion.div
                    initial={{ height: 0, opacity: 0 }}
                    animate={{ height: "auto", opacity: 1 }}
                    exit={{ height: 0, opacity: 0 }}
                    transition={{ duration: 0.3, ease: "easeInOut" }}
                    className="overflow-hidden"
                  >
                    <div className="px-5 sm:px-6 pb-5 sm:pb-6">
                      <p className="text-sm text-muted leading-relaxed">
                        {faq.answer}
                      </p>
                    </div>
                  </motion.div>
                )}
              </AnimatePresence>
            </div>
          ))}
        </motion.div>
      </div>
    </section>
  );
}
"use client";

import { motion } from "framer-motion";
import { ArrowRight, Sparkles } from "lucide-react";

export default function CTA() {
  return (
    <section className="relative py-24 sm:py-32">
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        <div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[400px] bg-primary/10 rounded-full blur-[120px]" />
        <div className="absolute top-1/2 left-1/4 -translate-y-1/2 w-[300px] h-[300px] bg-accent/10 rounded-full blur-[100px]" />
        <div className="absolute top-1/2 right-1/4 -translate-y-1/2 w-[300px] h-[300px] bg-secondary/10 rounded-full blur-[100px]" />
      </div>

      <div className="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
        <motion.div
          initial={{ opacity: 0, y: 40 }}
          whileInView={{ opacity: 1, y: 0 }}
          viewport={{ once: true, margin: "-100px" }}
          transition={{ duration: 0.7 }}
          className="relative text-center p-8 sm:p-12 lg:p-16 rounded-3xl bg-surface-light/60 border border-border-light backdrop-blur-xl overflow-hidden"
        >
          <div className="absolute inset-0 bg-gradient-to-br from-primary/5 via-transparent to-accent/5 pointer-events-none" />

          <div className="relative z-10">
            <motion.div
              initial={{ scale: 0 }}
              whileInView={{ scale: 1 }}
              viewport={{ once: true }}
              transition={{ duration: 0.5, delay: 0.2 }}
              className="inline-flex items-center justify-center w-14 h-14 rounded-2xl bg-gradient-to-br from-primary to-accent mb-8 shadow-lg shadow-primary/25"
            >
              <Sparkles className="w-7 h-7 text-white" />
            </motion.div>

            <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
              Ready to{" "}
              <span className="text-gradient">transform</span> your
              workflow?
            </h2>

            <p className="max-w-xl mx-auto text-base sm:text-lg text-muted mb-10">
              Join 10,000+ teams already using Nexus to ship faster and
              understand their users better. Start your free trial today.
            </p>

            <div className="flex flex-col sm:flex-row items-center justify-center gap-4">
              <a
                href="#pricing"
                className="group flex items-center gap-2 px-8 py-4 bg-primary hover:bg-primary-hover text-white font-semibold rounded-xl transition-all hover:shadow-xl hover:shadow-primary/25"
              >
                Start Free Trial
                <ArrowRight className="w-4 h-4 group-hover:translate-x-1 transition-transform" />
              </a>
              <a
                href="#"
                className="px-8 py-4 text-sm font-semibold text-foreground bg-surface hover:bg-surface-hover rounded-xl border border-border hover:border-border-light transition-all"
              >
                Talk to Sales
              </a>
            </div>

            <p className="mt-6 text-xs text-muted">
              No credit card required. 14-day free trial.
            </p>
          </div>
        </motion.div>
      </div>
    </section>
  );
}
"use client";

import { Zap, Github, Twitter, Linkedin, Youtube } from "lucide-react";

const footerLinks = {
  Product: [
    { label: "Features", href: "#features" },
    { label: "Pricing", href: "#pricing" },
    { label: "Changelog", href: "#" },
    { label: "Roadmap", href: "#" },
    { label: "Integrations", href: "#" },
  ],
  Company: [
    { label: "About", href: "#" },
    { label: "Blog", href: "#" },
    { label: "Careers", href: "#" },
    { label: "Press Kit", href: "#" },
    { label: "Contact", href: "#" },
  ],
  Resources: [
    { label: "Documentation", href: "#" },
    { label: "API Reference", href: "#" },
    { label: "Guides", href: "#" },
    { label: "Community", href: "#" },
    { label: "Status", href: "#" },
  ],
  Legal: [
    { label: "Privacy Policy", href: "#" },
    { label: "Terms of Service", href: "#" },
    { label: "Cookie Policy", href: "#" },
    { label: "Security", href: "#" },
    { label: "GDPR", href: "#" },
  ],
};

const socialLinks = [
  { icon: Twitter, href: "#", label: "Twitter" },
  { icon: Github, href: "#", label: "GitHub" },
  { icon: Linkedin, href: "#", label: "LinkedIn" },
  { icon: Youtube, href: "#", label: "YouTube" },
];

export default function Footer() {
  return (
    <footer className="relative border-t border-border/50">
      <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16 sm:py-20">
        <div className="grid grid-cols-2 md:grid-cols-6 gap-8 lg:gap-12">
          <div className="col-span-2">
            <a href="#" className="flex items-center gap-2 mb-4">
              <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-primary to-accent flex items-center justify-center">
                <Zap className="w-4 h-4 text-white" />
              </div>
              <span className="text-lg font-bold text-foreground">Nexus</span>
            </a>
            <p className="text-sm text-muted mb-6 max-w-xs">
              The all-in-one analytics platform for modern teams. Ship faster,
              analyze smarter, scale effortlessly.
            </p>
            <div className="flex gap-3">
              {socialLinks.map((social) => {
                const Icon = social.icon;
                return (
                  <a
                    key={social.label}
                    href={social.href}
                    aria-label={social.label}
                    className="w-9 h-9 rounded-lg bg-surface-light border border-border flex items-center justify-center text-muted hover:text-foreground hover:border-border-light transition-all"
                  >
                    <Icon className="w-4 h-4" />
                  </a>
                );
              })}
            </div>
          </div>

          {Object.entries(footerLinks).map(([category, links]) => (
            <div key={category}>
              <h4 className="text-sm font-semibold text-foreground mb-4">
                {category}
              </h4>
              <ul className="space-y-2.5">
                {links.map((link) => (
                  <li key={link.label}>
                    <a
                      href={link.href}
                      className="text-sm text-muted hover:text-foreground transition-colors"
                    >
                      {link.label}
                    </a>
                  </li>
                ))}
              </ul>
            </div>
          ))}
        </div>

        <div className="mt-16 pt-8 border-t border-border/50 flex flex-col sm:flex-row items-center justify-between gap-4">
          <p className="text-xs text-muted">
            &copy; {new Date().getFullYear()} Nexus, Inc. All rights reserved.
          </p>
          <div className="flex items-center gap-6">
            <a
              href="#"
              className="text-xs text-muted hover:text-foreground transition-colors"
            >
              Privacy
            </a>
            <a
              href="#"
              className="text-xs text-muted hover:text-foreground transition-colors"
            >
              Terms
            </a>
            <a
              href="#"
              className="text-xs text-muted hover:text-foreground transition-colors"
            >
              Cookies
            </a>
          </div>
        </div>
      </div>
    </footer>
  );
}
mkdir saas-landing && cd saas-landing
# Create all files above in their respective paths
npm install
npm run dev
I'll build a complete, production-ready SaaS landing page for you. Let me create every file in the project.
I've built the complete Nexus SaaS landing page project. Here's every file in the project, ready to copy and deploy:
📁 Project Structure
saas-landing/
├── app/
│   ├── components/
│   │   ├── Navbar.tsx
│   │   ├── Hero.tsx
│   │   ├── Features.tsx
│   │   ├── Pricing.tsx
│   │   ├── Testimonials.tsx
│   │   ├── FAQ.tsx
│   │   ├── CTA.tsx
│   │   └── Footer.tsx
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
├── public/
├── next.config.ts
├── next-env.d.ts
├── tailwind.config.ts
├── tsconfig.json
├── postcss.config.js
├── package.json
├── .gitignore
└── README.md
----
📦 package.json
{
"name": "saas-landing",
"version": "1.0.0",
"private": true,
"scripts": {
"dev": "next dev",
"build": "next build",
"start": "next start",
"lint": "next lint"
},
"dependencies": {
"next": "15.1.0",
"react": "^19.0.0",
"react-dom": "^19.0.0",
"framer-motion": "^11.15.0",
"lucide-react": "^0.468.0"
},
"devDependencies": {
"@types/node": "^22.10.0",
"@types/react": "^19.0.0",
"@types/react-dom": "^19.0.0",
"typescript": "^5.7.0",
"tailwindcss": "^3.4.0",
"postcss": "^8.4.0",
"autoprefixer": "^10.4.0"
}
}
----
⚙️ tsconfig.json
{
"compilerOptions": {
"lib": ["dom", "dom.iterable", "esnext"],
"allowJs": true,
"skipLibCheck": true,
"strict": true,
"noEmit": true,
"esModuleInterop": true,
"module": "esnext",
"moduleResolution": "bundler",
"resolveJsonModule": true,
"isolatedModules": true,
"jsx": "preserve",
"incremental": true,
"plugins": [{ "name": "next" }],
"paths": { "@/": ["./"] },
"target": "ES2017"
},
"include": ["next-env.d.ts", "/*.ts", "/.tsx", ".next/types/**/.ts"],
"exclude": ["node_modules"]
}
----
⚙️ next.config.ts
import type { NextConfig } from "next";
const nextConfig: NextConfig = {
output: "export",
images: {
unoptimized: true,
},
};
export default nextConfig;
----
🎨 tailwind.config.ts
import type { Config } from "tailwindcss";
const config: Config = {
darkMode: "class",
content: [
"./app//*.{js,ts,jsx,tsx,mdx}",
"./components//*.{js,ts,jsx,tsx,mdx}",
],
theme: {
extend: {
colors: {
background: "#0a0a0f",
surface: "#111118",
"surface-light": "#1a1a24",
"surface-hover": "#222230",
border: "#1e1e2e",
"border-light": "#2a2a3c",
foreground: "#f0f0f5",
muted: "#8a8a9a",
primary: "#6366f1",
"primary-hover": "#4f46e5",
"primary-glow": "rgba(99, 102, 241, 0.15)",
secondary: "#22d3ee",
accent: "#a78bfa",
success: "#34d399",
warning: "#fbbf24",
},
fontFamily: {
sans: ["Inter", "system-ui", "sans-serif"],
},
animation: {
"gradient-x": "gradient-x 8s ease infinite",
"float": "float 6s ease-in-out infinite",
"pulse-slow": "pulse 4s cubic-bezier(0.4, 0, 0.6, 1) infinite",
"shimmer": "shimmer 2s linear infinite",
},
keyframes: {
"gradient-x": {
"0%, 100%": { backgroundPosition: "0% 50%" },
"50%": { backgroundPosition: "100% 50%" },
},
float: {
"0%, 100%": { transform: "translateY(0px)" },
"50%": { transform: "translateY(-20px)" },
},
shimmer: {
"0%": { backgroundPosition: "-200% 0" },
"100%": { backgroundPosition: "200% 0" },
},
},
backgroundImage: {
"gradient-radial": "radial-gradient(var(--tw-gradient-stops))",
"hero-glow":
"radial-gradient(ellipse 80% 60% at 50% -20%, rgba(99,102,241,0.15), transparent)",
},
},
},
plugins: [],
};
export default config;
----
⚙️ postcss.config.js
module.exports = {
plugins: {
tailwindcss: {},
autoprefixer: {},
},
};
----
🌐 app/layout.tsx
import type { Metadata } from "next";
import "./globals.css";
export const metadata: Metadata = {
title: "Nexus — Build Faster with AI-Powered Analytics",
description:
"Nexus is the all-in-one platform for modern teams. Ship faster, analyze smarter, and scale effortlessly with AI-powered insights.",
keywords: [
"SaaS",
"analytics",
"AI",
"dashboard",
"data visualization",
"business intelligence",
],
authors: [{ name: "Nexus" }],
creator: "Nexus",
metadataBase: new URL("https://nexus.dev"),
openGraph: {
type: "website",
locale: "en_US",
url: "https://nexus.dev",
siteName: "Nexus",
title: "Nexus — Build Faster with AI-Powered Analytics",
description:
"The all-in-one platform for modern teams. Ship faster, analyze smarter, and scale effortlessly.",
images: [
{
url: "/og-image.jpg",
width: 1200,
height: 630,
alt: "Nexus Dashboard Preview",
},
],
},
twitter: {
card: "summary_large_image",
title: "Nexus — Build Faster with AI-Powered Analytics",
description:
"The all-in-one platform for modern teams. Ship faster, analyze smarter, and scale effortlessly.",
images: ["/og-image.jpg"],
creator: "@nexus",
},
robots: {
index: true,
follow: true,
googleBot: {
index: true,
follow: true,
"max-video-preview": -1,
"max-image-preview": "large",
"max-snippet": -1,
},
},
icons: {
icon: "/favicon.ico",
shortcut: "/favicon-16x16.png",
apple: "/apple-touch-icon.png",
},
manifest: "/site.webmanifest",
};
export default function RootLayout({
children,
}: Readonly<{
children: React.ReactNode;
}>) {
return (
<html lang="en" className="dark">
<body className="antialiased">{children}</body>
</html>
);
}
----
💅 app/globals.css
@tailwind base;
@tailwind components;
@tailwind utilities;
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap');
@layer base {
:root {
--background: #0a0a0f;
--surface: #111118;
--surface-light: #1a1a24;
--foreground: #f0f0f5;
--muted: #8a8a9a;
--border: #1e1e2e;
--primary: #6366f1;
}
•  {
@apply border-border;
}
html {
scroll-behavior: smooth;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
}
body {
@apply bg-background text-foreground font-sans;
background-color: #0a0a0f;
overflow-x: hidden;
}
::selection {
background-color: rgba(99, 102, 241, 0.3);
color: #f0f0f5;
}
::-webkit-scrollbar {
width: 8px;
}
::-webkit-scrollbar-track {
background: #0a0a0f;
}
::-webkit-scrollbar-thumb {
background: #2a2a3c;
border-radius: 4px;
}
::-webkit-scrollbar-thumb:hover {
background: #3a3a50;
}
}
@layer utilities {
.text-gradient {
@apply bg-clip-text text-transparent bg-gradient-to-r from-primary via-accent to-secondary;
}
.glass {
@apply bg-surface/80 backdrop-blur-xl border border-border/50;
}
.glow-primary {
box-shadow: 0 0 40px rgba(99, 102, 241, 0.15), 0 0 80px rgba(99, 102, 241, 0.05);
}
.glow-secondary {
box-shadow: 0 0 40px rgba(34, 211, 238, 0.1), 0 0 80px rgba(34, 211, 238, 0.05);
}
}
----
🏠 app/page.tsx
import Navbar from "./components/Navbar";
import Hero from "./components/Hero";
import Features from "./components/Features";
import Pricing from "./components/Pricing";
import Testimonials from "./components/Testimonials";
import FAQ from "./components/FAQ";
import CTA from "./components/CTA";
import Footer from "./components/Footer";
export default function Home() {
return (
<main className="relative min-h-screen bg-background">
<Navbar />
<Hero />
<Features />
<Pricing />
<Testimonials />
<FAQ />
<CTA />
<Footer />
</main>
);
}
----
🧭 app/components/Navbar.tsx
"use client";
import { useState, useEffect } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { Menu, X, Zap } from "lucide-react";
const navLinks = [
{ label: "Features", href: "#features" },
{ label: "Pricing", href: "#pricing" },
{ label: "Testimonials", href: "#testimonials" },
{ label: "FAQ", href: "#faq" },
];
export default function Navbar() {
const [scrolled, setScrolled] = useState(false);
const [mobileOpen, setMobileOpen] = useState(false);
useEffect(() => {
const handleScroll = () => setScrolled(window.scrollY > 20);
window.addEventListener("scroll", handleScroll);
return () => window.removeEventListener("scroll", handleScroll);
}, []);
return (

</div>
<span className="text-lg font-bold tracking-tight text-foreground">
Nexus
</span>
</a>
      <div className="hidden md:flex items-center gap-1">
        {navLinks.map((link) => (
          <a
            key={link.label}
            href={link.href}
            className="px-4 py-2 text-sm font-medium text-muted hover:text-foreground transition-colors rounded-lg hover:bg-surface-light"
          >
            {link.label}
          </a>
        ))}
      </div>

      <div className="hidden md:flex items-center gap-3">
        <a
          href="#"
          className="px-4 py-2 text-sm font-medium text-muted hover:text-foreground transition-colors"
        >
          Sign in
        </a>
        <a
          href="#pricing"
          className="px-4 py-2 text-sm font-semibold text-white bg-primary hover:bg-primary-hover rounded-lg transition-all hover:shadow-lg hover:shadow-primary/25"
        >
          Get Started
        </a>
      </div>

      <button
        onClick={() => setMobileOpen(!mobileOpen)}
        className="md:hidden p-2 text-muted hover:text-foreground transition-colors"
      >
        {mobileOpen ? <X className="w-5 h-5" /> : <Menu className="w-5 h-5" />}
      </button>
    </div>
  </nav>

  <AnimatePresence>
    {mobileOpen && (
      <motion.div
        initial={{ opacity: 0, height: 0 }}
        animate={{ opacity: 1, height: "auto" }}
        exit={{ opacity: 0, height: 0 }}
        transition={{ duration: 0.3 }}
        className="md:hidden bg-background/95 backdrop-blur-xl border-b border-border/50 overflow-hidden"
      >
        <div className="px-4 py-4 space-y-1">
          {navLinks.map((link) => (
            <a
              key={link.label}
              href={link.href}
              onClick={() => setMobileOpen(false)}
              className="block px-4 py-3 text-sm font-medium text-muted hover:text-foreground hover:bg-surface-light rounded-lg transition-colors"
            >
              {link.label}
            </a>
          ))}
          <div className="pt-3 flex flex-col gap-2">
            <a
              href="#"
              className="px-4 py-2.5 text-sm font-medium text-center text-muted hover:text-foreground border border-border rounded-lg transition-colors"
            >
              Sign in
            </a>
            <a
              href="#pricing"
              onClick={() => setMobileOpen(false)}
              className="px-4 py-2.5 text-sm font-semibold text-center text-white bg-primary hover:bg-primary-hover rounded-lg transition-colors"
            >
              Get Started
            </a>
          </div>
        </div>
      </motion.div>
    )}
  </AnimatePresence>
</motion.header>

);
}
----
🚀 app/components/Hero.tsx
"use client";
import { motion } from "framer-motion";
import { ArrowRight, Play, Sparkles } from "lucide-react";
export default function Hero() {
return (
<section className="relative min-h-screen flex items-center justify-center overflow-hidden pt-20">
<div className="absolute inset-0 bg-hero-glow pointer-events-none" />
<div className="absolute top-1/4 left-1/4 w-96 h-96 bg-primary/10 rounded-full blur-[128px] pointer-events-none" />
<div className="absolute bottom-1/4 right-1/4 w-96 h-96 bg-accent/10 rounded-full blur-[128px] pointer-events-none" />
<div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[600px] bg-secondary/5 rounded-full blur-[150px] pointer-events-none" />
  <div
    className="absolute inset-0 opacity-[0.03]"
    style={{
      backgroundImage:
        "linear-gradient(rgba(255,255,255,0.1) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,0.1) 1px, transparent 1px)",
      backgroundSize: "60px 60px",
    }}
  />

  <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.5 }}
      className="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-surface-light border border-border-light mb-8"
    >
      <Sparkles className="w-3.5 h-3.5 text-secondary" />
      <span className="text-xs font-medium text-muted">
        Now with AI-powered insights
      </span>
    </motion.div>

    <motion.h1
      initial={{ opacity: 0, y: 30 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.6, delay: 0.1 }}
      className="text-4xl sm:text-5xl md:text-7xl font-bold tracking-tight leading-[1.1] mb-6"
    >
      Build{" "}
      <span className="text-gradient">faster</span>
      <br />
      with intelligent
      <br />
      analytics
    </motion.h1>

    <motion.p
      initial={{ opacity: 0, y: 30 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.6, delay: 0.2 }}
      className="max-w-2xl mx-auto text-base sm:text-lg text-muted leading-relaxed mb-10"
    >
      Nexus gives your team the power to ship products faster, understand
      users deeper, and make data-driven decisions with confidence. All in
      one beautiful platform.
    </motion.p>

    <motion.div
      initial={{ opacity: 0, y: 30 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.6, delay: 0.3 }}
      className="flex flex-col sm:flex-row items-center justify-center gap-4 mb-16"
    >
      <a
        href="#pricing"
        className="group flex items-center gap-2 px-8 py-3.5 bg-primary hover:bg-primary-hover text-white font-semibold rounded-xl transition-all hover:shadow-xl hover:shadow-primary/25"
      >
        Start Free Trial
        <ArrowRight className="w-4 h-4 group-hover:translate-x-1 transition-transform" />
      </a>
      <a
        href="#features"
        className="flex items-center gap-2 px-8 py-3.5 bg-surface-light hover:bg-surface-hover text-foreground font-semibold rounded-xl border border-border-light transition-all hover:border-border"
      >
        <Play className="w-4 h-4" />
        Watch Demo
      </a>
    </motion.div>

    <motion.div
      initial={{ opacity: 0, y: 60, scale: 0.95 }}
      animate={{ opacity: 1, y: 0, scale: 1 }}
      transition={{ duration: 0.8, delay: 0.5 }}
      className="relative max-w-5xl mx-auto"
    >
      <div className="relative rounded-2xl overflow-hidden border border-border-light bg-surface/50 backdrop-blur-sm glow-primary">
        <div className="flex items-center gap-2 px-4 py-3 border-b border-border/50 bg-surface-light/50">
          <div className="flex gap-1.5">
            <div className="w-3 h-3 rounded-full bg-red-500/80" />
            <div className="w-3 h-3 rounded-full bg-yellow-500/80" />
            <div className="w-3 h-3 rounded-full bg-green-500/80" />
          </div>
          <div className="flex-1 mx-4">
            <div className="max-w-md mx-auto h-6 rounded-md bg-background/60 flex items-center px-3">
              <span className="text-[10px] text-muted/60">app.nexus.dev/dashboard</span>
            </div>
          </div>
        </div>

        <div className="p-6 sm:p-8">
          <div className="grid grid-cols-2 sm:grid-cols-4 gap-3 sm:gap-4 mb-6">
            {[
              { label: "Total Users", value: "24,592", change: "+12.5%", positive: true },
              { label: "Revenue", value: "$84.2K", change: "+8.2%", positive: true },
              { label: "Conversion", value: "3.24%", change: "+0.4%", positive: true },
              { label: "Churn Rate", value: "2.1%", change: "-0.3%", positive: true },
            ].map((stat) => (
              <div
                key={stat.label}
                className="p-3 sm:p-4 rounded-xl bg-surface-light/60 border border-border/30"
              >
                <p className="text-[10px] sm:text-xs text-muted mb-1">{stat.label}</p>
                <p className="text-lg sm:text-xl font-bold text-foreground">{stat.value}</p>
                <p className="text-[10px] sm:text-xs text-success mt-0.5">{stat.change}</p>
              </div>
            ))}
          </div>

          <div className="grid grid-cols-1 lg:grid-cols-3 gap-4">
            <div className="lg:col-span-2 p-4 sm:p-5 rounded-xl bg-surface-light/60 border border-border/30">
              <div className="flex items-center justify-between mb-4">
                <p className="text-xs sm:text-sm font-medium text-foreground">Revenue Overview</p>
                <div className="flex gap-2">
                  <span className="px-2 py-0.5 text-[10px] rounded bg-primary/20 text-primary">Monthly</span>
                </div>
              </div>
              <svg viewBox="0 0 400 120" className="w-full h-24 sm:h-32">
                <defs>
                  <linearGradient id="chartGrad" x1="0" y1="0" x2="0" y2="1">
                    <stop offset="0%" stopColor="#6366f1" stopOpacity="0.3" />
                    <stop offset="100%" stopColor="#6366f1" stopOpacity="0" />
                  </linearGradient>
                </defs>
                <path
                  d="M0,100 Q40,80 80,85 T160,60 T240,50 T320,30 T400,20 L400,120 L0,120 Z"
                  fill="url(#chartGrad)"
                />
                <path
                  d="M0,100 Q40,80 80,85 T160,60 T240,50 T320,30 T400,20"
                  fill="none"
                  stroke="#6366f1"
                  strokeWidth="2"
                />
                <circle cx="320" cy="30" r="4" fill="#6366f1" />
                <circle cx="320" cy="30" r="8" fill="#6366f1" opacity="0.2" />
              </svg>
            </div>
            <div className="p-4 sm:p-5 rounded-xl bg-surface-light/60 border border-border/30">
              <p className="text-xs sm:text-sm font-medium text-foreground mb-4">Traffic Sources</p>
              <div className="space-y-3">
                {[
                  { label: "Direct", pct: 45, color: "#6366f1" },
                  { label: "Organic", pct: 30, color: "#22d3ee" },
                  { label: "Referral", pct: 15, color: "#a78bfa" },
                  { label: "Social", pct: 10, color: "#34d399" },
                ].map((item) => (
                  <div key={item.label}>
                    <div className="flex justify-between text-[10px] sm:text-xs text-muted mb-1">
                      <span>{item.label}</span>
                      <span>{item.pct}%</span>
                    </div>
                    <div className="h-1.5 rounded-full bg-background/60 overflow-hidden">
                      <div
                        className="h-full rounded-full transition-all"
                        style={{ width: `${item.pct}%`, backgroundColor: item.color }}
                      />
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        </div>
      </div>

      <div className="absolute -bottom-4 left-1/2 -translate-x-1/2 w-[90%] h-8 bg-primary/10 blur-xl rounded-full" />
    </motion.div>
  </div>
</section>

);
}
----
✨ app/components/Features.tsx
"use client";
import { motion } from "framer-motion";
import {
BarChart3,
Brain,
Shield,
Zap,
Globe,
Users,
Layers,
Clock,
} from "lucide-react";
const features = [
{
icon: Brain,
title: "AI-Powered Insights",
description:
"Our machine learning models analyze your data in real-time to surface actionable insights you might have missed.",
color: "from-violet-500 to-purple-600",
bgColor: "bg-violet-500/10",
borderColor: "border-violet-500/20",
},
{
icon: BarChart3,
title: "Advanced Analytics",
description:
"Deep-dive into every metric with customizable dashboards, funnel analysis, and cohort tracking built for scale.",
color: "from-blue-500 to-cyan-500",
bgColor: "bg-blue-500/10",
borderColor: "border-blue-500/20",
},
{
icon: Shield,
title: "Enterprise Security",
description:
"SOC 2 Type II certified with end-to-end encryption, SSO, and granular role-based access controls.",
color: "from-emerald-500 to-teal-500",
bgColor: "bg-emerald-500/10",
borderColor: "border-emerald-500/20",
},
{
icon: Zap,
title: "Real-time Sync",
description:
"Data updates in milliseconds. See changes as they happen with our blazing-fast real-time engine.",
color: "from-amber-500 to-orange-500",
bgColor: "bg-amber-500/10",
borderColor: "border-amber-500/20",
},
{
icon: Globe,
title: "Global CDN",
description:
"Deploy across 200+ edge locations worldwide. Your dashboards load instantly, everywhere.",
color: "from-rose-500 to-pink-500",
bgColor: "bg-rose-500/10",
borderColor: "border-rose-500/20",
},
{
icon: Users,
title: "Team Collaboration",
description:
"Comment on charts, share reports, and collaborate seamlessly with your entire organization.",
color: "from-indigo-500 to-blue-500",
bgColor: "bg-indigo-500/10",
borderColor: "border-indigo-500/20",
},
{
icon: Layers,
title: "200+ Integrations",
description:
"Connect with Slack, Salesforce, Stripe, Segment, and hundreds more with one-click integrations.",
color: "from-cyan-500 to-sky-500",
bgColor: "bg-cyan-500/10",
borderColor: "border-cyan-500/20",
},
{
icon: Clock,
title: "24/7 Support",
description:
"Our dedicated success team is available around the clock to help you get the most out of Nexus.",
color: "from-fuchsia-500 to-purple-500",
bgColor: "bg-fuchsia-500/10",
borderColor: "border-fuchsia-500/20",
},
];
const containerVariants = {
hidden: {},
visible: {
transition: {
staggerChildren: 0.08,
},
},
};
const itemVariants = {
hidden: { opacity: 0, y: 30 },
visible: {
opacity: 1,
y: 0,
transition: { duration: 0.5, ease: "easeOut" },
},
};
export default function Features() {
return (
<section id="features" className="relative py-24 sm:py-32">
<div className="absolute top-0 left-1/2 -translate-x-1/2 w-[800px] h-[400px] bg-primary/5 rounded-full blur-[120px] pointer-events-none" />
  <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true, margin: "-100px" }}
      transition={{ duration: 0.6 }}
      className="text-center mb-16 sm:mb-20"
    >
      <span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-primary bg-primary/10 rounded-full mb-4 border border-primary/20">
        Features
      </span>
      <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
        Build faster with{" "}
        <span className="text-gradient">intelligent tools</span>
      </h2>
      <p className="max-w-2xl mx-auto text-base sm:text-lg text-muted">
        Powerful tools designed for modern teams who demand precision,
        speed, and reliability.
      </p>
    </motion.div>

    <motion.div
      variants={containerVariants}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: "-50px" }}
      className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6"
    >
      {features.map((feature) => {
        const Icon = feature.icon;
        return (
          <motion.div
            key={feature.title}
            variants={itemVariants}
            className={`group relative p-5 sm:p-6 rounded-2xl bg-surface-light/40 border ${feature.borderColor} hover:border-border-light transition-all duration-300 hover:-translate-y-1 hover:shadow-xl`}
          >
            <div
              className={`w-10 h-10 sm:w-11 sm:h-11 rounded-xl ${feature.bgColor} flex items-center justify-center mb-4 group-hover:scale-110 transition-transform duration-300`}
            >
              <Icon className="w-5 h-5 sm:w-6 sm:h-6 text-foreground" />
            </div>

            <h3 className="text-base sm:text-lg font-semibold text-foreground mb-2">
              {feature.title}
            </h3>
            <p className="text-sm text-muted leading-relaxed">
              {feature.description}
            </p>

            <div
              className={`absolute inset-0 rounded-2xl bg-gradient-to-br ${feature.color} opacity-0 group-hover:opacity-[0.03] transition-opacity duration-300 pointer-events-none`}
            />
          </motion.div>
        );
      })}
    </motion.div>
  </div>
</section>

);
}
----
💳 app/components/Pricing.tsx
"use client";
import { motion } from "framer-motion";
import { Check, Sparkles } from "lucide-react";
const plans = [
{
name: "Starter",
description: "Perfect for individuals and small projects getting started.",
price: "$0",
period: "/month",
badge: null,
features: [
"Up to 3 team members",
"10,000 events/month",
"7-day data retention",
"Basic analytics dashboard",
"Email support",
"1 project",
"Community access",
],
cta: "Get Started Free",
ctaStyle: "outline",
popular: false,
},
{
name: "Pro",
description: "For growing teams that need advanced analytics and collaboration.",
price: "$49",
period: "/month",
badge: "Most Popular",
features: [
"Up to 20 team members",
"500,000 events/month",
"1-year data retention",
"Advanced analytics & AI insights",
"Priority email & chat support",
"Unlimited projects",
"Custom dashboards",
"API access",
"SSO authentication",
"Slack integration",
],
cta: "Start Pro Trial",
ctaStyle: "primary",
popular: true,
},
{
name: "Enterprise",
description: "Custom solutions for large organizations with advanced needs.",
price: "Custom",
period: "",
badge: null,
features: [
"Unlimited team members",
"Unlimited events",
"Unlimited data retention",
"Dedicated AI model training",
"24/7 phone & email support",
"Unlimited projects",
"Custom dashboards & reports",
"Full API & webhook access",
"Advanced SSO & SAML",
"Custom integrations",
"SLA guarantee",
"Dedicated success manager",
],
cta: "Contact Sales",
ctaStyle: "outline",
popular: false,
},
];
const containerVariants = {
hidden: {},
visible: {
transition: { staggerChildren: 0.12 },
},
};
const cardVariants = {
hidden: { opacity: 0, y: 40 },
visible: {
opacity: 1,
y: 0,
transition: { duration: 0.6, ease: "easeOut" },
},
};
export default function Pricing() {
return (
<section id="pricing" className="relative py-24 sm:py-32">
<div className="absolute inset-0 bg-gradient-to-b from-transparent via-primary/[0.02] to-transparent pointer-events-none" />
  <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true, margin: "-100px" }}
      transition={{ duration: 0.6 }}
      className="text-center mb-16 sm:mb-20"
    >
      <span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-secondary bg-secondary/10 rounded-full mb-4 border border-secondary/20">
        Pricing
      </span>
      <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
        Simple, transparent{" "}
        <span className="text-gradient">pricing</span>
      </h2>
      <p className="max-w-2xl mx-auto text-base sm:text-lg text-muted">
        Start free, scale as you grow. No hidden fees, no surprises.
      </p>
    </motion.div>

    <motion.div
      variants={containerVariants}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: "-50px" }}
      className="grid grid-cols-1 md:grid-cols-3 gap-6 lg:gap-8"
    >
      {plans.map((plan) => (
        <motion.div
          key={plan.name}
          variants={cardVariants}
          className={`relative flex flex-col rounded-2xl p-6 sm:p-8 transition-all duration-300 ${
            plan.popular
              ? "bg-surface-light border-2 border-primary/50 shadow-2xl shadow-primary/10 scale-[1.02] md:scale-105"
              : "bg-surface-light/40 border border-border hover:border-border-light"
          }`}
        >
          {plan.badge && (
            <div className="absolute -top-4 left-1/2 -translate-x-1/2">
              <div className="flex items-center gap-1.5 px-4 py-1.5 bg-gradient-to-r from-primary to-accent text-white text-xs font-semibold rounded-full shadow-lg shadow-primary/25">
                <Sparkles className="w-3 h-3" />
                {plan.badge}
              </div>
            </div>
          )}

          <div className="mb-6">
            <h3 className="text-lg font-semibold text-foreground mb-1">
              {plan.name}
            </h3>
            <p className="text-sm text-muted">{plan.description}</p>
          </div>

          <div className="mb-6">
            <span className="text-4xl sm:text-5xl font-bold text-foreground tracking-tight">
              {plan.price}
            </span>
            <span className="text-muted text-sm">{plan.period}</span>
          </div>

          <a
            href="#"
            className={`w-full py-3 px-4 rounded-xl text-sm font-semibold text-center transition-all mb-8 ${
              plan.popular
                ? "bg-primary hover:bg-primary-hover text-white shadow-lg shadow-primary/25 hover:shadow-xl hover:shadow-primary/30"
                : "bg-surface hover:bg-surface-hover text-foreground border border-border hover:border-border-light"
            }`}
          >
            {plan.cta}
          </a>

          <div className="flex-1">
            <p className="text-xs font-semibold text-muted uppercase tracking-wider mb-4">
              What's included
            </p>
            <ul className="space-y-3">
              {plan.features.map((feature) => (
                <li key={feature} className="flex items-start gap-3">
                  <div
                    className={`mt-0.5 w-4 h-4 rounded-full flex items-center justify-center flex-shrink-0 ${
                      plan.popular
                        ? "bg-primary/20 text-primary"
                        : "bg-surface-hover text-muted"
                    }`}
                  >
                    <Check className="w-2.5 h-2.5" />
                  </div>
                  <span className="text-sm text-muted">{feature}</span>
                </li>
              ))}
            </ul>
          </div>
        </motion.div>
      ))}
    </motion.div>
  </div>
</section>

);
}
----
💬 app/components/Testimonials.tsx
"use client";
import { motion } from "framer-motion";
import { Star, Quote } from "lucide-react";
const testimonials = [
{
name: "Sarah Chen",
role: "CTO at VercelFlow",
avatar: "SC",
content:
"Nexus transformed how we understand our users. The AI insights surfaced patterns we never knew existed. Our conversion rate jumped 34% in the first quarter.",
rating: 5,
},
{
name: "Marcus Johnson",
role: "Head of Product at StripeScale",
avatar: "MJ",
content:
"The real-time dashboards are incredibly fast. We went from waiting hours for reports to seeing data update instantly. It changed how our team makes decisions.",
rating: 5,
},
{
name: "Elena Rodriguez",
role: "VP Engineering at CloudNine",
avatar: "ER",
content:
"We evaluated 12 analytics platforms. Nexus was the only one that combined power with elegance. The team adopted it in days, not months.",
rating: 5,
},
{
name: "David Park",
role: "Founder at DataPulse",
avatar: "DP",
content:
"The API is beautifully designed. We integrated Nexus into our entire stack in under a week. Documentation is world-class and support is genuinely helpful.",
rating: 5,
},
{
name: "Aisha Patel",
role: "Director of Analytics at FinTrack",
avatar: "AP",
content:
"Enterprise security was non-negotiable for us. Nexus exceeded every requirement and the SSO setup was seamless. Our security team loves it.",
rating: 5,
},
{
name: "James Wilson",
role: "CEO at GrowthLab",
avatar: "JW",
content:
"We replaced three separate tools with Nexus. The ROI was immediate. Less context switching, cleaner data, and our team is actually excited to open the dashboard.",
rating: 5,
},
];
const containerVariants = {
hidden: {},
visible: {
transition: { staggerChildren: 0.1 },
},
};
const itemVariants = {
hidden: { opacity: 0, y: 30 },
visible: {
opacity: 1,
y: 0,
transition: { duration: 0.5, ease: "easeOut" },
},
};
export default function Testimonials() {
return (
<section id="testimonials" className="relative py-24 sm:py-32">
<div className="absolute inset-0 bg-gradient-to-b from-transparent via-accent/[0.02] to-transparent pointer-events-none" />
  <div className="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true, margin: "-100px" }}
      transition={{ duration: 0.6 }}
      className="text-center mb-16 sm:mb-20"
    >
      <span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-accent bg-accent/10 rounded-full mb-4 border border-accent/20">
        Testimonials
      </span>
      <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
        Loved by{" "}
        <span className="text-gradient">thousands</span> of teams
      </h2>
      <p className="max-w-2xl mx-auto text-base sm:text-lg text-muted">
        See what industry leaders say about their experience with Nexus.
      </p>
    </motion.div>

    <motion.div
      variants={containerVariants}
      initial="hidden"
      whileInView="visible"
      viewport={{ once: true, margin: "-50px" }}
      className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-6"
    >
      {testimonials.map((t, i) => (
        <motion.div
          key={t.name}
          variants={itemVariants}
          className={`group relative p-6 rounded-2xl bg-surface-light/40 border border-border hover:border-border-light transition-all duration-300 hover:-translate-y-1 ${
            i === 0 || i === 3 ? "lg:row-span-1" : ""
          }`}
        >
          <Quote className="w-8 h-8 text-primary/20 mb-4" />

          <div className="flex gap-1 mb-4">
            {Array.from({ length: t.rating }).map((_, j) => (
              <Star
                key={j}
                className="w-4 h-4 fill-warning text-warning"
              />
            ))}
          </div>

          <p className="text-sm sm:text-base text-foreground/90 leading-relaxed mb-6">
            &ldquo;{t.content}&rdquo;
          </p>

          <div className="flex items-center gap-3">
            <div className="w-10 h-10 rounded-full bg-gradient-to-br from-primary to-accent flex items-center justify-center text-white text-xs font-bold">
              {t.avatar}
            </div>
            <div>
              <p className="text-sm font-semibold text-foreground">
                {t.name}
              </p>
              <p className="text-xs text-muted">{t.role}</p>
            </div>
          </div>
        </motion.div>
      ))}
    </motion.div>
  </div>
</section>

);
}
----
❓ app/components/FAQ.tsx
"use client";
import { useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { ChevronDown } from "lucide-react";
const faqs = [
{
question: "How does the free trial work?",
answer:
"You get full access to all Pro features for 14 days, no credit card required. After the trial, you can choose to upgrade or continue with our free Starter plan. Your data stays intact either way.",
},
{
question: "Can I switch plans at any time?",
answer:
"Absolutely. You can upgrade, downgrade, or cancel your plan at any time from your billing dashboard. Prorated credits are applied automatically when you upgrade mid-cycle.",
},
{
question: "Is my data secure?",
answer:
"Security is our top priority. We are SOC 2 Type II certified, use AES-256 encryption at rest and TLS 1.3 in transit. Your data is never sold, shared, or used to train AI models without explicit consent.",
},
{
question: "Do you offer refunds?",
answer:
"Yes, we offer a 30-day money-back guarantee on all paid plans. If Nexus is not the right fit for your team, contact support within 30 days for a full refund, no questions asked.",
},
{
question: "What integrations are supported?",
answer:
"We support 200+ integrations including Slack, Salesforce, Stripe, Segment, HubSpot, Zendesk, GitHub, Jira, and more. We also offer a robust REST API and webhooks for custom integrations.",
},
{
question: "How does the AI insights feature work?",
answer:
"Our AI analyzes your data patterns to detect anomalies, predict trends, and surface actionable recommendations. All processing happens in real-time using models trained specifically for analytics workloads.",
},
{
question: "Do you offer onboarding support?",
answer:
"Every Pro and Enterprise plan includes onboarding support. Enterprise customers get a dedicated success manager who will help migrate your data, set up dashboards, and train your team.",
},
{
question: "What happens if I exceed my event limit?",
answer:
"We never drop your data. If you exceed your plan limit, we will notify you and give you a grace period to upgrade. Events are still collected and you can access them once you adjust your plan.",
},
];
export default function FAQ() {
const [openIndex, setOpenIndex] = useState<number | null>(0);
return (
<section id="faq" className="relative py-24 sm:py-32">
<div className="relative z-10 max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
<motion.div
initial={{ opacity: 0, y: 20 }}
whileInView={{ opacity: 1, y: 0 }}
viewport={{ once: true, margin: "-100px" }}
transition={{ duration: 0.6 }}
className="text-center mb-16 sm:mb-20"
>
<span className="inline-block px-3 py-1 text-xs font-semibold tracking-wide text-primary bg-primary/10 rounded-full mb-4 border border-primary/20">
FAQ
</span>
<h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
Frequently asked{" "}
<span className="text-gradient">questions</span>
</h2>
<p className="text-base sm:text-lg text-muted">
Everything you need to know about Nexus.
</p>
</motion.div>
    <motion.div
      initial={{ opacity: 0 }}
      whileInView={{ opacity: 1 }}
      viewport={{ once: true, margin: "-50px" }}
      transition={{ duration: 0.6 }}
      className="space-y-3"
    >
      {faqs.map((faq, index) => (
        <div
          key={index}
          className={`rounded-xl border transition-all duration-300 ${
            openIndex === index
              ? "bg-surface-light border-border-light"
              : "bg-surface-light/30 border-border hover:border-border-light"
          }`}
        >
          <button
            onClick={() =>
              setOpenIndex(openIndex === index ? null : index)
            }
            className="w-full flex items-center justify-between p-5 sm:p-6 text-left"
          >
            <span className="text-sm sm:text-base font-medium text-foreground pr-4">
              {faq.question}
            </span>
            <motion.div
              animate={{ rotate: openIndex === index ? 180 : 0 }}
              transition={{ duration: 0.2 }}
              className="flex-shrink-0"
            >
              <ChevronDown className="w-5 h-5 text-muted" />
            </motion.div>
          </button>

          <AnimatePresence initial={false}>
            {openIndex === index && (
              <motion.div
                initial={{ height: 0, opacity: 0 }}
                animate={{ height: "auto", opacity: 1 }}
                exit={{ height: 0, opacity: 0 }}
                transition={{ duration: 0.3, ease: "easeInOut" }}
                className="overflow-hidden"
              >
                <div className="px-5 sm:px-6 pb-5 sm:pb-6">
                  <p className="text-sm text-muted leading-relaxed">
                    {faq.answer}
                  </p>
                </div>
              </motion.div>
            )}
          </AnimatePresence>
        </div>
      ))}
    </motion.div>
  </div>
</section>

);
}
----
🎯 app/components/CTA.tsx
"use client";
import { motion } from "framer-motion";
import { ArrowRight, Sparkles } from "lucide-react";
export default function CTA() {
return (
<section className="relative py-24 sm:py-32">
<div className="absolute inset-0 overflow-hidden pointer-events-none">
<div className="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[600px] h-[400px] bg-primary/10 rounded-full blur-[120px]" />
<div className="absolute top-1/2 left-1/4 -translate-y-1/2 w-[300px] h-[300px] bg-accent/10 rounded-full blur-[100px]" />
<div className="absolute top-1/2 right-1/4 -translate-y-1/2 w-[300px] h-[300px] bg-secondary/10 rounded-full blur-[100px]" />
</div>
  <div className="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
    <motion.div
      initial={{ opacity: 0, y: 40 }}
      whileInView={{ opacity: 1, y: 0 }}
      viewport={{ once: true, margin: "-100px" }}
      transition={{ duration: 0.7 }}
      className="relative text-center p-8 sm:p-12 lg:p-16 rounded-3xl bg-surface-light/60 border border-border-light backdrop-blur-xl overflow-hidden"
    >
      <div className="absolute inset-0 bg-gradient-to-br from-primary/5 via-transparent to-accent/5 pointer-events-none" />

      <div className="relative z-10">
        <motion.div
          initial={{ scale: 0 }}
          whileInView={{ scale: 1 }}
          viewport={{ once: true }}
          transition={{ duration: 0.5, delay: 0.2 }}
          className="inline-flex items-center justify-center w-14 h-14 rounded-2xl bg-gradient-to-br from-primary to-accent mb-8 shadow-lg shadow-primary/25"
        >
          <Sparkles className="w-7 h-7 text-white" />
        </motion.div>

        <h2 className="text-3xl sm:text-4xl md:text-5xl font-bold tracking-tight mb-4">
          Ready to{" "}
          <span className="text-gradient">transform</span> your
          workflow?
        </h2>

        <p className="max-w-xl mx-auto text-base sm:text-lg text-muted mb-10">
          Join 10,000+ teams already using Nexus to ship faster and
          understand their users better. Start your free trial today.
        </p>

        <div className="flex flex-col sm:flex-row items-center justify-center gap-4">
          <a
            href="#pricing"
            className="group flex items-center gap-2 px-8 py-4 bg-primary hover:bg-primary-hover text-white font-semibold rounded-xl transition-all hover:shadow-xl hover:shadow-primary/25"
          >
            Start Free Trial
            <ArrowRight className="w-4 h-4 group-hover:translate-x-1 transition-transform" />
          </a>
          <a
            href="#"
            className="px-8 py-4 text-sm font-semibold text-foreground bg-surface hover:bg-surface-hover rounded-xl border border-border hover:border-border-light transition-all"
          >
            Talk to Sales
          </a>
        </div>

        <p className="mt-6 text-xs text-muted">
          No credit card required. 14-day free trial.
        </p>
      </div>
    </motion.div>
  </div>
</section>

);
}
----
🦶 app/components/Footer.tsx
"use client";
import { Zap, Github, Twitter, Linkedin, Youtube } from "lucide-react";
const footerLinks = {
Product: [
{ label: "Features", href: "#features" },
{ label: "Pricing", href: "#pricing" },
{ label: "Changelog", href: "#" },
{ label: "Roadmap", href: "#" },
{ label: "Integrations", href: "#" },
],
Company: [
{ label: "About", href: "#" },
{ label: "Blog", href: "#" },
{ label: "Careers", href: "#" },
{ label: "Press Kit", href: "#" },
{ label: "Contact", href: "#" },
],
Resources: [
{ label: "Documentation", href: "#" },
{ label: "API Reference", href: "#" },
{ label: "Guides", href: "#" },
{ label: "Community", href: "#" },
{ label: "Status", href: "#" },
],
Legal: [
{ label: "Privacy Policy", href: "#" },
{ label: "Terms of Service", href: "#" },
{ label: "Cookie Policy", href: "#" },
{ label: "Security", href: "#" },
{ label: "GDPR", href: "#" },
],
};
const socialLinks = [
{ icon: Twitter, href: "#", label: "Twitter" },
{ icon: Github, href: "#", label: "GitHub" },
{ icon: Linkedin, href: "#", label: "LinkedIn" },
{ icon: Youtube, href: "#", label: "YouTube" },
];
export default function Footer() {
return (
<footer className="relative border-t border-border/50">
<div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16 sm:py-20">
<div className="grid grid-cols-2 md:grid-cols-6 gap-8 lg:gap-12">
<div className="col-span-2">
<a href="#" className="flex items-center gap-2 mb-4">
<div className="w-8 h-8 rounded-lg bg-gradient-to-br from-primary to-accent flex items-center justify-center">
<Zap className="w-4 h-4 text-white" />
</div>
<span className="text-lg font-bold text-foreground">Nexus</span>
</a>
<p className="text-sm text-muted mb-6 max-w-xs">
The all-in-one analytics platform for modern teams. Ship faster,
analyze smarter, scale effortlessly.
</p>
<div className="flex gap-3">
{socialLinks.map((social) => {
const Icon = social.icon;
return (
<a
key={social.label}
href={social.href}
aria-label={social.label}
className="w-9 h-9 rounded-lg bg-surface-light border border-border flex items-center justify-center text-muted hover:text-foreground hover:border-border-light transition-all"
>
<Icon className="w-4 h-4" />
</a>
);
})}
</div>
</div>
      {Object.entries(footerLinks).map(([category, links]) => (
        <div key={category}>
          <h4 className="text-sm font-semibold text-foreground mb-4">
            {category}
          </h4>
          <ul className="space-y-2.5">
            {links.map((link) => (
              <li key={link.label}>
                <a
                  href={link.href}
                  className="text-sm text-muted hover:text-foreground transition-colors"
                >
                  {link.label}
                </a>
              </li>
            ))}
          </ul>
        </div>
      ))}
    </div>

    <div className="mt-16 pt-8 border-t border-border/50 flex flex-col sm:flex-row items-center justify-between gap-4">
      <p className="text-xs text-muted">
        &copy; {new Date().getFullYear()} Nexus, Inc. All rights reserved.
      </p>
      <div className="flex items-center gap-6">
        <a
          href="#"
          className="text-xs text-muted hover:text-foreground transition-colors"
        >
          Privacy
        </a>
        <a
          href="#"
          className="text-xs text-muted hover:text-foreground transition-colors"
        >
          Terms
        </a>
        <a
          href="#"
          className="text-xs text-muted hover:text-foreground transition-colors"
        >
          Cookies
        </a>
      </div>
    </div>
  </div>
</footer>

);
}
mkdir saas-landing && cd saas-landing
# Create all files above in their respective paths
npm install
npm run dev
Open http://localhost:3000
npm run build
npm i -g vercel
vercel --prod
