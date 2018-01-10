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
ms.workload: cplusplus
ms.openlocfilehash: fe97f1658a74b0db5985ed755bf387811f2c6d1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1307"></a>Závažná chyba C1307
Program byl upraven, protože nebyla shromážděna data profilu  
  
 Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), linkeru zjistil vstupní modul, který byl překompilovat po /LTCG:PGINSTRUMENT a že modul byl změněn na bodu, pokud je existující data profilu už relevantní. Například pokud grafu volání změnili v modulu Rekompilované, vygeneruje kompilátor C1307.  
  
 Chcete-li tuto chybu vyřešit, spusťte /LTCG:PGINSTRUMENT, vrátit všechny testovací spouští a spusťte /LTCG:PGOPTIMIZE. Pokud /LTCG:PGINSTRUMENT a opakování akce, které všechny testovací nelze spustit spustí, použijte /LTCG:PGUPDATE místo /LTCG:PGOPTIMIZE vytvoření optimalizované bitové kopie.