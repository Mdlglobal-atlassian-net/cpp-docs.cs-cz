---
title: Závažná chyba C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: a7130ed0568de387c99b8296dc4e10d92baec337
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821362"
---
# <a name="fatal-error-c1001"></a>Závažná chyba C1001

> VNITŘNÍ KOMPILÁTOR ERROR(compiler file *file*, line *number*)

Kompilátor nelze generovat správný kód konstrukce, často kvůli kombinaci konkrétní výraz a možnosti optimalizace nebo problému při analýze. Pokud má soubor kompilátoru uvedené utc nebo segment cesty C2, je pravděpodobně chyba optimalizace. Pokud soubor obsahuje cxxfe nebo c1xx segment cesty nebo je msc1.cpp, je pravděpodobně Chyba analyzátoru. Pokud je soubor s názvem cl.exe, nejsou žádné informace k dispozici.

Optimalizaci problém můžete vyřešit často odebráním jedné nebo více možností optimalizace. Pokud chcete zjistit, která možnost je při selhání, odeberte možnosti v době a překompilujte, dokud zmizet, chybová zpráva. Jsou nejčastěji odpovídá možnosti [/Og (globální optimalizace)](../../build/reference/og-global-optimizations.md) a [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md). Jakmile určíte, jakou možnost optimalizace zodpovídá, můžete jej zakázat kolem funkce, kde dojde k chybě s použitím [optimalizovat](../../preprocessor/optimize.md) – Direktiva pragma a nadále používat možnost pro zbytek modulu. Další informace o možnostech optimalizace najdete v tématu [doporučené postupy optimalizace](../../build/optimization-best-practices.md).

Není-li optimalizace způsobily chybu, zkuste přepisování řádku, kde je Chyba hlášená nebo několik řádků kódu tento řádek. Chcete-li zobrazit kód tak, jak kompilátor narazí po předběžném zpracování, můžete použít [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) možnost.

Další informace o tom, jak izolovat příčiny chyby a hlášení vnitřní chyba kompilátoru Microsoftu, najdete v části [postup ohlášení problému se sadou nástrojů Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).