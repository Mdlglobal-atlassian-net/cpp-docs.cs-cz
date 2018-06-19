---
title: Agregace a sjednocení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b1afd3be89e1d18da9889d88dbbbef3fb104e02
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363256"
---
# <a name="aggregates-and-unions"></a>Agregace a sjednocení
Jiné typy, jako je například pole, struktur a sjednocení, mít přísnější požadavky na zarovnání, které zajišťují konzistentní agregace a sjednocení uložení a načtení dat. Zde jsou uvedeny definice pro pole, struktury a sjednocení:  
  
 Pole  
 Obsahuje uspořádanou skupinu sousedních datových objektů. Každý objekt, se nazývá prvek. Všechny elementy v rámci pole mít stejný typ velikost a data.  
  
 Struktura  
 Obsahuje skupinu seřazené datových objektů. Na rozdíl od prvky pole datové objekty v rámci struktury může mít různé datové typy a velikosti. Každý datový objekt ve struktuře se nazývá členem.  
  
 Unie  
 Objekt, který uchovává některý sadu s názvem členů. Členové pojmenované sady mohou být jakéhokoli typu. Úložiště přidělené pro spojení se rovná úložiště potřebné pro největší členem této sjednocení plus žádné odsazení požadované pro zarovnání.  
  
 V následující tabulce jsou uvedeny důrazně navrhované zarovnání pro skalární členy sjednocení a struktury.  
  
||||  
|-|-|-|  
|Skalární typ.|C – datový typ|Požadované zarovnání|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|Word|  
|**UINT16**|**short bez znaménka**|Word|  
|**INT32**|**int, dlouho**|Doubleword|  
|**UINT32**|**nepodepsané int, long bez znaménka**|Doubleword|  
|**INT64**|`__int64`|Quadword|  
|**UINT64**|**__int64 bez znaménka**|Quadword|  
|**FP32 (jednoduchá přesnost)**|**float**|Doubleword|  
|**FP64 (Dvojitá přesnost)**|**double**|Quadword|  
|**UKAZATELE**|**\***|Quadword|  
|`__m64`|**__m64 – struktura**|Quadword|  
|`__m128`|**__m128 – struktura**|Octaword|  
  
 Platí následující pravidla agregační zarovnání:  
  
-   Zarovnání pole je stejný jako jeden z elementů pole zarovnání.  
  
-   Zarovnání začátku struktury nebo sjednocení je maximální zarovnání každého jednotlivého člena. Každý člen v rámci struktury nebo sjednocení musí být umístěné na správném zarovnání, jak jsou definovány v předchozí tabulce, což může vyžadovat implicitní vnitřní odsazení, v závislosti na předchozího člena.  
  
-   Struktura velikost musí být násobkem svého zarovnání, což může vyžadovat odsazení za posledním členem. Vzhledem k tomu, že struktury a sjednocení mohou být seskupeny do pole, každý element pole struktury nebo sjednocení musí začínat a končit na správné zarovnání dříve určené.  
  
-   Je možné zarovnat data tak, aby být větší než požadavky na zarovnání tak dlouho, dokud předchozí pravidla jsou zachována.  
  
-   Jednotlivé kompilátoru může upravit okolních struktury důvodů velikost. Například [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md) umožňuje upravování okolních struktur.  
  
## <a name="see-also"></a>Viz také  
 [Typy a úložiště](../build/types-and-storage.md)
