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
ms.workload: cplusplus
ms.openlocfilehash: 8977c70fc2ebdc6e9fccf22e44a04afaceae1392
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|**Char**1|**short**|Rozšíření přihlášení|  
|**char**|**long**|Rozšíření přihlášení|  
|**char**|**unsigned char**|Zachovat vzor; bit horní ztratí funkce jako přihlašovací bit|  
|**char**|**short bez znaménka**|Přihlašovací rozšíření na **krátké**; převést **krátké** k **prostě bez znaménka**|  
|**char**|**dlouho bez znaménka**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|  
|**char**|**float**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **float**|  
|**char**|**double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**char**|**dlouhé double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**short**|**char**|Zachovat nejnižší bajtů|  
|**short**|**long**|Rozšíření přihlášení|  
|**short**|**unsigned char**|Zachovat nejnižší bajtů|  
|**short**|**short bez znaménka**|Zachovat bitový; bit horní ztratí funkce jako přihlašovací bit|  
|**short**|**dlouho bez znaménka**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **dlouho bez znaménka**|  
|**short**|**float**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **float**|  
|**short**|**double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**short**|**dlouhé double**|Přihlašovací rozšíření na **dlouho**; převést **dlouho** k **double**|  
|**long**|**char**|Zachovat nejnižší bajtů|  
|**long**|**short**|Zachovat nejnižší aplikace word|  
|**long**|**unsigned char**|Zachovat nejnižší bajtů|  
|**long**|**short bez znaménka**|Zachovat nejnižší aplikace word|  
|**long**|**dlouho bez znaménka**|Zachovat bitový; bit horní ztratí funkce jako přihlašovací bit|  
|**long**|**float**|Představují jako **float**. Pokud **dlouho** nemůže být reprezentovaný přesně, některé je ztráta přesnosti.|  
|**long**|**double**|Představují jako **dvojité**. Pokud **dlouho** nelze reprezentovat přesně tak jako **dvojité**, dojde ke ztrátě některých přesnost.|  
|**long**|**dlouhé double**|Představují jako **dvojité**. Pokud **dlouho** nelze reprezentovat přesně tak jako **dvojité**, dojde ke ztrátě některých přesnost.|  
  
 1. Všechny **char** položky předpokládat, že **char** ve výchozím nastavení je podepsaný typu.  
  
 **Konkrétní Microsoft**  
  
 Pro kompilátor C Microsoft 32bitové celé číslo se rovná **dlouho**. Převod **int** hodnota stejná jako u pokračuje **dlouho**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)