---
title: Generování manifestu v aplikaci Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273355"
---
# <a name="manifest-generation-in-visual-studio"></a>Generování manifestu v aplikaci Visual Studio

Generování souboru manifestu pro konkrétní projekt lze ovládat v dialogovém okně **stránky vlastností** projektu. Na kartě **Vlastnosti konfigurace** klikněte na **linker**, pak na **soubor manifestu**a pak na **Generovat Manifest**. Ve výchozím nastavení jsou vlastnosti projektu pro nové projekty nastaveny k vygenerování souboru manifestu. Je však možné zakázat generování manifestu pro projekt pomocí vlastnosti **Generovat Manifest** projektu. Pokud je tato vlastnost nastavená na **hodnotu Ano**, manifest pro tento projekt se vygeneruje. V opačném případě linker ignoruje informace o sestavení při vyhodnocování závislostí kódu aplikace a negeneruje manifest.

Systém sestavení v aplikaci Visual Studio umožňuje vložit manifest do finálního binárního souboru aplikace nebo vygenerovaný jako externí soubor. Toto chování je řízeno možností pro **vložení manifestu** v dialogovém okně **Vlastnosti projektu** . Chcete-li nastavit tuto vlastnost, otevřete uzel **nástroje manifestu** a pak vyberte **vstup a výstup**. Pokud manifest není vložený, vygeneruje se jako externí soubor a uloží se do stejného adresáře jako finální binární soubor. Pokud je manifest vložen, Visual Studio vloží konečné manifesty pomocí následujícího procesu:

1. Po kompilaci zdrojového kódu do souborů objektů linker shromáždí informace o závislém sestavení. Při propojování finálního binárního souboru linker vygeneruje zprostředkující manifest, který se později použije ke generování konečného manifestu.

1. Po dokončení zprostředkujícího manifestu a propojení se spustí nástroj manifest, který sloučí finální manifest a uloží ho jako externí soubor.

1. Systém sestavení projektu pak zjistí, zda manifest generovaný nástrojem manifest obsahuje jiné informace než manifest, který je již vložen v binárním souboru.

1. Pokud je manifest vložený v binárním souboru odlišný od manifestu generovaného nástrojem manifestu nebo binární soubor neobsahuje vložený manifest, Visual Studio vyvolá linker ještě jednou k vložení externího souboru manifestu do binárního souboru jako prostředku.

1. Pokud je manifest vložený v binárním souboru stejný jako manifest generovaný nástrojem manifestu, sestavení bude pokračovat dalším postupem sestavení.

Manifest je vložen do finálního binárního souboru jako textový zdroj a lze jej zobrazit otevřením finálního binárního souboru jako souboru v aplikaci Visual Studio. Chcete-li zajistit, aby manifest odkazoval na správné knihovny, postupujte podle kroků popsaných v tématu [Principy závislostí Visual C++ aplikace](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) nebo postupujte podle návrhů popsaných v části [řešení potíží](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) .

## <a name="see-also"></a>Viz také

[Základní informace o generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
