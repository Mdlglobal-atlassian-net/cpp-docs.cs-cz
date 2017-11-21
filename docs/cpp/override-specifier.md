---
title: "override – specifikátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c182404618e36fe3b7fa0ed72d3a2e39569f7ac0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="override-specifier"></a>override – specifikátor
Můžete použít `override` – klíčové slovo k určení členské funkce, které přepsat virtuální funkce v základní třídě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
function-declaration override;  
```  
  
## <a name="remarks"></a>Poznámky  
 `override`Kontextová a má zvláštní význam jenom v případě, že se používá po deklaraci členské funkce; jinak není rezervované klíčové slovo.  
  
## <a name="example"></a>Příklad  
 Použití `override` pomáhá zabránit nechtěnému dědičnosti chování ve vašem kódu. Následující příklad ukazuje, kde, bez použití `override`, nemusí byla určena chování funkce člen odvozené třídy. Kompilátor není emitování všechny chyby pro tento kód.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA(); // ok, works as intended  
  
    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not  
                          // override BaseClass::funcB() const and it is a new member function  
  
    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different  
                                      // parameter type than BaseClass::funcC(int), so  
                                      // DerivedClass::funcC(double) is a new member function  
  
};  
  
```  
  
 Při použití `override`, kompilátor generuje chyby místo bezobslužně vytvoření nového člena funkce.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA() override; // ok  
  
    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not   
                                   // override BaseClass::funcB() const  
  
    virtual void funcC( double = 0.0 ) override; // compiler error:   
                                                 // DerivedClass::funcC(double) does not   
                                                 // override BaseClass::funcC(int)  
  
    void funcD() override; // compiler error: DerivedClass::funcD() does not   
                           // override the non-virtual BaseClass::funcD()  
};  
  
```  
  
 Chcete-li určit, že nejde přepsat, funkce a že nelze zděděné třídy, použijte [konečné](../cpp/final-specifier.md) – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [final – specifikátor](../cpp/final-specifier.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 