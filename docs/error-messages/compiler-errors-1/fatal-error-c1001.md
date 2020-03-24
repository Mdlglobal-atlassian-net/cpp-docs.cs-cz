---
title: Závažná chyba C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: e1255578883c8d2bc278184a02575a0a51ed9b6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204955"
---
# <a name="fatal-error-c1001"></a>Závažná chyba C1001

> Vnitřní chyba kompilátoru ( *soubor*souboru kompilátoru, *číslo*řádku)

Kompilátor nemůže vygenerovat správný kód pro konstrukci, často z důvodu kombinace konkrétního výrazu a možnosti optimalizace nebo problému při analýze. Pokud je v uvedeném souboru kompilátoru uveden segment cesty UTC nebo C2, pravděpodobně došlo k chybě optimalizace. Pokud má soubor segment cesty cxxfe nebo c1xx nebo je msc1. cpp, pravděpodobně došlo k chybě analyzátoru. Pokud soubor s názvem je CL. exe, nejsou k dispozici žádné další informace.

Problém optimalizace můžete často opravit odebráním jedné nebo více možností optimalizace. Chcete-li určit, která možnost je chybná, odeberte možnosti postupně a znovu zkompilujte, dokud nezmizí chybová zpráva. Nejpoužívanějšími možnostmi jsou [/og (globální optimalizace)](../../build/reference/og-global-optimizations.md) a [/Oi (generování vnitřních funkcí)](../../build/reference/oi-generate-intrinsic-functions.md). Jakmile určíte, která možnost optimalizace je zodpovědná, můžete ji vypnout kolem funkce, kde k chybě dochází, pomocí direktivy pragma [optimize](../../preprocessor/optimize.md) a pokračovat v používání možnosti pro zbytek modulu. Další informace o možnostech optimalizace najdete v tématu věnovaném [osvědčeným postupům optimalizace](../../build/optimization-best-practices.md).

Pokud optimalizace nejsou zodpovědné za chybu, zkuste přepsat řádek, kde je chyba nahlášena, nebo několik řádků kódu obklopujících daný řádek. Chcete-li zobrazit kód tak, jak ho kompilátor uvidí po předběžném zpracování, můžete použít možnost [/p (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) .

Další informace o tom, jak izolovat zdroj chyby a jak ohlásit vnitřní chybu kompilátoru společnosti Microsoft, naleznete v tématu [How to nahlásit problém s C++ vizuální sadou nástrojů](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).
