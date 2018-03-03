---
title: "Závažná chyba C1001 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a72a99e566474145857e265edde548ebf38e180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1001"></a>Závažná chyba C1001

> INTERNÍ ERROR(compiler file *file*, line *number*) KOMPILÁTORU  
  
Kompilátor nemůže generovat správný kód for – konstrukce, často kvůli kombinace konkrétní výraz a možnost optimalizace nebo o problém při analýze. Pokud v uvedeném souboru kompilátoru utc nebo segment cesty C2, je pravděpodobně chyba optimalizace. Pokud soubor obsahuje segment cesty cxxfe nebo c1xx nebo je msc1.cpp, je pravděpodobně chybě analyzátoru. Pokud je soubor s názvem cl.exe, nejsou žádné další informace k dispozici.  

Často můžete opravit problém s optimalizace odebrání jednoho nebo více možností optimalizace. Určete, které možnosti se na chyby, odeberte možnosti, jeden v době a pak ji znovu zkompilovat, dokud vyčkat, chybová zpráva. Jsou nejčastěji zodpovědná možnosti [/Og (globální optimalizace)](../../build/reference/og-global-optimizations.md) a [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md). Jakmile zjistíte, kterou možnost optimalizace zodpovídá, můžete ji zakázat kolem funkce, kde dojde k chybě pomocí [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma a nadále používat možnost pro zbytek modul. Další informace o možnostech optimalizace najdete v tématu [doporučené postupy optimalizace](../../build/reference/optimization-best-practices.md).

Pokud není optimalizace zodpovědná za chyba, zkuste přepisování řádku, kde je chybě nebo několika řádků kódu, které obaluje daného řádku. Chcete-li zobrazit kód způsob kompilátor uvidí ho po předběžného zpracování, můžete použít [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) možnost.

Další informace o zdroji této chyby izolovat a vnitřní chyba kompilátoru nahlásit společnosti Microsoft najdete v tématu [postup nahlásit problém s sady nástrojů Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).