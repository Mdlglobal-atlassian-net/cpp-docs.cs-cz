---
title: Generování manifestu v aplikaci Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: eabd488e581357ec1386b20597c1987e4c8b2c19
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809727"
---
# <a name="manifest-generation-in-visual-studio"></a>Generování manifestu v aplikaci Visual Studio

Generování souboru manifestu pro konkrétní projekt se dá řídit v projektu **stránky vlastností** dialogového okna. Na **vlastnosti konfigurace** klikněte na tlačítko **Linkeru**, pak **soubor manifestu**, pak **generovat Manifest**. Vlastnosti projektu pro nové projekty jsou ve výchozím nastavení generovat soubor manifestu. Je ale možné zakázat generování manifestu pro projekt používá **generovat Manifest** vlastnost projektu. Pokud je tato vlastnost nastavena na **Ano**, vygeneruje manifest pro tento projekt. V opačném případě linkeru ignoruje informace o sestavení při řešení závislostí v kódu aplikace a nevygeneruje žádný manifest.

Systém sestavení v sadě Visual Studio umožňuje manifest vložený do souboru konečného binárního aplikace, nebo generovány jako externího souboru. Toto chování se řídí **vložit Manifest** možnost **vlastnosti projektu** dialogového okna. Chcete-li tuto vlastnost nastavte, otevřete **Nástroj Manifest** uzlu, pak vyberte **vstupní a výstupní**. Pokud manifest není vložená, je generována jako externí soubor a uloží do stejného adresáře jako koncovém binárním souboru. Pokud je manifest vložený, Visual Studio vloží konečné manifesty provedením následujících kroků:

1. Po zdrojový kód je zkompilován do souborů objektu, linker shromažďuje informace o závislého sestavení. Při propojování koncovém binárním souboru, linker generuje zprostředkující manifestu, který se použije v pozdější ke generování manifestu poslední.

1. Po dokončení zprostředkující manifestu a vytváření odkazů, nástroj manifest se spustí sloučení konečné manifestu a uložte ho jako externího souboru.

1. Projekt sestavovací systém a zjistí, zda manifest generovaný nástrojem manifestu obsahuje jiné informace než již vložen do binárního souboru manifestu.

1. Je-li manifest vložen do binárního souboru se liší od manifest generovaný nástrojem manifestu nebo binární soubor neobsahuje vložený manifest, Visual Studio vyvolá linker ještě jednou k vložení do binárního souboru jako externí soubor manifestu prostředek.

1. Je-li manifest vložen do binárního souboru je stejný jako v manifestu generované nástroj manifest, sestavení bude pokračovat na další kroky sestavení.

Je manifest vložený v koncovém binárním souboru jako prostředek text a bude možné dokument zobrazit tak, že otevřete koncovém binárním souboru jako soubor v sadě Visual Studio. Aby bylo zajištěno, že manifest se odkazuje na správný knihovny, postupujte podle kroků popsaných v [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md) nebo postupujte podle doporučení podle [Poradce při potížích s](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) oddílu.

## <a name="see-also"></a>Viz také:

[Základní informace o generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
