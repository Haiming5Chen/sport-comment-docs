# Understand Comment Data Flow

## Audience

Entry-level developers who want to understand how comments move through the system.

## Purpose

Understanding the comment data flow helps developers debug issues, extend features, and maintain the application.

## Overview

When a user submits a comment, the system processes the request through multiple layers:

1. Frontend interface
2. Backend API
3. Database storage
4. Frontend update

This process ensures that comments are validated, stored correctly, and displayed to users.

## Comment Submission Flow

```text
Step 1: User submits a comment from the frontend interface.

Step 2: The frontend sends a request to the backend API.

Step 3: The backend verifies the user authentication status.

Step 4: If authentication is valid, the backend stores the comment in the database.
        The comment is linked to:
        - userId
        - eventId or playerId

Step 5: The backend returns the updated comment data to the frontend.

Step 6: The frontend updates the comment thread on the page.
```

## Developer Notes

- Frontend components should only handle user interface updates.
- Validation and authentication should be handled by the backend.
- Database writes should always occur through backend APIs to maintain security.

## Result

After the process completes:

- The new comment appears in the discussion thread
- Other users can see the comment
- Additional replies or interactions can occur
