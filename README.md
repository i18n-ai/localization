# i18n Translation GitHub Action

Automatically translate i18n JSON files from a source language to multiple target languages using Lingovo's professional translation service.

## Features

- 🌍 **Multi-language support** - Translate to multiple languages simultaneously
- 📁 **Nested JSON structures** - Maintains complex file hierarchies
- 🔒 **Secure** - Uses encrypted API tokens for authentication
- ⚡ **Fast** - Batch processing for optimal performance
- 🎯 **Accurate** - Professional-grade translation service
- 🔄 **Preserves structure** - Maintains original JSON formatting and nesting

## Usage

### Quick Start

```yaml
name: Translate i18n Files

on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  translate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Translate i18n files
        uses: i18n-ai/localization@v1
        with:
          access_token: ${{ secrets.LINGOVO_API_TOKEN }}
          i18n_dir: './src/locales'
          source_language: 'en-US'
          target_languages: 'fr-FR,es-ES,de-DE,it-IT,ja-JP'
      
      - name: Commit translations
        uses: stefanzweifel/git-auto-commit-action@v4
        with:
          commit_message: 'chore: update translations'
          file_pattern: 'src/locales/**/*.json'
```

### Inputs

| Input | Description | Required | Example |
|-------|-------------|----------|---------|
| `access_token` | Lingovo API access token | ✅ | `${{ secrets.LINGOVO_API_TOKEN }}` |
| `i18n_dir` | Path to i18n directory | ✅ | `./src/locales` |
| `source_language` | Source language code | ✅ | `en-US` |
| `target_languages` | Comma-separated target languages | ✅ | `fr-FR,es-ES,de-DE` |

### Supported Languages

Standard language codes are supported:
- **Simple format**: `en`, `fr`, `es`, `de`, `ja`, `zh`
- **Region-specific**: `en-US`, `fr-FR`, `es-ES`, `de-DE`, `ja-JP`, `zh-CN`

### Getting Started

1. **Get your API token** from [Lingovo Dashboard](https://lingovo.com/dashboard)
2. **Add the token** to your repository secrets as `LINGOVO_API_TOKEN`
3. **Set up the workflow** using the example above
4. **Push to trigger** the translation process

### Example File Structure

**Before:**
```
src/locales/
├── en-US.json
```

**After:**
```
src/locales/
├── en-US.json
├── fr-FR.json
├── es-ES.json
├── de-DE.json
└── it-IT.json
```

### Advanced Configuration

#### Custom Workflow Triggers

```yaml
on:
  push:
    branches: [ main ]
    paths: [ 'src/locales/en-US.json' ]  # Only when source file changes
  
  schedule:
    - cron: '0 2 * * *'  # Daily at 2 AM
  
  workflow_dispatch:  # Manual trigger
```

#### Multiple Source Files

```yaml
- name: Translate multiple source files
  uses: i18n-ai/localization@v1
  with:
    access_token: ${{ secrets.LINGOVO_API_TOKEN }}
    i18n_dir: './locales'
    source_language: 'en-US'
    target_languages: 'fr-FR,es-ES,de-DE'
```

### Pricing & API Access

This action requires a Lingovo API subscription:
- **Free tier**: 1,000 characters/month
- **Pro tier**: 100,000 characters/month
- **Enterprise**: Custom limits

[Get your API token →](https://lingovo.com/pricing)

### Support

- 📧 **Email**: support@lingovo.com
- 💬 **Chat**: [lingovo.com/support](https://lingovo.com/support)
- 🐛 **Issues**: [GitHub Issues](https://github.com/i18n-ai/localization/issues)

### License

This action is proprietary software. By using this action, you agree to the [Lingovo Terms of Service](https://lingovo.com/terms).

---

**Made with ❤️ by the Lingovo team** 