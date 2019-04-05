---
title: Chyba kompilátoru C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: eb5ba268508922daf00adb49cf611c038db76343
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776697"
---
# <a name="compiler-error-c3246"></a>Chyba kompilátoru C3246

'class': nemůže dědit z 'type', protože byl deklarován jako 'sealed'

Třída, která je označena jako [zapečetěné](../../extensions/sealed-cpp-component-extensions.md) nemůže být základní třída pro jiné třídy.

Následující ukázka generuje C3246:

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
