# Test Yocto Manifest Repository

A minimal test manifest repository for quick testing of Yocto/BitBake manifest sync functionality.

## Structure

This manifest includes:
- **meta-test-core**: Core layer with basic recipes
- **meta-test-apps**: Application layer with sample recipes

## Quick Test

### Using Repo Tool

```bash
# Initialize repo
repo init -u https://github.com/kavia-common/test-yocto-manifest -b main -m default.xml

# Sync repositories
repo sync -j2

# List synced projects
repo list
```

### Using API

```bash
curl -X POST "http://localhost:8000/api/repo-manifest/sync" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{
    "project_id": 4806,
    "manifest_url": "https://github.com/kavia-common/test-yocto-manifest",
    "manifest_branch": "main",
    "manifest_file": "default.xml",
    "repo_type": "public",
    "sync_jobs": 2
  }'
```

## What's Included

- **meta-test-core**: Contains basic system recipes
- **meta-test-apps**: Contains application recipes with SRC_URI dependencies

This is designed for quick testing and should sync in under 2 minutes.

