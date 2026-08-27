# git-urls

[![CI](https://github.com/mojotx/git-urls/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/mojotx/git-urls/actions/workflows/ci.yml)
[![CodeQL](https://github.com/mojotx/git-urls/actions/workflows/codeql.yml/badge.svg?branch=master)](https://github.com/mojotx/git-urls/actions/workflows/codeql.yml)
[![Go Reference](https://pkg.go.dev/badge/github.com/mojotx/git-urls.svg)](https://pkg.go.dev/github.com/mojotx/git-urls)

Docs: [pkg.go.dev/github.com/mojotx/git-urls](https://pkg.go.dev/github.com/mojotx/git-urls?tab=overview)

This module is forked from [github.com/whilp/git-urls](https://github.com/whilp/git-urls). The upstream project appears to be abandoned: security fixes submitted upstream, including [whilp/git-urls#27](https://github.com/whilp/git-urls/pull/27), have remained open without review. This fork exists so important security issues can be fixed and released for downstream users.

## Improvements over the original

- Fixes the regular-expression denial-of-service issue reported as [GHSA-3f2q-6294-fmq5](https://github.com/advisories/GHSA-3f2q-6294-fmq5) by rejecting excessively long SCP-like URLs before running the regexp.
- Tightens SCP-style URL parsing so query data is only accepted after an actual `?` separator.
- Uses a single anchored regexp match instead of collecting all matches for an input that can only match once.
- Adds regression tests for the URL length guard, valid SCP-like URLs, SCP-like URLs with query strings, and malformed trailing text.
- Updates the Go module path to `github.com/mojotx/git-urls` and publishes tagged releases for consumers that need the security fix.
- Updates project tooling from the obsolete `gometalinter` workflow to `golangci-lint` and Go module commands.
