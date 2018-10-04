---
title: Upozornění (úroveň 3) C4580 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90cd0b401624ea6815b31b55a7da9c8796746ce8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789199"
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