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
ms.openlocfilehash: efb4b4a283964230d191962db40c4d061a039dfd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4951"></a>C4951 kompilátoru upozornění (úroveň 1)
Po profil, který data nebyla shromážděna, data profilu funkce nepoužívá upraven 'function'.  
  
 Funkce bylo upraveno v modulu vstupní s [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)tak, aby data profilu je nyní není platný. Vstupní modul byl překompilovat po **/LTCG:PGINSTRUMENT** a má funkci (***funkce***) s jinou toku řízení, než se v modulu v době **/LTCG:PGINSTRUMENT**  operaci.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním **/LTCG:PGINSTRUMENT**, znovu všechny testovací běží a spusťte **/LTCG:PGOPTIMIZE**.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud **/LTCG:PGOPTIMIZE** bylo použito.