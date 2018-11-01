---
title: Agregace a sjednocení
ms.date: 11/04/2016
helpviewer_keywords:
- aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
ms.openlocfilehash: a4206a5e07c765e9c789eab5c8963c9db4c2f234
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496252"
---
# <a name="aggregates-and-unions"></a>Agregace a sjednocení

Jiné typy, jako je například pole, struktury a sjednocení, mít přísnější požadavky na zarovnání, které zajišťují konzistentní agregace a sjednocení načítání úložiště a data. Zde najdete definice pro pole, struktury a sjednocení:

- Pole

   Obsahuje skupinu seřazený sousedními datovými objekty. Každý objekt je názvem elementu. Všechny prvky v rámci pole mají stejnou velikost a datový typ.

- Struktura

   Obsahuje skupinu seřazený datových objektů. Na rozdíl od prvků pole datových objektů v rámci struktury můžete mít různé datové typy a velikosti. Každý datový objekt ve struktuře je názvem člena.

- Unie

   Objekt, který obsahuje některý ze sady pojmenované členy. Členové pojmenovaná sada může být libovolného typu. Úložiště přidělené pro sjednocení je rovna požadované pro největšího člena v tomto sjednocení, plus všechny odsazení na zarovnání.

V následující tabulce jsou uvedeny důrazně doporučené zarovnání skalární členy struktury a sjednocení.

||||
|-|-|-|
|Skalární typ.|Datový typ jazyka C|Požadované zarovnání|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**short bez znaménka**|Word|
|**INT32**|**int**, **dlouhý**|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|Doubleword|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 (jednoduché přesnosti)**|**float**|Doubleword|
|**FP64 (Dvojitá přesnost)**|**double**|Quadword|
|**UKAZATEL**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 – struktura**|Quadword|
|**__m128**|**__m128 – struktura**|Octaword|

Platí následující pravidla agregační zarovnání:

- Zarovnání pole je stejná jako zarovnání prvků pole.

- Zarovnání začátek struktury nebo sjednocení je maximální zarovnání každého jednotlivého člena. Každý člen v rámci struktury nebo sjednocení musí být umístěny na správném zarovnání, jak je definováno v předchozí tabulce, která může vyžadovat implicitní vnitřní odsazení, v závislosti na předchozí člen.

- Velikost struktury musí být integrální násobek jeho zarovnání, které mohou vyžadovat odsazení za posledním členem. Protože struktury a sjednocení mohou být seskupeny do pole, musí každý prvek pole, struktury nebo sjednocení začínají i končí na řádné zarovnání dříve určené.

- Je možné zarovnání dat tak, aby byly větší než požadavky na zarovnání jako předchozí pravidla jsou zachována.

- Jednotlivé kompilátor může upravit balení struktury důvodů velikost. Například [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md) umožňuje pro úpravu balení struktury.

## <a name="see-also"></a>Viz také

[Typy a úložiště](../build/types-and-storage.md)
