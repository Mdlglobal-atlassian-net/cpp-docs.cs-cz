---
title: "Chyba linkerů Lnk1277 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1277
dev_langs: C++
helpviewer_keywords: LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 868fb4ef472aaf80242c276a9052562779da745c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1277"></a>Chyba linkerů LNK1277
Objekt nelze najít záznam v pgd (název souboru)  
  
 Při použití [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), cestu k jednomu vstupní soubory LIB, def nebo .obj se liší od cesty, na kterém nebyly nalezeny během /LTCG:PGINSTRUMENT. To může být vysvětleny změnou v proměnná prostředí LIB po /LTCG:PGINSTRUMENT. Úplná cesta k vstupní soubory jsou uloženy v souboru .pgd.  
  
 /LTCG:PGOPTIMIZE vyžaduje, aby vstupy do fáze /LTCG:PGINSTRUMENT identické.  
  
 Pro vyřešení toto upozornění, proveďte jednu z těchto možností:  
  
-   Spustit /LTCG:PGINSTRUMENT, vrátit všechny testovací spouští a spusťte /LTCG:PGOPTIMIZE.  
  
-   Které byly při spuštění /LTCG:PGINSTRUMENT změňte proměnná prostředí LIB.  
  
 Není doporučeno pomocí /LTCG:PGUPDATE LNK1277 obejít.