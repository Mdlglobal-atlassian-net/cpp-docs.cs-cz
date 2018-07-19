---
title: override – specifikátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50ffc096cc710f4028c7effc2dda8822f077f29
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940651"
---
# <a name="override-specifier"></a>override – specifikátor
Můžete použít **přepsat** – klíčové slovo k určení členských funkcí, které přepíšou virtuální funkci v základní třídě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
function-declaration override;  
```  
  
## <a name="remarks"></a>Poznámky  
 **Přepsat** je kontextový a má zvláštní význam pouze tehdy, když se používá po deklaraci členské funkce; v opačném případě to není rezervované klíčové slovo.  
  
## <a name="example"></a>Příklad  
 Použití **přepsat** zabránit neúmyslnému chování dědičnosti ve vašem kódu. Následující příklad ukazuje, kde bez použití **přepsat**, nemusí je žádoucí chování členské funkce odvozené třídy. Kompilátor nebude posílat žádné chyby pro tento kód.  
  
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
  
 Při použití **přepsat**, kompilátor vygeneruje chyby tichého vytváření nové členské funkce.  
  
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
  
 Chcete-li určit, že funkce nelze přepsat a že nelze dědit třídy, použijte [konečné](../cpp/final-specifier.md) – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 [final – specifikátor](../cpp/final-specifier.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 