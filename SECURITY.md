# Security & Privacy — FizzRead Skill

## Network Requests

This skill makes HTTP requests only to the following endpoints:

| Endpoint | Data Sent | Purpose |
|----------|-----------|---------|
| `api.xiai.xyz/api/skill/v1/*` | API Key (Authorization header), search keywords, category names, book slugs | Fetch book data (daily pick, search, summaries, recommendations) |
| `nccgpub.blob.core.windows.net` | None (read-only CDN) | Serve audio files (.mp3) and cover images (.webp) |

## Data Flow

1. The user's `FIZZREAD_API_KEY` is sent as a Bearer token in the Authorization header to `api.xiai.xyz` only.
2. Search queries and category names entered by the user are sent as URL query parameters.
3. Audio and cover image URLs returned by the API point to a CDN (`nccgpub.blob.core.windows.net`). No user data is sent to the CDN.

## Privacy

- **No chat content collected**: This skill does not send conversation messages, user prompts, or chat history to any external service.
- **No personal information collected**: No names, emails, device IDs, or other personal data are transmitted.
- **No analytics or tracking**: This skill does not collect usage statistics or telemetry.
- **No data storage**: This skill does not persist any data between sessions. All API calls are stateless.

## Permissions

- This skill requires the `curl` binary for making HTTP requests.
- This skill requires the `FIZZREAD_API_KEY` environment variable to authenticate with the FizzRead API.
- This skill does not require filesystem write access, network listen ports, or any other system permissions.

## Input Sanitization

All user-provided search terms and category names are URL-encoded before being included in API request URLs, preventing shell injection and ensuring safe request construction.
