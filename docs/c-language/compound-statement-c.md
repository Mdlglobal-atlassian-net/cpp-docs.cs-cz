---
title: "Složené Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9422e3229aa5e800859f50e1ca058e32a4120074
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compound-statement-c"></a>Složený příkaz (C)
Složený příkaz (také nazývané "blok") se obvykle zobrazují jako text jiného příkazu, jako **Pokud** příkaz. [Deklarace a typy](../c-language/declarations-and-types.md) popisuje formuláře a význam deklarace, které se mohou objevit v hlavě složený příkaz.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz složené*:  
 **{***seznam prohlášení* opt*seznam příkazů*opt**}**   
  
 *seznam prohlášení*:  
 *deklarace*  
  
 *seznam prohlášení deklarace*  
  
 *seznam příkazů*:  
 s*dokončování příkazu šablon stylů*  
  
 *příkaz seznam příkazů*  
  
 Pokud jsou deklarace, musí být zadán před žádné příkazy. Rozsah každý identifikátor deklarovaný na začátku složený příkaz rozšiřuje z bodu deklarace na konci bloku. Viditelné v rámci bloku je prohlášení o stejný identifikátor neexistuje v informacích o vnitřní bloku.  
  
 Identifikátory v složené příkazu se předpokládá, že **automaticky** Pokud explicitně jinak deklarovat s **zaregistrovat**, **statické**, nebo `extern`, s výjimkou funkce může být pouze `extern`. Můžete ponechat `extern` specifikace v deklarace funkce a funkce budou mít pořád `extern`.  
  
 Úložiště není přidělen a inicializace není povolena, pokud proměnné nebo funkce je v složený příkaz s třídy úložiště deklarována `extern`. Deklaraci odkazuje na externí proměnné nebo funkce definované jinde.  
  
 Deklarovat proměnné v bloku s **automaticky** nebo **zaregistrovat** – klíčové slovo jsou znovu přidělit, a pokud potřeby inicializovat pokaždé, když se zadá složený příkaz. Tyto proměnné nejsou definovány po složený příkaz je byl ukončen. Pokud proměnná definovaná uvnitř bloku **statické** atribut, proměnná inicializován při spuštění programu začne a jeho hodnotu v rámci programu zachová. V tématu [třídy úložiště](../c-language/c-storage-classes.md) informace o **statické**.  
  
 Tento příklad ukazuje složený příkaz:  
  
```  
if ( i > 0 )   
{  
    line[i] = x;  
    x++;  
    i--;  
}  
```  
  
 V tomto příkladu Pokud `i` je větší než 0, všechny příkazy uvnitř složený příkaz jsou spouštěny v pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)