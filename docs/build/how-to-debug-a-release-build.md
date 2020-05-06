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

Můžete ladit sestavení pro vydání aplikace.

### <a name="to-debug-a-release-build"></a>Ladění sestavení pro vydání

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](working-with-project-properties.md).

1. Klikněte na uzel **C/C++** . Nastavte **formát informací o ladění** na [kompatibilní s C7 (/Z7)](reference/z7-zi-zi-debug-information-format.md) nebo **databáze programu (/Zi)**.

1. Rozbalte **linker** a klikněte na uzel **Obecné** . Nastavte **Povolit přírůstkové propojení** na [ne (/INCREMENTAL: No)](reference/incremental-link-incrementally.md).

1. Vyberte uzel **ladění** . Nastavte **generovat ladicí informace** na [Ano (/debug)](reference/debug-generate-debug-info.md).

1. Vyberte uzel **optimalizace** . Nastavte **odkazy** na [/OPT: ref](reference/opt-optimizations.md) a **Povolte skládání COMDAT** na [/OPT: ICF](reference/opt-optimizations.md).

1. Nyní můžete ladit aplikaci sestavení pro vydání. Chcete-li najít problém, krokovat kód (nebo použít ladění za běhu), dokud nezjistíte, kde dojde k selhání, a pak určete nesprávné parametry nebo kód.

   Pokud aplikace funguje v sestavení pro ladění, ale v sestavení pro vydání dojde k chybě, jedna z optimalizací kompilátoru může vystavit vadu ve zdrojovém kódu. Chcete-li izolovat problém, zakažte vybrané optimalizace pro každý soubor zdrojového kódu, dokud nenajdete soubor a optimalizaci, která tento problém způsobuje. (Pokud chcete tento proces urychlit, můžete soubory rozdělit do dvou skupin, zakázat optimalizaci pro jednu skupinu a při hledání problému ve skupině pokračovat v rozdělování, dokud neizolujete soubor problému.)

   [/RTC](reference/rtc-run-time-error-checks.md) můžete použít k pokusu o zveřejnění takových chyb v sestavení ladění.

   Další informace najdete v tématu [optimalizace kódu](optimizing-your-code.md).

## <a name="see-also"></a>Viz také

[Oprava problémů se sestavením pro vydání](fixing-release-build-problems.md)
