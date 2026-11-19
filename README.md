import {
  ArrowRight,
  Sparkles,
  Users,
  Settings,
  Award,
  Code2,
  MessageCircle,
  Headphones,
} from "lucide-react";
import { Link } from "react-router-dom";
import { useState, useEffect } from "react";

import companyLogo from "../assets/logo.png";
import { CONTACT_DETAILS } from "../data/contact";

import SectionHeading from "../components/SectionHeading";
import services from "../data/services";
import introImage from "../assets/services/it-solutions.jpg";
import careersImage from "../assets/services/recruitment.jpg";

/* WHY CHOOSE US - card data */
const whyChooseUs = [
  {
    icon: Users,
    tone: "peach",
    title: "Customer-Focused Approach",
    text: "We understand your requirements before recommending solutions.We understand your requirements before recommending solutions—ensuring every product aligns closely with your business goals, workflows, and long-term vision.",
  },
  {
    icon: Settings,
    tone: "blue",
    title: "Customized Solutions",
    text: "We develop solutions aligned with your business objectives.We develop solutions aligned with your business objectives—building scalable, flexible, and tailored digital applications designed to solve your specific operational challenges.",
  },
  {
    icon: Award,
    tone: "green",
    title: "Quality Commitment",
    text: "We emphasize functionality, usability, and reliability.We emphasize functionality, usability, and reliability—delivering secure, well-tested, and user-friendly software that performs seamlessly under real-world business demands.",
  },
  {
    icon: Code2,
    tone: "purple",
    title: "Technology Expertise",
    text: "We work with modern technologies and development practices.We work with modern technologies and development practices—leveraging proven frameworks, clean architecture, and continuous innovation to build future-ready platforms..",
  },
  {
    icon: MessageCircle,
    tone: "yellow",
    title: "Transparent Communication",
    text: "We maintain clear communication throughout the project.We maintain clear communication throughout the project—keeping you informed at every milestone with regular progress updates, honest timelines, and collaborative feedback.",
  },
  {
    icon: Headphones,
    tone: "pink",
    title: "Continuous Support",
    text: "We aim to build long-term relationships through ongoing technical support.We aim to build long-term relationships through ongoing technical support—providing proactive maintenance, timely upgrades, and dedicated post-launch assistance whenever you need it.",
  },
];

