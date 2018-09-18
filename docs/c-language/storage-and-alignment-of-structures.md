---
title: Uchovávání a zarovnání struktur | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 867b549575847a59f7d1e8a61792c8b097383a10
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092827"
---
# <a name="storage-and-alignment-of-structures"></a>Uchovávání a zarovnání struktur

**Specifické pro Microsoft**

Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.

Každý datový objekt má *požadavek zarovnání*. U struktur je požadavek ten největší ze svých členů. Každému objektu je přiřazen *posun* tak, aby

*Posun* `%` *požadavek zarovnání* `==` 0

Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.

Z důvodu úspory místa nebo vyhovění existujícím datovým strukturám, lze struktury uložit více či méně kompaktně. [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] – možnost kompilátoru a [#pragma pack](../preprocessor/pack.md) ovládacího prvku, jak data struktury "komprimace" do paměti. Při použití/zp [*n*] možnost, kde *n* je 1, 2, 4, 8 nebo 16, každý člen struktury po prvním uložen v bajtu hranice, které jsou buď dané požadavkem zarovnání pole nebo komprimaci velikost () *n*), podle toho, co je menší. Vyjádřené jako vzorec, jsou hranice bajtu

```
min( n, sizeof( item ) )
```

kde *n* je velikost komprimace vyjádřená/zp [*n*] možnost a *položky* je člen struktury. Výchozí velikost komprimace je /Zp8.

Chcete-li pomocí direktivy pragma `pack` pro danou strukturu určit jinou komprimaci než specifikovanou příkazovým řádkem, použijte před touto strukturou direktivu pragma `pack`, kde je velikost komprimace 1, 2, 4, 8 nebo 16. Chcete-li obnovit komprimaci zadanou na příkazovém řádku, zadejte direktivu pragma `pack` bez argumentů.

Bitová pole výchozí velikost **dlouhé** pro kompilátor Microsoft C. Členy struktury jsou zarovnány velikostí typu nebo/zp [*n*] velikost, podle toho, co je menší. Výchozí velikost je 4.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Deklarace struktury](../c-language/structure-declarations.md)