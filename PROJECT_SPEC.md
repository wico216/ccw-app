# CCW App - Collectible Card Wizard

## Project Specification Document

**Project Name**: CCW App (Collectible Card Wizard)
**Version**: 1.0.0
**Date**: 2025-11-15
**Status**: Planning Phase

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Goals and Objectives](#goals-and-objectives)
3. [Technical Stack](#technical-stack)
4. [Features and Requirements](#features-and-requirements)
5. [Database Design](#database-design)
6. [API Design](#api-design)
7. [UI/UX Design](#uiux-design)
8. [Implementation Plan](#implementation-plan)
9. [Testing Strategy](#testing-strategy)
10. [Deployment Strategy](#deployment-strategy)

---

## Project Overview

### Description

CCW App is a web-based Progressive Web App (PWA) for managing Magic: The Gathering card collections, building decks, and tracking card values. Inspired by Manabox, it provides a personal, customizable solution with no subscription fees and full data ownership.

### Target Users

- Primary: Personal use for MTG collection management
- Secondary: Extendable to other collectible card games

### Key Differentiators

- **Free and Open**: No subscription costs
- **Privacy-Focused**: Data stays under your control
- **Customizable**: Tailored to specific needs
- **Web-First**: Works on any device with a browser
- **Offline-Capable**: PWA with offline support

---

## Goals and Objectives

### Primary Goals

1. **Track Collection**: Maintain accurate inventory of owned cards
2. **Organize Cards**: Group cards in virtual binders and lists
3. **Build Decks**: Create and manage deck lists
4. **View Values**: Track collection and deck values
5. **Search Efficiently**: Find cards quickly with powerful search

### Secondary Goals

1. **Offline Access**: Work without internet connection
2. **Statistics**: Visual analytics for collection and decks
3. **Export/Import**: Data portability
4. **Multi-Device**: Sync across devices

### Success Metrics

- Can add and find cards in under 10 seconds
- Offline functionality for core features
- 99.9% uptime
- Sub-2 second page loads

---

## Technical Stack

### Frontend

```json
{
  "framework": "React 18",
  "language": "TypeScript",
  "build": "Vite",
  "routing": "React Router v6",
  "state": "Zustand",
  "ui": "shadcn/ui + Tailwind CSS",
  "data-fetching": "React Query (TanStack Query)",
  "forms": "React Hook Form + Zod",
  "charts": "Recharts",
  "offline": "Dexie.js (IndexedDB)"
}
```

### Backend

```json
{
  "platform": "Supabase",
  "database": "PostgreSQL",
  "auth": "Supabase Auth",
  "storage": "Supabase Storage",
  "realtime": "Supabase Realtime"
}
```

### External Services

```json
{
  "card-data": "Scryfall API",
  "images": "Scryfall CDN",
  "deployment": "Vercel",
  "analytics": "Plausible (privacy-friendly)"
}
```

### Development Tools

```json
{
  "version-control": "Git/GitHub",
  "package-manager": "npm",
  "code-quality": "ESLint + Prettier",
  "type-checking": "TypeScript strict mode",
  "testing": "Vitest + React Testing Library",
  "e2e": "Playwright"
}
```

---

## Features and Requirements

### Phase 1: MVP (Weeks 1-3)

#### 1.1 Card Search

**Requirements:**
- Search cards by name (autocomplete)
- Display card details (image, text, stats)
- Filter by color, type, rarity, set
- View all printings of a card
- Integration with Scryfall API

**User Stories:**
- As a user, I can search for cards by typing their name
- As a user, I can see card images and details
- As a user, I can filter search results by color/type/rarity

**Acceptance Criteria:**
- Search returns results in < 1 second
- Autocomplete shows suggestions after 2 characters
- Card details show all relevant information
- Filters work correctly and can be combined

#### 1.2 Collection Management

**Requirements:**
- Add cards to collection
- Remove cards from collection
- Update card quantity
- Track card condition and foil status
- View total collection value

**User Stories:**
- As a user, I can add cards I own to my collection
- As a user, I can specify quantity, condition, and foil status
- As a user, I can see the total value of my collection

**Acceptance Criteria:**
- Cards can be added with all metadata
- Quantities can be incremented/decremented easily
- Collection value updates automatically
- Can remove cards from collection

#### 1.3 Collection Display

**Requirements:**
- List view with sorting
- Grid view with card images
- Filter collection by color/type/set
- Search within collection
- Group by different attributes

**User Stories:**
- As a user, I can view my collection as a list or grid
- As a user, I can sort my collection by different criteria
- As a user, I can quickly find cards in my collection

**Acceptance Criteria:**
- Both list and grid views work smoothly
- Sorting is instant and correct
- Search within collection is fast
- Filters can be combined

#### 1.4 Basic Statistics

**Requirements:**
- Total cards owned
- Total collection value
- Cards by color distribution
- Cards by type distribution
- Cards by set distribution

**User Stories:**
- As a user, I can see statistics about my collection
- As a user, I can visualize my collection breakdown

**Acceptance Criteria:**
- Statistics are accurate
- Charts are readable and interactive
- Statistics update when collection changes

### Phase 2: Organization (Weeks 4-5)

#### 2.1 Binders

**Requirements:**
- Create named binders
- Move cards between binders
- Delete binders
- View binder contents
- Binder statistics

**User Stories:**
- As a user, I can organize cards into virtual binders
- As a user, I can name binders after my physical binders
- As a user, I can move cards between binders

**Acceptance Criteria:**
- Binders can be created, renamed, deleted
- Cards can be moved via drag-and-drop or menu
- Binder view shows only cards in that binder
- Each binder shows its own statistics

#### 2.2 Lists

**Requirements:**
- Create named lists (wishlist, trade list, etc.)
- Add cards to lists
- Mark list items as owned/wanted
- Export lists

**User Stories:**
- As a user, I can create wishlists of cards I want
- As a user, I can create trade lists
- As a user, I can export my lists to share

**Acceptance Criteria:**
- Lists can be created with custom names
- Lists can contain cards not in collection
- Lists can be exported to text/CSV
- Lists show total value

#### 2.3 Advanced Search

**Requirements:**
- Oracle text search
- Mana cost filter
- CMC (converted mana cost) filter
- Power/toughness filter
- Legality filter (format)
- Price range filter
- Save search filters

**User Stories:**
- As a user, I can search for cards with specific abilities
- As a user, I can filter by mana cost and CMC
- As a user, I can save my common search filters

**Acceptance Criteria:**
- All filters work correctly
- Filters can be combined logically (AND/OR)
- Saved searches can be recalled
- Complex queries return correct results

### Phase 3: Deck Building (Weeks 6-8)

#### 3.1 Deck Creation

**Requirements:**
- Create new deck
- Name and describe deck
- Select format (Standard, Modern, Commander, etc.)
- Add cards to mainboard
- Add cards to sideboard
- Set commander (for Commander format)
- Mark deck as "built" (physical)

**User Stories:**
- As a user, I can create new deck lists
- As a user, I can add cards to my deck
- As a user, I can track which decks I've physically built

**Acceptance Criteria:**
- Decks can be created with metadata
- Cards can be added from search or collection
- Deck respects format rules (60 card minimum for Standard, etc.)
- Commander decks have special commander slot

#### 3.2 Deck Statistics

**Requirements:**
- Mana curve chart
- Color distribution pie chart
- Type distribution chart
- Average CMC
- Land/spell ratio
- Deck value
- Format legality check

**User Stories:**
- As a user, I can see my deck's mana curve
- As a user, I can analyze my deck's color requirements
- As a user, I can verify my deck is format-legal

**Acceptance Criteria:**
- Mana curve displays correctly
- Color analysis shows all color requirements
- Type breakdown is accurate
- Legality checker works for all formats
- Statistics update as deck changes

#### 3.3 Deck Management

**Requirements:**
- List all decks
- Duplicate deck
- Delete deck
- Export deck (text, Arena format, MTGO format)
- Import deck from text
- Compare deck to collection (owned cards)

**User Stories:**
- As a user, I can manage multiple decks
- As a user, I can export decks to play online
- As a user, I can see which deck cards I already own

**Acceptance Criteria:**
- Deck list view shows all decks
- Export formats are correct
- Import parses common deck list formats
- Collection comparison highlights missing cards

#### 3.4 Deck Simulator (Basic)

**Requirements:**
- Draw opening hand
- Mulligan
- Draw cards
- Reset simulation

**User Stories:**
- As a user, I can test my deck's opening hands
- As a user, I can practice mulligan decisions

**Acceptance Criteria:**
- Opening hand is random 7 cards
- Mulligan follows official rules
- Draw button draws next card
- Reset starts new simulation

### Phase 4: Advanced Features (Weeks 9-12)

#### 4.1 Offline Support

**Requirements:**
- Cache card data in IndexedDB
- Offline-first architecture
- Sync when online
- Background data updates

**User Stories:**
- As a user, I can use the app without internet
- As a user, my changes sync when I go back online

**Acceptance Criteria:**
- Core features work offline
- Data syncs correctly when online
- No data loss during offline usage
- User is notified of sync status

#### 4.2 Data Import/Export

**Requirements:**
- Export collection to CSV
- Import collection from CSV
- Export all data (backup)
- Import from Manabox/Deckbox (if feasible)

**User Stories:**
- As a user, I can backup my entire collection
- As a user, I can import from other apps

**Acceptance Criteria:**
- Export includes all card metadata
- Import handles various CSV formats
- Backup includes everything (decks, lists, etc.)
- Import validation prevents errors

#### 4.3 Price Tracking

**Requirements:**
- Display current prices
- Show price trends (graph)
- Price alerts (optional)
- Multiple price sources

**User Stories:**
- As a user, I can see if my cards' values are increasing
- As a user, I can get notified when a card hits a price target

**Acceptance Criteria:**
- Prices update daily
- Trend graph shows historical data
- Alerts work reliably
- Multiple sources can be compared

#### 4.4 Responsive Mobile UI

**Requirements:**
- Mobile-optimized layout
- Touch-friendly controls
- PWA installable
- Mobile navigation

**User Stories:**
- As a user, I can use the app on my phone
- As a user, I can install it as an app

**Acceptance Criteria:**
- Works well on all screen sizes
- Touch gestures work smoothly
- PWA can be installed
- Mobile performance is good

---

## Database Design

### Schema

```sql
-- Enable UUID extension
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

-- Users table
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  email TEXT UNIQUE NOT NULL,
  username TEXT UNIQUE,
  avatar_url TEXT,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Collections (Binders and Lists)
CREATE TABLE collections (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  type TEXT NOT NULL CHECK (type IN ('binder', 'list', 'wishlist', 'tradelist')),
  description TEXT,
  is_default BOOLEAN DEFAULT FALSE,
  sort_order INTEGER DEFAULT 0,
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  UNIQUE(user_id, name, type)
);

-- Collection Cards (Cards in binders/lists)
CREATE TABLE collection_cards (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  collection_id UUID NOT NULL REFERENCES collections(id) ON DELETE CASCADE,
  scryfall_id UUID NOT NULL,
  quantity INTEGER NOT NULL DEFAULT 1 CHECK (quantity >= 0),
  foil BOOLEAN DEFAULT FALSE,
  condition TEXT CHECK (condition IN ('mint', 'near_mint', 'excellent', 'good', 'light_played', 'played', 'poor')),
  language TEXT DEFAULT 'en',
  signed BOOLEAN DEFAULT FALSE,
  altered BOOLEAN DEFAULT FALSE,
  notes TEXT,
  acquired_date DATE,
  acquired_price NUMERIC(10, 2),
  tags TEXT[], -- Array of custom tags
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  UNIQUE(collection_id, scryfall_id, foil, condition)
);

-- Decks
CREATE TABLE decks (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  description TEXT,
  format TEXT, -- 'standard', 'modern', 'commander', 'legacy', etc.
  is_built BOOLEAN DEFAULT FALSE,
  is_public BOOLEAN DEFAULT FALSE,
  commander_id UUID, -- Reference to card for Commander format
  color_identity TEXT[], -- Color identity of deck
  tags TEXT[],
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Deck Cards
CREATE TABLE deck_cards (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  deck_id UUID NOT NULL REFERENCES decks(id) ON DELETE CASCADE,
  scryfall_id UUID NOT NULL,
  quantity INTEGER NOT NULL DEFAULT 1 CHECK (quantity >= 0),
  board TEXT NOT NULL DEFAULT 'mainboard' CHECK (board IN ('mainboard', 'sideboard', 'commander', 'maybeboard')),
  category TEXT, -- Optional: 'removal', 'ramp', 'draw', etc.
  is_owned BOOLEAN DEFAULT FALSE, -- Whether user owns this card
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Card Cache (Scryfall data cache)
CREATE TABLE card_cache (
  scryfall_id UUID PRIMARY KEY,
  oracle_id UUID,
  name TEXT NOT NULL,
  mana_cost TEXT,
  cmc NUMERIC,
  type_line TEXT,
  oracle_text TEXT,
  colors TEXT[],
  color_identity TEXT[],
  keywords TEXT[],
  set_code TEXT,
  set_name TEXT,
  rarity TEXT,
  power TEXT,
  toughness TEXT,
  loyalty TEXT,
  image_uris JSONB,
  prices JSONB,
  legalities JSONB,
  rulings JSONB,
  data JSONB, -- Full Scryfall card object
  last_updated TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Price History
CREATE TABLE price_history (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  scryfall_id UUID NOT NULL REFERENCES card_cache(scryfall_id),
  source TEXT NOT NULL, -- 'tcgplayer', 'cardmarket', 'scryfall'
  price_usd NUMERIC(10, 2),
  price_usd_foil NUMERIC(10, 2),
  price_eur NUMERIC(10, 2),
  price_eur_foil NUMERIC(10, 2),
  recorded_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Saved Searches
CREATE TABLE saved_searches (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  query JSONB NOT NULL, -- Search filters as JSON
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- User Preferences
CREATE TABLE user_preferences (
  user_id UUID PRIMARY KEY REFERENCES users(id) ON DELETE CASCADE,
  default_collection_id UUID REFERENCES collections(id),
  preferred_currency TEXT DEFAULT 'usd',
  preferred_language TEXT DEFAULT 'en',
  theme TEXT DEFAULT 'light',
  settings JSONB DEFAULT '{}',
  updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Indexes for performance
CREATE INDEX idx_collections_user ON collections(user_id);
CREATE INDEX idx_collection_cards_collection ON collection_cards(collection_id);
CREATE INDEX idx_collection_cards_scryfall ON collection_cards(scryfall_id);
CREATE INDEX idx_decks_user ON decks(user_id);
CREATE INDEX idx_deck_cards_deck ON deck_cards(deck_id);
CREATE INDEX idx_deck_cards_scryfall ON deck_cards(scryfall_id);
CREATE INDEX idx_card_cache_name ON card_cache(name);
CREATE INDEX idx_card_cache_updated ON card_cache(last_updated);
CREATE INDEX idx_price_history_scryfall ON price_history(scryfall_id);
CREATE INDEX idx_price_history_recorded ON price_history(recorded_at);

-- Full-text search index
CREATE INDEX idx_card_cache_name_search ON card_cache USING gin(to_tsvector('english', name));
CREATE INDEX idx_card_cache_text_search ON card_cache USING gin(to_tsvector('english', oracle_text));

-- Functions for updating timestamps
CREATE OR REPLACE FUNCTION update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Triggers for auto-updating timestamps
CREATE TRIGGER update_users_updated_at BEFORE UPDATE ON users
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_collections_updated_at BEFORE UPDATE ON collections
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_collection_cards_updated_at BEFORE UPDATE ON collection_cards
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_decks_updated_at BEFORE UPDATE ON decks
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

CREATE TRIGGER update_deck_cards_updated_at BEFORE UPDATE ON deck_cards
  FOR EACH ROW EXECUTE FUNCTION update_updated_at_column();

-- Row Level Security (RLS) Policies
ALTER TABLE collections ENABLE ROW LEVEL SECURITY;
ALTER TABLE collection_cards ENABLE ROW LEVEL SECURITY;
ALTER TABLE decks ENABLE ROW LEVEL SECURITY;
ALTER TABLE deck_cards ENABLE ROW LEVEL SECURITY;
ALTER TABLE saved_searches ENABLE ROW LEVEL SECURITY;
ALTER TABLE user_preferences ENABLE ROW LEVEL SECURITY;

-- Collections policies
CREATE POLICY "Users can view their own collections"
  ON collections FOR SELECT
  USING (auth.uid() = user_id);

CREATE POLICY "Users can insert their own collections"
  ON collections FOR INSERT
  WITH CHECK (auth.uid() = user_id);

CREATE POLICY "Users can update their own collections"
  ON collections FOR UPDATE
  USING (auth.uid() = user_id);

CREATE POLICY "Users can delete their own collections"
  ON collections FOR DELETE
  USING (auth.uid() = user_id);

-- Collection cards policies
CREATE POLICY "Users can view their own collection cards"
  ON collection_cards FOR SELECT
  USING (EXISTS (
    SELECT 1 FROM collections
    WHERE collections.id = collection_cards.collection_id
    AND collections.user_id = auth.uid()
  ));

CREATE POLICY "Users can insert their own collection cards"
  ON collection_cards FOR INSERT
  WITH CHECK (EXISTS (
    SELECT 1 FROM collections
    WHERE collections.id = collection_cards.collection_id
    AND collections.user_id = auth.uid()
  ));

CREATE POLICY "Users can update their own collection cards"
  ON collection_cards FOR UPDATE
  USING (EXISTS (
    SELECT 1 FROM collections
    WHERE collections.id = collection_cards.collection_id
    AND collections.user_id = auth.uid()
  ));

CREATE POLICY "Users can delete their own collection cards"
  ON collection_cards FOR DELETE
  USING (EXISTS (
    SELECT 1 FROM collections
    WHERE collections.id = collection_cards.collection_id
    AND collections.user_id = auth.uid()
  ));

-- Similar policies for decks, deck_cards, saved_searches, user_preferences
-- (Abbreviated for brevity - would include all tables)
```

---

## API Design

### Supabase Client API

```typescript
// lib/supabase.ts
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseKey);

// Types
export interface Collection {
  id: string;
  user_id: string;
  name: string;
  type: 'binder' | 'list' | 'wishlist' | 'tradelist';
  description?: string;
  is_default: boolean;
  created_at: string;
  updated_at: string;
}

export interface CollectionCard {
  id: string;
  collection_id: string;
  scryfall_id: string;
  quantity: number;
  foil: boolean;
  condition?: string;
  notes?: string;
  acquired_date?: string;
  acquired_price?: number;
}

export interface Deck {
  id: string;
  user_id: string;
  name: string;
  description?: string;
  format?: string;
  is_built: boolean;
  created_at: string;
  updated_at: string;
}
```

### Service Layer

```typescript
// services/collection.service.ts
import { supabase } from '@/lib/supabase';

export class CollectionService {
  // Get all collections for current user
  async getCollections() {
    const { data, error } = await supabase
      .from('collections')
      .select('*')
      .order('sort_order', { ascending: true });

    if (error) throw error;
    return data;
  }

  // Create new collection
  async createCollection(collection: Partial<Collection>) {
    const { data, error } = await supabase
      .from('collections')
      .insert([collection])
      .select()
      .single();

    if (error) throw error;
    return data;
  }

  // Add card to collection
  async addCard(collectionId: string, card: Partial<CollectionCard>) {
    const { data, error } = await supabase
      .from('collection_cards')
      .insert([{ ...card, collection_id: collectionId }])
      .select()
      .single();

    if (error) throw error;
    return data;
  }

  // Get cards in collection
  async getCards(collectionId: string) {
    const { data, error } = await supabase
      .from('collection_cards')
      .select('*, card:card_cache(*)')
      .eq('collection_id', collectionId);

    if (error) throw error;
    return data;
  }

  // Update card quantity
  async updateCardQuantity(cardId: string, quantity: number) {
    const { data, error } = await supabase
      .from('collection_cards')
      .update({ quantity })
      .eq('id', cardId)
      .select()
      .single();

    if (error) throw error;
    return data;
  }

  // Remove card from collection
  async removeCard(cardId: string) {
    const { error } = await supabase
      .from('collection_cards')
      .delete()
      .eq('id', cardId);

    if (error) throw error;
  }
}

export const collectionService = new CollectionService();
```

### Scryfall Integration

```typescript
// services/scryfall.service.ts
export class ScryfallService {
  private baseURL = 'https://api.scryfall.com';
  private cache = new Map();

  async searchCards(query: string) {
    const url = `${this.baseURL}/cards/search?q=${encodeURIComponent(query)}`;
    const response = await fetch(url);
    if (!response.ok) throw new Error('Search failed');
    return response.json();
  }

  async getCard(id: string) {
    if (this.cache.has(id)) {
      return this.cache.get(id);
    }

    const url = `${this.baseURL}/cards/${id}`;
    const response = await fetch(url);
    if (!response.ok) throw new Error('Card not found');

    const data = await response.json();
    this.cache.set(id, data);
    return data;
  }

  async autocomplete(query: string) {
    const url = `${this.baseURL}/cards/autocomplete?q=${encodeURIComponent(query)}`;
    const response = await fetch(url);
    if (!response.ok) throw new Error('Autocomplete failed');
    return response.json();
  }

  // Cache card data locally
  async cacheCard(card: any) {
    const { error } = await supabase
      .from('card_cache')
      .upsert([{
        scryfall_id: card.id,
        oracle_id: card.oracle_id,
        name: card.name,
        mana_cost: card.mana_cost,
        cmc: card.cmc,
        type_line: card.type_line,
        oracle_text: card.oracle_text,
        colors: card.colors,
        color_identity: card.color_identity,
        keywords: card.keywords,
        set_code: card.set,
        set_name: card.set_name,
        rarity: card.rarity,
        power: card.power,
        toughness: card.toughness,
        image_uris: card.image_uris,
        prices: card.prices,
        legalities: card.legalities,
        data: card,
        last_updated: new Date().toISOString()
      }]);

    if (error) console.error('Failed to cache card:', error);
  }
}

export const scryfallService = new ScryfallService();
```

---

## UI/UX Design

### Layout Structure

```
┌─────────────────────────────────────┐
│           Header/Nav Bar             │
├─────────────────────────────────────┤
│                                     │
│                                     │
│          Main Content Area          │
│                                     │
│                                     │
├─────────────────────────────────────┤
│      Bottom Navigation (Mobile)     │
└─────────────────────────────────────┘
```

### Navigation

**Desktop:**
- Horizontal top navigation
- Sidebar for secondary navigation

**Mobile:**
- Bottom tab bar
- Hamburger menu for additional options

### Page Routes

```
/                       → Home/Dashboard
/collection             → All Collections
/collection/:id         → Specific Collection/Binder
/search                 → Card Search
/card/:id               → Card Details
/decks                  → All Decks
/deck/:id               → Deck Builder/View
/deck/:id/simulator     → Deck Simulator
/lists                  → Lists (Wishlists, etc.)
/stats                  → Statistics Dashboard
/settings               → User Settings
/import                 → Import Data
/export                 → Export Data
```

### Color Scheme

```typescript
// Tailwind config
const colors = {
  // Magic colors
  white: '#F0E4D7',
  blue: '#0E68AB',
  black: '#150B00',
  red: '#D3202A',
  green: '#00733E',

  // UI colors
  primary: '#2563eb',
  secondary: '#64748b',
  success: '#10b981',
  warning: '#f59e0b',
  error: '#ef4444',

  // Neutral
  background: '#f8fafc',
  surface: '#ffffff',
  text: '#1e293b',
}
```

### Component Library

Use shadcn/ui components:
- Button
- Card
- Dialog/Modal
- Dropdown Menu
- Input
- Select
- Table
- Tabs
- Toast (notifications)
- Command (search/command palette)

---

## Implementation Plan

### Week 1: Project Setup

**Tasks:**
- [x] Research and documentation
- [ ] Initialize Vite + React + TypeScript project
- [ ] Set up Tailwind CSS + shadcn/ui
- [ ] Configure ESLint + Prettier
- [ ] Set up Supabase project
- [ ] Create database schema
- [ ] Configure environment variables
- [ ] Set up Git repository structure

**Deliverables:**
- Working development environment
- Database schema deployed
- Basic project structure

### Week 2: Card Search & Display

**Tasks:**
- [ ] Implement Scryfall API service
- [ ] Create card search component
- [ ] Create card display component
- [ ] Implement autocomplete
- [ ] Create card details page
- [ ] Add basic filters (color, type)
- [ ] Set up React Query for data fetching

**Deliverables:**
- Functional card search
- Card details view
- Working filters

### Week 3: Collection Management

**Tasks:**
- [ ] Create collection service
- [ ] Implement add to collection
- [ ] Create collection list view
- [ ] Create collection grid view
- [ ] Implement quantity adjustment
- [ ] Add remove from collection
- [ ] Show collection statistics

**Deliverables:**
- Working collection management
- Multiple view options
- Basic statistics

### Week 4: Organization (Binders)

**Tasks:**
- [ ] Create binder management UI
- [ ] Implement create/delete binders
- [ ] Add move cards between binders
- [ ] Create binder detail view
- [ ] Implement binder statistics
- [ ] Add sorting and filtering

**Deliverables:**
- Functional binder system
- Card organization features

### Week 5: Lists & Advanced Search

**Tasks:**
- [ ] Create list management UI
- [ ] Implement wishlist functionality
- [ ] Add Oracle text search
- [ ] Implement CMC filters
- [ ] Add legality filters
- [ ] Create saved searches feature

**Deliverables:**
- Working lists system
- Advanced search capabilities

### Week 6: Deck Creation

**Tasks:**
- [ ] Create deck service
- [ ] Implement deck creation UI
- [ ] Add deck builder interface
- [ ] Create card selection UI
- [ ] Implement mainboard/sideboard
- [ ] Add commander support

**Deliverables:**
- Functional deck builder
- Multiple format support

### Week 7: Deck Statistics

**Tasks:**
- [ ] Implement mana curve chart
- [ ] Create color distribution chart
- [ ] Add type distribution chart
- [ ] Calculate deck statistics
- [ ] Implement legality checker
- [ ] Show deck value

**Deliverables:**
- Complete deck analytics
- Visual statistics

### Week 8: Deck Management

**Tasks:**
- [ ] Create deck list view
- [ ] Implement deck export
- [ ] Add deck import
- [ ] Create deck duplication
- [ ] Add collection comparison
- [ ] Implement deck simulator

**Deliverables:**
- Complete deck management
- Import/export functionality
- Basic simulator

### Week 9: Offline Support

**Tasks:**
- [ ] Set up IndexedDB with Dexie
- [ ] Implement card caching
- [ ] Create sync service
- [ ] Add offline detection
- [ ] Implement conflict resolution
- [ ] Create PWA manifest

**Deliverables:**
- Offline-capable app
- PWA installable

### Week 10: Polish & Testing

**Tasks:**
- [ ] Write unit tests
- [ ] Write integration tests
- [ ] Add E2E tests
- [ ] Performance optimization
- [ ] Accessibility audit
- [ ] Mobile responsiveness
- [ ] Bug fixes

**Deliverables:**
- Test coverage > 70%
- Performance optimized
- Mobile-friendly

### Week 11: Import/Export

**Tasks:**
- [ ] Implement CSV export
- [ ] Create CSV import
- [ ] Add data validation
- [ ] Create backup/restore
- [ ] Add import from other apps

**Deliverables:**
- Data portability
- Backup functionality

### Week 12: Deployment & Documentation

**Tasks:**
- [ ] Deploy to Vercel
- [ ] Set up analytics
- [ ] Write user documentation
- [ ] Create video tutorials
- [ ] Final testing
- [ ] Launch!

**Deliverables:**
- Live application
- Complete documentation
- User guide

---

## Testing Strategy

### Unit Tests (Vitest)

Test individual functions and components:
- Service layer methods
- Utility functions
- Component logic
- State management

### Integration Tests (React Testing Library)

Test component interactions:
- Form submissions
- API calls
- User workflows
- Navigation

### E2E Tests (Playwright)

Test complete user journeys:
- Search and add card
- Create collection
- Build deck
- Export data

### Test Coverage Goals

- Unit tests: > 80%
- Integration tests: > 60%
- E2E tests: Critical paths

---

## Deployment Strategy

### Development Environment

```bash
npm run dev        # Start dev server
npm run test       # Run tests
npm run lint       # Lint code
npm run type-check # TypeScript check
```

### Staging Environment

- Deploy to Vercel preview
- Test with production data copy
- Perform QA testing

### Production Environment

- Deploy to Vercel
- Use production Supabase instance
- Monitor with analytics
- Set up error tracking (Sentry)

### Environment Variables

```env
# .env.example
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_APP_URL=http://localhost:5173
VITE_ENABLE_ANALYTICS=false
```

### Deployment Checklist

- [ ] All tests passing
- [ ] No TypeScript errors
- [ ] Environment variables set
- [ ] Database migrations run
- [ ] Performance tested
- [ ] Security audit completed
- [ ] Backup strategy in place
- [ ] Monitoring enabled

---

## Future Enhancements

### Post-Launch Features

1. **Mobile Apps**: Native iOS/Android with React Native
2. **Social Features**: Share collections, follow friends
3. **Trading System**: Built-in trading workflow
4. **Price Alerts**: Notifications for price changes
5. **Card Scanner**: ML-based card recognition
6. **Multi-Game Support**: Pokémon, Yu-Gi-Oh!, etc.
7. **Marketplace Integration**: Direct buying/selling
8. **Collection Insurance**: Value tracking for insurance
9. **Advanced Analytics**: Trends, predictions, insights
10. **AI Deck Suggestions**: ML-powered deck recommendations

---

## Success Criteria

### Technical Success

- [ ] Page load < 2 seconds
- [ ] No critical bugs
- [ ] 99.9% uptime
- [ ] Offline functionality works
- [ ] Mobile responsive
- [ ] Accessible (WCAG AA)

### User Success

- [ ] Can add card in < 10 seconds
- [ ] Can build deck in < 5 minutes
- [ ] Can find any card quickly
- [ ] Data exports correctly
- [ ] Works on phone and desktop

### Business Success

- [ ] Zero ongoing costs (free tier)
- [ ] Personal use satisfaction
- [ ] Potential for open source
- [ ] Good portfolio piece
- [ ] Learning objectives met

---

**Document Version**: 1.0.0
**Last Updated**: 2025-11-15
**Next Review**: Start of each phase
