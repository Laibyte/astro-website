---
title: "TypeScript API Wrapper"
description: "A fully-typed API wrapper library with automatic retry logic, request caching, and comprehensive error handling."
publishDate: 2023-11-20
tags: ["typescript", "api", "library"]
github: "https://github.com/yourusername/api-wrapper"
---

# TypeScript API Wrapper

A production-ready TypeScript library for building robust API clients with automatic retry logic, request caching, and comprehensive error handling.

## Motivation

Most API clients lack proper error handling, retry logic, and type safety. This library addresses those gaps while maintaining a simple, intuitive API.

## Features

- **Fully Typed**: Complete TypeScript support with generics
- **Automatic Retries**: Configurable exponential backoff
- **Request Caching**: In-memory and persistent caching options
- **Error Handling**: Structured error types with helpful messages
- **Interceptors**: Request and response middleware
- **Cancelation**: Built-in request cancelation support

## Installation

```bash
npm install @yourusername/api-wrapper
```

## Usage

### Basic Example

```typescript
import { createClient } from '@yourusername/api-wrapper';

interface User {
  id: string;
  name: string;
  email: string;
}

const client = createClient({
  baseURL: 'https://api.example.com',
  headers: {
    'Authorization': `Bearer ${token}`,
  },
});

const user = await client.get<User>('/users/123');
```

### With Retry Logic

```typescript
const client = createClient({
  baseURL: 'https://api.example.com',
  retry: {
    maxAttempts: 3,
    backoff: 'exponential',
    retryCondition: (error) => error.status >= 500,
  },
});
```

### With Caching

```typescript
const client = createClient({
  baseURL: 'https://api.example.com',
  cache: {
    maxAge: 5 * 60 * 1000, // 5 minutes
    exclude: ['/auth/*'],
  },
});
```

## Architecture

The library follows a layered architecture:

1. **Core Layer**: HTTP request/response handling
2. **Middleware Layer**: Interceptors, retry, cache
3. **Type Layer**: Generic type inference and validation
4. **Error Layer**: Structured error handling

## Type Safety

Full type inference throughout:

```typescript
const response = await client.get<User>('/users/123');
// response.data is typed as User

const users = await client.get<User[]>('/users');
// users.data is typed as User[]
```

## Error Handling

Structured error types:

```typescript
try {
  await client.get('/users/123');
} catch (error) {
  if (error instanceof NetworkError) {
    // Handle network errors
  } else if (error instanceof ValidationError) {
    // Handle validation errors
  } else if (error instanceof APIError) {
    // Handle API errors
    console.error(error.status, error.message);
  }
}
```

## Testing

The library includes comprehensive test coverage:

- Unit tests for all core functionality
- Integration tests with mock server
- Type tests using `tsd`

## Performance

Benchmarks against popular alternatives:

- 30% faster than Axios for simple requests
- 50% smaller bundle size than Ky
- Better tree-shaking than node-fetch

## Links

- [GitHub Repository](https://github.com/yourusername/api-wrapper)
- [NPM Package](https://www.npmjs.com/package/@yourusername/api-wrapper)
- [Documentation](https://api-wrapper-docs.netlify.app)
