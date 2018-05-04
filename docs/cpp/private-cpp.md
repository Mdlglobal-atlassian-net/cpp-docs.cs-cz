---
title: soukromé (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- private_cpp
dev_langs:
- C++
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb0b8c748a3cf92faae451ab024d5592bb24b47
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="private-c"></a>private (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## <a name="remarks"></a>Poznámky  
 Při předchozím seznam členy třídy, `private` – klíčové slovo určuje, že jsou přístupné pouze z členských funkcí a přátel třídy členů. To platí pro všechny členy deklarovaný až další specifikátor přístupu nebo na konci třídy.  
  
 Při předchozím název základní třídy, `private` – klíčové slovo určuje, že veřejné a chráněné členy základní třídy jsou soukromé členy odvozené třídy.  
  
 Výchozí úroveň přístupu členů v třídě je soukromé. Výchozí úroveň přístupu členů ve struktuře nebo sjednocení je veřejný.  
  
 Pro třídy privátní a veřejné pro struktury je výchozí přístup základní třídy. Sjednocení nemůžou mít základní třídy.  
  
 Související informace najdete v tématu [friend](../cpp/friend-cpp.md), [veřejné](../cpp/public-cpp.md), [chráněné](../cpp/protected-cpp.md)a přístup ke členu tabulkou v [řízení přístupu ke členům třídy](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>Specifické pro možnost /clr  
 Typy CLR C++ přístup specifikátor klíčová slova (**veřejné**, `private`, a `protected`) může ovlivnit viditelnost typy a metody s ohledem na sestavení. Další informace najdete v tématu [řízení přístupu ke členu](member-access-control-cpp.md).  
  
> [!NOTE]
>  Soubory kompilovat s [/LN](../build/reference/ln-create-msil-module.md) nemá vliv toto chování. V tomto případě budou všechny spravované třídy (veřejné nebo soukromé) viditelné.  
  
## <a name="end-clr-specific"></a>Specifické pro možnost END /clr  
  
## <a name="example"></a>Příklad  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení přístupu ke členům třídy](member-access-control-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)