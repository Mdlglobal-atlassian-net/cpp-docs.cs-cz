---
title: Public (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- public_cpp
dev_langs:
- C++
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff41d2b12f43deabd82538a3e2fb10eb35ead16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="public-c"></a>public (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
public:  
   [member-list]  
public base-class  
```  
  
## <a name="remarks"></a>Poznámky  
 Při předchozím seznam členy třídy, **veřejné** – klíčové slovo určuje, že členů, jsou k dispozici žádné funkce. To platí pro všechny členy deklarovaný až další specifikátor přístupu nebo na konci třídy.  
  
 Při předchozím název základní třídy, **veřejné** – klíčové slovo určuje, že jsou veřejné veřejné a chráněné členy základní třídy a chráněné členy, v uvedeném pořadí, odvozené třídy.  
  
 Výchozí úroveň přístupu členů v třídě je soukromé. Výchozí úroveň přístupu členů ve struktuře nebo sjednocení je veřejný.  
  
 Pro třídy privátní a veřejné pro struktury je výchozí přístup základní třídy. Sjednocení nemůžou mít základní třídy.  
  
 Další informace najdete v tématu [privátní](../cpp/private-cpp.md), [chráněné](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)a přístup ke členu tabulkou v [řízení přístupu ke členům třídy](member-access-control-cpp.md) .  
  
## <a name="clr-specific"></a>Specifické pro možnost /clr  
 Typy CLR C++ přístup specifikátor klíčová slova (**veřejné**, `private`, a `protected`) může ovlivnit viditelnost typy a metody s ohledem na sestavení. Další informace najdete v tématu [řízení přístupu ke členu](member-access-control-cpp.md).  
  
> [!NOTE]
>  Soubory kompilovat s [/LN](../build/reference/ln-create-msil-module.md) nemá vliv toto chování. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.  
  
## <a name="end-clr-specific"></a>Specifické pro možnost END /clr  
  
## <a name="example"></a>Příklad  
  
```  
// keyword_public.cpp  
class BaseClass {  
public:  
   int pubFunc() { return 0; }  
};  
  
class DerivedClass : public BaseClass {};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   aBase.pubFunc();       // pubFunc() is accessible   
                          //    from any function  
   aDerived.pubFunc();    // pubFunc() is still public in   
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení přístupu ke členům třídy](member-access-control-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)