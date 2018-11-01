---
title: Kompilátor upozornění (úroveň 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: a26356dd32f1513eadf4ef2b82175cf71aed13a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536666"
---
# <a name="compiler-warning-level-4-c4634"></a>Kompilátor upozornění (úroveň 4) C4634

Komentář k dokumentu XML: nelze použít: důvod

Dokumentační značky XML nejde použít u všech C++ vytvoří.  Například nelze přidat komentáře dokumentace do oboru názvů nebo šablony.

Další informace najdete v tématu [dokumentace XML](../../ide/xml-documentation-visual-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4634.

```
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C4634.

```
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```