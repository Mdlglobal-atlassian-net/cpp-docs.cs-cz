---
title: "Chyba v běhu R6028 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1d7260cd2416e9d157931b037cfd7fbe4c0081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-runtime-error-r6028"></a>R6028 Chyba za běhu C
Nelze inicializovat haldu  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má problém s interní paměť. Existuje mnoho možných příčin této chyby, ale často je způsobeno podmínku velmi málo paměti chyby v programu, nebo vadný ovladačů.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Ukončete ostatní spuštěné aplikace nebo restartujte počítač k uvolnění paměti.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Pokud byla aplikace funguje před poslední instalace jinou aplikaci aplikační nebo ovladačů, použijte **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat nové aplikace nebo ovladače a zkuste aplikaci znovu.  
> -   Zkontrolujte webu dodavatele hardwaru nebo **Windows Update** v **ovládací panely** pro aktualizace softwaru a ovladačů.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 K této chybě dojde, když se operačnímu systému nepodaří vytvořit fond paměti pro aplikace. Konkrétně C Runtime (CRT) volal funkci Win32 `HeapCreate`, který vrátil hodnotu NULL udávající neúspěch.  
  
 Pokud k této chybě dojde během spouštění aplikace, nemusí být systém schopen splnit požadavky haldy, protože jsou načteny vadné ovladače. Pomocí služby Windows Update nebo na webu dodavatele hardwaru vyhledejte aktualizované ovladače.