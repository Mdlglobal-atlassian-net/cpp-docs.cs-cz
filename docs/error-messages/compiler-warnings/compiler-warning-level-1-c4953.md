---
title: "Kompilátoru (úroveň 1) upozornění C4953 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4953
dev_langs: C++
helpviewer_keywords: C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c330076e7c0b4ff6daded94ef5fc038bd9dad759
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4953"></a>C4953 kompilátoru upozornění (úroveň 1)
Po profil, který data nebyla shromážděna, data profilu nepoužívá upraven Inlinee 'function'.  
  
 Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl překompilovat po `/LTCG:PGINSTRUMENT` a má funkci (***funkce***) byl upraven, a kde se spouští identifikovaných existujícího testu funkce jako kandidáta na vložené. Ale v důsledku o nutnosti rekompilace modulu, funkce už bude kandidátem na vložené.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním `/LTCG:PGINSTRUMENT`, znovu všechny testovací běží a spusťte `/LTCG:PGOPTIMIZE`.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud `/LTCG:PGOPTIMIZE` byly použity.