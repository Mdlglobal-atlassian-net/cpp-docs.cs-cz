---
title: C4867 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46bf4866791ec82ac5984132903e22ab16e07ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4867"></a>C4867 upozornění kompilátoru
'function': volání funkce chybí seznam argumentů; Vytvořte ukazatel na člena pomocí 'volání.  
  
 Ukazatel na funkci člen byl nesprávně inicializován.  
  
 Toto upozornění můžete vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual C++ 2005: shoda lepší ukazatele na člena.  Kód, který zkompiluje před Visual C++ 2005 nyní generovat C4867.  
  
 Toto upozornění je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro vypnutí tohoto upozornění. Další informace o C4867 a MFC/ATL najdete v tématu [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4867.  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```