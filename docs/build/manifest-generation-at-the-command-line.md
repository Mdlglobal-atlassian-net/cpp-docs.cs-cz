---
title: Generování manifestu v příkazovém řádku
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 440bf785f61a438099a394319a6df6e7389a608d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692525"
---
# <a name="manifest-generation-at-the-command-line"></a>Generování manifestu v příkazovém řádku

Při vytváření aplikací C/C++ z příkazového řádku pomocí nmake nebo podobné nástroje, manifest se vygeneruje po zpracování všech souborů objektů a vytvořené koncovém binárním souboru linkeru. Propojovací program shromažďuje informace o sestavení, které jsou uloženy v souborech objektů a slučuje tyto informace do konečného souboru manifestu. Ve výchozím nastavení bude linkeru generovat soubor s názvem *binary_name*. *rozšíření*.manifest k popisu koncovém binárním souboru. Propojovací program nelze vložit soubor manifestu do binárního souboru a můžou jenom generovat manifest jako externího souboru. Existuje několik způsobů pro vložení manifestu do konečného binárního souboru, jako je třeba použití [Nástroj Manifest (mt.exe)](https://msdn.microsoft.com/library/aa375649) nebo kompilování manifestu do souboru prostředků. Je důležité mít na paměti, které určitá pravidla platí při vkládání manifestu v koncovém binárním souboru k povolení funkcí, jako přírůstkové propojování, podepisování, a upravit a pokračovat. Tyto a další možnosti jsou popsány v [postupy: vložení manifestu uvnitř jazyka C/C++ aplikace](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) při sestavování v příkazovém řádku.

## <a name="see-also"></a>Viz také

[Manifesty](/windows/desktop/sbscs/manifests)<br/>
[/INCREMENTAL (přírůstkové propojení)](../build/reference/incremental-link-incrementally.md)<br/>
[Sestavení se silným názvem (podepisování sestavení) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Operace Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)<br/>
[Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)<br/>
