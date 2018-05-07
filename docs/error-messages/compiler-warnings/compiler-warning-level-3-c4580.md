---
title: Kompilátoru (úroveň 3) upozornění C4580 | Microsoft Docs
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
ms.openlocfilehash: 89ad08af77b62cd0992e9415e2df8b31233e4e0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4580"></a>C4580 kompilátoru upozornění (úroveň 3)
[atribut] je zastaralá; Místo toho zadejte System::Attribute nebo Platform::Metadata jako základní třída  
  
[[atribut](../../windows/attribute.md)] již není upřednostňovaný syntaxe pro vytváření uživatelsky definované atributy. Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md). Pro kód CLR odvozena atributů z `System::Attribute`. Pro prostředí Windows Runtime kód odvozena atributů z `Platform::Metadata`.  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3454 a ukazuje, jak ji odstranit.  
  
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