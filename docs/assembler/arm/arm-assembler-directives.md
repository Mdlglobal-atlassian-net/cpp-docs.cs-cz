---
title: Direktivy assembleru ARM | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fee551d667b40b3fc36b3ca1f91e093148083a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="arm-assembler-directives"></a>Direktivy assembleru ARM
Ve většině případů assembleru Microsoft ARM používá jazyk sestavení ARM, která je popsána v kapitole 7 [příručka nástroje assembleru ARM](http://go.microsoft.com/fwlink/?LinkId=246102). Ale implementace Microsoft direktiv některé sestavení se liší od direktivy sestavení ARM. Tento článek vysvětluje rozdíly.  
  
## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Implementace Microsoft direktiv sestavení ARM  
 OBLASTI  
 Assembleru Microsoft ARM podporuje tyto atributy oblasti: ZAROVNAT, kód, CODEALIGN, DATA, NOINIT, jen pro čtení, READWRITE, Flash, ARM.  
  
 Všechny kromě Flash a ARM fungovat, jak je uvedeno v [příručka nástroje assembleru ARM](http://go.microsoft.com/fwlink/?LinkId=246102).  
  
 V assembleru Microsoft ARM Flash označuje, že část kódu obsahuje kód, Flash a je výchozí pro části kódu.  ARM znamená, že oddíl obsahuje kód ARM.  
  
 LINE  
 Není podporováno.  
  
 CODE16  
 Není podporována, protože předpokládají pre-UAL jezdec syntaxi, což není povoleno assembleru Microsoft ARM.  Místo toho použijte JEZDEC – direktiva společně s syntaxe protokolování přístupu uživatele.  
  
 BĚŽNÉ  
 Specifikace zarovnání pro běžné oblast není podporována.  
  
 DCDO  
 Není podporováno.  
  
 ROZLIŠUJÍCÍ NÁZEV, QN SN  
 Specifikace typu nebo dráhy na alias registrace není podporována.  
  
 POLOŽKA  
 Není podporováno.  
  
 EQU  
 Specifikace typu pro definovaný symbol není podporována.  
  
 EXPORT a globální  
 ```  
EXPORTsym {[type]}  
```  
  
 `sym`je symbol pro export.  `[type]`, pokud jsou zadané, může být buď `[DATA]` indikující, zda je symbol ukazuje na data nebo `[FUNC]` indikující, zda je symbol ukazuje na kódu.  
  
 GLOBÁLNÍ je synonymum pro EXPORT.  
  
 EXPORTAS  
 Není podporováno.  
  
 RÁMCE  
 Není podporováno.  
  
 Funkce a PROC  
 I když syntaxe sestavení podporuje specifikaci vlastní konvence volání na postupech tak, že uvedete registrů, které jsou volající uložit a ty, které jsou volaný ukládání, assembleru Microsoft ARM přijímá syntaxe, ale ignoruje seznamy registrace.  Informace o ladění, která je vytvořena pomocí assembleru podporuje pouze výchozí konvenci volání.  
  
 IMPORT a EXTERN  
 ```  
IMPORT sym{, WEAK alias{, TYPE t}}  
```  
  
 `sym`je název symbol, který má být importován.  
  
 Pokud SLABÉ `alias` není zadaný, značí to, `sym` je slabé externí. Pokud je nalezena žádná definice pro něj v době spojení, pak všechny odkazy na jeho místo navázat na `alias`.  
  
 Pokud typ `t` se `t` označuje linkeru mají pokusit o tom, jak vyřešit `sym`.  Tyto hodnoty pro `t` je možné:   
1 – neprovádět knihovny Hledat`sym`  
2 – knihovna hledání pro`sym`  
3 –`sym` je alias `alias` (výchozí)  
  
 EXTERN je synonymum pro IMPORT, vyjma toho, že `sym` importu pouze v případě, že existují odkazy na ni v aktuální sestavení.  
  
 MACRO  
 Použití proměnné pro uložení kód podmínku makra není podporováno. Výchozí hodnoty pro makra, které parametry nejsou podporovány.  
  
 NOFP  
 Není podporováno.  
  
 OPT, TTL, SUBT  
 Není podporována, protože assembleru Microsoft ARM nevytváří seznamy.  
  
 PRESERVE8  
 Není podporováno.  
  
 RELOC  
 `RELOC n`může používat pouze instrukce nebo direktivu definice data. Neexistuje žádné "anonymní symbol", může být přemístění.  
  
 VYŽADOVAT  
 Není podporováno.  
  
 REQUIRE8  
 Není podporováno.  
  
 THUMBX  
 Není podporováno, protože assembleru Microsoft ARM nepodporuje sada instrukcí 2EE jezdce.  
  
## <a name="see-also"></a>Viz také  
 [Reference k příkazovému řádku assembleru ARM](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [Diagnostické zprávy assembleru ARM](../../assembler/arm/arm-assembler-diagnostic-messages.md)