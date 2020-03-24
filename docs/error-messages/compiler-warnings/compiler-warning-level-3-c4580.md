---
title: Upozornění kompilátoru (úroveň 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: 28d8534dad5fc1b234c180b879ad0645f05cfd65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198611"
---
# <a name="compiler-warning-level-3-c4580"></a>Upozornění kompilátoru (úroveň 3) C4580

[Attribute] je zastaralá; místo toho zadejte System:: Attribute nebo Platform:: metadata jako základní (Base) třídu.

[[attribute](../../windows/attributes/attribute.md)] již není upřednostňovanou syntaxí pro vytváření uživatelsky definovaných atributů. Další informace najdete v tématu [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md). Pro kód CLR odvozuje atributy z `System::Attribute`. Pro prostředí Windows Runtime kód odvozuje atributy z `Platform::Metadata`.

## <a name="example"></a>Příklad

Následující ukázka generuje C3454 a ukazuje, jak ji opravit.

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
