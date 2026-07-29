# Snippet Engine

The Snippet Engine is a design folder for a snippet compiler built around reusable business particle components.

## Purpose

- Organize snippet concepts as small, composable units.
- Parse snippet definitions before package assembly.
- Keep package management rules close to the compiler pipeline.

## Compiler Flow

1. Prompt interface receives a snippet request.
2. Parser validates structure, dependencies, and package metadata.
3. Business particle components are selected and combined.
4. The compiler builds the final snippet package.
5. 1970ai can assist with orchestration, review, and generation.

## Core Parts

- **Prompt interface**: the entry point for creating or updating snippets.
- **Parser**: maintains syntax and package rules.
- **Business particle components**: reusable building blocks for snippet behavior.
- **Snippet compiler**: assembles and exports the final output.
- **1970ai**: assistive layer for guided snippet creation.

## Notes

This folder is intended to stay documentation-first and can grow into a full engine specification over time.
