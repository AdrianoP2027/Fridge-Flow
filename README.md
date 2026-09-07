# FridgeFlow

A web-based food waste reduction and meal-planning application developed using HTML, CSS, and JavaScript, with AI-assisted development and prompt engineering.

FridgeFlow allows users to enter the ingredients and quantities available in their fridge or pantry, configure the number of people and planning period, and generate a multi-day meal plan. The application uses an optimization engine to prioritize higher-perishability ingredients, calculate ingredient usage based on serving requirements, track remaining inventory, and identify missing ingredients needed to complete the generated meals.

The project was also developed as an experiment in AI-assisted software development, exploring how prompt engineering and AI tools can be used alongside programming to build, debug, and improve a functional software application.

## How It Works

The process is simple:

**Enter your inventory → Configure your plan → Generate an optimized meal plan → Track what remains**

The user provides their available ingredients, quantities, units, and perishability priorities. They can then specify how many people they are planning for and how many days the meal plan should cover.

FridgeFlow evaluates available ingredients against its recipe database, selects meals based on ingredient availability and perishability, sequentially deducts ingredients as meals are generated, and produces a multi-day meal plan.

The application also calculates remaining inventory and generates a shopping-gap list for ingredients that are required but unavailable.

## Features

* Custom ingredient input
* Ingredient quantity and unit tracking
* Quick-add ingredient presets
* Perishability and priority system
* Adjustable number of people
* Adjustable planning horizon
* Multi-day meal generation
* Breakfast, lunch, and dinner planning
* Recipe database with cooking instructions
* Perishability-based recipe selection
* Sequential inventory deduction
* Remaining inventory tracking
* Automatic shopping-gap generation
* Ingredient utilization efficiency score
* Dynamic fallback recipe generation
* Expandable recipe instructions
* Copyable shopping list
* Copyable remaining inventory summary
* Dark mode
* Responsive interface
* Toast notifications
* Reset functionality

## Technologies

**Languages**

* HTML
* CSS
* JavaScript

**Frameworks & Libraries**

* Tailwind CSS
* Font Awesome
* Google Fonts

**Programming Concepts**

* Arrays and Objects
* Functions
* DOM Manipulation
* Event-Driven Programming
* State Management
* Conditional Logic
* Iteration
* Data Filtering
* Data Transformation
* Algorithmic Problem Solving
* Sequential Simulation
* Dynamic UI Rendering

**Development Approach**

* AI-Assisted Development
* Prompt Engineering
* AI-Assisted Debugging
* Iterative Development

## Project Architecture

The application is organized into several major components responsible for managing inventory, meal generation, optimization, and the user interface.

### Pantry & Inventory System

Responsible for:

* Adding custom ingredients
* Adding preset ingredients
* Tracking quantities and units
* Managing perishability priorities
* Updating ingredient quantities
* Removing ingredients
* Sorting ingredients by perishability
* Maintaining the active pantry state

### Planning Configuration

Responsible for:

* Setting the number of people
* Setting the number of planning days
* Limiting configuration values to valid ranges
* Updating planning statistics

### Recipe Database

Contains predefined breakfast, lunch, and dinner recipes.

Each recipe contains:

* Recipe type
* Recipe name
* Preparation time
* Cooking time
* Base serving size
* Required ingredients
* Ingredient quantities
* Cooking instructions
* Recipe icon

### Optimization Engine

The optimization engine is the core of FridgeFlow.

It is responsible for:

* Evaluating available pantry ingredients
* Comparing recipes against current inventory
* Prioritizing high-perishability ingredients
* Scaling recipe requirements based on the number of people
* Sequentially consuming ingredients
* Tracking ingredient deductions
* Calculating missing ingredients
* Generating the final meal plan
* Calculating the efficiency score

### Recipe Selection Engine

The recipe selection system evaluates available recipes for each meal type.

Recipes receive higher scores when they contain ingredients that:

* Are currently available
* Have available quantities
* Have higher perishability priorities

The highest-scoring recipe is selected for each meal slot.

### Fallback Recipe Generator

When no predefined recipe has a meaningful match with the available inventory, FridgeFlow can dynamically generate a simple fallback meal using available pantry ingredients.

This allows the system to continue producing meal suggestions even when the user's inventory does not match the predefined recipe database.

### Remaining Inventory System

After the meal plan has been generated, FridgeFlow maintains a simulated copy of the pantry and deducts ingredients as they are used.

The system then displays:

* Initial quantities
* Remaining quantities
* Fully used ingredients
* Post-plan inventory

### Shopping Gap System

If a generated recipe requires more of an ingredient than the user currently has, the deficit is recorded.

The shopping-gap system aggregates these missing quantities and creates a list of additional ingredients needed to complete the planned meals.

## Development Highlights

### Perishability-Based Optimization

One of the main design goals of FridgeFlow is to prioritize ingredients that are more likely to go unused.

