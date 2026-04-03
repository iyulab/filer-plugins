# Filer Plugins Registry

Community registry of plugin sources for the [Filer](https://github.com/iyulab/filer) app.

Filer fetches `registry.json` from this repository to discover available plugin sources.

## Registered Sources

| Name | Description | URL |
|------|-------------|-----|
| filer-official-plugins | Official plugins maintained by iyulab | [GitHub](https://github.com/iyulab/filer-official-plugins) |

## How It Works

Each **plugin source** is a GitHub repository containing a `filer-plugins.json` catalog at its root. The catalog lists individual plugins that Filer can install.

```
registry.json (this repo)
  └── source: filer-official-plugins (GitHub repo)
        └── filer-plugins.json (plugin catalog)
              ├── plugin-a
              ├── plugin-b
              └── ...
```

## Adding Your Plugin Source

Anyone can register a plugin source by submitting a Pull Request:

1. **Create your plugin source repository** with a valid `filer-plugins.json` at the root
2. **Fork this repository**
3. **Edit `registry.json`** — add your source to the `sources` array:
   ```json
   {
     "name": "your-source-name",
     "url": "https://github.com/your-org/your-plugins-repo",
     "description": "Brief description of your plugins"
   }
   ```
4. **Update the table** in this README
5. **Submit a Pull Request**

### Plugin Source Requirements

Your plugin source repository must include a `filer-plugins.json` file at the root:

```json
{
  "name": "your-source-name",
  "displayName": "Your Source Display Name",
  "owner": { "name": "Your Name", "url": "https://your-site.com" },
  "version": "1.0.0",
  "plugins": [
    {
      "name": "my-plugin",
      "source": { "type": "github", "repo": "your-org/my-filer-plugin" },
      "description": "What this plugin does",
      "version": "1.0.0",
      "tags": ["utility"]
    }
  ]
}
```

### Review Criteria

- The source repository must be publicly accessible
- `filer-plugins.json` must be valid and well-formed
- Plugin descriptions should be clear and accurate
- No malicious or deceptive content

## License

[MIT](LICENSE)
