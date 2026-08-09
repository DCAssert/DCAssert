# Boundary Category Library and Input-Pattern Classification Rules

This document provides the complete type-level Boundary Category Library used to guide assertion generation and the deterministic input-pattern classification rules used to measure input diversity.

## 1. Boundary Category Library

The Boundary Category Library guides assertion generation by defining representative boundary, special, and structural categories for each supported data type.

| Data Type | Boundary Categories | Count |
|:--:|:--|--:|
| `str` | Empty string; minimal-length string; whitespace-only string; whitespace-position string; control and escaped string; ordinary ASCII string; punctuation and symbolic string; multilingual string; emoji-containing string; special Unicode string; long string; format-like and noisy string. | 12 |
| `int` | Zero; one; minus one; ordinary positive integer; ordinary negative integer; positive platform extreme; negative platform extreme; arbitrary-precision positive extreme; arbitrary-precision negative extreme. | 9 |
| `float` | Zero float; ordinary positive float; ordinary negative float; positive infinity; negative infinity; NaN; near-zero positive finite value; near-zero negative finite value; large positive finite value; large negative finite value; scientific-notation float; float with many decimal places. | 12 |
| `bool` | `True`; `False`. | 2 |
| `list` | Empty list; single-element list; homogeneous numeric list; homogeneous textual list; heterogeneous list; nested list; long list. | 7 |
| `tuple` | Empty tuple; single-element tuple; homogeneous multi-element tuple; heterogeneous multi-element tuple. | 4 |
| `dict` | Empty dictionary; single-entry dictionary; multiple-entry dictionary; nested dictionary; dictionary containing `None` values; dictionary with heterogeneous key types. | 6 |
| **Total** | **All type-level boundary categories** | **52** |

## 2. Input-Pattern Classification Rules

Unlike the Boundary Category Library, which guides candidate generation, the following rules are applied after generation. They map concrete inputs into deterministic, mutually exclusive patterns for calculating pattern coverage and pattern distribution entropy.

### 2.1 Scalar Parameters

| Data Type | Input Patterns | Count |
|:--:|:--|--:|
| `int` | Zero; one; minus one; non-boundary positive value; non-boundary negative value; positive extreme value; negative extreme value. | 7 |
| `float` | Zero; non-boundary positive finite value; non-boundary negative finite value; positive finite extreme value; negative finite extreme value; positive infinity; negative infinity; NaN. | 8 |
| `bool` | `True`; `False`. | 2 |
| **Subtotal** | **All scalar input patterns** | **17** |

### 2.2 Struct Parameters

| Data Type | Input Patterns | Count |
|:--:|:--|--:|
| `str` | Empty; minimal-length; whitespace-related; special-character; ordinary ASCII; Unicode-related; long or irregular. | 7 |
| `list` | Empty list; single-element list; homogeneous numeric list; homogeneous textual list; heterogeneous list; nested list; long list. | 7 |
| `tuple` | Empty tuple; single-element tuple; homogeneous multi-element tuple; heterogeneous multi-element tuple. | 4 |
| `dict` | Empty dictionary; single-entry dictionary; multiple-entry dictionary; nested dictionary; dictionary containing `None` values; dictionary with heterogeneous key types. | 6 |
| **Subtotal** | **All structural input patterns** | **24** |

| Summary | Count |
|:--|--:|
| Scalar input patterns | 17 |
| Structural input patterns | 24 |
| **All predefined input patterns** | **41** |