function Home() {
  const [reviews, setReviews] = useState(() => {
    if (typeof window !== "undefined") {
      const savedReviews = localStorage.getItem("saitejaProductionReviews");
      return savedReviews ? JSON.parse(savedReviews) : [];
    }
    return [];
  });

  const [clientName, setClientName] = useState("");
  const [clientDesignation, setClientDesignation] = useState("");
  const [clientReview, setClientReview] = useState("");

  useEffect(() => {
    localStorage.setItem("saitejaProductionReviews", JSON.stringify(reviews));
  }, [reviews]);

  const handleSubmitReview = (e) => {
    e.preventDefault();

    if (!clientName || !clientReview) {
      alert("Please enter both Name and Review!");
      return;
    }

    const newReview = {
      name: clientName,
      designation: clientDesignation || "Client Partner",
      review: clientReview,
    };

    setReviews([newReview, ...reviews]);
    setClientName("");
    setClientDesignation("");
    setClientReview("");
  };

  const handleClearAllReviews = () => {
    if (
      window.confirm(
        "Are you sure you want to clear all reviews and start fresh?"
      )
    ) {
      setReviews([]);
    }
  };

  return (
    <main>
      {/* HERO */}
      <section className="hero-section" id="home">
        <div className="hero-content">
          <div className="eyebrow">
            <Sparkles size={15} />
            Technology • Talent • Transformation
          </div>

          <h1>
            Building what's next
            <span> for ambitious businesses.</span>
          </h1>

          <p>
            SAITEJA INFOTECH PRIVATE LIMITED is a top-tier{" "}
            <strong>Software Development Company in Tirupati</strong>,
            delivering premium <strong>IT Services Tirupati</strong> wide.
            As a leading <strong>Web Development Company Andhra Pradesh</strong>,
            we provide custom business software, staffing, and premium
            <strong> DevOps Consulting India</strong> solutions to help
            organizations move forward with confidence.
          </p>

          <div className="hero-actions">
            <a className="primary-button" href="#services">
              Explore Services <ArrowRight size={18} />
            </a>

            <Link className="secondary-button" to="/contact">
              Start a Conversation
            </Link>
          </div>
        </div>

        <div className="hero-visual" aria-hidden="true">
          <div className="hero-logo-container">
            <img
              src={companyLogo}
              alt=""
              className="hero-company-logo"
            />
          </div>
        </div>
      </section>

      {/* TOP 3 FEATURED SERVICES */}
      <section className="services-section" id="featured-services">
        <SectionHeading
          label="OUR KEY SERVICES"
          title="Explore our"
          highlight=" core services."
          description="Discover our key technology capabilities."
        />

        <div className="services-grid">
          {services.slice(0, 3).map(
            ({ image, number, title, description }) => (
              <article
                className="service-card"
                key={`featured-${title}`}
              >
                <div className="service-image">
                  <img src={image} alt={title} />
                  <span className="service-image-number">
                    {number}
                  </span>
                </div>

                <div className="service-card-content">
                  <h3>{title}</h3>
                  <p>{description}</p>

                  <a href="#services">
                    Explore all services <ArrowRight size={16} />
                  </a>
                </div>
              </article>
            )
          )}
        </div>
      </section>

      {/* STATS STRIP */}
      <section className="stats-strip">
        <div className="stats-strip-inner">
          <div className="stat-item">
            <strong>2+</strong>
            <span>Years of Experience</span>
          </div>

          <div className="stat-item">
            <strong>20+</strong>
            <span>Projects Delivered</span>
          </div>

          <div className="stat-item">
            <strong>10+</strong>
            <span>Happy Clients</span>
          </div>
        </div>
      </section>

      {/* ABOUT PREVIEW */}
      <section className="intro-section" id="about">
        <div className="section-label">WHO WE ARE</div>

        <div className="intro-grid">
          <h2>
            One partner.
            <br />
            <span>Multiple possibilities.</span>
          </h2>

          <div>
            <p>
              We combine technology, talent and business understanding.
            </p>

            <Link className="text-link" to="/about">
              Discover SAITEJA INFOTECH <ArrowRight size={17} />
            </Link>
          </div>
        </div>

        <figure className="section-photo">
          <img src={introImage} alt="" loading="lazy" />
        </figure>
      </section>

      {/* EXISTING MIDDLE SECTION - ALL 8 SERVICES */}
      <section className="services-section" id="services">
        <SectionHeading
          label="WHAT WE DO"
          title="Solutions built around"
          highlight=" your goals."
          description="Capabilities designed to work together."
        />

        <div className="services-grid">
          {services.map(({ image, number, title, description }) => (
            <article className="service-card" key={title}>
              <div className="service-image">
                <img src={image} alt={title} />
                <span className="service-image-number">
                  {number}
                </span>
              </div>

              <div className="service-card-content">
                <h3>{title}</h3>
                <p>{description}</p>

                <Link to="/services">
                  Learn more <ArrowRight size={16} />
                </Link>
              </div>
            </article>
          ))}
        </div>
      </section>

      {/* VISION */}
      <section className="vision-section">
        <div className="vision-box">
          <h2>
            Technology should
            <span> create momentum.</span>
          </h2>

          <p>
            We believe the best solutions solve problems.
          </p>
        </div>
      </section>

      {/* WHY CHOOSE US SECTION (UPDATED - light colored cards) */}
      <section className="why-choose-us-section">
        <div className="why-choose-us-container">
          <div className="why-choose-us-heading">
            <div className="section-label">WHY CHOOSE US</div>

            <h2>Why Choose Saiteja Infotech?</h2>

            <p>
              We deliver reliable technology solutions through innovation,
              quality, and customer-focused services.
            </p>
          </div>

          <div className="why-choose-us-grid">
            {whyChooseUs.map(({ icon: Icon, tone, title, text }) => (
              <div className={`why-card why-${tone}`} key={title}>
                <span className="why-icon">
                  <Icon size={24} />
                </span>

                <h3>{title}</h3>
                <p>{text}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* TESTIMONIALS SECTION */}
      <section
        style={{
          display: "flex",
          justifyContent: "space-between",
          alignItems: "flex-start",
          padding: "80px max(40px, 8%)",
          fontFamily: "sans-serif",
          backgroundColor: "#f2eedd",
          gap: "50px",
          flexWrap: "wrap",
          maxWidth: "1300px",
          margin: "0 auto",
        }}
      >
        {/* Left Side */}
        <div style={{ flex: "1", minWidth: "300px", textAlign: "left" }}>
          <span
            style={{
              color: "#b75f0d",
              fontSize: "0.8rem",
              fontWeight: "bold",
              letterSpacing: "1px",
              display: "block",
              marginBottom: "15px",
            }}
          >
            WHAT OUR CLIENTS SAY
          </span>

          <h2
            style={{
              fontSize: "2.5rem",
              fontWeight: "bold",
              color: "#0f172a",
              lineHeight: "1.2",
              margin: "0 0 20px 0",
            }}
          >
            Trusted by
            <br />
            innovative
            <br />
            companies
            <br />
            worldwide.
          </h2>

          <p
            style={{
              color: "#293546",
              fontSize: "0.95rem",
              lineHeight: "1.6",
              marginBottom: "35px",
              maxWidth: "340px",
            }}
          >
            Your Experience inspires us to deliver better technology
            solutions and create lasting partnerships.
          </p>

          <Link
            to="/contact"
            style={{
              backgroundColor: "#d9d0c2",
              color: "#090603",
              textDecoration: "none",
              padding: "14px 28px",
              fontSize: "0.95rem",
              fontWeight: "bold",
              borderRadius: "8px",
              display: "inline-flex",
              alignItems: "center",
              gap: "8px",
              boxShadow: "0 4px 14px rgba(255, 122, 0, 0.35)",
            }}
          >
            Share Your Experience <ArrowRight size={16} />
          </Link>
        </div>

        {/* Right Side: Static Reviews */}
        <div
          style={{
            flex: "2",
            display: "grid",
            gridTemplateColumns: "repeat(auto-fit, minmax(290px, 1fr))",
            gap: "24px",
            minWidth: "320px",
            width: "100%",
            alignItems: "stretch",
          }}
        >
          {/* Card 1 */}
          <div
            style={{
              backgroundColor: "#cee5ea",
              borderRadius: "16px",
              padding: "32px",
              boxShadow: "0 10px 30px rgba(0,0,0,0.04)",
              border: "1px solid #f1f5f9",
              borderBottom: "4px solid #8fe0e9",
              display: "flex",
              flexDirection: "column",
              justifyContent: "space-between",
              textAlign: "left",
            }}
          >
            <p
              style={{
                color: "#0e1414",
                fontSize: "0.95rem",
                lineHeight: "1.6",
                margin: "0 0 24px 0",
              }}
            >
              "Saiteja Infotech provides excellent IT services with a
              professional and supportive team. Their solutions are reliable,
              innovative, and delivered with great attention to quality. I
              truly appreciate their commitment and customer service. Highly
              recommended!"
            </p>

            <div>
              <div
                style={{
                  height: "1px",
                  backgroundColor: "#121517",
                  width: "100%",
                  marginBottom: "16px",
                }}
              ></div>

              <h4
                style={{
                  fontSize: "1rem",
                  fontWeight: "bold",
                  color: "#080c13",
                  margin: "0 0 4px 0",
                }}
              >
                Mohan Kumar
              </h4>

              <span
                style={{
                  color: "#15110d",
                  fontSize: "0.8rem",
                  fontWeight: "600",
                }}
              >
                Manager
              </span>
            </div>
          </div>

          {/* Card 2 */}
          <div
            style={{
              backgroundColor: "#f4cafa",
              borderRadius: "16px",
              padding: "32px",
              boxShadow: "0 10px 30px rgba(0,0,0,0.04)",
              border: "1px solid #f1f5f9",
              borderBottom: "4px solid #eca2e3",
              display: "flex",
              flexDirection: "column",
              justifyContent: "space-between",
              textAlign: "left",
            }}
          >
            <p
              style={{
                color: "#0a0c0f",
                fontSize: "0.95rem",
                lineHeight: "1.6",
                margin: "0 0 24px 0",
              }}
            >
              "We had a great experience working with Saiteja Infotech. Their
              team understood our business requirements and delivered a
              reliable software solution. Their technical support and
              dedication were impressive."
            </p>

            <div>
              <div
                style={{
                  height: "1px",
                  backgroundColor: "#030404",
                  width: "100%",
                  marginBottom: "16px",
                }}
              ></div>

              <h4
                style={{
                  fontSize: "1rem",
                  fontWeight: "bold",
                  color: "#0c0d0d",
                  margin: "0 0 4px 0",
                }}
              >
                Preethi Reddy
              </h4>

              <span
                style={{
                  color: "#18140f",
                  fontSize: "0.8rem",
                  fontWeight: "600",
                }}
              >
                Managing Director
              </span>
            </div>
          </div>

          {/* Card 3 */}
          <div
            style={{
              backgroundColor: "#f1c3c3",
              borderRadius: "16px",
              padding: "32px",
              boxShadow: "0 10px 30px rgba(0,0,0,0.04)",
              border: "1px solid #f1f5f9",
              borderBottom: "4px solid #e69999",
              display: "flex",
              flexDirection: "column",
              justifyContent: "space-between",
              textAlign: "left",
            }}
          >
            <p
              style={{
                color: "#0d0d0e",
                fontSize: "0.95rem",
                lineHeight: "1.6",
                margin: "0 0 24px 0",
              }}
            >
              "Saiteja Infotech helped us improve our business operations
              through their technology solutions. Their support and innovative
              approach made our work easier and more efficient. We appreciate
              their commitment and professionalism."
            </p>

            <div>
              <div
                style={{
                  height: "1px",
                  backgroundColor: "#090a0b",
                  width: "100%",
                  marginBottom: "16px",
                }}
              ></div>

              <h4
                style={{
                  fontSize: "1rem",
                  fontWeight: "bold",
                  color: "#0f172a",
                  margin: "0 0 4px 0",
                }}
              >
                Manoj Kumar
              </h4>

              <span
                style={{
                  color: "#0c0c0c",
                  fontSize: "0.8rem",
                  fontWeight: "600",
                }}
              >
                Business Owner
              </span>
            </div>
          </div>

          {/* Card 4 */}
          <div
            style={{
              backgroundColor: "#e0e0fa",
              borderRadius: "16px",
              padding: "32px",
              boxShadow: "0 10px 30px rgba(127, 125, 160, 0.04)",
              border: "1px solid #f1f5f9",
              borderBottom: "4px solid #beb3f6",
              display: "flex",
              flexDirection: "column",
              justifyContent: "space-between",
              textAlign: "left",
            }}
          >
            <p
              style={{
                color: "#050606",
                fontSize: "0.95rem",
                lineHeight: "1.6",
                margin: "0 0 24px 0",
              }}
            >
              "Their web development support was exceptional. The custom
              workflow applications built by their developers significantly
              optimized our digital infrastructure and saved us countess
              operation hours."
            </p>

            <div>
              <div
                style={{
                  height: "1px",
                  backgroundColor: "#0a0b0b",
                  width: "100%",
                  marginBottom: "16px",
                }}
              ></div>

              <h4
                style={{
                  fontSize: "1rem",
                  fontWeight: "bold",
                  color: "#111112",
                  margin: "0 0 4px 0",
                }}
              >
                Rajesh Sharma
              </h4>

              <span
                style={{
                  color: "#0d0d0c",
                  fontSize: "0.8rem",
                  fontWeight: "600",
                }}
              >
                Operations Manager
              </span>
            </div>
          </div>
        </div>
      </section>

      {/* CAREERS */}
      <section className="careers-section" id="careers">
        <div className="careers-grid">
          <figure className="section-photo">
            <img src={careersImage} alt="" loading="lazy" />
          </figure>

          <div className="careers-content">
            <div className="section-label">CAREERS</div>

            <h2>
              Grow your career
              <br />
              <span>with us.</span>
            </h2>

            <p>
              We are always looking for passionate people to join our
              expanding team.
            </p>

            <Link className="primary-button" to="/careers">
              View Openings <ArrowRight size={18} />
            </Link>
          </div>
        </div>
      </section>
    </main>
  );
}

export default Home;
