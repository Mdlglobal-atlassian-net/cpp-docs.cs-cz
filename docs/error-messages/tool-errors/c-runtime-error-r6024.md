---
title: "Chyba v běhu R6024 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6024
dev_langs: C++
helpviewer_keywords: R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d032bbcb6e28d78f5e43b9c12499c6d47ca0310
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6024"></a>R6024 Chyba za běhu C
není dostatek místa pro tabulku _onexit – / atexit  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má problém s interní paměť. Tato chyba je obvykle způsobeno podmínku velmi málo paměti nebo výjimečně podle chyby v programu nebo poškození knihoven Visual C++, které používá.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Ukončete ostatní spuštěné aplikace nebo restartujte počítač k uvolnění paměti.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravit nebo znovu nainstalovat všechny kopie systému Microsoft Visual C++ Redistributable.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 K této chybě dojde, protože nebylo k dispozici pro žádné paměti `_onexit` nebo `atexit` funkce. Tato chyba je způsobená podmínku nedostatku paměti. Zvažte předběžné přidělení vyrovnávací paměti při spuštění aplikace, který pomáhá při ukládání uživatelských dat a provedení čisté aplikace ukončete v nedostatku paměti.