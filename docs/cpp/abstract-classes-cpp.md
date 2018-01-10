---
title: "Abstraktní třídy (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 23cdff4d0e2eb213a98b2e90d7df41af226edd86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="abstract-classes-c"></a>Abstraktní třídy (C++)
Abstraktní třídy fungují jako výrazy obecné koncepty, ze kterých lze odvodit více určité třídy. Nelze vytvořit objekt typu abstraktní třídy; Můžete však použít ukazatelů a odkazy na abstraktní typy tříd.  
  
 Třída, která obsahuje alespoň jeden čistý virtuální funkce považuje za abstraktní třídu. Třídy odvozené od abstraktní třídy musí implementovat čistou virtuální funkci nebo, příliš, jsou abstraktní třídy.  
  
 Virtuální funkce je deklarován jako "čisté" pomocí *čistý specifikátor* syntaxe (popsané v [třída implementace protokolu](http://msdn.microsoft.com/en-us/a319f1b3-05e8-400e-950a-1ca6eb105ab5)). Podívejte se na příklad uvedené v [virtuální funkce](../cpp/virtual-functions.md). Záměr třídy `Account` je poskytnout obecné funkce, ale objekty typu `Account` jsou příliš široké, aby byla užitečná. Proto `Account` je vhodným kandidátem pro abstraktní třídu:  
  
```  
// deriv_AbstractClasses.cpp  
// compile with: /LD  
class Account {  
public:  
   Account( double d );   // Constructor.  
   virtual double GetBalance();   // Obtain balance.  
   virtual void PrintBalance() = 0;   // Pure virtual function.  
private:  
    double _balance;  
};  
  
```  
  
 Jediným rozdílem mezi toto prohlášení a předchozí je, že `PrintBalance` je deklarovaný s čistě specifikátor (`= 0`).  
  
## <a name="restrictions-on-abstract-classes"></a>Omezení na abstraktní třídy  
 Abstraktní třídy nelze použít pro:  
  
-   Proměnné nebo členská data  
  
-   Typy argumentů  
  
-   Návratové typy funkcí  
  
-   Typy explicitních převodů  
  
 Dalším omezením je skutečnost, že pokud konstruktor abstraktní třídy zavolá čistě virtuální funkci, ať už přímo či nepřímo, není výsledek definován. Konstruktory a destruktory abstraktních tříd však mohou volat ostatní členské funkce.  
  
 Čistě virtuální funkce mohou být definovány pro abstraktní třídy, ale mohou být volány pouze pomocí této syntaxe:  
  
 *Název třídy abstraktní* `::` *název funkce***)**  
  
 Tato vlastnost je výhodná při návrhu hierarchií tříd, jejichž základní třídy zahrnují čistě virtuální destruktory, protože destruktory základních tříd jsou vždy volány během procesu ničení objektu. Podívejte se na následující příklad:  
  
```  
// Declare an abstract base class with a pure virtual destructor.  
// deriv_RestrictionsonUsingAbstractClasses.cpp  
class base {  
public:  
    base() {}  
    virtual ~base()=0;  
};  
  
// Provide a definition for destructor.  
base::~base() {}  
  
class derived:public base {  
public:  
    derived() {}  
    ~derived(){}  
};  
  
int main() {  
    derived *pDerived = new derived;  
    delete pDerived;  
}  
```  
  
 Je-li objekt, na nějž ukazuje ukazatel `pDerived`, odstraněn, je zavolán destruktor třídy `derived` a poté destruktor třídy `base`. Prázdná implementace čistě virtuální funkce zajišťuje existenci alespoň jedné její implementace.  
  
> [!NOTE]
>  V předchozím příkladu je čistě virtuální funkce `base::~base` zavolána implicitně z funkce `derived::~derived`. Čistě virtuální funkce lze zavolat i explicitně pomocí plně kvalifikovaného názvu členské funkce.  
  
## <a name="see-also"></a>Viz také  
 [Dědičnost](../cpp/inheritance-cpp.md)