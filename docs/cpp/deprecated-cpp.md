---
title: "Zastaralé (C++) | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: deprecated_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d3ec06d469f6fc71b23c9bdc6a67e5ed741d9f5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="deprecated-c"></a>deprecated (C++)
Toto téma se věnuje specifické pro společnost Microsoft nepoužívá declspec deklarace. Informace o C ++ 14 `[[deprecated]]` atribut a pokyny k kdy použít tento atribut oproti declspec specifické pro společnost Microsoft nebo – Direktiva pragma, najdete v části [standardní atributy C++](attributes2.md).

 S výjimky uvedené níže **zastaralé** deklarace nabízí stejné funkce jako [zastaralé](../preprocessor/deprecated-c-cpp.md) – Direktiva pragma:  
  
-   **Zastaralé** deklarace umožňuje určit konkrétní formy přetížení funkce jako zastaralé, zatímco – Direktiva pragma formuláře se vztahuje na všechny přetížené formy název funkce.  
  
-   **Zastaralé** deklarace umožňuje zadat zprávu, která se zobrazí v době kompilace. Text zprávy může být z makra.  
  
-   Makra může být označen pouze jako zastaralé s **zastaralé** – Direktiva pragma.  
  
 Pokud kompilátor narazí použití standard nebo identifikátor nepoužívané [ `[[deprecated]]` ](attributes2.md) atribut [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) upozornění je vyvolána výjimka.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak označit funkce jako zastaralé a jak určit zprávu, která se zobrazí v době kompilace při použití zastaralé funkce.  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak označit třídy jako zastaralé a jak určit zprávu, která se zobrazí v době kompilace při použití zastaralé třídy.  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)