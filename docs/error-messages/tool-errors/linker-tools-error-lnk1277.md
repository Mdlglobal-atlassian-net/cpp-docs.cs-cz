---
title: Chyba linkerů Lnk1277 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec8f00793fcda748c60d9d8ea775611e3d025cd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298727"
---
# <a name="linker-tools-error-lnk1277"></a>Chyba linkerů LNK1277
Objekt nelze najít záznam v pgd (název souboru)  
  
 Při použití [/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), cestu k jednomu vstupní soubory LIB, def nebo .obj se liší od cesty, na kterém nebyly nalezeny během /LTCG:PGINSTRUMENT. To může být vysvětleny změnou v proměnná prostředí LIB po /LTCG:PGINSTRUMENT. Úplná cesta k vstupní soubory jsou uloženy v souboru .pgd.  
  
 /LTCG:PGOPTIMIZE vyžaduje, aby vstupy do fáze /LTCG:PGINSTRUMENT identické.  
  
 Pro vyřešení toto upozornění, proveďte jednu z těchto možností:  
  
-   Spustit /LTCG:PGINSTRUMENT, vrátit všechny testovací spouští a spusťte /LTCG:PGOPTIMIZE.  
  
-   Které byly při spuštění /LTCG:PGINSTRUMENT změňte proměnná prostředí LIB.  
  
 Není doporučeno pomocí /LTCG:PGUPDATE LNK1277 obejít.