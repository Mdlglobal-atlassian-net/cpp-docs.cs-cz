---
title: "Dědičnost (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 50b6b180a6def741daa47a5054f1c61d3265ebd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inheritance--c"></a>Dědičnost (C++)
Tento oddíl vysvětluje, jak lze pomocí odvozených tříd vytvářet rozšiřitelné programy.  
  
## <a name="overview"></a>Přehled  
 Nové třídy mohou být odvozen z existujících tříd pomocí mechanismus názvem "dědičnosti" (počínaje informace v tématu [jedna dědičnost](../cpp/single-inheritance.md)). Třídy, které jsou používány pro odvození, se nazývají „základní třídy“ určitých odvozených tříd. Odvozená třída je deklarována pomocí následující syntaxe:  
  
```  
 class Derived : [virtual] [access-specifier] Base  
{  
   // member list  
};  
 class Derived : [virtual] [access-specifier] Base1,  
 [virtual] [access-specifier] Base2, . . .  
{  
   // member list  
};  
```  
  
 Po značce (názvu) třídy zadejte dvojtečku následovanou seznamem základních specifikací.  Základní třídy s těmito názvy musí být deklarovány dříve.  Základní specifikace může obsahovat specifikátor přístupu, který je jedním z klíčových slov **veřejné**, `protected` nebo `private`.  Tyto specifikátory přístupu zadejte před název základní třídy a platí pouze pro tuto základní třídu.  Tyto specifikátory řídí oprávnění odvozené třídy k použití členů základní třídy.  V tématu [řízení přístup ke členu](../cpp/member-access-control-cpp.md) informace o přístup na členy základní třídy.  Pokud je specifikátor přístupu vynechán, je přístup k této základní třídě považován za `private`.  Základní specifikace může obsahovat klíčové slovo **virtuální** udávajících virtuální dědičnost.  Toto klíčové slovo lze zadat před nebo za specifikátor přístupu, pokud existuje.  Pokud je použita virtuální dědičnost, základní třída se nazývá virtuální základní třída.  
  
 Lze zadat více základních tříd oddělených čárkami.  Pokud jediná základní třída není zadaný, je model dědičnosti [jedna dědičnost](../cpp/single-inheritance.md). Pokud je zadán více než jedné základní třídy, se nazývá model dědičnosti [vícenásobná dědičnost](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca),  
  
 V následujících tématech jsou zahrnuty:  
  
-   [Jedna dědičnost](../cpp/single-inheritance.md)  
  
-   [Vícenásobná dědičnost](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)  
  
-   [Vícenásobné třídy base](../cpp/multiple-base-classes.md)  
  
-   [Virtuální funkce](../cpp/virtual-functions.md)  
  
-   [Explicitní přepsání](../cpp/explicit-overrides-cpp.md)  
  
-   [Abstraktní třídy](../cpp/abstract-classes-cpp.md)  
  
-   [Souhrn pravidel rozsahu](../cpp/summary-of-scope-rules.md)  
  
 [__Super](../cpp/super.md) a [__interface](../cpp/interface.md) klíčová slova jsou popsané v této části.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)