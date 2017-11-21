---
title: "chráněné (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: protected_cpp
dev_langs: C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1996ce93be7fc5f722936dee0f04923cafa5d767
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Poznámky  
 `protected` – Klíčové slovo určuje přístupu ke členům třídy v *seznam členů* až další specifikátor přístupu (**veřejné** nebo `private`) nebo na konci definici třídy. Členy třídy deklarované jako `protected` lze použít pouze následujícími:  
  
-   členskými funkcemi třídy, která původně deklarovala tyto členy,  
  
-   přáteli třídy, která původně deklarovala tyto členy,  
  
-   třídami odvozenými s veřejnou nebo chráněnou přístupností z této třídy, která původně deklarovala tyto členy,  
  
-   přímými soukromě odvozenými třídami, které mají také soukromý přístup k chráněným členům.  
  
 Pokud klíčové slovo `protected` předchází název základní třídy, určuje, že jsou veřejné a chráněné členy základní třídy chráněnými členy odvozených tříd.  
  
 Chráněné členy nejsou jako soukromé jako `private` členy, které jsou přístupné pouze pro členy třídy, ve které jsou deklarovány, ale nejsou jako veřejné jako **veřejné** členy, které jsou k dispozici v žádné funkce.  
  
 Chránění členové, které jsou také deklarované jako **statické** jsou přístupné pro všechny funkce známý nebo odvozené třídy. Chránění členové, které nejsou deklarované jako **statické** jsou k dispozici přátelům a členské funkce v odvozené třídě pouze prostřednictvím ukazatel na odkaz na nebo objekt odvozené třídy.  
  
 Související informace najdete v tématu [friend](../cpp/friend-cpp.md), [veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md)a přístup ke členu tabulkou v [řízení přístupu ke členům třídy](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Specifické pro možnost /clr  
 Typy CLR C++ přístup specifikátor klíčová slova (**veřejné**, `private`, a `protected`) může ovlivnit viditelnost typy a metody s ohledem na sestavení. Další informace najdete v tématu [řízení přístupu ke členu](member-access-control-cpp.md).  
  
> [!NOTE]
>  Soubory kompilovat s [/LN](../build/reference/ln-create-msil-module.md) nemá vliv toto chování. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.  
  
## <a name="end-clr-specific"></a>Specifické pro možnost END /clr  
  
## <a name="example"></a>Příklad  
  
```  
// keyword_protected.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class X {  
public:  
   void setProtMemb( int i ) { m_protMemb = i; }  
   void Display() { cout << m_protMemb << endl; }  
protected:  
   int  m_protMemb;  
   void Protfunc() { cout << "\nAccess allowed\n"; }  
} x;  
  
class Y : public X {  
public:  
   void useProtfunc() { Protfunc(); }  
} y;  
  
int main() {  
   // x.m_protMemb;         error, m_protMemb is protected  
   x.setProtMemb( 0 );   // OK, uses public access function  
   x.Display();  
   y.setProtMemb( 5 );   // OK, uses public access function  
   y.Display();  
   // x.Protfunc();         error, Protfunc() is protected  
   y.useProtfunc();      // OK, uses public access function  
                        // in derived class  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení přístupu ke členům třídy](member-access-control-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)