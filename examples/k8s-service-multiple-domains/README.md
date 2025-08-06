# Multiple Domains with Google Managed Certificate

This example demonstrates how to use the Helm chart with multiple domains in a single Google Managed Certificate.

## Configuration Options

The chart now supports both legacy single domain and new multiple domains configuration:

### Option 1: Legacy Single Domain (Backwards Compatible)

```yaml
google:
  managedCertificate:
    enabled: true
    name: "my-cert"
    domainName: "api.example.com"  # Legacy way - still works
```

### Option 2: Single Domain (Recommended)

```yaml
google:
  managedCertificate:
    enabled: true
    name: "my-cert"
    domainNames:  # New way - supports both single and multiple domains
      - "api.example.com"
```

### Option 3: Multiple Domains

```yaml
google:
  managedCertificate:
    enabled: true
    name: "my-cert"
    domainNames:
      - "api.example.com"
      - "www.example.com"
      - "app.example.com"
```

## Backwards Compatibility

The implementation is fully backwards compatible:

- **Existing configurations** using `domainName` will continue to work unchanged
- **New configurations** can use `domainNames` for better flexibility
- **If both are provided**, `domainNames` takes precedence over `domainName`

## Example Values

See `values.yaml` for a complete example configuration. 