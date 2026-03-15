# Conceptual Overview

## Audience and Purpose

This conceptual overview is written for two primary audiences:

1. **Sports fans** who want to participate in online discussions about sports events
2. **Entry-level developers** who want to understand how the application is structured and how its parts work together

The purpose of this document is to introduce the Sport Comment Web Application, explain what it does and does not do, and provide the conceptual background readers need before using the task-based or reference documentation.

This document does not provide step-by-step instructions. Instead, it explains the key ideas, system components, and terminology that support later tasks.

## What the Sport Comment Web Application Is

The Sport Comment Web Application is a web-based platform that allows users to view and interact with comments related to sports events.

Each event, such as a game or match, includes discussion areas where users can share reactions, opinions, and conversations. The system focuses on sports discussion rather than long-form content creation such as articles or blogs.

On the user side, the application supports:

- User accounts and authentication
- Event-based and player-focused comment discussions
- Real-time or near-real-time comment updates
- A browser-based user interface
- Viewing commented games and players

Users cannot create entirely new event threads for games. Instead, they participate in discussion under the games, matches, or players already provided by the system.

## What the Application Can and Cannot Do

### What It Can Do

- Allow users to register and log in securely
- Allow users to create a username and avatar
- Display sports events with related discussion areas
- Let users post, read, and interact with comments
- Store user, event, player, and comment data in a database
- Provide a responsive interface accessible from modern browsers

### What It Cannot Do

- It does not stream live sports video or broadcasts
- It does not provide advanced analytics or sentiment analysis
- It does not support private messaging between users
- It does not automatically pull official scores from paid sports APIs beyond the system’s configured data sources
- It does not allow users to create their own completely independent event pages

Understanding these limitations helps both users and developers set realistic expectations for the system.

## Key Concepts and Terminology

Before using or developing the application, readers should understand the following concepts.

### User Authentication

Authentication is the process the system uses to verify a user’s identity. In this application, authentication ensures that registered users can post comments and interact with other content.

Users who are not logged in may be limited to viewing content only.

### Events

An **event** is a specific sports game or match. Events act as containers for related information, such as teams, scores, players, and comments.

### Player Discussions

The application also supports discussions connected to players within a game context. This helps users talk about individual player performance while keeping discussion tied to a specific event.

### Comment Threads

A **comment thread** is a collection of comments attached to a game or player context. Threads help keep conversations organized and easier to follow.

### Frontend and Backend

- The **frontend** is the part of the application users see and interact with in a web browser
- The **backend** handles authentication, data processing, storage, and communication between the frontend and the database

## Overview of the System Architecture

The Sport Comment Web Application uses a **client-server architecture**.

This means the system is divided into separate parts that handle different responsibilities.

### Frontend

The frontend is the browser-based interface built with modern web technologies such as React.

It is responsible for:

- Displaying sports events, player information, and comments
- Handling user input
- Sending requests to the backend
- Updating the interface when new data is returned

### Backend Server and APIs

The backend acts as the control center of the application.

It is responsible for:

- Processing requests from the frontend
- Enforcing authentication and authorization rules
- Retrieving sports data from external APIs
- Writing and reading data from the database
- Returning structured data to the frontend

APIs define how information moves between the frontend and backend in a secure and organized way.

### Database

The database stores persistent information, including:

- User accounts
- Usernames and avatars
- Games and leagues
- Players and player statistics
- Comments associated with games or players

The data model links comments to both users and events so that conversations remain traceable and consistent.

## Development Environment and Tools

Developers working on this project need a basic web development environment.

### Required Tools

- A code editor such as Visual Studio Code
- A modern web browser for testing
- A local development environment
- Project packages and dependencies
- A Google Cloud account for API-related configuration
- A Firebase account for authentication and data visualization

### Libraries and Frameworks

The application uses established web frameworks and libraries to support:

- User interface design
- API communication
- Authentication
- Data management
- Project organization

Developers do not need advanced experience, but they should understand basic frontend and backend concepts.

## How the Pieces Fit Together

When a user interacts with the application, the system works like this:

1. The frontend displays data retrieved from the backend
2. The user performs an action, such as submitting a comment
3. The frontend sends the request to the backend
4. The backend validates the request and stores or retrieves data from the database
5. The backend returns updated data
6. The frontend updates the page

This separation makes the application easier to maintain, test, and expand.

## Background Knowledge for New Users

Sports fans do not need technical knowledge beyond basic web browsing skills.

Users should understand:

- What a game page represents
- That comments are public and connected to user accounts
- That discussions are organized by game or player context
- That sports event data may update over time

Developers should understand:

- Client-server architecture
- REST-style APIs
- Basic frontend and backend workflows

## Where This Document Fits in the Doc Set

This conceptual overview appears at the beginning of the documentation set. It prepares readers for:

- The **User Guide**, which explains how to use the website
- The **Developer Guide**, which explains setup and maintenance
- The **Reference** section, which provides quick facts and technical details

By keeping concepts separate from instructions, this document helps readers build understanding before taking action.
