---
title: Závažná chyba C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204175"
---
# <a name="fatal-error-c1076"></a>Závažná chyba C1076

> Omezení kompilátoru: bylo dosaženo limitu interní haldy; pomocí parametru /Zm nastavte vyšší limit

Tuto chybu může způsobovat příliš mnoho symbolů nebo příliš mnoho instancí šablony. Počínaje verzí sady Visual Studio 2015 Tato zpráva může být způsobena tlakem virtuální paměti Windows způsobeným příliš mnoha paralelními procesy sestavení. V takovém případě by se doporučení k použití možnosti **/zm** mělo ignorovat, pokud nepoužíváte direktivu `#pragma hdrstop`.

Vyřešení této chyby:

1. Pokud Předkompilovaná hlavička používá direktivu `#pragma hdrstop`, nastavte limit paměti kompilátoru na hodnotu zadanou v chybové zprávě [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) pomocí možnosti [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) . Další informace, které obsahují informace o tom, jak tuto hodnotu nastavit v sadě Visual Studio, naleznete v části poznámky v [/zm (určení limitu přidělení paměti pro předkompilované hlavičky)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Zvažte snížení počtu paralelních procesů určených pomocí možnosti **/maxcpucount** na MSBuild. EXE ve spojení s možností **/MP** na CL. Programu. Další informace najdete v tématu [problémy a doporučení k předkompilovaným hlavičkám (PCH)](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Pokud používáte 32bitové hostované kompilátory v 64bitovém operačním systému, použijte místo nich 64bitové hostované kompilátory. Další informace naleznete v tématu [How to: Enable a 64-bit Visual C++ sada nástrojů na příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Odstraňte nepotřebné vkládané soubory.

1. Odstraňte nepotřebné globální proměnné – například dynamickým přidělením paměti namísto deklarování velkého pole.

1. Odstraňte nepoužité deklarace.

Pokud k C1076 dojde ihned po zahájení sestavení, hodnota zadaná pro **/zm** je pravděpodobně pro váš program příliš vysoká. Snižte hodnotu **/zm** .
