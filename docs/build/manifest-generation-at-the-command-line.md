---
title: Generování manifestu v příkazovém řádku
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493193"
---
# <a name="manifest-generation-at-the-command-line"></a>Generování manifestu v příkazovém řádku

Při sestavování aplikací C/C++ z příkazového řádku pomocí nástroje NMAKE nebo podobných nástrojů je manifest vygenerován poté, co linker zpracovává všechny soubory objektů a sestavil konečný binární soubor. Linker shromáždí informace o sestavení uložené v souborech objektů a zkombinuje tyto informace do finálního souboru manifestu. Ve výchozím nastavení linker vygeneruje soubor s názvem *binary_name*. *přípona*. manifest pro popis finálního binárního souboru. Linker nevloží soubor manifestu do binárního souboru a může vytvořit pouze manifest jako externí soubor. Existuje několik způsobů, jak vložit manifest do finálního binárního souboru, například pomocí [nástroje manifest (Mt. exe)](/windows/win32/sbscs/mt-exe) nebo kompilování manifestu do souboru prostředků. Je důležité mít na paměti, že při vložení manifestu do finálního binárního souboru se musí dodržovat konkrétní pravidla, která tyto funkce umožní jako přírůstkové propojování, podepisování a úpravy a pokračování. Tyto a další možnosti jsou popsány v tématu [Postupy: vložení manifestu do aplikace C/C++](how-to-embed-a-manifest-inside-a-c-cpp-application.md) při sestavování na příkazovém řádku.

## <a name="see-also"></a>Viz také

[Manifesty](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (inkrementální odkaz)](reference/incremental-link-incrementally.md)<br/>
[Sestavení se silným názvem (Podepisování sestavení) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Operace Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)<br/>
[Základní informace o generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
