---
title: Chyba kompilátoru C3859
ms.date: 03/08/2019
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: 9b20224207ba797c6ee93c06404e4d90c3d02525
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391878"
---
# <a name="compiler-error-c3859"></a>Chyba kompilátoru C3859

> rozsah virtuální paměti pro PCH překročil; Zkompilujte znovu s možností příkazového řádku z "-Zm*hodnotu*" nebo vyšší

Virtuální paměť přidělené pro předkompilované hlavičky je moc malé množství dat, který kompilátor pokouší vložit v ní. Spouští se v sadě Visual Studio 2015 **/Zm** doporučení je významných pouze při použití `#pragma hdrstop` směrnice. V ostatních případech je detekováno falešné chyby, která označuje problémy tlak virtuální paměti Windows.

Pokud používá předkompilovanou hlavičku `#pragma hdrstop` direktiv, použijte **/Zm** kompilátoru příznak pro označení větší hodnotu pro soubor předkompilované hlavičky. V opačném případě zvažte snížení počtu procesů souběžné kompilace v sestavení. Další informace najdete v tématu [/Zm (zadat předkompilované hlavičky Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).
