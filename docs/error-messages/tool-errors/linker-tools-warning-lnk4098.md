---
title: Upozornění linkerů LNK4098
ms.date: 03/26/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 66cf1a1bc75405ffc9bae8158bfc8682776a8228
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508725"
---
# <a name="linker-tools-warning-lnk4098"></a>Upozornění linkerů LNK4098

> DEFAULTLIB "*knihovny*' je v konfliktu s použitím jiných knihoven; použijte parametr/NODEFAULTLIB:*knihovny*

Se snažíte propojit pomocí kompatibilní knihovny.

> [!NOTE]
> Knihovny za běhu nyní obsahovat direktivy, aby se zabránilo kombinace různých typů. Zobrazí se toto upozornění, pokud se pokusíte použít různé typy nebo ladění a verze knihovny run-time ve stejném programu. Například, pokud kompilujete jeden soubor se má použít jeden druh knihovny run-time a jiný soubor, který použijete jiný typ (například ladění oproti maloobchodního prodeje) a propojují se pokusili, zobrazí se toto upozornění. Byste měli kompilovat všechny zdrojové soubory používat stejné knihovny run-time. Další informace najdete v tématu [/ / MD, / MT, /LD (použití knihovny Run-Time)](../../build/reference/md-mt-ld-use-run-time-library.md) – možnosti kompilátoru.

Můžete použít propojovacího programu [: lib](../../build/reference/verbose-print-progress-messages.md) přepínače a zjistěte, které knihovny, linker hledá. Například pokud spustitelný soubor používá knihovny Vícevláknová, bez ladění za běhu, v seznamu uvedena by měl zahrnovat LIBCMT.lib a ne LIBCMTD.lib, MSVCRT.lib nebo MSVCRTD.lib. Poznáte linkeru, aby ignorovat nesprávné knihovny za běhu pomocí [: / NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pro každou knihovnu, kterou chcete ignorovat.

Následující tabulka uvádí, které knihovny mají být ignorovány, v závislosti na tom, které knihovny run-time, kterou chcete použít. Na příkazovém řádku, použijte jednu **: / NODEFAULTLIB** možnost pro každou knihovnu ignorovat. V sadě Visual Studio IDE, oddělte knihoven k ignorování středníky v **ignorovat konkrétní výchozí knihovny** vlastnost.

| Použití této knihovny run-time | Ignorovat tyto knihovny |
|-----------------------------------|----------------------------|
| Vícevláknové (libcmt.lib) | msvcrt.lib; libcmtd.lib; msvcrtd.lib |
| Vícevláknové použití knihovny DLL (msvcrt.lib) | libcmt.lib; libcmtd.lib; msvcrtd.lib |
| Ladění vícevláknových (libcmtd.lib) | libcmt.lib; msvcrt.lib; msvcrtd.lib |
| Ladění vícevláknové použití knihovny DLL (msvcrtd.lib) | libcmt.lib; msvcrt.lib; libcmtd.lib |

Pokud obdržíte toto upozornění a chcete ji vytvořit spustitelný soubor, který používá bez ladění, DLL verze knihovny za běhu, můžete použít následující možnosti s linkeru:

```cmd
/NODEFAULTLIB:libcmt.lib NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```