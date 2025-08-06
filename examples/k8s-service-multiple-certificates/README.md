# Multiple Certificates with Google Managed Certificates

This example demonstrates how to use the Helm chart with multiple Google Managed Certificates for different domains.

## Configuration Options

The chart now supports both legacy single certificate and new multiple certificates configuration:

### Option 1: Legacy Single Certificate (Backwards Compatible)

```yaml
google:
  managedCertificate:
    enabled: true
    name: "my-cert"
    domainName: "api.example.com"  # Legacy way - still works
```

### Option 2: Multiple Certificates (Recommended)

```yaml
google:
  managedCertificate:
    enabled: true
    certificates:
      - name: "api-cert"
        domainName: "api.example.com"
      - name: "www-cert"
        domainName: "www.example.com"
      - name: "app-cert"
        domainName: "app.example.com"
```

## Backwards Compatibility

The implementation is fully backwards compatible:

- **Existing configurations** using `domainName` and `name` will continue to work unchanged
- **New configurations** can use `certificates` array for multiple certificates
- **If both are provided**, `certificates` array takes precedence over legacy `domainName`/`name`

## Benefits of Multiple Certificates

This approach is better when:

- **Domains are for different applications/services**
- **You need different certificate configurations per domain**
- **You want to manage certificates independently**
- **You need to add/remove domains without affecting existing certificates**

## Example Values

See `values.yaml` for a complete example configuration. 