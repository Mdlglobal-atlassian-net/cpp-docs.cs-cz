---
title: Upozornění kompilátoru (úroveň 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 69ca60e2cba338bf1bd1ac3470e583739e72a68e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186449"
---
# <a name="compiler-warning-level-1-c4530"></a>Upozornění kompilátoru (úroveň 1) C4530

C++použila se obslužná rutina výjimky, ale není povolená sémantika unwind. Zadat/EHsc

C++bylo použito zpracování výjimek, ale [/EHsc](../../build/reference/eh-exception-handling-model.md) nebylo vybráno.

Pokud možnost/EHsc není povolená, objekt s automatickým úložištěm v rámci, mezi funkcí, kterou vyvolává throw, a funkcí, které zachytí throw, nebude zničen. Objekt s automatickým úložištěm vytvořeným v bloku **Try** nebo **catch** však bude zničen.

Následující ukázka generuje C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Chcete-li vyřešit upozornění, zkompilujte ukázku pomocí/EHsc.
