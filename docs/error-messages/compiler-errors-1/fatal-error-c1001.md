---
title: Závažná chyba C1001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f605dd7e4892c4a8b57e544ed857257be72f020d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199025"
---
# <a name="fatal-error-c1001"></a>Závažná chyba C1001

> INTERNÍ ERROR(compiler file *file*, line *number*) KOMPILÁTORU  
  
Kompilátor nemůže generovat správný kód for – konstrukce, často kvůli kombinace konkrétní výraz a možnost optimalizace nebo o problém při analýze. Pokud v uvedeném souboru kompilátoru utc nebo segment cesty C2, je pravděpodobně chyba optimalizace. Pokud soubor obsahuje segment cesty cxxfe nebo c1xx nebo je msc1.cpp, je pravděpodobně chybě analyzátoru. Pokud je soubor s názvem cl.exe, nejsou žádné další informace k dispozici.  

Často můžete opravit problém s optimalizace odebrání jednoho nebo více možností optimalizace. Určete, které možnosti se na chyby, odeberte možnosti, jeden v době a pak ji znovu zkompilovat, dokud vyčkat, chybová zpráva. Jsou nejčastěji zodpovědná možnosti [/Og (globální optimalizace)](../../build/reference/og-global-optimizations.md) a [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md). Jakmile zjistíte, kterou možnost optimalizace zodpovídá, můžete ji zakázat kolem funkce, kde dojde k chybě pomocí [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma a nadále používat možnost pro zbytek modul. Další informace o možnostech optimalizace najdete v tématu [doporučené postupy optimalizace](../../build/reference/optimization-best-practices.md).

Pokud není optimalizace zodpovědná za chyba, zkuste přepisování řádku, kde je chybě nebo několika řádků kódu, které obaluje daného řádku. Chcete-li zobrazit kód způsob kompilátor uvidí ho po předběžného zpracování, můžete použít [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) možnost.

Další informace o zdroji této chyby izolovat a vnitřní chyba kompilátoru nahlásit společnosti Microsoft najdete v tématu [postup nahlásit problém s sady nástrojů Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).