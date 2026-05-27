# Importing Types

```
// Import a single type
import type { Person } from './models';

// Import multiple types
import type { Person, Address, Company } from './models';

// Import all types from a module
import type * as Types from './models';

// Default import as type
import type DefaultType from './default-export';

// Mixed import with default
import DefaultComponent, { type Props, type State } from './Component';

// Import both types and values
import { Component, type ComponentProps } from 'react';

// Renaming
import type { Person as User } from './models';
```
