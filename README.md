**Performance Issue Analysis**

The UI lag on iOS was caused by improper state management and excessive widget rebuilding. Multiple nested widgets were being rebuilt whenever tasks were added or removed, even when only a small portion of the UI actually changed. This increased layout calculations, paint cycles, and frame workload, leading to sluggish animations and delayed UI updates — more noticeable on iOS due to tighter frame rendering constraints.

How Flutter & Dart Handle Smooth Performance

Flutter uses a reactive rendering model, where the UI updates only when state changes. When state is managed correctly (using scoped state, providers, or controllers), rebuilds are limited to affected widgets instead of the entire tree — reducing unnecessary work and improving frame stability.

Dart’s asynchronous model (async/await, Futures, Streams) ensures heavy operations like database writes or network sync run off the main UI thread. This prevents frame drops, keeps animations smooth, and helps maintain a consistent 60/120 FPS experience across both Android and iOS.

**Backend Challenge Analysis**

The app initially worked well offline but lacked real-time synchronization. Updates made by one user were stored locally and pushed with delays, causing inconsistent task data across devices. Additionally, handling image uploads and maintaining secure user sessions required backend infrastructure, which increased development complexity and maintenance overhead.

Firebase solved these challenges by providing a serverless backend with built-in services for authentication, real-time databases, and file storage — eliminating the need to manually manage servers, APIs, and security layers.

Firebase Integration in Flutter App

1️⃣ Firebase Authentication
Firebase Auth was integrated to handle secure user sign-in and session management. It supports email/password (and optional social logins), automatically manages tokens, and keeps users securely authenticated across app sessions.

2️⃣ Cloud Firestore (Real-Time Database)
Cloud Firestore was used to store tasks and collaboration data. Its real-time listeners instantly sync updates across devices whenever data changes. This ensures that when one user adds, edits, or deletes a task, all connected users see the update live without manual refresh.

3️⃣ Firebase Storage
Firebase Storage was integrated for handling image uploads (e.g., task attachments). It provides secure file upload/download, scalable storage, and access control via Firebase Auth — ensuring only authorized users can view or modify files.

Resulting User Experience Improvements

Real-time task updates across all devices

Secure authentication without custom backend

Reliable image upload & retrieval

Reduced sync delays and data conflicts

Scalable backend with minimal maintenance