Each pantry ingredient receives a perishability priority:

* 🔴 High — Eat First
* 🟡 Medium — Medium Priority
* 🟢 Low — Shelf Stable

The recipe selection system uses these priorities when scoring potential meals, encouraging the system to use higher-priority ingredients first.

### Sequential Inventory Simulation

Rather than generating every meal independently, FridgeFlow creates a simulated copy of the user's pantry.

When a meal is selected, the required ingredients are deducted from this simulated inventory.

The next meal is then generated using the updated inventory.

This allows the system to account for the fact that an ingredient used in one meal is no longer available in the same quantity for later meals.

### Serving Scaling

Recipes are stored using base per-serving quantities.

When the user selects the number of people they are planning for, the application scales ingredient requirements accordingly.

For example, a recipe requiring 100 g of chicken per serving will require 400 g when generating a meal for four people.

### Shopping Gap Analysis

When the pantry does not contain enough of an ingredient to fully satisfy a recipe, FridgeFlow calculates the deficit.

These deficits are aggregated across the entire meal plan and displayed as a shopping-gap list.

This allows the application to distinguish between ingredients that are completely unavailable and ingredients where the user simply does not have enough.

### Dynamic Fallback Generation

FridgeFlow includes a fallback system for unusual pantry combinations.

If no predefined recipe has a meaningful ingredient match, the application can construct a simple meal using available ingredients rather than returning an empty result.

This makes the application more flexible when users enter ingredients that are not included in the main recipe database.

### Efficiency Score

After generating a meal plan, FridgeFlow compares the initial simulated inventory against the remaining inventory.

The difference is used to calculate an efficiency percentage representing how much of the available inventory was utilized by the generated plan.

## Problem Solving

One of the main challenges in FridgeFlow was turning a simple idea — "make meals from what I have" — into an actual planning system.

A basic recipe matcher could simply check whether an ingredient exists. However, this would not account for quantities, serving sizes, ingredient depletion, or perishability.

FridgeFlow instead treats the problem as a sequential planning process.

The system maintains a simulated pantry, generates a meal, deducts the ingredients used, and then uses the updated pantry when generating the next meal.

Another challenge was handling ingredients that do not perfectly match the recipe database. The fallback recipe generator was introduced so that the application could still produce a useful result for unfamiliar ingredient combinations.

Developing the application with AI also introduced a different type of problem solving. AI-generated code needed to be reviewed, tested, and modified when it did not behave as expected. This required understanding the underlying JavaScript logic rather than simply accepting generated code.

## AI-Assisted Development

FridgeFlow was developed as an experiment in **AI-assisted software development and prompt engineering**.

AI was used as a development partner to help:

* Brainstorm application features
* Explore implementation approaches
* Generate and refine code
* Debug JavaScript functionality
* Improve the user interface
* Refine application logic
* Suggest additional features
* Polish the overall design

The project was used to explore the strengths and limitations of AI during software development.

An important part of the process was evaluating AI-generated solutions, testing them within the application, identifying issues, and deciding which suggestions should actually be implemented.

## What I Learned

This project strengthened my understanding of JavaScript, web development, and algorithmic problem solving.

In particular, I developed a better understanding of:

* Managing application state
* Working with arrays and objects
* Manipulating the DOM dynamically
* Designing algorithms around real-world constraints
* Simulating changing inventory states
* Scaling data based on user requirements
* Building rule-based recommendation systems
* Handling missing and unexpected inputs
* Designing responsive user interfaces
* Debugging JavaScript
* Using AI effectively during software development
* Writing and refining prompts
* Evaluating AI-generated code
* Iterating on software with AI as a development partner

The project also demonstrated that effective AI-assisted development requires more than generating code. Understanding the problem, testing the output, identifying mistakes, and making informed decisions about the implementation remain important parts of the development process.

## Future Improvements

Potential future additions include:

* Ingredient expiration dates
* Automatic expiration-based prioritization
* More advanced meal-plan optimization
* Improved unit conversion
* Dietary and allergy preferences
* Ingredient substitution
* Larger recipe database
* Recipe API integration
* Grocery-list categorization
* Saved meal plans
* User accounts
* Food-waste analytics
* More sophisticated optimization algorithms
* Personalized meal recommendations

## Project Status

**Completed Prototype**

The core inventory system, planning configuration, recipe database, optimization engine, sequential inventory simulation, meal generation, shopping-gap analysis, remaining inventory tracking, efficiency scoring, and responsive user interface were implemented as part of the project.

FridgeFlow was also used as an experiment in AI-assisted software development and prompt engineering, exploring how AI can work alongside human decision-making throughout the software development process.

© 2026 Adriano P. | AI-Assisted Project

Developed with AI-assisted tools and third-party resources. Please do not copy, redistribute, or reuse the code without my permission.
