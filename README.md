# @muhammedv/powersync-attachments-for-node

This is a fixed version of `@powersync/attachments` that resolves Node.js compatibility issues.

## What was fixed

### 1. ES Module Import Issues
- Fixed relative imports in `lib/index.js` and `lib/AbstractAttachmentQueue.js` to include `.js` extensions
- Original: `export * from './Schema'`
- Fixed: `export * from './Schema.js'`

### 2. Node.js Compatibility
- Replaced `FileReader` (browser API) with Node.js `Buffer` for blob-to-base64 conversion
- Original: Used `FileReader` which doesn't exist in Node.js
- Fixed: Used `Buffer.from(arrayBuffer).toString('base64')`

### 3. File Extension Handling
- Updated all import statements to include proper file extensions for ES modules

## Installation

```bash
npm install @muhammedv/powersync-attachments-for-node
```

## Usage

Replace the original package import:

```javascript
// Before
import { AbstractAttachmentQueue } from '@powersync/attachments';

// After
import { AbstractAttachmentQueue } from '@muhammedv/powersync-attachments-for-node';
```

## Changes Made

1. **lib/index.js**: Added `.js` extensions to all export statements
2. **lib/AbstractAttachmentQueue.js**: 
   - Added `.js` extensions to import statements
   - Replaced FileReader with Buffer for base64 conversion
3. **package.json**: Updated name and version to avoid conflicts

## License

Same as original: Apache-2.0

## Original Package

This is a fork of `@powersync/attachments` version 2.3.1 with Node.js compatibility fixes.
