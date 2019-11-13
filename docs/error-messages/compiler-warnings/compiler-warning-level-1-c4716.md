---
title: Upozornění kompilátoru (úroveň 1) C4716
ms.date: 11/04/2016
f1_keywords:
- C4716
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
ms.openlocfilehash: 5215e8fd0bdd44c9bdfc731d2b74499d38853e80
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052465"
---
# <a name="compiler-warning-level-1-c4716"></a>Upozornění kompilátoru (úroveň 1) C4716

klíčové slovo Function musí vracet hodnotu.

Daná funkce nevrátila hodnotu.

Návratový příkaz bez doprovodné návratové hodnoty můžou použít jenom funkce s návratovým typem void.

Při volání této funkce bude vrácena Nedefinovaná hodnota.

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md).

Následující ukázka generuje C4716:

```cpp
// C4716.cpp
// compile with: /c /W1
// C4716 expected
#pragma warning(default:4716)
int test() {
   // uncomment the following line to resolve
   // return 0;
}
```