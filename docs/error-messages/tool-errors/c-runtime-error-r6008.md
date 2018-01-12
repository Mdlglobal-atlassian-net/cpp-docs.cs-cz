---
title: "Chyba v běhu R6008 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6008
dev_langs: C++
helpviewer_keywords: R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b64f97768359b95d2c5e2003cfb5b95a2aac71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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