---
title: "Převody z podepsaných integrálních typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ccda8d6fa2573245f34a38f327395955bf92fdc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-signed-integral-types"></a>Převody z podepsaných integrálních typů
Když znaménkem je převést na celé číslo bez znaménka s stejné nebo větší velikosti a není záporná hodnota podepsaná hodnota typu integer, hodnota je beze změny. Převod přišla tím, že přihlašovací rozšíří číslo se znaménkem. Znaménkem jsou převedeny na kratší znaménkem zkrácením nejvyšších bitů. Výsledek interpretována jako hodnotu bez znaménka, jak je znázorněno v tomto příkladu.  
  
```  
int i = -3;  
unsigned short u;  
  
u = i;   
printf_s( "%hu\n", u );  // Prints 65533  
  
```  
  
 Žádné informace bude ztracena, jakmile znaménkem jsou převedeny na hodnotu plovoucí s tím rozdílem, že některé přesnost může dojít ke ztrátě při **dlouho int** nebo **nepodepsané dlouho int** je převést hodnotu **float** hodnotu.  
  
 Následující tabulka shrnuje převody z podepsaných integrálních typů. Tato tabulka předpokládá, že **char** ve výchozím nastavení je podepsaný typu. Pokud použijete možnost kompilaci, chcete-li změnit výchozí nastavení pro **char** převody uvedenému v typu na nepodepsané, [převody z nepodepsaných integrálních typů](../c-language/conversions-from-unsigned-integral-types.md) tabulky pro **nepodepsané char**  typu použít místo převody v následující tabulce, převody z podepsané integrálních typů.  
  
### <a name="conversions-from-signed-integral-types"></a>Převody z podepsaných integrálních typů  
  
|From|Chcete-li|Metoda|  
|----------|--------|------------|  
|**Char**1|**krátký**|Rozšíření přihlášení|  
|**Char**|**dlouhá**|Rozšíření přihlášení|  
|**Char**|**unsigned char**|Zachovat vzor; bit horní ztratí funkce jako přihlašovací bit|  
|**Char**|**short bez znaménka**|Přihlašovací rozšíření na **krátké**; převést **krátké** k **prostě bez znaménka**|  
|**Char**|**dlouho bez znaménka**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|  
|**Char**|**plovoucí desetinná čárka**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **float**|  
|**Char**|**Double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**Char**|**dlouhé double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**krátký**|**Char**|Zachovat nejnižší bajtů|  
|**krátký**|**dlouhá**|Rozšíření přihlášení|  
|**krátký**|**unsigned char**|Zachovat nejnižší bajtů|  
|**krátký**|**short bez znaménka**|Zachovat bitový; bit horní ztratí funkce jako přihlašovací bit|  
|**krátký**|**dlouho bez znaménka**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|  
|**krátký**|**plovoucí desetinná čárka**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **float**|  
|**krátký**|**Double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**krátký**|**dlouhé double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**dlouhá**|**Char**|Zachovat nejnižší bajtů|  
|**dlouhá**|**krátký**|Zachovat nejnižší aplikace word|  
|**dlouhá**|**unsigned char**|Zachovat nejnižší bajtů|  
|**dlouhá**|**short bez znaménka**|Zachovat nejnižší aplikace word|  
|**dlouhá**|**dlouho bez znaménka**|Zachovat bitový; bit horní ztratí funkce jako přihlašovací bit|  
|**dlouhá**|**plovoucí desetinná čárka**|Představují jako **float**. Pokud **dlouho** nemůže být reprezentovaný přesně, některé je ztráta přesnosti.|  
|**dlouhá**|**Double**|Představují jako **dvojité**. Pokud **dlouho** nelze reprezentovat přesně tak jako **dvojité**, dojde ke ztrátě některých přesnost.|  
|**dlouhá**|**dlouhé double**|Představují jako **dvojité**. Pokud **dlouho** nelze reprezentovat přesně tak jako **dvojité**, dojde ke ztrátě některých přesnost.|  
  
 1. Všechny **char** položky předpokládat, že **char** ve výchozím nastavení je podepsaný typu.  
  
 **Konkrétní Microsoft**  
  
 Pro kompilátor C Microsoft 32bitové celé číslo se rovná **dlouho**. Převod **int** hodnota stejná jako u pokračuje **dlouho**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)