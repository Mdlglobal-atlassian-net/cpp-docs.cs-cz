---
title: Odsazení a zarovnání členů struktury | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 959d6296c563958a0c8bdd1ecca660680941755f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074848"
---
# <a name="padding-and-alignment-of-structure-members"></a>Odsazení a zarovnání členů struktury

**ANSI 3.5.2.1** odsazení a zarovnání členů struktury a určuje, zda lze bitového pole obtížemi hranici jednotky úložiště

Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.

Každý datový objekt má požadavek zarovnání. Požadavek zarovnání pro všechna data s výjimkou struktury, sjednocení a pole je velikost objektu nebo aktuální velikost komprimace (zadaný buď/zp nebo `pack` – Direktiva pragma, podle toho, co je menší). Struktury, sjednocení a pole je požadavkem zarovnání největšího požadavku zarovnání jeho členů. Každému objektu je přiřazen posun tak, aby

*Posun* `%` *požadavek zarovnání* `==` 0  

Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)