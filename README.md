# Rowl: A Decentralized Social Networking Platform on the Sui Blockchain

![Rowl Logo](https://img.shields.io/badge/Rowl-Decentralized%20Social%20Network-blue?style=for-the-badge&logo=sui&logoColor=white)
![Sui Blockchain](https://img.shields.io/badge/Powered%20by-Sui%20Blockchain-blue?style=flat-square)
![Hackathon Project](https://img.shields.io/badge/Sui%20Move-Hackathon%20Project-orange?style=flat-square)

A censorship-resistant, user-owned social networking platform built on the Sui blockchain. Rowl empowers users with full ownership of their content, data, and social connections.

## Live Demo

**Deployment URL:** [https://suiitter.vercel.app](https://suitter.vercel.app)

**Status:** ✅ Production Ready (Deployed on Sui Testnet)

**Smart Contract Package ID:** `0x85adced0fe590c6d94a07ba8d8034868227d3de4e7d540c1cded78fd6cb38183`

**Network:** Sui Testnet

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Technical Stack](#technical-stack)
- [Smart Contracts](#smart-contracts)
- [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Known Improvements](#known-improvements)
- [Contributing](#contributing)
- [License](#license)

## Overview

Rowl is a decentralized social networking platform built on the Sui blockchain that provides users with ownership of their data and content. Unlike traditional social platforms, Rowl offers censorship resistance, user sovereignty, and monetization opportunities through on-chain interactions.

Users can create posts (Suits), interact with content through likes and comments, discover and connect with other users, and start direct conversations - all while maintaining full ownership of their data and content.


## Features

### Core Features

- **Decentralized Posting:** Create and own your posts as Sui objects (Suits)
- **Content Types:** Support for text, image, and video posts (280 char limit for text)
- **Real-time Feed:** Dynamic feed with automatic refresh every 5 seconds
- **Video Autoplay:** TikTok-style video autoplay when scrolled into view
- **User Profiles:** Custom usernames, bios, and profile pictures
- **Profile Discovery:** View and explore other users' profiles
- **Direct Messaging:** Encrypted messaging with on-chain chat objects
- **Interactions:** Like, comment, and repost functionality with on-chain tracking
- **Tipping System:** Send tips to content creators with on-chain balance tracking
- **Advanced Search:** Search users, posts, and content with filters
- **Wallet Integration:** Seamless Sui wallet connection via @mysten/dapp-kit
- **File Upload:** Multiple Walrus publisher endpoints with automatic fallback (3MB videos, 5MB images)

### User Experience

- **Responsive Design:** Optimized for desktop and mobile devices
- **Dark/Light Mode:** Theme switching with system preference detection
- **Skeleton Loaders:** Professional loading states with animated skeletons
- **Empty States:** Friendly messages when no content is available
- **Fast Performance:** Optimized with React 18 and Vite for fast builds
- **Intuitive UI:** Twitter-like interface with modern design and smooth animations
- **Real-time Updates:** Live feed updates and optimistic UI updates
- **Enhanced Compose:** Clickable compose section with profile avatar and emoji picker
- **File Validation:** Pre-upload file size and type validation with helpful error messages

### Advanced Features

- **Balance Management:** Real SUI balance display with hide/show toggle
- **Tip Balances:** Track received tips and withdraw funds on-chain
- **NFT Assets:** View and manage your Suit NFTs and other Sui assets
- **Smart Search:** Multi-type search (users, posts, content) with filters
- **Engagement Metrics:** Like counts, comment counts, repost counts, and tip totals
- **Media Support:** Images (JPEG, PNG, GIF, WebP) and videos (MP4, WebM, MOV)
- **Multiple Publishers:** 4 Walrus publisher endpoints with automatic fallback for reliability

## Architecture

### System Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Smart         │    │   Sui           │
│   (React/TS)    │◄──►│   Contracts     │◄──►│   Blockchain    │
│                 │    │   (Move)        │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   User          │    │   Sui Objects   │    │   Walrus        │
│   Interface     │    │   (Suits,       │    │   Storage       │
│                 │    │    Profiles)    │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Smart Contract Architecture

**Package ID:** `0x85adced0fe590c6d94a07ba8d8034868227d3de4e7d540c1cded78fd6cb38183`

```
SuitRegistry
├── Suit Objects
│   ├── Content (text, max 280 chars)
│   ├── Content Type (text/image/video)
│   ├── Creator (address)
│   ├── Timestamp (created_at)
│   ├── Engagement (like_count, comment_count, retweet_count)
│   ├── Tip Total (accumulated tips in MIST)
│   └── Media URLs (vector<String>)
│
├── InteractionRegistry
│   ├── Like Objects (suit_id, liker)
│   ├── Comment Objects (suit_id, commenter, content)
│   └── Repost Objects (suit_id, reposter)
│
├── UsernameRegistry
│   └── Profile Objects
│       ├── Owner (address)
│       ├── Username (unique)
│       ├── Bio
│       └── Profile Picture URL
│
├── TipBalanceRegistry
│   └── TipBalance Objects
│       ├── Owner (address)
│       ├── Balance (total received tips)
│       └── Total Received (lifetime tips)
│
└── ChatRegistry
    └── Chat Objects
        ├── Participants (user1, user2)
        ├── Messages (encrypted content)
        └── Read Status (unread counts)
```

**Modules:** 
- `suits.move` - Post creation and management
- `interactions.move` - Likes, comments, reposts
- `profile.move` - User profiles and usernames
- `tipping.move` - Tip system and balance management
- `messaging.move` - Direct messaging and chat

## Technical Stack

### Frontend
- Framework: React 18 with TypeScript
- Build Tool: Vite
- Styling: Tailwind CSS + Radix UI
- State Management: React Hooks + Context
- Blockchain: @mysten/dapp-kit, @mysten/sui.js
- Storage: Walrus (decentralized storage)

### Backend (Smart Contracts)
- **Language:** Move (Sui)
- **Runtime:** Sui Testnet
- **Package ID:** `0x85adced0fe590c6d94a07ba8d8034868227d3de4e7d540c1cded78fd6cb38183`
- **Edition:** 2024.beta
- **Test Coverage:** 15/15 tests passing ✅
- **Modules:** 5 (suits, interactions, profile, tipping, messaging)

### Development Tools
- Package Manager: pnpm
- Linting: ESLint
- Type Checking: TypeScript
- Deployment: Vercel
- Version Control: Git

## Smart Contracts

### Package Information
- **Package ID:** `0x85adced0fe590c6d94a07ba8d8034868227d3de4e7d540c1cded78fd6cb38183`
- **Network:** Sui Testnet
- **Modules:** suits, interactions, profile, tipping, messaging
- **Dependencies:** Sui Framework
- **Test Status:** ✅ 15/15 tests passing

### Key Objects

#### 1. Suit (Post Object)
```move
struct Suit has key, store {
    id: UID,
    creator: address,
    content: String,              // Max 280 characters
    content_type: String,         // "text", "image", or "video"
    media_urls: vector<String>,   // Walrus URLs
    created_at: u64,
    like_count: u64,
    comment_count: u64,
    retweet_count: u64,
    tip_total: u64,              // Total tips received (in MIST)
}
```

#### 2. Profile
```move
struct Profile has key, store {
    id: UID,
    owner: address,
    username: String,             // Unique, min 3 chars
    bio: String,
    pfp_url: String,              // Profile picture URL
}
```

#### 3. Like
```move
struct Like has key, store {
    id: UID,
    suit_id: ID,
    liker: address,
}
```

#### 4. TipBalance
```move
struct TipBalance has key, store {
    id: UID,
    owner: address,
    balance: u64,                 // Withdrawable balance
    total_received: u64,          // Lifetime total
}
```

#### 5. Chat
```move
struct Chat has key, store {
    id: UID,
    user1: address,
    user2: address,
    messages: vector<Message>,
    // ... read status tracking
}
```

## Installation & Setup

### Prerequisites

- Node.js: v18 or higher
- pnpm: v8 or higher
- Sui Wallet: Browser extension or mobile wallet
- Git: Version control system

### Local Development Setup

1. Clone the repository
   ```bash
   git clone https://github.com/RicheySon/Suitter.git
   cd Suitter
   # Note: Repository may be renamed to match the new project name
   ```

2. Install dependencies
   ```bash
   cd next-frontend
   pnpm install
   ```

3. Environment Configuration
   ```bash
   # Create .env.local file in next-frontend directory
   # Add your configuration (required variables)
   
   # Smart Contract Package ID (Required)
   VITE_PACKAGE_ID=0x85adced0fe590c6d94a07ba8d8034868227d3de4e7d540c1cded78fd6cb38183
   
   # Registry IDs (Required)
   VITE_SUIT_REGISTRY=0xdf6309497d5dcb7e5a4aefb8e90392d10675e4efc4bcf85470978c181e18c63e
   VITE_INTERACTION_REGISTRY=0xb602fa6e7d602d95ae48b1c5735d02b7448ad91fea33bae2be0c0c42666f1bc5
   VITE_USERNAME_REGISTRY=0x4fb3b92339aee9f4c8282b5eaee221eb5ffba8796d90a48a6b7a26b1fc94260a
   VITE_TIP_BALANCE_REGISTRY=0xeba4d8d3f39db0c4cc650d4c22e846f7b4a96c6c08de15f1081aadd0c71cea00
   VITE_CHAT_REGISTRY=0x352e601455695225ee3d6b1231da6ab8cd6e497ce7f5183c0dae6dbced2fd9dc
   
   # Optional: Custom Walrus URL (defaults to multiple publishers with fallback)
   VITE_WALRUS_URL=https://walrus-testnet-publisher.nodes.guru
   ```

   **Note:** The project uses multiple Walrus publisher endpoints with automatic fallback by default. You don't need to set `VITE_WALRUS_URL` unless you want to override this behavior.

4. Deploy Smart Contracts (Optional for development)
   ```bash
   cd ../Suits
   sui client publish --gas-budget 100000000
   ```

5. Start development server
   ```bash
   cd ../next-frontend
   pnpm dev
   ```

6. Build for production
   ```bash
   pnpm build
   pnpm preview
   ```

### Smart Contract Deployment

```bash
# Navigate to contracts directory
cd Suits

# Publish to Sui testnet
sui client publish --gas-budget 100000000

# Note the package ID from the output
# Update config/index.ts with the deployed package ID
```

## Usage

### For Users

1. Connect Wallet: Click "Connect Wallet" and select your Sui wallet
2. Create Profile: Set up your username, bio, and profile picture
3. Start Posting: Create your first Suit (post) with text and media
4. Explore: Browse the feed, search for users and content
5. Discover Users: Click on usernames in posts to view other users' profiles
6. Connect: Start direct conversations with other users from their profiles
7. Interact: Like, comment, and repost other users' content
8. Manage Assets: View your SUI balance and NFT collection

### For Developers

```typescript
// Example: Create a new Suit
import { useSuits } from '../hooks/useSuits'

const { postSuit } = useSuits()

await postSuit("Hello, Rowl! This is my first post on the decentralized social network!")

// Example: Fetch user profile
import { useProfile } from '../hooks/useProfile'

const { fetchProfileByAddress } = useProfile()

const profile = await fetchProfileByAddress(userAddress)
```

## API Reference

### Hooks

#### `useSuits()`
- `fetchSuits(limit, offset)`: Fetch suits from blockchain
- `postSuit(content, mediaUrls?, contentType)`: Create new suit with content type
- `fetchVideoFeed(limit, offset)`: Fetch only video posts
- `fetchImageFeed(limit, offset)`: Fetch only image posts
- `fetchSuitsByContentType(type, limit, offset)`: Filter by content type
- `isPosting`: Loading state for posting
- `isFetching`: Loading state for fetching
- `error`: Error state

#### `useProfile()`
- `fetchMyProfile()`: Get current user's profile
- `fetchProfileByAddress(address)`: Get profile by address
- `fetchMyProfileFields()`: Get current user's profile fields
- `createProfile(username, bio, pfpUrl)`: Create new profile

#### `useInteractions()`
- `likeSuit(suitId)`: Like/unlike a suit (toggles like state)
- `commentOnSuit(suitId, content)`: Comment on a suit (max 280 chars)
- `retweetSuit(suitId)`: Repost/unrepost a suit (toggles repost state)
- Optimistic updates for instant UI feedback

#### `useMessaging()`
- `startChat(otherUserAddress)`: Start a new chat with another user
- `fetchChats()`: Fetch user's chat conversations
- `sendMessage(chatId, content)`: Send message in a chat

#### `useSearch()`
- `search(query, filters)`: Search users and posts with filters
- `searchUsers(query)`: Search only users by username
- `searchPosts(query)`: Search only posts by content
- `isSearching`: Loading state for search operations
- `error`: Error state for search operations

#### `useTipping()`
- `tipSuit(suitId, recipientAddress, amount)`: Send tip in SUI
- `getTipBalanceInfo(address)`: Get user's tip balance
- `withdrawFunds(amount)`: Withdraw tips to wallet
- `isTipping`: Loading state for tipping operations

#### `useWalrusUpload()`
- `uploadImage(file)`: Upload image file to Walrus (max 5MB)
- `uploadVideo(file)`: Upload video file to Walrus (max 3MB)
- `isUploading`: Loading state for upload operations
- Automatic fallback across 4 Walrus publisher endpoints

### Development Guidelines

- **TypeScript:** Follow strict TypeScript best practices (strict mode enabled)
- **Code Style:** Use ESLint for code quality (max-warnings: 0)
- **Testing:** Write tests for all smart contract changes (Move tests)
- **Commits:** Write meaningful commit messages following conventional commits
- **Documentation:** Update README and code comments as features change
- **Linting:** Ensure code passes linting checks before committing

### Current Project Status

**✅ Completed Features:**
- Content type support (text/image/video) with auto-detection
- Video autoplay with Intersection Observer
- Skeleton loaders and empty states
- Multiple Walrus publishers with fallback
- File size validation (3MB videos, 5MB images)
- All smart contract tests passing (15/15)
- Production build successful
- TypeScript compilation with no errors

**📊 Metrics:**
- Bundle Size: ~390 KB (gzipped)
- Build Time: ~10 seconds
- Test Coverage: 15/15 smart contract tests passing
- Modules: 2,657 transformed modules

**🔧 Configuration:**
- Package Manager: pnpm
- Node Version: v18+
- TypeScript: v5.6.3
- React: v18.3.1
- Vite: v6.0.1

### File Size Limits

| Type | Max Size | Supported Formats |
|------|----------|-------------------|
| Images | 5 MB | JPEG, PNG, GIF, WebP |
| Videos | 3 MB | MP4, WebM, MOV |
| Text | 280 chars | Plain text |

**Note:** For videos exceeding 3MB, use compression tools like FFmpeg or online compressors before uploading.

### Known Improvements

The project is production-ready and functional. For detailed improvement recommendations, see [IMPROVEMENT_ANALYSIS.md](./IMPROVEMENT_ANALYSIS.md).

**Planned Enhancements:**
- Frontend testing infrastructure (unit and integration tests)
- Performance optimizations (profile caching, event subscriptions)
- Security enhancements (input sanitization, CSP headers)
- Code quality improvements (removing console.log, better TypeScript types)

## Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines

- Follow TypeScript best practices
- Write tests for new features
- Update documentation as needed
- Ensure all tests pass before submitting
- Use conventional commit messages

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

