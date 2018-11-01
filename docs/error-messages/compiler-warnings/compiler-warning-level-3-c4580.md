---
title: Kompilátor upozornění (úroveň 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: e215dc98f62a90325e83068a640b0503a612c434
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427804"
---
# <a name="compiler-warning-level-3-c4580"></a>Kompilátor upozornění (úroveň 3) C4580

[attribute] je zastaralá; Místo toho zadejte System::Attribute nebo Platform::metadata – jako základní třída

[[atribut](../../windows/attributes/attribute.md)] už není preferovanou syntaxí pro vytvoření uživatelsky definované atributy. Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md). Kód CLR jsou odvozeny atributů z `System::Attribute`. Pro prostředí Windows Runtime kód odvodit atributů z `Platform::Metadata`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3454 a ukazuje, jak ho opravit.

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```