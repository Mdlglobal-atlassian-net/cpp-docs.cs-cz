---
title: "C2143 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2143
dev_langs: C++
helpviewer_keywords: C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fa7560b3b7d13beb416c2f500c0ab692e9f0d717
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2143"></a>C2143 chyby kompilátoru
Chyba syntaxe: chybějící 'token1' než 'token2.  
  
 Kompilátor očekávaný token konkrétní (to znamená, jazyk element a jiné než prázdné znaky) a místo toho nalézt další token.  
  
 Informace o této chybě dojde-li se při použití bloku try funkce, najdete v části [článku znalostní báze 241706](http://support.microsoft.com/kb/241706).  
  
 Zkontrolujte [referenční příručka jazyka C++](../../cpp/cpp-language-reference.md) k určení, kde je syntakticky správný kód. Protože kompilátor může ohlaste tuto chybu, jakmile narazí na řádku, který způsobuje, že problém, zkontrolujte několika řádků kódu, které předcházet chyba.  
  
 C2143 situace může nastat v různých situacích.  
  
 Může dojít, když operátor, kterou je možné získat název (`::`, `->`, a `.`) musí být následováno klíčové slovo `template`, protože v tomto příkladu:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 Ve výchozím nastavení, C++ předpokládá, že `Ty::PutFuncType` není šablonu; proto následující `<` interpretována jako méně – znaménko.  Se musí zjistit kompilátor explicitně který `PutFuncType` je šablona, aby ho mohou správně analyzovat lomená závorka. Chcete-li opravit tuto chybu, použijte `template` – klíčové slovo na název závislého typu, jak je vidět tady:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 C2143 může dojít, když **/CLR** se používá a `using` – direktiva obsahuje chybu syntaxe:  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 Může také nastat, když se pokoušíte kompilaci souboru zdrojového kódu pomocí syntaxe CLR bez použití také **/CLR**:  
  
```cpp  
// C2143b.cpp  
ref struct A {   // C2143 error compile with /clr  
   void Test() {}  
};  
  
int main() {  
   A a;  
   a.Test();  
}  
```  
  
 První neprázdný znak, který následuje `if` příkaz musí být levé závorky. Kompilátor nemůže překládat cokoliv jiného:  
  
```cpp  
// C2143c.cpp  
int main() {  
   int j = 0;  
  
   // OK  
   if (j < 25)  
      ;  
  
   if (j < 25)   // C2143  
}  
```  
  
 C2143 může dojít, když pravé složené závorce, závorky nebo středníkem chybí na řádku, kde je zjištěna chyba nebo na jeden z řádků právě výše:  
  
```cpp  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 Nebo pokud je v deklaraci třídy neplatnou značku:  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 Nebo Pokud štítek není připojen k příkazu. Pokud musíte umístit štítek samostatně, například na konci složené příkazu, připojte ji k null příkaz:  
  
```cpp  
// C2143f.cpp  
// compile with: /c  
void func1() {  
   // OK  
   end1:  
      ;  
  
   end2:   // C2143  
}  
```  
  
 Chyba se může objevit při nekvalifikované volání typu v standardní knihovna C++:  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 Nebo je chybějící `typename` – klíčové slovo:  
  
```cpp  
// C2143h.cpp  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
template <typename T>  
X<T>::Y X<T>::memFunc() {   // C2143  
// try the following line instead  
// typename X<T>::Y X<T>::memFunc() {  
   return Y();  
}  
```  
  
 Nebo pokud se pokusíte definovat explicitní vytvoření instance:  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 V programu C je nutné deklarovat proměnné na začátku funkce a nemůže být deklarována po funkce spouští instrukce bez deklarace.  
  
```C  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
```  
