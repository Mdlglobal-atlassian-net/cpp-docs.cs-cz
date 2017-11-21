---
title: "Převody z typů s plovoucí desetinnou čárkou | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4974edd25d0fcdd8d990b60459517bb1148c74ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou
A **float** převést na hodnotu **dvojité** nebo `long double`, nebo **dvojité** převést na `long double`, zde nevyskytlo žádná změna v poli hodnota. A **dvojité** převést na hodnotu **float** hodnota je reprezentována přesně, pokud je to možné. Přesnost může dojít ke ztrátě, pokud hodnota není možné vyjádřit přesně. Pokud je výsledek mimo rozsah, chování nedefinovaný. V tématu [omezení Floating-Point konstanty](../c-language/limits-on-floating-point-constants.md) pro rozsah typů s plovoucí desetinnou čárkou.  
  
 Je převést hodnotu plovoucí celočíselné hodnoty podle první převod na **dlouho**, pak z **dlouho** hodnotu s konkrétní hodnotou integrální. Za desetinnou hodnotu s plovoucí se zahodí v převod na **dlouho**. Pokud je stále výsledek příliš velký pro uložení do **dlouho**, výsledek převodu není definován.  
  
 **Konkrétní Microsoft**  
  
 Při převodu **dvojité** nebo `long double` číslo s plovoucí desetinnou čárkou menší na dvě desetinná čísla, hodnota proměnné s plovoucí desetinnou čárkou se zkrátí směrem k nule, když dojde podtečení. Přetečení způsobí, že chyba spuštění. Všimněte si, že mapuje kompilátoru Microsoft C `long double` na typ **dvojité**.  
  
 **Konkrétní Microsoft END**  
  
 Následující tabulka shrnuje převody z typů s plovoucí čárkou.  
  
### <a name="conversions-from-floating-point-types"></a>Převody z typů s plovoucí desetinnou čárkou  
  
|From|Chcete-li|Metoda|  
|----------|--------|------------|  
|**plovoucí desetinná čárka**|`char`|Převést na **dlouho**; převést **dlouho** na`char`|  
|**plovoucí desetinná čárka**|**krátký**|Převést na **dlouho**; převést **dlouho** k **krátké**|  
|**plovoucí desetinná čárka**|**dlouhá**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|  
|**plovoucí desetinná čárka**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k `unsigned` **krátké**|  
|**plovoucí desetinná čárka**|`unsigned long`|Převést na **dlouho**; převést **dlouho** k `unsigned` **dlouho**|  
|**plovoucí desetinná čárka**|**Double**|Změnit interního vyjádření|  
|**plovoucí desetinná čárka**|`long double`|Změnit interního vyjádření|  
|**Double**|`char`|Převést na **float**; převést **float** na`char`|  
|**Double**|**krátký**|Převést na **float**; převést **float** k **krátké**|  
|**Double**|**dlouhá**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|  
|**Double**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k **prostě bez znaménka**|  
|**Double**|`unsigned long`|Převést na **dlouho**; převést **dlouho** k `unsigned` **dlouho**|  
|**Double**|**plovoucí desetinná čárka**|Představují jako **float**. Pokud **dvojité** hodnotu nelze reprezentovat přesně tak, jak **float**, dojde ke ztrátě přesnosti. Pokud hodnota je příliš velký a nelze je jako **float**, výsledkem nedefinovaný.|  
|`long double`|`char`|Převést na **float**; převést **float** na`char`|  
|`long double`|**krátký**|Převést na **float**; převést **float** k **krátké**|  
|`long double`|**dlouhá**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|  
|`long double`|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k `unsigned` **krátké**|  
|`long double`|`unsigned long`|Převést na **dlouho**; převést **dlouho** k `unsigned` **dlouho**|  
|`long double`|**plovoucí desetinná čárka**|Představují jako **float**. Pokud **dvojité** hodnotu nelze reprezentovat přesně tak, jak **float**, dojde ke ztrátě přesnosti. Pokud hodnota je příliš velký a nelze je jako **float**, výsledkem nedefinovaný.|  
|`long double`|**Double**|**Long double** hodnota je považována za **dvojité**.|  
  
 Převody z **float**, **dvojité**, nebo `long double` hodnoty k `unsigned long` nejsou přesné, pokud je větší než maximální kladnou hodnotu převáděné **dlouho**hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)