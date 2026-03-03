# ext-http-client

[![npm version](https://img.shields.io/npm/v/ext-http-client)](https://npmjs.com/package/ext-http-client)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue.svg)](https://www.typescriptlang.org/)
[![CI Status](https://github.com/theluckystrike/ext-http-client/actions/workflows/ci.yml/badge.svg)](https://github.com/theluckystrike/ext-http-client/actions)
[![Discord](https://img.shields.io/badge/Discord-Zovo-blueviolet.svg?logo=discord)](https://discord.gg/zovo)
[![Website](https://img.shields.io/badge/Website-zovo.one-blue)](https://zovo.one)
[![GitHub Stars](https://img.shields.io/github/stars/theluckystrike/ext-http-client?style=social)](https://github.com/theluckystrike/ext-http-client)

> HTTP client library for Chrome extensions with enhanced features.

Part of the [Zovo](https://zovo.one) family of privacy-first Chrome extensions and developer tools.

## Overview

`ext-http-client` is a powerful HTTP client library designed specifically for Chrome extensions. It provides a clean, promise-based API for making network requests with built-in support for extension-specific features.

## Features

- ✅ **Promise-based API** - Modern async/await syntax
- ✅ **Request/Response Interceptors** - Hook into request/response lifecycle
- ✅ **Automatic Retry** - Built-in retry logic
- ✅ **TypeScript Support** - Fully typed for better developer experience
- ✅ **MV3 Compatible** - Works with Manifest V3 extensions
- ✅ **Privacy-First** - No data collection, all local

## Installation

### From npm

```bash
npm install ext-http-client
```

### From Source

```bash
# Clone the repository
git clone https://github.com/theluckystrike/ext-http-client.git
cd ext-http-client

# Install dependencies
npm install

# Build the project
npm run build
```

## Usage

### Basic Requests

```typescript
import { HttpClient } from 'ext-http-client';

const client = new HttpClient();

// GET request
const response = await client.get('https://api.example.com/data');

// POST request
const postResponse = await client.post('https://api.example.com/data', {
  body: JSON.stringify({ name: 'value' })
});
```

### With Interceptors

```typescript
import { HttpClient, Interceptor } from 'ext-http-client';

const client = new HttpClient();

// Add request interceptor
client.interceptors.request.use((config) => {
  config.headers['Authorization'] = `Bearer ${getToken()}`;
  return config;
});

// Add response interceptor
client.interceptors.response.use((response) => {
  console.log('Response received:', response.status);
  return response;
});
```

### Error Handling

```typescript
import { HttpClient, HttpError } from 'ext-http-client';

const client = new HttpClient();

try {
  const response = await client.get('https://api.example.com/data');
} catch (error) {
  if (error instanceof HttpError) {
    console.error('HTTP Error:', error.status, error.message);
  }
}
```

## API Reference

### HttpClient

| Method | Description |
|--------|-------------|
| `get(url, config)` | GET request |
| `post(url, data, config)` | POST request |
| `put(url, data, config)` | PUT request |
| `delete(url, config)` | DELETE request |
| `patch(url, data, config)` | PATCH request |

### Interceptors

| Method | Description |
|--------|-------------|
| `request.use(fn)` | Add request interceptor |
| `response.use(fn)` | Add response interceptor |

## Related Packages

This package is part of the Zovo extension networking ecosystem:

- [ext-fetch-wrapper](https://github.com/theluckystrike/ext-fetch-wrapper) - Fetch API wrapper
- [ext-network-layer-full](https://github.com/theluckystrike/ext-network-layer-full) - Full network layer
- [ext-network-status](https://github.com/theluckystrike/ext-network-status) - Network status

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/http-improvement`
3. **Make** your changes
4. **Test** your changes: `npm test`
5. **Commit** your changes: `git commit -m 'Add new feature'`
6. **Push** to the branch: `git push origin feature/http-improvement`
7. **Submit** a Pull Request

### Development Setup

```bash
# Clone the repository
git clone https://github.com/theluckystrike/ext-http-client.git
cd ext-http-client

# Install dependencies
npm install

# Run tests
npm test

# Build
npm run build
```

## Built by Zovo

Part of the [Zovo](https://zovo.one) developer tools family — privacy-first Chrome extensions built by developers, for developers.

## See Also

### Related Zovo Repositories

- [zovo-extension-template](https://github.com/theluckystrike/zovo-extension-template) - Boilerplate for building privacy-first Chrome extensions
- [zovo-types-webext](https://github.com/theluckystrike/zovo-types-webext) - Comprehensive TypeScript type definitions for browser extensions
- [zovo-permissions-scanner](https://github.com/theluckystrike/zovo-permissions-scanner) - Privacy scanner for Chrome extensions
- [zovo-indexer](https://github.com/theluckystrike/zovo-indexer) - Indexing service for Zovo extensions

### Zovo Chrome Extensions

- [Zovo Tab Manager](https://chrome.google.com/webstore/detail/zovo-tab-manager) - Manage tabs efficiently
- [Zovo Focus](https://chrome.google.com/webstore/detail/zovo-focus) - Block distractions
- [Zovo Permissions Scanner](https://chrome.google.com/webstore/detail/zovo-permissions-scanner) - Check extension privacy grades

Visit [zovo.one](https://zovo.one) for more information.

## License

MIT - [Zovo](https://zovo.one)

---

*Built by developers, for developers. No compromises on privacy.*
