---
title: Kompilátoru (úroveň 1) upozornění C4951 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3ebf012338bdf6b90cc943e754056335c6751a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290462"
---
# <a name="compiler-warning-level-1-c4951"></a>C4951 kompilátoru upozornění (úroveň 1)
Po profil, který data nebyla shromážděna, data profilu funkce nepoužívá upraven 'function'.  
  
 Funkce bylo upraveno v modulu vstupní s [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)tak, aby data profilu je nyní není platný. Vstupní modul byl překompilovat po **/LTCG:PGINSTRUMENT** a má funkci (***funkce***) s jinou toku řízení, než se v modulu v době **/LTCG:PGINSTRUMENT**  operaci.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním **/LTCG:PGINSTRUMENT**, znovu všechny testovací běží a spusťte **/LTCG:PGOPTIMIZE**.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud **/LTCG:PGOPTIMIZE** bylo použito.