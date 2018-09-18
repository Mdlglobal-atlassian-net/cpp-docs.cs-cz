---
title: Chyba kompilátoru C3675 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4b6656753ab4a611dcb80d1473e0b44bf47a270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094777"
---
# <a name="compiler-error-c3675"></a>Chyba kompilátoru C3675

'function': je vyhrazené, protože 'property' je definován.

Když deklarujete jednoduchou vlastnost, kompilátor vygeneruje get a set přístupové metody a ty názvy jsou k dispozici v rámci programu.  Názvy generované kompilátorem jsou vytvářena předřazení get_ a set_ název vlastnosti.  Proto nelze deklarovat funkce se stejným názvem jako přístupové objekty generovaný kompilátorem.

Zobrazit [vlastnost](../../windows/property-cpp-component-extensions.md) Další informace.

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