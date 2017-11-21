---
title: "Závažná chyba C1307 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1307
dev_langs: C++
helpviewer_keywords: C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1173f538f02e8178d523bb51476b4a10427099ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1307"></a>Závažná chyba C1307
Program byl upraven, protože nebyla shromážděna data profilu  
  
 Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), linkeru zjistil vstupní modul, který byl překompilovat po /LTCG:PGINSTRUMENT a že modul byl změněn na bodu, pokud je existující data profilu už relevantní. Například pokud grafu volání změnili v modulu Rekompilované, vygeneruje kompilátor C1307.  
  
 Chcete-li tuto chybu vyřešit, spusťte /LTCG:PGINSTRUMENT, vrátit všechny testovací spouští a spusťte /LTCG:PGOPTIMIZE. Pokud /LTCG:PGINSTRUMENT a opakování akce, které všechny testovací nelze spustit spustí, použijte /LTCG:PGUPDATE místo /LTCG:PGOPTIMIZE vytvoření optimalizované bitové kopie.