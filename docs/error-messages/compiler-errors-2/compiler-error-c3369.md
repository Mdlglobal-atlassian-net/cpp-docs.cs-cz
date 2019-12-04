---
title: Chyba kompilátoru C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: ee936f4921369b1d59d81b51dcb3e81c69be083c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755600"
---
# <a name="compiler-error-c3369"></a>Chyba kompilátoru C3369

název modulu: idl_module už je definovaný.

[Idl_module](../../windows/idl-module.md) použití, kde můžete definovat knihovnu DLL, lze v programu provést pouze jednou.

Následující ukázka generuje C3369:

```cpp
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```
