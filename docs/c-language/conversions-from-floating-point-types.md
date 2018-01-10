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
ms.workload: cplusplus
ms.openlocfilehash: 4a95596b2c9e7312d4581d1a4c641c2466420158
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|**float**|`char`|Převést na **dlouho**; převést **dlouho** na`char`|  
|**float**|**short**|Převést na **dlouho**; převést **dlouho** k **krátké**|  
|**float**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|  
|**float**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k `unsigned` **krátké**|  
|**float**|`unsigned long`|Převést na **dlouho**; převést **dlouho** k `unsigned` **dlouho**|  
|**float**|**double**|Změnit interního vyjádření|  
|**float**|`long double`|Změnit interního vyjádření|  
|**double**|`char`|Převést na **float**; převést **float** na`char`|  
|**double**|**short**|Převést na **float**; převést **float** k **krátké**|  
|**double**|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|  
|**double**|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k **prostě bez znaménka**|  
|**double**|`unsigned long`|Převést na **dlouho**; převést **dlouho** k `unsigned` **dlouho**|  
|**double**|**float**|Představují jako **float**. Pokud **dvojité** hodnotu nelze reprezentovat přesně tak, jak **float**, dojde ke ztrátě přesnosti. Pokud hodnota je příliš velký a nelze je jako **float**, výsledkem nedefinovaný.|  
|`long double`|`char`|Převést na **float**; převést **float** na`char`|  
|`long double`|**short**|Převést na **float**; převést **float** k **krátké**|  
|`long double`|**long**|Zkraťte na desetinné čárky. Pokud je výsledek příliš velký a nelze je jako **dlouho**, výsledkem nedefinovaný.|  
|`long double`|**short bez znaménka**|Převést na **dlouho**; převést **dlouho** k `unsigned` **krátké**|  
|`long double`|`unsigned long`|Převést na **dlouho**; převést **dlouho** k `unsigned` **dlouho**|  
|`long double`|**float**|Představují jako **float**. Pokud **dvojité** hodnotu nelze reprezentovat přesně tak, jak **float**, dojde ke ztrátě přesnosti. Pokud hodnota je příliš velký a nelze je jako **float**, výsledkem nedefinovaný.|  
|`long double`|**double**|**Long double** hodnota je považována za **dvojité**.|  
  
 Převody z **float**, **dvojité**, nebo `long double` hodnoty k `unsigned long` nejsou přesné, pokud je větší než maximální kladnou hodnotu převáděné **dlouho**hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)