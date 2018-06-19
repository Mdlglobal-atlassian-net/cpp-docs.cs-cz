---
title: Generování manifestu v příkazovém řádku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f740030e48a33284a31da4ebd46f0c4d7b6ac7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368496"
---
# <a name="manifest-generation-at-the-command-line"></a>Generování manifestu v příkazovém řádku
Při sestavování aplikací C/C++ z příkazového řádku pomocí nmake nebo podobné nástrojů, manifest se generuje po linkeru má zpracovat všechny soubory objektů a vytvořené konečné binárního souboru. Linkeru shromažďuje informace o sestavení, které jsou uložené v souborech objektu a kombinuje tyto informace do konečné souboru manifestu. Ve výchozím nastavení vygeneruje linkeru do souboru s názvem < binary_name >. \<rozšíření > Manifest k popisu konečné binárního souboru. Linkeru nevloží soubor manifestu uvnitř binárního souboru a můžete pouze generování manifestu jako externí soubor. Existuje několik způsobů pro vložení manifestu do konečné binárního souboru, například pomocí [Nástroj Manifest (mt.exe)](http://msdn.microsoft.com/library/aa375649) nebo kompilování manifest do souboru prostředků. Je důležité mějte na paměti, které specifická pravidla k při vložení manifestu do konečné binárního souboru k povolení funkcí, jako jsou přírůstkové propojování dodržovat podepisování, upravit a pokračovat. Tyto a další možnosti jsou popsané v [postupy: vložení manifestu uvnitř C/C++ aplikace](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) při sestavování na příkazovém řádku.  
  
## <a name="see-also"></a>Viz také  
 [Manifesty](http://msdn.microsoft.com/library/aa375365)   
 [/ INCREMENTAL (Inkrementální odkaz)](../build/reference/incremental-link-incrementally.md)   
 [Sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)   
 [Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)