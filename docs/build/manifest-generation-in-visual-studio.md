---
title: Generování manifestu v sadě Visual Studio | Dokumentace Microsoftu
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
ms.openlocfilehash: 6f927e153c25b41b48b783281a36dd2705e42006
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205797"
---
# <a name="manifest-generation-in-visual-studio"></a>Generování manifestu v aplikaci Visual Studio
Generování souboru manifestu pro konkrétní projekt se dá řídit v projektu **stránky vlastností** dialogového okna. Na **vlastnosti konfigurace** klikněte na tlačítko **Linkeru**, pak **soubor manifestu**, pak **generovat Manifest**. Vlastnosti projektu pro nové projekty jsou ve výchozím nastavení generovat soubor manifestu. Je ale možné zakázat generování manifestu pro projekt používá **generovat Manifest** vlastnost projektu. Pokud je tato vlastnost nastavena na **Ano**, vygeneruje manifest pro tento projekt. V opačném případě linkeru ignoruje informace o sestavení při řešení závislostí v kódu aplikace a nevygeneruje žádný manifest.  
  
 Systém sestavení v sadě Visual Studio umožňuje manifest vložený do souboru konečného binárního aplikace, nebo generovány jako externího souboru. Toto chování se řídí **vložit Manifest** možnost **vlastnosti projektu** dialogového okna. Chcete-li tuto vlastnost nastavte, otevřete **Nástroj Manifest** uzlu, pak vyberte **vstupní a výstupní**. Pokud manifest není vložená, je generována jako externí soubor a uloží do stejného adresáře jako koncovém binárním souboru. Pokud je manifest vložený, Visual Studio vloží konečné manifesty provedením následujících kroků:  
  
1.  Po zdrojový kód je zkompilován do souborů objektu, linker shromažďuje informace o závislého sestavení. Při propojování koncovém binárním souboru, linker generuje zprostředkující manifestu, který se použije v pozdější ke generování manifestu poslední.  
  
2.  Po dokončení zprostředkující manifestu a vytváření odkazů, nástroj manifest se spustí sloučení konečné manifestu a uložte ho jako externího souboru.  
  
3.  Projekt sestavovací systém a zjistí, zda manifest generovaný nástrojem manifestu obsahuje jiné informace než již vložen do binárního souboru manifestu.  
  
4.  Je-li manifest vložen do binárního souboru se liší od manifest generovaný nástrojem manifestu nebo binární soubor neobsahuje vložený manifest, Visual Studio vyvolá linker ještě jednou k vložení do binárního souboru jako externí soubor manifestu prostředek.  
  
5.  Je-li manifest vložen do binárního souboru je stejný jako v manifestu generované nástroj manifest, sestavení bude pokračovat na další kroky sestavení.  
  
 Je manifest vložený v koncovém binárním souboru jako prostředek text a bude možné dokument zobrazit tak, že otevřete koncovém binárním souboru jako soubor v sadě Visual Studio. Aby bylo zajištěno, že manifest se odkazuje na správný knihovny, postupujte podle kroků popsaných v [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) nebo postupujte podle doporučení podle [Poradce při potížích s](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) oddílu.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vložení manifestu do aplikace C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)   
 [O soukromých sestaveních](/windows/desktop/SbsCs/about-private-assemblies-)   
 [Nástroj manifest](/windows/desktop/SbsCs/mt-exe)   
 [Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)