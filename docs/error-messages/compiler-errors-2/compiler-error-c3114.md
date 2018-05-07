---
title: C3114 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3114
dev_langs:
- C++
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69001d415167f976d0f30c2dd5a0181cc032d0d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3114"></a>C3114 chyby kompilátoru
'argument': není platný argument atributu s názvem  
  
 V pořadí pro datový člen třídy atributů platná s názvem argument nesmí být označené `static`, `const`, nebo `literal`. Pokud vlastnost, nesmí být vlastnost `static` a musí mít get a nastavení přístupových objektů.  
  
 Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md) a [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3114.  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```