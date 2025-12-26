# ChatHub - Real-time Chat Application

A full-featured chat application built with React, TypeScript, Tailwind CSS, and Supabase. Features real-time messaging, friend management, group chats, file sharing, and more.

## Features

- **Authentication**: Secure login and signup with email/password
- **Real-time Messaging**: Instant message delivery using Supabase Realtime
- **Direct Chats**: One-on-one conversations with friends
- **Group Chats**: Create and manage group conversations
- **Friend Management**: Add friends, accept/decline requests, block users
- **User Profiles**: Customizable profiles with bio and avatar
- **Message Features**:
  - Edit messages
  - Delete messages
  - Emoji support
  - File and image sharing
- **User Status**: Online/offline status tracking
- **Typing Indicators**: See when someone is typing
- **Search**: Search for users and messages
- **Dark Mode**: Toggle between light and dark themes
- **Responsive Design**: Works seamlessly on desktop and mobile

## Tech Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS
- **Backend**: Supabase (PostgreSQL, Realtime, Auth, Storage)
- **Real-time**: Supabase Realtime Subscriptions
- **UI Components**: Lucide React Icons, Emoji Picker
- **Routing**: React Router DOM

## Getting Started

### Prerequisites

- Node.js 16+ and npm
- Supabase account and project

### Installation

1. Install dependencies:
```bash
npm install
```

2. Environment variables are already configured in `.env` with your Supabase credentials

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to the displayed URL (usually `http://localhost:5173`)

## Project Structure

```
src/
├── components/          # React components
│   ├── ChatWindow.tsx   # Main chat interface
│   ├── Sidebar.tsx      # Chat list and navigation
│   ├── UserProfile.tsx  # User profile modal
│   ├── AddFriendModal.tsx
│   ├── CreateGroupModal.tsx
│   ├── SearchModal.tsx
│   ├── FileUpload.tsx
│   └── TypingIndicator.tsx
├── contexts/           # React context providers
│   └── AuthContext.tsx # Authentication state
├── hooks/             # Custom React hooks
│   └── useUserStatus.ts # User status management
├── pages/            # Page components
│   ├── Login.tsx
│   ├── Signup.tsx
│   └── Chat.tsx
├── lib/             # Utilities and helpers
│   └── supabase.ts  # Supabase client
└── App.tsx         # Main app component

```

## Key Features Explained

### Real-time Messaging
Messages are synchronized across all connected clients using Supabase Realtime subscriptions. Changes (new messages, edits, deletes) appear instantly.

### Friend System
- Send friend requests to other users
- Accept/decline incoming requests
- Block users to prevent communication
- View friend list in the sidebar

### Group Chats
- Create new groups with selected friends
- Add multiple members
- View member list
- Full chat history

### File Sharing
- Upload images and files
- Image preview in messages
- File download support
- Maximum file size depends on Supabase configuration

### User Status
- Automatic online/offline status tracking
- Last seen timestamp
- Status persists across sessions

## Database Schema

The application uses Supabase with the following main tables:
- `users` - User profiles and preferences
- `messages` - All messages (direct and group)
- `friendships` - Friend relationships and requests
- `group_chats` - Group chat metadata
- `group_members` - Group membership
- `user_status` - Online status tracking
- `notifications` - User notifications
- `blocked_users` - Blocked user relationships

All tables have Row Level Security (RLS) policies enabled for data privacy.

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint
- `npm run typecheck` - Run TypeScript type checking

## Authentication

The app uses Supabase Email/Password authentication:
- Users register with email and password
- Sessions are managed securely
- Protected routes require authentication
- Automatic redirects for unauthenticated users

## Real-time Subscriptions

The app subscribes to:
- Message changes (new, update, delete)
- User status updates
- Friend request notifications

Subscriptions are automatically cleaned up when components unmount.

## Dark Mode

Toggle dark mode in the user profile. Theme preference is stored in the database.

## Security

- Row Level Security (RLS) enabled on all tables
- Users can only access their own data
- Friend relationships required for direct messaging
- Group members can only see group messages
- File uploads are validated and stored securely

## Limitations & Future Improvements

- File upload size limits (configured in Supabase)
- No message encryption (uses HTTPS)
- Notifications shown only for online users
- Group invitations not yet implemented
- Voice/video calling not included

## Troubleshooting

**Messages not appearing?**
- Ensure RLS policies are correctly applied
- Check Supabase real-time is enabled in project settings
- Verify user is authenticated

**File uploads failing?**
- Check storage bucket exists and is public
- Verify file size is within limits
- Check browser console for specific errors

**Authentication issues?**
- Clear browser cache
- Check Supabase API keys in `.env`
- Verify email isn't already registered

## Support

For issues or questions:
1. Check the Supabase documentation
2. Review browser console for error messages
3. Verify all environment variables are set correctly

## License

This project is open source and available under the MIT License.
