---
title: Závažná chyba C1307 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d06ce51ada7cd9159b8e02ff627bf12ebb7293d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227132"
---
# <a name="fatal-error-c1307"></a>Závažná chyba C1307
Program byl upraven, protože nebyla shromážděna data profilu  
  
 Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), linkeru zjistil vstupní modul, který byl překompilovat po /LTCG:PGINSTRUMENT a že modul byl změněn na bodu, pokud je existující data profilu už relevantní. Například pokud grafu volání změnili v modulu Rekompilované, vygeneruje kompilátor C1307.  
  
 Chcete-li tuto chybu vyřešit, spusťte /LTCG:PGINSTRUMENT, vrátit všechny testovací spouští a spusťte /LTCG:PGOPTIMIZE. Pokud /LTCG:PGINSTRUMENT a opakování akce, které všechny testovací nelze spustit spustí, použijte /LTCG:PGUPDATE místo /LTCG:PGOPTIMIZE vytvoření optimalizované bitové kopie.