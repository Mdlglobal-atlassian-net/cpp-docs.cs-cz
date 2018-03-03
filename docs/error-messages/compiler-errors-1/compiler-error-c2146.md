---
title: "C2146 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2146
dev_langs:
- C++
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7da8021cabb5eab31ae12912374268ee4d7d24b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2146"></a>C2146 chyby kompilátoru
Chyba syntaxe: chybějící token před identifikátor "identifikátor"  
  
 Kompilátor očekává `token` a najít `identifier` místo.  Možné příčiny:  
  
1.  Došlo k chybě pravopis nebo malá a velká písmena.  
  
2.  V deklaraci identifikátor chybějící specifikátor typu.  
  
 Tato chyba může být způsobeno typografickou chybu. Chyba [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) obvykle předchází této chybě.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2146.  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## <a name="example"></a>Příklad  
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: chybí `typename` – klíčové slovo.  
  
 Následující ukázka zkompiluje v sadě Visual Studio .NET 2002 ale selže v sadě Visual Studio .NET 2003:  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## <a name="example"></a>Příklad  
 Zobrazí se také k této chybě v důsledku kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: explicitní specializací již nelze najít parametry šablony z primární šablony.  
  
 Použití `T` z primární šablony není povolen v explicitní specializace. Pro kód platný v verze Visual C++ pro Visual Studio .NET 2003 a sady Visual Studio .NET nahraďte všechny výskyty parametr šablony v specializace explicitně speciálním typem.  
  
 Následující ukázka zkompiluje v sadě Visual Studio .NET ale selže v sadě Visual Studio .NET 2003:  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```