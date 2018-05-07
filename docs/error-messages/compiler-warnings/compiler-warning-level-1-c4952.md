---
title: Kompilátoru (úroveň 1) upozornění C4952 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 42696dfae816742c958bca23e25e311e834dd62a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4952"></a>C4952 kompilátoru upozornění (úroveň 1)
'function': v programu databáze 'pgd_file' nalezena žádná data profilu  
  
 Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl překompilovat po `/LTCG:PGINSTRUMENT` a má novou funkci (***funkce***) existuje.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním `/LTCG:PGINSTRUMENT`, znovu všechny testovací běží a spusťte `/LTCG:PGOPTIMIZE`.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud `/LTCG:PGOPTIMIZE` byly použity.