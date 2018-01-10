---
title: "Převody přetypování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data type conversion [C++], type-cast conversions
- conversions [C++], type-cast
- type casts
- explicit type conversions
- type casts [C++], about type-cast conversion
- type-cast conversions [C++]
ms.assetid: 57ab5902-f12f-4326-a2f6-6282f1d4025a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f402eb49e86c8d6d3ce6c332172375125f577a2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="type-cast-conversions"></a>Převody přetypování
Přetypování typu můžete explicitně převést typy.  
  
 **Syntaxe**  
  
 *výraz CAST*:  
 *Unární výraz*  
  
 **(***název typu***)***výraz cast*   
  
 *Název typu*:  
 *specifikátor. kvalifikátor seznamu abstraktní – deklarátor* opt  
  
 *Název typu* typu a *výraz cast* je hodnota má být převeden na typu. Výraz s přetypování není l hodnota. *Výraz cast* je převést, jako by měl přiřazený k proměnné typu *název typu*. Převod pravidel pro přiřazení (uvedených v [převody přiřazení](../c-language/assignment-conversions.md)) použít na typ přetypování také. Následující tabulka uvádí typy, které lze převést do daného typu.  
  
### <a name="legal-type-casts"></a>Přetypování právní typu  
  
|Určení typů|Potenciální zdroje|  
|-----------------------|-----------------------|  
|Celočíselné typy|Všechny typ celé číslo nebo s plovoucí desetinnou čárkou nebo ukazatel na objekt|  
|S plovoucí desetinnou čárkou|Žádný typ, aritmetické|  
|Ukazatel na objekt, nebo (**void \*** )|Libovolného typu integer, (**void \*** ), ukazatel na objekt nebo ukazatel na funkci|  
|Ukazatel na funkci|Žádný typ, integrální, ukazatel na objekt nebo ukazatel na funkci|  
|Struktury, sjednocení nebo pole|Žádné|  
|Typ void|Jakýkoli typ|  
  
 Všechny identifikátor lze převést na `void` typu. Ale pokud typ zadaný v výraz přetypování není `void`, potom se identifikátor přetypovat na že nemůže být typu `void` výraz. Jakýkoli výraz lze převést na `void`, ale výraz typu `void` nelze převést na jiný typ. Například funkce s `void` vrátí typ nemůže mít jeho vraťte se k jinému typu přetypování.  
  
 Všimněte si, že **void \***  výraz má ukazatel typu `void`, ne typ `void`. Pokud je objekt přetypovat `void` typu, výsledný výraz nelze přiřadit k žádné položky. Podobně objekt přetypování není přijatelná l hodnota, proto nelze realizovat žádná přiřazení na objekt přetypování.  
  
 **Konkrétní Microsoft**  
  
 Přetypování může být výraz l-value tak dlouho, dokud velikost identifikátor se nemění. Informace na výrazy hodnot l najdete v tématu [L-Value a R-Value výrazy](../c-language/l-value-and-r-value-expressions.md).  
  
 **Konkrétní Microsoft END**  
  
 Můžete převést na typ výrazu `void` s přetypování, ale výsledný výraz lze použít pouze kde hodnotu se nevyžaduje. Ukazatele na objekt převést na **void \***  a vrátí zpět na původní typ na původní hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Převody typu](../c-language/type-conversions-c.md)