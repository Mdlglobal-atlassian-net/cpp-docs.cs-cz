---
title: Uchovávání a zarovnání struktur
ms.date: 11/04/2016
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
ms.openlocfilehash: 8e15f39b5a7a78da117c3b8a551ebfba5e07c194
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336165"
---
# <a name="storage-and-alignment-of-structures"></a>Uchovávání a zarovnání struktur

**Specifické pro Microsoft**

Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.

Každý datový objekt má *požadavek na zarovnání*. U struktur je požadavek ten největší ze svých členů. Každému objektu je přidělen *posun* , aby

zarovnání *odsazení* `%` *– požadavek* `==` 0

Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.

Z důvodu úspory místa nebo vyhovění existujícím datovým strukturám, lze struktury uložit více či méně kompaktně. Možnost kompilátoru [/zp](../build/reference/zp-struct-member-alignment.md)[*n*] a [sada #pragma pack](../preprocessor/pack.md) řídí způsob, jakým jsou data struktury "zabalena" do paměti. Použijete-li možnost/Zp [*n*], kde *n* je 1, 2, 4, 8 nebo 16, každý člen struktury po prvním je uložen na hranicích bajtů, které jsou buď požadavkem na zarovnání pole, nebo velikostí balení (*n*), podle toho, která hodnota je menší. Vyjádřené jako vzorec, jsou hranice bajtu

```
min( n, sizeof( item ) )
```

kde *n* je velikost balení vyjádřená možností/zp [*n*] a *položka* je členem struktury. Výchozí velikost komprimace je /Zp8.

Chcete-li pomocí direktivy pragma `pack` pro danou strukturu určit jinou komprimaci než specifikovanou příkazovým řádkem, použijte před touto strukturou direktivu pragma `pack`, kde je velikost komprimace 1, 2, 4, 8 nebo 16. Chcete-li obnovit komprimaci zadanou na příkazovém řádku, zadejte direktivu pragma `pack` bez argumentů.

Pro kompilátor jazyka C společnosti Microsoft je **výchozí velikost bitových polí velká.** Členy struktury jsou zarovnané na velikost typu nebo velikost/zp [*n*], podle toho, která hodnota je menší. Výchozí velikost je 4.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarace struktury](../c-language/structure-declarations.md)
