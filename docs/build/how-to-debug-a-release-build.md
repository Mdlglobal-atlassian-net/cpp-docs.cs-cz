---
title: 'Postupy: Ladění sestavení pro vydání'
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds, debugging
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
ms.openlocfilehash: 6d93fac4e980085c322acb55e6f8758e6cea0a00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188961"
---
# <a name="how-to-debug-a-release-build"></a>Postupy: Ladění sestavení pro vydání

Ladíte sestavení pro vydání aplikace.

### <a name="to-debug-a-release-build"></a>Chcete-li ladit sestavení pro vydání

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** uzlu. Nastavte **formát informací o ladění** k [kompatibilní s C7 (/ Z7)](reference/z7-zi-zi-debug-information-format.md) nebo **databázi programu (/Zi)**.

1. Rozbalte **Linkeru** a klikněte na tlačítko **Obecné** uzlu. Nastavte **umožnil přírůstkové propojování** k [ne (/ INCREMENTAL: NO)](reference/incremental-link-incrementally.md).

1. Vyberte **ladění** uzlu. Nastavte **Generovat ladicí informace** k [Ano (/ DEBUG)](reference/debug-generate-debug-info.md).

1. Vyberte **optimalizace** uzlu. Nastavte **odkazy** k [OPT](reference/opt-optimizations.md) a **Povolit skládání sekvencí COMDAT** k [/OPT:ICF](reference/opt-optimizations.md).

1. Teď můžete ladit aplikaci verzi sestavení. Chcete-li najít problém, krokovat kód (nebo ladění použití Just-In-Time), dokud nenajdete, kde dojde k selhání a potom určit nesprávné parametry nebo kódu.

   Pokud aplikace funguje v sestavení pro ladění, ale selže v sestavení pro vydání, jeden z optimalizace kompilátoru může vystavení vadu ve zdrojovém kódu. A izolovat daný problém, zakážete vybrané optimalizace pro každý soubor zdrojového kódu, dokud nenajdete soubor a optimalizace, která je příčinou problému. (Pokud chcete tento proces urychlit, můžete rozdělit do dvou skupin souborů, zakáže optimalizaci na jednu skupinu a zjistíte problém ve skupině,-li pokračovat, dělení, dokud problém souboru.)

   Můžete použít [/RTC](reference/rtc-run-time-error-checks.md) se pokouší vystavit takové chyby v sestavení ladění.

   Další informace najdete v tématu [optimalizace kódu](optimizing-your-code.md).

## <a name="see-also"></a>Viz také:

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
