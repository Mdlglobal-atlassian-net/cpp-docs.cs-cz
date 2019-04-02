---
title: Chyba kompilátoru C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: e29e536bf89aef887dc043327e4b4596703d0538
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775189"
---
# <a name="compiler-error-c3675"></a>Chyba kompilátoru C3675

'function': je vyhrazené, protože 'property' je definován.

Když deklarujete jednoduchou vlastnost, kompilátor vygeneruje get a set přístupové metody a ty názvy jsou k dispozici v rámci programu.  Názvy generované kompilátorem jsou vytvářena předřazení get_ a set_ název vlastnosti.  Proto nelze deklarovat funkce se stejným názvem jako přístupové objekty generovaný kompilátorem.

Zobrazit [vlastnost](../../extensions/property-cpp-component-extensions.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3675.

```
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```