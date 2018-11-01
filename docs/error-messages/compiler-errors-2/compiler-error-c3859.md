---
title: Chyba kompilátoru C3859
ms.date: 11/04/2016
f1_keywords:
- C3859
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
ms.openlocfilehash: be6ccaab49cb329e862fb6068af1337eddbaac8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490272"
---
# <a name="compiler-error-c3859"></a>Chyba kompilátoru C3859

rozsah virtuální paměti pro PCH překročil; Zkompilujte znovu s možností příkazového řádku z "-Zmvalue" nebo vyšší

Předkompilované hlavičky je moc malé množství dat, který kompilátor pokouší vložit v ní. Použití **/Zm** kompilátoru příznak pro označení větší hodnotu pro soubor předkompilované hlavičky. Další informace najdete v tématu [/Zm (zadat předkompilované hlavičky Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).