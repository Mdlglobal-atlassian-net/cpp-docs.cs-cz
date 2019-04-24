---
title: Chyba kompilátoru C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: d0a1f7bdc493a16b38dc2348097cc6cbea7ed898
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62282284"
---
# <a name="compiler-error-c2518"></a>Chyba kompilátoru C2518

klíčové slovo '– klíčové slovo' neplatné v seznamu základních tříd; Ignorovat

Klíčová slova `class` a `struct` by se neměl zobrazit v seznamu základních tříd.

Následující ukázka generuje C2518:

```
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```