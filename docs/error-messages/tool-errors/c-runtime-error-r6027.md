---
title: "Chyba v běhu R6027 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6027
dev_langs: C++
helpviewer_keywords: R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f8110dc8d3ee580c8ba94336bd4818dd928310e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6027"></a>R6027 Chyba za běhu C
není dostatek místa pro inicializaci lowio  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má problém s interní paměť. Existuje několik možných příčin této chyby, avšak obvykle je způsobena podmínku velmi málo paměti. Může být také způsobeno, chyb v aplikaci, poškození knihoven Visual C++, které používá nebo ovladač.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Ukončete ostatní spuštěné aplikace nebo restartujte počítač k uvolnění paměti.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Pokud byla aplikace funguje před poslední instalace jinou aplikaci aplikační nebo ovladačů, použijte **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** odebrat nové aplikace nebo ovladače a zkuste aplikaci znovu.  
> -   Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravit nebo znovu nainstalovat všechny kopie systému Microsoft Visual C++ Redistributable.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 K této chybě dojde, když není dostatek volného paměti k dispozici k chybě při inicializaci nízké úrovně podpory vstupně-výstupních operací v modulu runtime C. Obvykle k této chybě dojde při spuštění aplikace. Ověřte, že vaše aplikace a ovladače a knihovny DLL, která načte nedošlo k poškození haldy při spuštění.