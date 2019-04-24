---
title: Chyba kompilátoru C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: eb5ba268508922daf00adb49cf611c038db76343
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173194"
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
