---
title: "Kompilátoru (úroveň 1) upozornění C4952 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4952
dev_langs: C++
helpviewer_keywords: C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3edf2d7be49375ad4c281bb8ff79c111fe6e15f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4952"></a>C4952 kompilátoru upozornění (úroveň 1)
'function': v programu databáze 'pgd_file' nalezena žádná data profilu  
  
 Při použití [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil vstupní modul, který byl překompilovat po `/LTCG:PGINSTRUMENT` a má novou funkci (***funkce***) existuje.  
  
 Toto upozornění je informační. Toto upozornění vyřešíte spuštěním `/LTCG:PGINSTRUMENT`, znovu všechny testovací běží a spusťte `/LTCG:PGOPTIMIZE`.  
  
 Toto upozornění se zobrazí se chyba nahrazený, pokud `/LTCG:PGOPTIMIZE` byly použity.