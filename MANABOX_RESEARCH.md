# Manabox Research & Analysis

## Executive Summary

This document provides comprehensive research on the **Manabox** app - a popular Magic: The Gathering collection management and deck building tool - and outlines technical requirements for building a similar application for personal use.

**Research Date:** 2025-11-15

---

## Table of Contents

1. [Manabox Overview](#manabox-overview)
2. [Core Features Analysis](#core-features-analysis)
3. [UI/UX Patterns](#uiux-patterns)
4. [Technical Architecture](#technical-architecture)
5. [Recommended Implementation](#recommended-implementation)
6. [Development Roadmap](#development-roadmap)

---

## Manabox Overview

### What is Manabox?

Manabox is an unofficial companion app for Magic: The Gathering players that provides comprehensive collection management, deck building, and trading tools. Available on both iOS and Android platforms.

### Business Model

- **Free Tier**: Core features including card search and basic collection management
- **Premium Subscription**:
  - $2.49/month
  - $22.99/year
  - Unlocks advanced features

### Platform Availability

- iOS (App Store)
- Android (Google Play)
- No web version currently
- Cross-device sync planned for early 2025

---

## Core Features Analysis

### 1. Collection Management

#### Card Database
- **Complete card catalog**: All MTG cards and sets
- **Offline access**: Full database available without internet
- **Multi-language support**: English, Spanish, French, German, Italian, Russian, Japanese
- **Always updated**: New sets automatically added

#### Organization Features
- **Binders**: Virtual binders that mirror physical collection organization
- **Lists**: Custom categorized lists for different purposes
- **Collector Mode**:
  - Group cards by set, color, or type
  - Visual tracking of owned vs. missing cards
  - Completion percentage tracking

#### Card Scanner
- **Camera-based scanning**: Use device camera to scan physical cards
- **Bulk scanning**: Quick digitization of large collections
- **Card recognition**: Automated identification of cards
- **Multiple versions**: Distinguishes between different printings/sets

### 2. Deck Building

#### Deck Creation
- **Deck lists**: Create and save multiple deck configurations
- **Collection integration**: Mark which decks are physically built vs. theoretical
- **Maybe board**: Additional card consideration list beyond sideboard

#### Statistics & Analysis
- **Mana Curve**: Visual representation of mana cost distribution
- **Mana Production**: Color and total mana generation analysis
- **Mana Cost Distribution**: Breakdown of mana symbols required
- **Type Distribution**: Card type categorization (creatures, instants, etc.)
- **Token Tracking**: Tokens produced by cards in deck

#### Deck Simulator
- **Test hands**: Simulate opening hands
- **Mulligan testing**: Practice mulligan decisions
- **Draw simulation**: Test deck consistency

#### Deck Value
- **Current pricing**: Real-time deck valuation
- **Price tracking**: Monitor deck value changes over time

### 3. Pricing & Market Data

#### Supported Marketplaces
- TCGplayer
- Cardmarket
- Card Kingdom
- Star City Games
- Cardhoarder

#### Pricing Features
- **Up-to-date prices**: Current market values
- **Multiple versions**: Pricing for different printings
- **Collection value**: Total collection worth
- **Deck value**: Individual deck pricing

### 4. Trading Tools

#### Trade Management
- **Trade builder**: Create and track trades
- **Price comparison**: Fair value verification
- **Version selection**: Choose specific card printings
- **Multi-card trades**: Complex trade calculations

#### Trade Workflow
- Search and add cards to trade
- Compare values from different marketplaces
- Track trade history (potential feature)

### 5. Search & Discovery

#### Powerful Filtering
- **Advanced search**: Complex queries with multiple filters
- **Filter by**: Set, color, type, rarity, mana cost, etc.
- **Oracle text search**: Search card text (sequential matching)
- **Visual filters**: Sort by card art, frame type, etc.

#### Favorites System
- Mark favorite cards
- Quick access to preferred cards
- Personal collections/wishlists

### 6. Social & Sharing

#### Deck Sharing
- Share decks with friends
- Export deck lists
- Import shared decks

#### Community Features
- Feed with MTG articles
- News updates
- Set releases

### 7. Card Information

#### Complete Card Data
- **Rules text**: Current Oracle text
- **Legality**: Format legality status (Standard, Modern, Commander, etc.)
- **Card images**: High-quality card art
- **Rulings**: Official rulings and clarifications
- **Card versions**: All printings and variations

---

## UI/UX Patterns

### Navigation Structure

```
Main Navigation (Bottom Tab Bar)
├── Collection
│   ├── All Collection
│   ├── Binders
│   │   └── Individual Binder View
│   ├── Lists
│   └── Collector Mode
├── Decks
│   ├── My Decks
│   ├── Deck Builder
│   └── Deck Simulator
├── Search
│   ├── Card Search
│   ├── Advanced Filters
│   └── Scanner (Camera)
├── Trades
│   ├── Active Trades
│   └── Trade Builder
└── More/Profile
    ├── Settings
    ├── Favorites
    ├── News Feed
    └── Pricing Sources
```

### Key UX Patterns

1. **Quick Actions**: Fast access to frequently used features (scan, search, add to deck)
2. **Visual Organization**: Card images prominent, grid and list views
3. **Contextual Actions**: Swipe gestures for quick operations
4. **Progressive Disclosure**: Simple interface with advanced options available
5. **Offline-First**: Core features work without internet connection

### Common Workflows

#### Adding Cards to Collection
1. Scan card with camera OR search manually
2. Verify card details (set, condition, foil, etc.)
3. Select quantity
4. Choose destination (binder/list)
5. Save to collection

#### Building a Deck
1. Create new deck or open existing
2. Search/browse cards
3. Add cards from collection or database
4. View statistics and adjust
5. Test with simulator
6. Mark as "built" if physical deck exists

#### Making a Trade
1. Open trade builder
2. Add cards offering
3. Add cards receiving
4. Compare values across marketplaces
5. Finalize trade
6. Update collection

---

## Technical Architecture

### Recommended Stack for Similar App

#### Frontend

**Mobile App (React Native or Flutter)**
- **Pros**: Single codebase for iOS and Android
- **React Native**: Better for web developers, large community
- **Flutter**: Better performance, modern UI framework

**Alternative: Web-First (Progressive Web App)**
- **Framework**: React, Vue, or Svelte
- **Mobile**: Can be installed as PWA
- **Desktop**: Works in browser
- **Pros**: Easier deployment, no app store approval
- **Cons**: Limited offline capabilities, no camera scanning on some devices

#### Backend

**Option 1: Serverless (Recommended for Personal Use)**
```
Frontend → Firebase/Supabase → Cloud Functions
```
- **Pros**: Low cost, auto-scaling, easy auth
- **Cons**: Vendor lock-in
- **Best for**: Personal projects, MVP

**Option 2: Traditional Backend**
```
Frontend → API Server (Node.js/Python) → Database
```
- **Stack**: Express/FastAPI + PostgreSQL
- **Pros**: Full control, flexible
- **Cons**: More maintenance

#### Database

**For Card Data (Read-Heavy)**
- PostgreSQL with full-text search
- MongoDB for flexible schema
- SQLite for offline-first mobile

**For User Data**
- Firebase Firestore (real-time sync)
- PostgreSQL (traditional, reliable)
- Supabase (PostgreSQL with real-time features)

#### Data Sources

**MTG Card Data**
- **Scryfall API**: Free, comprehensive MTG card database
  - https://scryfall.com/docs/api
  - All cards, sets, rulings, images
  - Rate limits: respectful use

- **MTG JSON**: Downloadable JSON files
  - https://mtgjson.com/
  - Complete offline database
  - Updated with each set release

**Pricing Data**
- TCGplayer API (requires approval)
- Scryfall includes some pricing
- Web scraping (check terms of service)

### Key Technical Challenges

1. **Card Recognition (Scanner)**
   - ML/Computer Vision required
   - Options:
     - Google ML Kit (free, on-device)
     - Custom TensorFlow model
     - AWS Rekognition (paid)
   - Need training data for card images

2. **Offline Support**
   - Large database (20,000+ cards)
   - Image caching strategy
   - Sync conflict resolution
   - Storage optimization

3. **Search Performance**
   - Full-text search on card text
   - Multi-field filtering
   - Fuzzy matching for card names
   - Indexed database queries

4. **Data Sync**
   - Multi-device synchronization
   - Conflict resolution
   - Bandwidth optimization
   - Incremental updates

---

## Recommended Implementation

### Phase 1: MVP (Minimum Viable Product)

**Goal**: Basic collection tracking

#### Features
1. **Card Search**
   - Search by name
   - Basic filters (color, type, set)
   - View card details
   - Data from Scryfall API

2. **Collection Management**
   - Add cards manually
   - Track quantity
   - Single collection view
   - List and grid views

3. **Basic Stats**
   - Total cards owned
   - Collection value (from Scryfall pricing)
   - Cards by color/type

#### Tech Stack (Recommended)
- **Frontend**: React + TypeScript (web)
- **Backend**: Supabase (free tier)
- **Database**: PostgreSQL (included with Supabase)
- **Data**: Scryfall API
- **Hosting**: Vercel/Netlify (free tier)

#### Timeline
- 2-3 weeks for basic functionality

### Phase 2: Enhanced Collection

**Goal**: Better organization and usability

#### Features
1. **Binders & Lists**
   - Create named binders
   - Organize cards into categories
   - Move cards between binders

2. **Advanced Search**
   - Mana cost filters
   - Rarity filters
   - Oracle text search
   - Multi-select filters

3. **Card Details**
   - Full card information
   - Rulings display
   - Legality by format
   - Different printings

4. **Offline Support**
   - Cache card data
   - Offline card database
   - Service worker for PWA

#### Timeline
- 2-3 weeks additional

### Phase 3: Deck Building

**Goal**: Create and manage decks

#### Features
1. **Deck Creation**
   - Create/edit decks
   - Add cards from collection
   - Sideboard support
   - Deck notes

2. **Deck Statistics**
   - Mana curve visualization
   - Color distribution
   - Type breakdown
   - Average mana cost

3. **Deck Management**
   - Multiple decks
   - Mark decks as "built"
   - Deck value calculation
   - Export deck list

#### Timeline
- 3-4 weeks additional

### Phase 4: Advanced Features

**Goal**: Feature parity with commercial apps

#### Features
1. **Card Scanner**
   - Camera-based scanning
   - Card recognition
   - Bulk scanning

2. **Trading Tools**
   - Create trades
   - Value comparison
   - Trade history

3. **Price Tracking**
   - Historical prices
   - Price alerts
   - Market trends

4. **Mobile Apps**
   - React Native conversion
   - Native camera features
   - Push notifications

#### Timeline
- 4-6 weeks additional

---

## Development Roadmap

### Project Setup (Week 1)

```bash
# Recommended initial structure
ccw-app/
├── frontend/              # React web app
│   ├── src/
│   │   ├── components/   # UI components
│   │   ├── pages/        # Page components
│   │   ├── hooks/        # Custom hooks
│   │   ├── services/     # API services
│   │   ├── types/        # TypeScript types
│   │   └── utils/        # Utility functions
│   ├── public/
│   └── package.json
├── backend/              # Optional backend
│   └── functions/        # Cloud functions
├── shared/               # Shared types/utils
└── docs/                 # Documentation
```

### Technology Decisions

#### For Personal Use (Recommended)

**Web-First Progressive Web App**

```typescript
// Tech stack
{
  "frontend": {
    "framework": "React 18+",
    "language": "TypeScript",
    "styling": "Tailwind CSS",
    "state": "Zustand or Redux Toolkit",
    "routing": "React Router",
    "ui": "shadcn/ui or Material-UI"
  },
  "backend": {
    "platform": "Supabase",
    "auth": "Supabase Auth",
    "database": "PostgreSQL",
    "storage": "Supabase Storage"
  },
  "data": {
    "cards": "Scryfall API",
    "pricing": "Scryfall or custom scraper",
    "cache": "IndexedDB (Dexie.js)"
  },
  "deployment": {
    "frontend": "Vercel",
    "backend": "Supabase (managed)"
  }
}
```

**Why This Stack?**
- **Low/No Cost**: Free tiers available for all services
- **Fast Development**: Modern tools, good DX
- **Scalable**: Can grow with your needs
- **Type-Safe**: TypeScript throughout
- **Offline-Capable**: PWA + IndexedDB
- **No App Store**: Deploy directly to web

### Database Schema

```sql
-- Users
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  email TEXT UNIQUE NOT NULL,
  username TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Collections (Binders/Lists)
CREATE TABLE collections (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  type TEXT CHECK (type IN ('binder', 'list', 'wishlist')),
  description TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Collection Cards (User's owned cards)
CREATE TABLE collection_cards (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  collection_id UUID REFERENCES collections(id) ON DELETE CASCADE,
  scryfall_id TEXT NOT NULL, -- Reference to Scryfall card
  quantity INTEGER DEFAULT 1,
  foil BOOLEAN DEFAULT FALSE,
  condition TEXT CHECK (condition IN ('mint', 'near_mint', 'excellent', 'good', 'light_played', 'played', 'poor')),
  notes TEXT,
  acquired_date DATE,
  acquired_price DECIMAL(10, 2),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Decks
CREATE TABLE decks (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  format TEXT, -- 'standard', 'modern', 'commander', etc.
  is_built BOOLEAN DEFAULT FALSE,
  description TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Deck Cards
CREATE TABLE deck_cards (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  deck_id UUID REFERENCES decks(id) ON DELETE CASCADE,
  scryfall_id TEXT NOT NULL,
  quantity INTEGER DEFAULT 1,
  board TEXT CHECK (board IN ('mainboard', 'sideboard', 'commander', 'maybeboard')),
  category TEXT, -- Optional categorization
  created_at TIMESTAMP DEFAULT NOW()
);

-- Card Cache (for offline)
CREATE TABLE card_cache (
  scryfall_id TEXT PRIMARY KEY,
  data JSONB NOT NULL,
  image_url TEXT,
  last_updated TIMESTAMP DEFAULT NOW()
);

-- Price History (optional)
CREATE TABLE price_history (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  scryfall_id TEXT NOT NULL,
  price DECIMAL(10, 2),
  source TEXT, -- 'tcgplayer', 'cardmarket', etc.
  recorded_at TIMESTAMP DEFAULT NOW()
);

-- Trades (future feature)
CREATE TABLE trades (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  partner_name TEXT,
  trade_date DATE,
  status TEXT CHECK (status IN ('pending', 'completed', 'cancelled')),
  notes TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Indexes for performance
CREATE INDEX idx_collection_cards_collection ON collection_cards(collection_id);
CREATE INDEX idx_collection_cards_scryfall ON collection_cards(scryfall_id);
CREATE INDEX idx_deck_cards_deck ON deck_cards(deck_id);
CREATE INDEX idx_deck_cards_scryfall ON deck_cards(scryfall_id);
CREATE INDEX idx_card_cache_updated ON card_cache(last_updated);
```

### API Integration Examples

#### Scryfall API Usage

```typescript
// services/scryfall.ts

interface ScryfallCard {
  id: string;
  name: string;
  mana_cost: string;
  type_line: string;
  oracle_text: string;
  colors: string[];
  set: string;
  rarity: string;
  prices: {
    usd?: string;
    usd_foil?: string;
    eur?: string;
  };
  image_uris?: {
    small: string;
    normal: string;
    large: string;
  };
}

class ScryfallService {
  private baseURL = 'https://api.scryfall.com';

  // Search cards by name
  async searchCards(query: string): Promise<ScryfallCard[]> {
    const response = await fetch(
      `${this.baseURL}/cards/search?q=${encodeURIComponent(query)}`
    );
    const data = await response.json();
    return data.data;
  }

  // Get card by ID
  async getCard(id: string): Promise<ScryfallCard> {
    const response = await fetch(`${this.baseURL}/cards/${id}`);
    return response.json();
  }

  // Get card by name (exact)
  async getCardByName(name: string): Promise<ScryfallCard> {
    const response = await fetch(
      `${this.baseURL}/cards/named?exact=${encodeURIComponent(name)}`
    );
    return response.json();
  }

  // Advanced search with filters
  async advancedSearch(filters: {
    colors?: string[];
    type?: string;
    rarity?: string;
    set?: string;
    text?: string;
  }): Promise<ScryfallCard[]> {
    let query = '';

    if (filters.colors) {
      query += `c:${filters.colors.join('')} `;
    }
    if (filters.type) {
      query += `t:${filters.type} `;
    }
    if (filters.rarity) {
      query += `r:${filters.rarity} `;
    }
    if (filters.set) {
      query += `s:${filters.set} `;
    }
    if (filters.text) {
      query += `o:"${filters.text}" `;
    }

    return this.searchCards(query.trim());
  }

  // Get all sets
  async getAllSets() {
    const response = await fetch(`${this.baseURL}/sets`);
    const data = await response.json();
    return data.data;
  }
}

export const scryfallService = new ScryfallService();
```

### Component Examples

```typescript
// components/CardSearch.tsx
import { useState } from 'react';
import { scryfallService } from '@/services/scryfall';

export function CardSearch() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);
  const [loading, setLoading] = useState(false);

  const handleSearch = async () => {
    if (!query) return;

    setLoading(true);
    try {
      const cards = await scryfallService.searchCards(query);
      setResults(cards);
    } catch (error) {
      console.error('Search failed:', error);
    } finally {
      setLoading(false);
    }
  };

  return (
    <div className="card-search">
      <input
        type="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        onKeyPress={(e) => e.key === 'Enter' && handleSearch()}
        placeholder="Search for cards..."
      />
      <button onClick={handleSearch} disabled={loading}>
        {loading ? 'Searching...' : 'Search'}
      </button>

      <div className="results">
        {results.map((card) => (
          <CardItem key={card.id} card={card} />
        ))}
      </div>
    </div>
  );
}
```

---

## Key Differences for Personal Use

### Advantages of Building Your Own

1. **Customization**: Tailor features to your specific needs
2. **No Subscription**: One-time development effort
3. **Data Ownership**: Full control over your data
4. **Privacy**: No third-party data collection
5. **Learning**: Great portfolio project
6. **Multi-Purpose**: Can adapt for other collectibles

### Simplifications You Can Make

1. **No Multi-User**: Single-user app (simpler auth)
2. **Limited Platforms**: Web-only initially
3. **Basic Scanner**: Manual entry vs. complex ML
4. **Simple Pricing**: Static prices vs. real-time
5. **No Trading**: Focus on collection/decks
6. **Simpler Sync**: Single device or basic export/import

### Recommended Scope for Personal Project

**Phase 1 - Core Features (Keep These)**
- Card search with Scryfall API
- Collection tracking (owned cards)
- Binders/lists organization
- Deck building
- Basic statistics
- Price viewing (from Scryfall)

**Phase 2 - Nice to Have**
- Deck simulator
- Advanced filtering
- Offline support
- Export/import
- Deck statistics visualizations

**Phase 3 - Advanced (Optional)**
- Card scanner (complex)
- Multi-device sync
- Trading tools
- Price tracking/alerts
- Mobile apps

---

## Cost Estimate

### Using Recommended Stack (Supabase + Vercel)

**Free Tier Limits (Sufficient for Personal Use)**
- Supabase: 500MB database, 1GB file storage, 2GB bandwidth
- Vercel: 100GB bandwidth, unlimited sites
- Scryfall API: Free with respectful use

**If You Need More**
- Supabase Pro: $25/month (8GB database, 100GB storage)
- Vercel Pro: $20/month (1TB bandwidth)

**Total Cost for Personal Use: $0-$45/month**

### Alternative: Self-Hosted

**One-Time Costs**
- Domain: $10-15/year
- VPS: $5-10/month (DigitalOcean, Linode)

**Total Cost: $70-135/year**

---

## Next Steps

### 1. Define Your Requirements

Questions to answer:
- Do you need mobile apps or is web sufficient?
- How many cards in your collection?
- Do you build many decks?
- Do you need offline access?
- Do you trade cards frequently?
- Will others use it?

### 2. Choose Your Stack

Based on requirements:
- **Simple web app**: React + Supabase
- **Mobile needed**: React Native + Supabase
- **Full control**: Custom backend + PostgreSQL
- **Offline-first**: Flutter + SQLite

### 3. Set Up Project

```bash
# Create React app with TypeScript
npx create-react-app ccw-app --template typescript
cd ccw-app

# Install dependencies
npm install @supabase/supabase-js
npm install react-router-dom
npm install zustand
npm install tailwindcss

# Or use Vite (faster alternative)
npm create vite@latest ccw-app -- --template react-ts
```

### 4. Start Development

**Week 1**: Setup + Card Search
- Project structure
- Scryfall API integration
- Basic card search
- Card detail view

**Week 2**: Collection Management
- Database schema
- Add cards to collection
- View collection
- Basic statistics

**Week 3**: Organization
- Binders/lists
- Move cards between collections
- Filtering and sorting

**Week 4**: Deck Building
- Create decks
- Add cards to decks
- Deck statistics

### 5. Iterate and Enhance

Add features based on your needs:
- Better UI/UX
- More statistics
- Advanced search
- Export/import
- Offline support

---

## Resources

### APIs and Data Sources

- **Scryfall API**: https://scryfall.com/docs/api
- **MTG JSON**: https://mtgjson.com/
- **MTG Developers**: https://magicthegathering.io/ (alternative API)

### Libraries and Tools

**React Ecosystem**
- **UI Components**: shadcn/ui, Material-UI, Chakra UI
- **State Management**: Zustand, Redux Toolkit, Jotai
- **Data Fetching**: React Query, SWR
- **Forms**: React Hook Form
- **Charts**: Recharts, Chart.js, D3.js

**Database**
- **Supabase**: https://supabase.com/
- **Firebase**: https://firebase.google.com/
- **PostgreSQL**: https://www.postgresql.org/

**Offline Storage**
- **Dexie.js**: https://dexie.org/ (IndexedDB wrapper)
- **localForage**: https://localforage.github.io/localForage/

### Learning Resources

- **React**: https://react.dev/
- **TypeScript**: https://www.typescriptlang.org/
- **Supabase Docs**: https://supabase.com/docs
- **PWA**: https://web.dev/progressive-web-apps/

---

## Conclusion

Building a Manabox-like app for personal use is very achievable with modern web technologies. The recommended approach is to:

1. Start with a **web-based PWA** using React + TypeScript
2. Use **Supabase** for backend (auth, database, storage)
3. Integrate **Scryfall API** for card data
4. Focus on **core features** first (search, collection, decks)
5. **Iterate** based on your actual usage patterns

**Estimated Time to MVP**: 4-6 weeks part-time
**Estimated Cost**: $0/month (free tiers)
**Complexity**: Moderate (good learning project)

The main advantage over using Manabox is complete customization and data ownership. You can add features specific to your needs, integrate with other tools, and avoid subscription costs.

---

**Document Version**: 1.0
**Last Updated**: 2025-11-15
**Next Review**: As project requirements are defined
