---
title: Chyba kompilátoru C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: 6772572d29765370d6cdbf52ed8470ff2f3f054e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758070"
---
# <a name="compiler-error-c3675"></a>Chyba kompilátoru C3675

' function ': je rezervováno, protože je definována vlastnost ' Property '

Pokud deklarujete jednoduchou vlastnost, kompilátor vygeneruje přístupové metody Get a set a tyto názvy jsou k dispozici v oboru programu.  Názvy vygenerované kompilátorem jsou vytvořeny pomocí předpřipraveného get_ a set_ k názvu vlastnosti.  Proto nelze deklarovat funkce se stejným názvem jako přistupující objekty vygenerované kompilátorem.

Další informace najdete v tématu [vlastnost](../../extensions/property-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3675.

```cpp
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```
