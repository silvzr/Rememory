# GitHub Actions Workflows

This directory contains GitHub Actions workflows for building the Rememory Windows application.

## Workflows

### 1. `build-windows.yml` - Full Build Matrix
- **Purpose**: Comprehensive build for all supported platforms and configurations
- **Triggers**: Push/PR to main branches, manual dispatch
- **Matrix**: Builds Debug/Release configurations for x64, x86, and ARM64 platforms
- **Artifacts**: Creates release artifacts for distribution

### 2. `ci-quick.yml` - Quick CI Check  
- **Purpose**: Fast build validation for pull requests
- **Triggers**: Push/PR to main branches
- **Build**: Single x64 Debug build to quickly validate changes

## Build Requirements

The project requires:
- Windows runner (windows-latest)
- .NET 8 SDK
- Visual Studio Build Tools (for C++ project)
- Windows SDK 10.0.26100.0

## Project Structure

- **Rememory.Core**: Native C++ library (produces DLL)
- **Rememory**: WinUI3 C# application (depends on Core DLL)
- **Build order**: C++ Core → .NET Application

## Artifacts

Release builds create platform-specific artifacts:
- `rememory-x64-Release`
- `rememory-x86-Release`  
- `rememory-ARM64-Release`

These contain the published application ready for distribution.