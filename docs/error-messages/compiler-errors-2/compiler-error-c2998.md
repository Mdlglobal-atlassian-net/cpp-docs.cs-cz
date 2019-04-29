---
title: Compiler Error C2998
ms.date: 11/04/2016
f1_keywords:
- C2998
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
ms.openlocfilehash: 16a3319e71d465082120cbc58e3c7c6b916be80f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393607"
---
# <a name="compiler-error-c2998"></a>Compiler Error C2998

'identifier': nemůže být definice šablony

Kompilátor nemůže zpracovat syntaxe používané v definici šablony.

Následující ukázka generuje C2998:

```
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```