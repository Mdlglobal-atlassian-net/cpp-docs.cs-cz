---
title: Upozornění linkerů LNK4098
description: Popisuje, jakým způsobem nekompatibilní knihovny způsobují LINKERŮ LNK4098 upozornění nástrojů linkeru a jak je lze opravit pomocí/NODEFAULTLIB.
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682947"
---
# <a name="linker-tools-warning-lnk4098"></a>Upozornění linkerů LNK4098

> DEFAULTLIB '*Library*' je v konfliktu s použitím jiných knihovny; použití/NODEFAULTLIB:*Library*

Pokoušíte se propojit s nekompatibilními knihovnami.

> [!NOTE]
> Běhové knihovny nyní obsahují direktivy, které zabraňují smíchání různých typů. Toto upozornění se zobrazí, pokud se pokusíte použít různé typy nebo ladit a neladit verze knihovny run-time ve stejném programu. Pokud jste například zkompilujete jeden soubor, abyste použili jeden typ knihovny run-time a jiný soubor pro použití jiného typu (například ladění oproti maloobchodním) a pokusili jste se ho propojit, zobrazí se toto upozornění. Všechny zdrojové soubory byste měli kompilovat pro použití stejné knihovny run-time. Další informace naleznete v tématu [/MD,/MT,/LD (použití běhové knihovny)](../../build/reference/md-mt-ld-use-run-time-library.md) – možnosti kompilátoru.

K zjištění, které knihovny vyhledává linker, můžete použít přepínač linkeru [/verbose: lib](../../build/reference/verbose-print-progress-messages.md) . Například pokud váš spustitelný soubor používá vícevláknové běhové knihovny, které nejsou ladit, seznam hlášených by měl obsahovat LIBCMT. lib, nikoli LIBCMTD. lib, MSVCRT. lib nebo MSVCRTD. lib. Můžete říct, že linker bude ignorovat nesprávné knihovny run-time pomocí [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pro každou knihovnu, kterou chcete ignorovat.

Následující tabulka ukazuje, které knihovny by se měly ignorovat v závislosti na tom, která knihovna run-time se má použít. Na příkazovém řádku použijte jednu možnost **/NODEFAULTLIB** pro každou knihovnu, kterou chcete ignorovat. V integrovaném vývojovém prostředí sady Visual Studio oddělte knihovny tak, aby byly ignorovány středníky ve vlastnosti **výchozí knihovny ignorovat specifické** .

| Použití této knihovny run-time | Ignorovat tyto knihovny |
|-----------------------------------|----------------------------|
| Vícevláknové (Libcmt. lib) | Msvcrt. lib; LIBCMTD. lib; msvcrtd. lib |
| Multithreading pomocí knihovny DLL (Msvcrt. lib) | Libcmt. lib; LIBCMTD. lib; msvcrtd. lib |
| Ladění s více vlákny (LIBCMTD. lib) | Libcmt. lib; Msvcrt. lib; msvcrtd. lib |
| Ladění s více vlákny pomocí knihovny DLL (msvcrtd. lib) | Libcmt. lib; Msvcrt. lib; LIBCMTD. lib |

Například pokud jste obdrželi toto upozornění a chcete vytvořit spustitelný soubor, který používá jinou verzi knihovny run-time DLL, můžete použít následující možnosti s linkerem:

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
