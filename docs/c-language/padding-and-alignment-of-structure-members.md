---
title: "Odsazení a zarovnání členů struktury | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cd8dc389f4a4140b78a78753f7f5a91168bd984
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="padding-and-alignment-of-structure-members"></a>Odsazení a zarovnání členů struktury
**ANSI 3.5.2.1** odsazení a zarovnání členů struktury a jestli můžete vytvářet bitové pole kolem hranici jednotky úložiště  
  
 Členy struktury jsou postupně uloženy v pořadí, ve kterém jsou deklarovány: první člen má nejnižší adresu paměti a poslední člen nejvyšší.  
  
 Každý datový objekt má zarovnání požadavek. Zarovnání požadavek pro všechna data s výjimkou struktury, sjednocení a pole je buď velikost objektu nebo aktuální velikost okolních (zadaný buď /Zp nebo `pack` – Direktiva pragma, podle toho, která je menší). Struktury, sjednocení a pole je požadavek na zarovnání největší požadavek zarovnání svých členů. Každý objekt je přidělen posun tak, aby  
  
 *Posun* `%` *zarovnání požadavek* `==` 0  
  
 Sousední bitová pole jsou zkomprimována do stejné 1, 2, a 4bajtové alokační jednotky, pokud mají celočíselné typy stejnou velikost a pokud další bitové pole zapadá do aktuální alokační jednotky bez překročení hranice stanovené běžnými požadavky zarovnání bitových polí.  
  
## <a name="see-also"></a>Viz také  
 [Struktury, sjednocení, výčty a bitová pole](../c-language/structures-unions-enumerations-and-bit-fields.md)