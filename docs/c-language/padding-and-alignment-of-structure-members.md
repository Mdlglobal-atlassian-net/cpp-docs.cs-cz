---
title: Odsazení a zarovnání členů struktury | Microsoft Docs
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
ms.openlocfilehash: fb090fc283da0a8aa86dac524272d308127059ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385374"
---
# <a name="padding-and-alignment-of-structure-members"></a>Odsazení a zarovnání členů struktury
**ANSI 3.5.2.1** odsazení a zarovnání členů struktury a jestli můžete vytvářet bitové pole kolem hranici jednotky úložiště  
  
 Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.  
  
 Každý datový objekt má zarovnání požadavek. Zarovnání požadavek pro všechna data s výjimkou struktury, sjednocení a pole je buď velikost objektu nebo aktuální velikost okolních (zadaný buď /Zp nebo `pack` – Direktiva pragma, podle toho, která je menší). Struktury, sjednocení a pole je požadavek na zarovnání největší požadavek zarovnání svých členů. Každý objekt je přidělen posun tak, aby  
  
 *Posun* `%` *zarovnání požadavek* `==` 0    
  
 Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)