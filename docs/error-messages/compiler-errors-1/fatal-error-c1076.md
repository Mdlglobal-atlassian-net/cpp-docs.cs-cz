---
title: Závažná chyba C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751671"
---
# <a name="fatal-error-c1076"></a>Závažná chyba C1076

> Omezení kompilátoru: bylo dosaženo limitu interní haldy; pomocí parametru /Zm nastavte vyšší limit

Tuto chybu může způsobovat příliš mnoho symbolů nebo příliš mnoho instancí šablony. Spouští se v sadě Visual Studio 2015, může způsobit tuto zprávu z tlaku na paměť virtuálního Windows způsobeno příliš mnoho paralelních sestavení procesů. V takovém případě použijte doporučení **/Zm** možnost mají být ignorovány, pokud nepoužíváte `#pragma hdrstop` – direktiva.

Vyřešení této chyby:

1. Pokud používá předkompilovanou hlavičku `#pragma hdrstop` direktiv, použijte [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) možnost nastavit limit paměti kompilátoru na hodnotu zadanou v [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) chybovou zprávu. Další informace o nastavení této hodnoty v sadě Visual Studio, naleznete v části poznámky v [/Zm (zadat předkompilované hlavičky Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Zvažte snížení počtu paralelní procesy, které jsou určeny pomocí **/maxcpucount** možnost MSBUILD. Soubor EXE ve spojení s **/MP** možnost CL. SOUBOR EXE. Další informace najdete v tématu [předkompilované hlavičky (PCH) problémů a doporučení](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Pokud používáte 32bitové hostované kompilátory v 64bitovém operačním systému, použijte místo nich 64bitové hostované kompilátory. Další informace najdete v tématu [jak: Povolit 64bitové sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Odstraňte nepotřebné vkládané soubory.

1. Odstraňte nepotřebné globální proměnné – například dynamickým přidělením paměti namísto deklarování velkého pole.

1. Odstraňte nepoužité deklarace.

Pokud C1076 zobrazí okamžitě po zahájení sestavení, je hodnota zadaná u **/Zm** je pravděpodobně příliš vysoká. pro váš program. Omezit **/Zm** hodnotu.