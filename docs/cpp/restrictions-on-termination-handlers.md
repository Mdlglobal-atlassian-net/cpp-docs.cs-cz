---
title: Omezení obslužných rutin ukončení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae16363956afc7cca853307ef2888846a02864d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461767"
---
# <a name="restrictions-on-termination-handlers"></a>Omezení obslužných rutin ukončení
Nelze použít **goto** příkazu Přejít do **__try** blok příkazů nebo **__finally** blok příkazů. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. (Můžete, ale přejít z celkového počtu **__try** blok příkazů.) Kromě toho nelze vnořovat obslužná rutina ukončení v případě obslužná rutina výjimky **__finally** bloku.  
  
 Kromě toho některé druhy kód v obslužné rutiny ukončení výsledkům sporné, proto byste měli použít opatrně, a pokud vůbec. Je **goto** příkaz, který vrací z celkového počtu **__finally** blok příkazů. Pokud blok se provádí jako součást normální ukončení, neobvyklé nic se nestane. Ale pokud systému je odvíjení zásobníku, který získá odvíjení zarážky a aktuální funkci řízení jakoby nebyly žádné abnormální ukončení.  
  
 A **vrátit** výroku uvnitř **__finally** blok příkazů představuje přibližně o stejnou situaci. Ovládací prvek vrátí volajícímu okamžitě funkce obsahující obslužné rutiny ukončení. Pokud systém byl odvíjení zásobníku, tento proces je zastaven a program pokračuje, jako kdyby byla bez výjimky vyvolána.  
  
## <a name="see-also"></a>Viz také:  
 [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)   
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)