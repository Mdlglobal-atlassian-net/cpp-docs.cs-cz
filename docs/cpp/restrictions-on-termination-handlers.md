---
title: "Omezení obslužných rutin ukončení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 593cb54298682c53f534e92f6553d86d2118d98b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="restrictions-on-termination-handlers"></a>Omezení obslužných rutin ukončení
Nelze použít `goto` příkaz Přejít do `__try` příkaz bloku nebo `__finally` příkaz bloku. Místo toho je nutné vstoupit do tohoto bloku příkazů prostřednictvím normálního toku řízení. (Můžete, ale přejít z `__try` příkaz bloku.) Navíc nelze vnořit obslužná rutina výjimky nebo obslužné rutiny ukončení uvnitř `__finally` bloku.  
  
 Kromě toho některé druhy kódu povolené v obslužné rutiny ukončení výsledkům sporná, takže byste měli použít s upozorněním, a pokud vůbec. Jedna je `goto` příkaz, který přejde z `__finally` příkaz bloku. Pokud bloku spouští jako součást normální ukončení, nedojde k žádné akci. Ale pokud je systém unwinding zásobníku, který získá unwinding zastaví a funkci current řídit, jako kdyby nebyla žádná abnormální ukončení.  
  
 A `return` příkaz uvnitř `__finally` blok příkazu uvede přibližně stejné situaci. Vrátí ovládací prvek pro bezprostředního volajícího funkce obsahující obslužné rutiny ukončení. Pokud v systému byla unwinding zásobníku, tento proces je zastavit a program bude pokračovat, protože, pokud by došlo bez byla vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)   
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)