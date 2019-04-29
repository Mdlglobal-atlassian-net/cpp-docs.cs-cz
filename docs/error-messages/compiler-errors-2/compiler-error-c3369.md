---
title: Chyba kompilátoru C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 0cd27da4b73732513afe0bd33a2d7312e6ddbe97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388723"
---
# <a name="compiler-error-c3369"></a>Chyba kompilátoru C3369

'název modulu': možnost idl_module už definovaná.

[Možnost idl_module](../../windows/idl-module.md) využití, ve kterém definujete knihovny DLL lze pouze jednou v jednom programu vyskytují.

Následující ukázka generuje C3369:

```
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```