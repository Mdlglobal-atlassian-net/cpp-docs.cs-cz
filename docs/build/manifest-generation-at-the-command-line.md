---
title: "Generování manifestu v příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bbbee2fc1402a49aa773afc8eb6ae830edaffcc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="manifest-generation-at-the-command-line"></a>Generování manifestu v příkazovém řádku
Při sestavování aplikací C/C++ z příkazového řádku pomocí nmake nebo podobné nástrojů, manifest se generuje po linkeru má zpracovat všechny soubory objektů a vytvořené konečné binárního souboru. Linkeru shromažďuje informace o sestavení, které jsou uložené v souborech objektu a kombinuje tyto informace do konečné souboru manifestu. Ve výchozím nastavení vygeneruje linkeru do souboru s názvem < binary_name >. \<rozšíření > Manifest k popisu konečné binárního souboru. Linkeru nevloží soubor manifestu uvnitř binárního souboru a můžete pouze generování manifestu jako externí soubor. Existuje několik způsobů pro vložení manifestu do konečné binárního souboru, například pomocí [Nástroj Manifest (mt.exe)](http://msdn.microsoft.com/library/aa375649) nebo kompilování manifest do souboru prostředků. Je důležité mějte na paměti, které specifická pravidla k při vložení manifestu do konečné binárního souboru k povolení funkcí, jako jsou přírůstkové propojování dodržovat podepisování, upravit a pokračovat. Tyto a další možnosti jsou popsané v [postupy: vložení manifestu uvnitř C/C++ aplikace](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) při sestavování na příkazovém řádku.  
  
## <a name="see-also"></a>Viz také  
 [Manifesty](http://msdn.microsoft.com/library/aa375365)   
 [/ INCREMENTAL (Inkrementální odkaz)](../build/reference/incremental-link-incrementally.md)   
 [Sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Upravit a pokračovat](/visualstudio/debugger/edit-and-continue)   
 [Principy generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)