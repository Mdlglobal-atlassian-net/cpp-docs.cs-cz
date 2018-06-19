---
title: Přehled příkazů jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a3cf80e6237b21101f737f496eb39688ec6ed0a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387174"
---
# <a name="overview-of-c-statements"></a>Přehled příkazů jazyka C
Příkazy C sestávají z tokenů, výrazů a jiných příkazů. Příkaz tvořící součást jiného příkazu je nazýván „tělem“ okolního příkazu. Typy příkazů dané následující syntaxí jsou popsány v tomto oddílu.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz*:  
 [příkaz s popiskem](../c-language/goto-and-labeled-statements-c.md)  
  
 [složené – příkaz](../c-language/compound-statement-c.md)  
  
 [příkaz výrazu](../c-language/expression-statement-c.md)  
  
 [Výběr – příkaz](../c-language/if-statement-c.md)  
  
 [iterace – příkaz](../c-language/do-while-statement-c.md)  
  
 [jump – příkaz](../c-language/break-statement-c.md)  
  
 [s výjimkou příkaz try](../c-language/try-except-statement-c.md)  
  
 / * Specifické pro Microsoft \* / [try-finally – příkaz](../c-language/try-finally-statement-c.md)  / \* specifické pro Microsoft \*/  
  
 Tělem příkazu je často „složený příkaz“. Složený příkaz sestává z jiných příkazů, které mohou obsahovat klíčová slova. Složený příkaz je oddělená složené závorky (**{}**). Všechny ostatní příkazy C končit středníkem (**;**). Středník je zakončením příkazu.  
  
 Příkaz výrazu obsahuje výraz C, která může obsahovat aritmetické operace nebo logické operátory byla zavedená v [výrazy a přiřazení](../c-language/expressions-and-assignments.md). Nulový příkaz je prázdným příkazem.  
  
 Všechny příkazy jazyka C mohou začínat identifikačním popiskem sestávajícím z názvu a dvojtečky. Jelikož pouze příkaz `goto` rozpoznává popisky příkazů, jsou tyto popisky popsány spolu s příkazem `goto`. V tématu [goto a příkazy s popiskem](../c-language/goto-and-labeled-statements-c.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)