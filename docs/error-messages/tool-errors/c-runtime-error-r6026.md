---
title: Chyba v běhu R6026 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6026
dev_langs:
- C++
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7c8bea41b946db67ce24a52393d87873926f3f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298126"
---
# <a name="c-runtime-error-r6026"></a>R6026 Chyba za běhu C
není dostatek místa pro inicializaci stdio  
  
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
  
 K této chybě dojde, když není dost paměti k dispozici inicializovat standardní podporu vstupně-výstupních operací v modulu runtime C. Obvykle k této chybě dojde při spuštění aplikace. Ověřte, že vaše aplikace a ovladače a knihovny DLL, která načte nedošlo k poškození haldy při spuštění.