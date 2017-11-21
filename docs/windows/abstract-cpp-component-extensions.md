---
title: "abstraktní (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs: C++
helpviewer_keywords: abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2f4a679b6945c98d591d3fbd64a6934ea17b0e88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="abstract--c-component-extensions"></a>abstract (rozšíření komponent C++)
`abstract` – Klíčové slovo deklaruje buď:  
  
-   Typ lze použít jako základní typ, ale samotný datový typ nelze vytvořit instanci.  
  
-   Členské funkce typ lze definovat pouze v odvozeném typu.  
  
## <a name="all-platforms"></a>Všechny platformy  
 **Syntaxe**  
  
```  
  
      class-declaration  
      class-identifier  
      abstract {}  
virtualreturn-typemember-function-identifier() abstract ;  
  
```  
  
 **Poznámky**  
  
 První příklad syntaxe deklaruje třídu jako abstraktní. *Deklaraci třídy* součástí může být buď nativní deklarace C++ (`class` nebo `struct`), nebo deklaraci rozšíření C++ (`ref class` nebo `ref struct`) Pokud **/ZW** nebo **/CLR** – možnost kompilátoru je zadán.  
  
 Druhý příklad syntaxe deklaruje virtuální členské funkce jako abstraktní. Deklarování abstraktní funkce je stejný jako deklarace ho čistou virtuální funkci. Deklarace členské funkce abstraktní také způsobí, že nadřazených tříd deklarovat abstraktní.  
  
 `abstract` – Klíčové slovo je podporována v nativní a specifické pro platformu kódu; to znamená, ji můžete zkompilovat bez ohledu **/ZW** nebo **/CLR** – možnost kompilátoru.  
  
 Pokud je abstraktní s typem, můžete zjistit v době kompilace `__is_abstract(type)` typ znak. Další informace najdete v tématu [podpora kompilátoru pro typové vlastnosti](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `abstract` – Klíčové slovo je kontextová přepsání specifikátor. Další informace o kontextově závislá klíčová slova, najdete v části [klíčová slova Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md). Další informace o specifikátorů override najdete v tématu [postupy: deklarace specifikátorů Override v nativní kompilaci](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 Další informace najdete v tématu [Ref třídy a struktury](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu vygeneruje chybu, protože třída `X` je označena `abstract`.  
  
```  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 **Příklad**  
  
 Následující příklad kódu vygeneruje chybu, protože ji vytvoří nativní třídu, která je označena `abstract`. Tato chyba nastane, bez ohledu **/CLR** – možnost kompilátoru.  
  
```  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
  
```  
  
 **Příklad**  
  
 Následující příklad kódu vygeneruje chybu, protože funkce `f` obsahuje definice, ale je označen `abstract`. Poslední příkaz příklad ukazuje, že je ekvivalentní deklarace čistou virtuální funkci deklarace abstraktní virtuální funkce.  
  
```  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)