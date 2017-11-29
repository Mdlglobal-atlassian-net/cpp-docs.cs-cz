---
title: "pro každou v | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
dev_langs: C++
helpviewer_keywords: for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1d89552bd299edc778b06bd01ee185c275c45db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="for-each-in"></a>for each, in
Prochází skrze pole nebo kolekci. Toto nestandardní klíčové slovo je k dispozici v projektech v jazyce C++/CLI a v nativním jazyce C++. Jeho použití se však nedoporučuje. Zvažte použití standardního [na základě rozsahu pro příkaz (C++)](../cpp/range-based-for-statement-cpp.md) místo.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 **Syntaxe**  
  
```  
  
      for each (typeidentifierinexpression) {  
   statements  
}  
  
```  
  
 **Parametry**  
  
 `type`  
 Typ `identifier`.  
  
 `identifier`  
 Iterační proměnná, která představuje prvek kolekce.  Když `identifier` je [sledování Reference – operátor](../windows/tracking-reference-operator-cpp-component-extensions.md), můžete upravit elementu.  
  
 `expression`  
 Výraz pole nebo kolekce. Element kolekcí musí být tak, aby kompilátor můžete převeďte ho na `identifier` typu.  
  
 `statements`  
 Jeden nebo více příkazů ke spuštění.  
  
 **Poznámky**  
  
 `for each` Příkaz je použít k iteraci v rámci kolekce. Prvky v kolekci je možné měnit, ale nelze je přidávat ani odstraňovat.  
  
 *Příkazy* jsou provést pro každý prvek v poli nebo kolekce. Po dokončení iterace pro všechny elementy v kolekci, je ovládací prvek přenesen do příkazu, který odpovídá `for each` bloku.  
  
 `for each`a `in` jsou [kontextově závislá klíčová slova](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Další informace:  
  
-   [Iterování přes kolekci knihoven C++ Standard pomocí pro každou](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [Postupy: iterace v polích s výrazem for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [Postupy: iterace v obecné kolekci s výrazem for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [Postupy: iterace v uživatelem definované kolekci s výrazem for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak používat `for each` k iteraci v rámci řetězce.  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **Výstup**  
  
```Output  
abcd  
  
Testing  
```  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 **Poznámky**  
  
 Syntaxe CLR je stejný jako **všechny moduly runtime** syntaxe, s výjimkou následujícím způsobem.  
  
 *výraz*  
 Výraz spravovaného pole nebo kolekce. Element kolekcí musí být tak, aby kompilátor můžete převést z <xref:System.Object> k *identifikátor* typu.  
  
 *výraz* vyhodnocen jako typ, který implementuje <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, nebo typ, který definuje `GetEnumerator` metoda, že buď vrátí typ, který implementuje <xref:System.Collections.IEnumerator> nebo deklaruje všechny metody, které jsou definovány v `IEnumerator`.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak používat `for each` k iteraci v rámci řetězce.  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **Výstup**  
  
```Output  
abcd  
  
Testing   
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)