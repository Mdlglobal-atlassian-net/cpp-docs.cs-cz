---
title: "Kompilátoru (úroveň 1) upozornění C4951 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4951
dev_langs: C++
helpviewer_keywords: C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 199df135d5d2c00255037e5a1b31db80e2683d4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4951"></a>C4951 kompilátoru upozornění (úroveň 1)
Po profil, který data nebyla shromážděna, data profilu funkce nepoužívá upraven 'function'.  
  
 Funkce bylo upraveno v modulu vstupní s [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)tak, aby data profilu je nyní není platný. Vstupní modul byl překompilovat po **/LTCG:PGINSTRUMENT** a má funkci (***funkce***) s jinou toku řízení, než se v modulu v době **/LTCG:PGINSTRUMENT**  operaci.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním **/LTCG:PGINSTRUMENT**, znovu všechny testovací běží a spusťte **/LTCG:PGOPTIMIZE**.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud **/LTCG:PGOPTIMIZE** bylo použito.