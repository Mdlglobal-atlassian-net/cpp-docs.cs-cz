---
title: "Přetypování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 85f26c61e1e4fa996f73b4f61f4f961ba59dec98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="casting"></a>Přetypování
Jazyk C++ udává, že je-li třída odvozena ze základní třídy obsahující virtuální funkce, lze ukazatel na typ této základní třídy použít k volání implementací virtuálních funkcí umístěných v objektu odvozené třídy. Třída obsahující virtuální funkce je někdy označována jako „polymorfní třída“.  
  
 Jelikož odvozená třída obsahuje všechny definice všech základních tříd, z nichž byla odvozena, lze ukazatel přetypovat na libovolnou z těchto tříd vyskytujících se výše v jejich hierarchii. Je-li dán ukazatel na základní třídu, může být bezpečné přetypovat ukazatel na třídu umístěnou v hierarchii níže. Přetypování je bezpečné, pokud objekt, na který ukazatel ukazuje, je ve skutečnosti typem odvozeným ze základní třídy. V takovém případě se skutečný objekt nazývá „kompletním objektem“. O ukazateli na základní třídu se říká, že ukazuje na „podobjekt“ kompletního objektu. Vezměte v úvahu například hierarchii tříd znázorněnou na následujícím obrázku.  
  
 ![Třídy hierarchie](../cpp/media/vc38zz1.gif "vc38ZZ1")  
Hierarchie tříd  
  
 Objekt typu `C` lze vizualizovat tak, jak ukazuje následující obrázek.  
  
 ![Třída C s dílčí & č. 45; objekty B a](../cpp/media/vc38zz2.gif "vc38ZZ2")  
Třída C s podobjekty B a A  
  
 Je-li dána instance třídy `C`, existuje podobjekt `B` a podobjekt `A`. Instance třídy `C`, včetně podobjektů `A` a `B`, je „kompletním objektem“.  
  
 Pomocí informací o typu modulu runtime lze zkontrolovat, zda ukazatel skutečně ukazuje na kompletní objekt a lze jej bezpečně přetypovat tak, aby ukazoval na jiný objekt ve své hierarchii. [Dynamic_cast](../cpp/dynamic-cast-operator.md) operátor lze provádět tyto typy přetypování. Operátor provádí za běhu také kontroly potřebné k zajištění bezpečnosti operace.  
  
 Pro převod typů nonpolymorphic, můžete použít [static_cast](../cpp/static-cast-operator.md) – operátor (v tomto tématu najdete vysvětlení rozdílu mezi statickým a dynamickým přetypování převody a kdy je vhodné používat každý).  
  
 Tato část obsahuje následující témata:  
  
-   [Operátory přetypování](../cpp/casting-operators.md)  
  
-   [Informace běhového typu](../cpp/run-time-type-information.md)  
  
## <a name="see-also"></a>Viz také  
 [Výrazy](../cpp/expressions-cpp.md)