---
title: Generování manifestu v příkazovém řádku | Dokumentace Microsoftu
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
ms.openlocfilehash: 97e2bb423deb4a50da0cf0772ae81e19bb4b48eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220724"
---
# <a name="manifest-generation-at-the-command-line"></a>Generování manifestu v příkazovém řádku
Při vytváření aplikací C/C++ z příkazového řádku pomocí nmake nebo podobné nástroje, manifest se vygeneruje po zpracování všech souborů objektů a vytvořené koncovém binárním souboru linkeru. Propojovací program shromažďuje informace o sestavení, které jsou uloženy v souborech objektů a slučuje tyto informace do konečného souboru manifestu. Ve výchozím nastavení bude linkeru generovat soubor s názvem < binary_name >. \<přípona > .manifest k popisu koncovém binárním souboru. Propojovací program nelze vložit soubor manifestu do binárního souboru a můžou jenom generovat manifest jako externího souboru. Existuje několik způsobů pro vložení manifestu do konečného binárního souboru, jako je třeba použití [Nástroj Manifest (mt.exe)](https://msdn.microsoft.com/library/aa375649) nebo kompilování manifestu do souboru prostředků. Je důležité mít na paměti, které určitá pravidla platí při vkládání manifestu v koncovém binárním souboru k povolení funkcí, jako přírůstkové propojování, podepisování, a upravit a pokračovat. Tyto a další možnosti jsou popsány v [postupy: vložení manifestu uvnitř jazyka C/C++ aplikace](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) při sestavování v příkazovém řádku.  
  
## <a name="see-also"></a>Viz také  
 [Manifesty](https://msdn.microsoft.com/library/aa375365)   
 [/ INCREMENTAL (Inkrementální odkaz)](../build/reference/incremental-link-incrementally.md)   
 [Sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)   
 [Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)