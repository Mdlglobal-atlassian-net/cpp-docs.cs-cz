---
title: Generování manifestu v sadě Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73b5cbe631d078dd6ee27b4f7e0a97503c36638b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="manifest-generation-in-visual-studio"></a>Generování manifestu v aplikaci Visual Studio
Generování souboru manifestu pro konkrétní projekt se dá řídit v projektu **stránky vlastností** dialogové okno. Na **vlastnosti konfigurace** , klikněte na **Linkeru**, pak **souboru Manifest**, pak **generovat Manifest**. Ve výchozím nastavení jsou nastaveny vlastnosti projektu nové projekty generovat soubor manifestu. Je ale možné zakázat generování manifestu pro projekt pomocí **generovat Manifest** vlastnosti projektu. Pokud je tato vlastnost nastavená na **Ano**, se generuje manifest pro tento projekt. V opačném případě linkeru ignoruje informací o sestavení při rozpoznávání závislostem kódu aplikace a negeneruje manifest.  
  
 Systém sestavení v sadě Visual Studio umožňuje manifest vložených v souboru konečné binární aplikace, nebo jako externí soubor. Toto chování je řízeno **vložení manifestu** možnost **vlastnosti projektu** dialogové okno. Pokud chcete nastavit tuto vlastnost, otevřete **Nástroj Manifest** uzlu, pak vyberte **vstup a výstup**. Pokud není vložená manifest, je jako externí soubor a uložit do stejného adresáře jako poslední binární. Pokud je vložen do manifestu, Visual Studio vloží konečné manifesty provedením následujících kroků:  
  
1.  Potom, co zdrojový kód je zkompilovány do souborů objekt, linkeru shromažďuje informace závislého sestavení. Při propojování konečné binární, linkeru generuje manifest zprostředkující, který slouží ke generování manifestu konečné později.  
  
2.  Po dokončení mezilehlých manifestu a propojení nástroje manifestu bude proveden sloučení konečné manifestu a uložte ho jako externí soubor.  
  
3.  Projekt sestavení systému a zjistí, zda manifest generovaný nástrojem manifestu obsahuje jiné informace než již vložený do binárního souboru manifest.  
  
4.  Pokud vložené do binárního souboru manifestu se liší od manifest generovaný nástrojem manifestu nebo binární soubor neobsahuje vložený manifest, Visual Studio bude vyvolání linkeru ještě jednou pro vložení externí soubor manifestu uvnitř binární soubor jako prostředek.  
  
5.  Pokud vložené do binárního souboru manifestu je stejný jako manifest generovaný nástrojem manifestu, sestavení bude pokračovat na další kroky sestavení.  
  
 Manifest je vložena do konečné binární soubor jako prostředek text a prohlížení otevřením konečné binární jako soubor v sadě Visual Studio. Aby se zajistilo, že manifest odkazuje na správný knihovny, postupujte podle kroků popsaných v [Principy závislostí aplikace Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) nebo postupujte podle doporučení popsaných v [Poradce při potížích s](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) části.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vložení manifestu do aplikace C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [O privátní sestavení](http://msdn.microsoft.com/library/ff951638)   
 [Nástroj manifest](http://msdn.microsoft.com/library/aa375649)   
 [Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)