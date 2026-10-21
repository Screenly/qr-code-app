[![Version](https://img.shields.io/github/v/release/Screenly/qr-code-app)](https://github.com/Screenly/qr-code-app/releases/latest)

# Screenly QR Code Generator App

![QR Code Generator App Preview](/screenshots/1920x1080.webp)

## Getting Started

```bash
bun install
```

## Deployment

Create and deploy the Edge App:

```bash
screenly edge-app create --name my-qr-code --in-place
bun run deploy
screenly edge-app instance create
```

### Releasing

Pushes to `main` deploy to stage automatically. To release to production, tag a commit on `main` and push the tag (the workflow refuses tags not on `main`):

```bash
git checkout main && git pull
git tag v26.10.0
git push origin v26.10.0
```

Then publish a GitHub Release whose notes list the pull requests merged since the previous release. Add `--draft` to review the notes before publishing:

```bash
gh release create v26.10.0 --verify-tag --generate-notes --title v26.10.0
```

## Configuration

The app accepts the following settings via `screenly.yml`:

| Setting          | Description                               | Type               | Default                                  |
| ---------------- | ----------------------------------------- | ------------------ | ---------------------------------------- |
| `call_to_action` | Instruction text below headline           | optional           | `Scan to visit`                          |
| `display_errors` | Display detailed error messages on screen | optional, advanced | `false`                                  |
| `enable_utm`     | Add UTM tracking parameters (true/false)  | optional, advanced | `true`                                   |
| `headline`       | Main message displayed above QR code      | required           | `Visit our website for exclusive offers` |
| `url`            | The URL to encode in the QR code          | required           | `https://www.screenly.io/`               |

### UTM Parameters

When `enable_utm` is enabled, the following parameters are automatically added:

- `utm_source=screenly`
- `utm_medium=digital-signage`
- `utm_location` - Screen location from metadata
- `utm_placement` - Screen hostname from metadata

## Development

```bash
bun install      # Install dependencies
bun run dev      # Start development server
```

## Testing

```bash
bun test
```

## Screenshots

Generate screenshots at all supported resolutions:

```bash
bun run screenshots
```

Screenshots are saved to the `screenshots/` directory.
