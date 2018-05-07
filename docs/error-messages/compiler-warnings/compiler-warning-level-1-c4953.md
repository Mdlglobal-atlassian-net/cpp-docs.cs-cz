---
title: Kompilátoru (úroveň 1) upozornění C4953 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af5a16ebbf7851eceb2f2cd355f953b14c4bd38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4953"></a>C4953 kompilátoru upozornění (úroveň 1)
Po profil, který data nebyla shromážděna, data profilu nepoužívá upraven Inlinee 'function'.  
  
 Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl překompilovat po `/LTCG:PGINSTRUMENT` a má funkci (***funkce***) byl upraven, a kde se spouští identifikovaných existujícího testu funkce jako kandidáta na vložené. Ale v důsledku o nutnosti rekompilace modulu, funkce už bude kandidátem na vložené.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním `/LTCG:PGINSTRUMENT`, znovu všechny testovací běží a spusťte `/LTCG:PGOPTIMIZE`.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud `/LTCG:PGOPTIMIZE` byly použity.