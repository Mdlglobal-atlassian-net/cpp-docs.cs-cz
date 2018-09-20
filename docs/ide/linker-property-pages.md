---
title: Stránky vlastností linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/21/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs:
- C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec1620d9ae84e5c0b957b7426ad388c70626813
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379213"
---
# <a name="linker-property-pages"></a>Stránky vlastností linkeru

Toto téma popisuje následující vlastnosti na **Obecné** stránky vlastností linkeru. Verzi Linuxu na této stránce, najdete v části [vlastnosti Linkeru (Linux C++)](../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Obecná stránka vlastností

### <a name="ignore-import-library"></a>Ignorovat knihovnu importů

Tato vlastnost říká linkeru, aby propojení veškerý výstup lib generovaný z tohoto buildu do jakékoli závislý projekt. To umožňuje projektový systém ke zpracování souborů DLL, které záměrně neprodukují .lib soubor při sestavení. Pokud projekt závisí na jiný projekt, který vytváří knihovnu DLL, systém projektu automaticky propojí .lib soubor vytvořený pomocí podřízených projektu. To nemusí být potřeba projekty, které vytvářejí knihovny COM DLL nebo knihovny DLL pouze prostředků; Tyto knihovny DLL nemají žádné smysluplné exporty. Pokud knihovna DLL nemá žádné exporty, linker nevygeneruje soubor LIB. Pokud není žádný export .lib soubor na disk a systém projektu přikazuje linkeru, aby propojení této knihovny DLL (chybějící), odkaz se nezdaří. Použití **ignorovat knihovnu importu** nastavte na tento problém vyřešit. Pokud je nastavena na **Ano**, systém projektu ignoruje přítomnosti nebo nepřítomnosti souborů .lib a způsobí, že jakýkoli projekt, který závisí na tomto projektu pro není propojení neexistující soubor LIB.

Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Registrovat výstup

Spuštění `regsvr32.exe /s $(TargetPath)` na výstupu sestavení, který je platná pouze u projektů knihovny DLL. Pro projekty, .exe tato vlastnost se ignoruje. Registrovat výstup .exe, nastavte v konfiguraci provedete vlastní registraci, která je vždy vyžadován pro soubory .exe registrované postbuild událost.

Programový přístup k této vlastnosti, najdete v článku <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Přesměrování pro uživatele

Registrace v sadě Visual Studio tradičně byla provedena HKEY_CLASSES_ROOT (HKCR). S Windows Vista a novějších operačních systémech pro přístup k HKCR musíte spustit aplikaci Visual Studio v režimu se zvýšenými oprávněními. Vývojáři vždy nechcete spustit v režimu se zvýšenými oprávněními, ale musí i nadále fungovat s registrací. Přesměrování dle uživatele můžete se zaregistrovat, aniž by bylo nutné v tomto režimu.

Přesměrování dle uživatele vynutí pro jakékoli zápisy HKCR přesměrovat na HKEY\_aktuální\_uživatele (HKCU). Pokud je vypnutý přesměrování pro uživatele, může to způsobit [chyba sestavení projektu PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) při program pokouší o zápis pro HKCR.

### <a name="link-library-dependencies"></a>Propojit závislé položky knihoven

Určuje, jestli se má propojit soubory .lib, které vytváří závislých projektů. Obvykle který chcete propojit v soubory .lib, ale to nemusí být v případě určité knihovny DLL.

Soubor .obj lze také určit zadáním názvu souboru a relativní cestu, například ".. \\.. \MyLibProject\MyObjFile.obj". Pokud zdrojový kód souboru .obj #includes předkompilované hlavičky, například soubor pch.h, pak je soubor pch.obj umístěn ve stejné složce jako MyObjFile.obj a pch.obj musíte taky přidat jako další závislost.

### <a name="use-library-dependency-inputs"></a>Použít vstupy závislých položek knihoven

Ve velkých projektech když to závislý projekt vytvoří soubor LIB přírůstkové propojení se vypne. Pokud existují mnoho závislých projektů, které vytvářejí soubory LIB, sestavení aplikace může trvat dlouhou dobu. Pokud je tato vlastnost nastavena na **Ano**, odkazy systému projektu v souborech .obj pro soubory LIB vytvářených závislých projektů, což umožní přírůstkové propojení.

Informace o tom, jak získat přístup **Obecné** stránky vlastností linkeru, naleznete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Viz také:

[Nastavení projektu VC++, Projekty a řešení, dialogové okno Možnosti](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)<br>
[Stránky vlastností](../ide/property-pages-visual-cpp.md)