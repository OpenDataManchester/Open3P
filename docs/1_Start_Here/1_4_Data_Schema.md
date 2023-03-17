---
title: Data Schema
description: The current data schema of the Open 3P open data standard for the packaging value chain.
---

# Data Schema
``` mermaid
erDiagram
  BASE_MATERIALS }o--o{ MATERIALS : within
  MATERIALS }o--o{ COMPONENTS : within
  COMPONENTS }o--o{ COMPLETE_PACKAGING : within
  COMPLETE_PACKAGING }o..o{ MULTIPACK : within
  COMPONENTS }o..o{ MULTIPACK : within
  COMPLETE_PACKAGING }o..o{ LOAD_CATALOGUE : within
  MULTIPACK }o..o{ LOAD_CATALOGUE : within
  COMPONENTS }o..o{ LOAD_CATALOGUE : within
  LOAD_CATALOGUE }o--o{ LOAD : within
```
