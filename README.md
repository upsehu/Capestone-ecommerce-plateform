# 🛒 Capstone E-Commerce System

![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen)
![Architecture](https://img.shields.io/badge/Architecture-Microservices-blue)
![Frontend](https://img.shields.io/badge/Frontend-React%20%7C%20TypeScript-61DAFB)
![Backend](https://img.shields.io/badge/Backend-FastAPI%20%7C%20Spring%20Boot%20%7C%20Node.js-orange)
![Cloud Native](https://img.shields.io/badge/Cloud--Native-Docker%20%7C%20Kubernetes-informational)
![License](https://img.shields.io/badge/License-MIT-green)

A **cloud-native, microservices-based e-commerce platform** designed to demonstrate modern software engineering concepts including **Object-Oriented Programming, REST APIs, distributed systems, containerization, caching, asynchronous processing, and Kubernetes-based deployment**.

The system separates major e-commerce functionalities into independently deployable services such as **User Management, Product Catalog, Shopping Cart, and Search**.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Project Objectives](#-project-objectives)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Microservices](#-microservices)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [How the System Works](#-how-the-system-works)
- [Prerequisites](#-prerequisites)
- [Local Installation](#-local-installation)
- [Running with Docker](#-running-with-docker)
- [API Documentation](#-api-documentation)
- [Engineering Highlights](#-engineering-highlights)
- [Testing](#-testing)
- [Deployment](#-deployment)
- [Future Enhancements](#-future-enhancements)
- [Learning Outcomes](#-learning-outcomes)
- [Author](#-author)

---

# 📖 Overview

Traditional e-commerce applications are often implemented as a single monolithic application where all business functionality is tightly coupled.

This project explores a **microservices architecture**, where individual business capabilities are separated into independent services.

### Core Services

```text
User Management
      │
      ├── User Profiles
      └── Account Management

Product Catalog
      │
      ├── Product Information
      └── Product Management

Shopping Cart
      │
      ├── Add / Remove Products
      └── Cart Management

Search Service
      │
      ├── Product Search
      └── Search Queries
