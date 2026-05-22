# AWS Extension to OCSF

[![Version](https://img.shields.io/badge/version-1.1.0-blue.svg)](extension.json)
[![Name](https://img.shields.io/badge/name-aws-teal.svg)](extension.json)
[![UID](https://img.shields.io/badge/UID-998-purple.svg)](https://github.com/ocsf/ocsf-schema/blob/main/extensions.md)
[![License](https://img.shields.io/badge/license-Apache%202.0-green.svg)](LICENSE)
[![Schema Browser](https://img.shields.io/badge/schema-browser-orange.svg)](https://schema.ocsf.io)

The AWS extension for the [Open Cybersecurity Schema Framework (OCSF)](https://github.com/ocsf/ocsf-schema). This extension adds AWS-specific event classes, objects, attributes, and profiles to the core OCSF schema, enabling richer representation of security events in AWS environments.

This extension is registered in the [OCSF Extensions Registry](https://github.com/ocsf/ocsf-schema/blob/main/extensions.md).

## Local Compilation

This extension is compiled together with the core [ocsf-schema](https://github.com/ocsf/ocsf-schema) using the [ocsf-schema-compiler](https://pypi.org/project/ocsf-schema-compiler/).

```bash
pip install ocsf-schema-compiler

# Clone the core schema if you haven't already
git clone https://github.com/ocsf/ocsf-schema.git

# Compile with the AWS extension
ocsf-schema-compiler path/to/ocsf-schema -e path/to/aws -a
```

The `-a` flag allows attribute shadowing, which is required for this extension.

## CI

A GitHub Actions workflow validates that the extension compiles successfully on every push and pull request to `main`. It checks out both this extension and the core schema, then runs the compiler to catch issues early.

## Contributing

We welcome contributions! Please refer to the core [OCSF Contribution Guide](https://github.com/ocsf/ocsf-schema/blob/main/CONTRIBUTING.md) for detailed guidelines.

## License

Licensed under the [Apache License 2.0](LICENSE).

---

**Resources:**
- [OCSF Documentation](https://github.com/ocsf/ocsf-docs)
- [Schema Browser](https://schema.ocsf.io)
- [Community Discussions](https://github.com/ocsf/ocsf-schema/discussions)
- [Slack Workspace](https://github.com/ocsf#slack-workspace)
