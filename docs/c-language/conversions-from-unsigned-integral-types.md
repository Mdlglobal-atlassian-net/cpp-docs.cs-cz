---
title: "Převody z nepodepsaných integrálních typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15e1bc61e9b15293290098b9414642d8edf46707
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-unsigned-integral-types"></a>Převody z nepodepsaných integrálních typů
Celé číslo bez znaménka jsou převedeny na kratší číslo bez znaménka nebo podepsaný zkrácením nejvyšších bitů, nebo již nepodepsaný nebo podepsaný celočíselná a tím, že rozšíří nula (viz [převody z nepodepsaných integrálních typů](#_clang_table_4..3) tabulky).  
  
 Pokud hodnotu s integrální typ převeden na znaménkem s menší velikostí, nebo celé číslo bez znaménka jsou převedeny na jeho odpovídající číslo se znaménkem, hodnota je beze změny, pokud může být reprezentován v nového typu. Ale hodnota představuje změny, pokud je bit přihlašovací nastavený, jako v následujícím příkladu.  
  
```  
int j;  
unsigned short k = 65533;  
  
j = k;  
printf_s( "%hd\n", j );   // Prints -3  
```  
  
 Pokud není možné vyjádřit, výsledkem je, definované implementací. V tématu [převody přetypování](../c-language/type-cast-conversions.md) informace o zpracování kompilátoru Microsoft C degradace celých čísel. Stejné výsledky chování z převod celé číslo nebo přetypování na celé číslo.  
  
 Nepodepsané hodnoty se převedou způsobem, který zachovává jejich hodnota a není reprezentovat přímo C. Jedinou výjimkou je převod z `unsigned long` k **float**, který ztratí maximálně nejnižší bits. Jinak je zachovaná hodnotu, podepsaný držitelem nebo bez znaménka. Pokud se hodnota typu integrální jsou převedeny na plovoucí a hodnota je mimo rozsah reprezentovat, výsledkem je definovaný. (Viz [úložiště základních typů](../c-language/storage-of-basic-types.md) informace o rozsahu pro typy s plovoucí desetinnou čárkou a integrální.)  
  
 Následující tabulka shrnuje převody z nepodepsaných integrálních typů.  
  
### <a name="conversions-from-unsigned-integral-types"></a>Převody z nepodepsaných integrálních typů  
  
|From|Chcete-li|Metoda|  
|----------|--------|------------|  
|`unsigned char`|`char`|Zachovat bitový; bit horní stane přihlašovací bit|  
|`unsigned char`|**krátký**|Rozšíření nula.|  
|`unsigned char`|**dlouhá**|Rozšíření nula.|  
|`unsigned char`|**short bez znaménka**|Rozšíření nula.|  
|`unsigned char`|`unsigned long`|Rozšíření nula.|  
|`unsigned char`|**plovoucí desetinná čárka**|Převést na **dlouho**; převést **dlouho** k **float**|  
|`unsigned char`|**Double**|Převést na **dlouho**; převést **dlouho** k **double**|  
|`unsigned char`|`long double`|Převést na **dlouho**; převést **dlouho** k **double**|  
|**short bez znaménka**|`char`|Zachovat nejnižší bajtů|  
|**short bez znaménka**|**krátký**|Zachovat bitový; bit horní stane přihlašovací bit|  
|**short bez znaménka**|**dlouhá**|Rozšíření nula.|  
|**short bez znaménka**|`unsigned char`|Zachovat nejnižší bajtů|  
|**short bez znaménka**|`unsigned long`|Rozšíření nula.|  
|**short bez znaménka**|**plovoucí desetinná čárka**|Převést na **dlouho**; převést **dlouho** k **float**|  
|**short bez znaménka**|**Double**|Převést na **dlouho**; převést **dlouho** k **double**|  
|**short bez znaménka**|`long double`|Převést na **dlouho**; převést **dlouho** k **double**|  
|`unsigned long`|`char`|Zachovat nejnižší bajtů|  
|`unsigned long`|**krátký**|Zachovat nejnižší aplikace word|  
|`unsigned long`|**dlouhá**|Zachovat bitový; bit horní stane přihlašovací bit|  
|`unsigned long`|`unsigned char`|Zachovat nejnižší bajtů|  
|`unsigned long`|**short bez znaménka**|Zachovat nejnižší aplikace word|  
|`unsigned long`|**plovoucí desetinná čárka**|Převést na **dlouho**; převést **dlouho** k **float**|  
|`unsigned long`|**Double**|Převést přímo na **double**|  
|`unsigned long`|`long double`|Převést na **dlouho**; převést **dlouho** k **double**|  
  
 **Konkrétní Microsoft**  
  
 Pro kompilátor C Microsoft 32bitová verze `unsigned int` typ je ekvivalentní `unsigned long` typu. Převod `unsigned int` hodnotu pokračuje stejným způsobem jako převod `unsigned long`. Převody z `unsigned long` hodnoty k **float** nejsou přesné, pokud je hodnota převáděné větší než maximální kladnou podepsané **dlouho** hodnotu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Převody přiřazení](../c-language/assignment-conversions.md)