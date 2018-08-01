---
title: chráněné (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- protected_cpp
dev_langs:
- C++
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68cf69cd0c14d56c75a2c67d4369264e7a2ee440
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406169"
---
# <a name="protected-c"></a>protected (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
protected:  
   [member-list]  
protected base-class  
```  
  
## <a name="remarks"></a>Poznámky  
 **Chráněné** – klíčové slovo určuje přístup k členům třídy v *seznam členů* až do dalšího specifikátoru přístupu (**veřejné** nebo **privátní**) nebo na konci definice třídy. Členy třídy deklarované jako **chráněné** mohou být používány pouze následující:  
  
-   členskými funkcemi třídy, která původně deklarovala tyto členy,  
  
-   přáteli třídy, která původně deklarovala tyto členy,  
  
-   třídami odvozenými s veřejnou nebo chráněnou přístupností z této třídy, která původně deklarovala tyto členy,  
  
-   přímými soukromě odvozenými třídami, které mají také soukromý přístup k chráněným členům.  
  
 Když předchází název základní třídy **chráněné** – klíčové slovo určuje, že jsou veřejné a chráněné členy základní třídy chráněnými členy odvozených tříd.  
  
 Chráněné členy nejsou tak soukromé jako **privátní** členy, které jsou k dispozici pouze pro členy třídy, ve kterém jsou deklarovány, ale nejsou veřejné jako **veřejné** členy, které jsou k dispozici v všechny funkce.  
  
 Chráněné členy, které jsou také deklarovány jako **statické** jsou k dispozici přátelům nebo členským funkcím odvozené třídy. Chráněné členy, které nejsou deklarovány jako **statické** jsou k dispozici přátelům a členským funkcím v odvozené třídě pouze prostřednictvím ukazatel, odkaz nebo objektu odvozené třídy.  
  
 Související informace naleznete v tématu [friend](../cpp/friend-cpp.md), [veřejné](../cpp/public-cpp.md), [privátní](../cpp/private-cpp.md)a v tabulce přístupu ke členům v [řízení přístupu ke členům třídy](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Specifické pro možnost /clr  
 U typů modulu CLR, klíčová slova specifikátoru přístupu jazyka C++ (**veřejné**, **privátní**, a **chráněné**) může ovlivnit viditelnost typů a metod s ohledem na sestavení. Další informace najdete v tématu [řízení přístupu ke členu](member-access-control-cpp.md).  
  
> [!NOTE]
>  Souborů zkompilovaných pomocí [/LN](../build/reference/ln-create-msil-module.md) toto chování netýká. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.  
  
## <a name="end-clr-specific"></a>Specifické pro možnost END /clr  
  
## <a name="example"></a>Příklad  
  
```cpp 
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
  
## <a name="see-also"></a>Viz také:  
 [Řízení přístupu ke členům třídy](member-access-control-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)