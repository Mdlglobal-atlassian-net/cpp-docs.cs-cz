---
title: Odsazení a zarovnání členů struktury
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: 0f9c70ed074a11800b707aa48ec8e0e2f8b4f999
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325354"
---
# <a name="padding-and-alignment-of-structure-members"></a>Odsazení a zarovnání členů struktury

**3.5.2.1 ANSI** Odsazení a zarovnání členů struktur a zda bitové pole může přetažný hranici jednotky úložiště

Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.

Každý datový objekt má požadavek na zarovnání. Zarovnání – požadavek pro všechna data s výjimkou struktur, sjednocení a polí je buď velikost objektu, nebo aktuální velikost balení (určená buď pomocí/zp nebo `pack` direktiva pragma, podle toho, co je menší). U struktur, sjednocení a polí jsou požadavky na zarovnání největší zarovnání požadavku členů. Každému objektu je přidělen posun, aby

*offset* **%** *Zarovnání odsazení – požadavek* **= = 0**

Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.

## <a name="see-also"></a>Viz také

[Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)
