---
title: Chyba v běhu R6008 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d32734850c58b64694e96c3a27b759131e6c5ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299874"
---
# <a name="c-runtime-error-r6008"></a>R6008 Chyba za běhu C
není dostatek místa pro argumenty  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má problém s interní paměť. Existuje několik možných příčin této chyby, avšak často je způsobena podmínku velmi málo paměti příliš mnoho paměti provedenou proměnné prostředí nebo chyby v programu.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Ukončete ostatní spuštěné aplikace nebo restartujte počítač k uvolnění paměti.  
> -   Snižte počet a velikost argumenty příkazového řádku na aplikaci.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Byl dostatek paměti pro načtení program, ale není dost paměti k vytvoření **argv –** pole. Příčinou může být velmi nedostatek paměti nebo neobvykle velký příkazové řádky nebo použití proměnných prostředí. Zvažte jednu z následujících řešení:  
  
-   Zvětšete velikost paměti k dispozici pro program.  
  
-   Snižte počet a velikost argumenty příkazového řádku.  
  
-   Snižte velikost prostředí odebráním nepotřebných proměnné.