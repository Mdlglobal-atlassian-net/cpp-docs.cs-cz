---
title: Stránky vlastností linkeru | Microsoft Docs
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
ms.openlocfilehash: 2cec232bb4e4f2f6ac1ab9af703b368eec0ba5dd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33331516"
---
# <a name="linker-property-pages"></a>Stránky vlastností linkeru

Toto téma popisuje následující vlastnosti na **Obecné** stránky vlastností linkeru. Linux verzi této stránce, naleznete v části [Linkeru vlastnosti (Linux C++)](../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Obecná stránka vlastností

### <a name="ignore-import-library"></a>Ignorovat knihovny importu

Tato vlastnost určuje linkeru nepropojíte veškerý výstup lib generovaný z tohoto buildu do jakékoli závislé projektu. To umožňuje systému projektu zpracování souborů .dll, které nevytváří soubor LIB při sestavení. Pokud projekt závisí na jiného projektu, který vytváří knihovny DLL, systém projektu automaticky propojí soubor LIB této podřízené projektu. Toto nemusí být nezbytné pro projekty, které jsou vytváření knihovny DLL modelu COM nebo pouze prostředky; Tyto knihovny DLL nemají žádný smysluplný export. Pokud žádné Export knihovny DLL, linkeru negeneruje soubor LIB. Pokud žádný soubor LIB se nachází na disku a systému projektu říká linkeru pro propojení této knihovny DLL (chybějící), odkaz se nezdaří. Použití **ignorovat knihovny importu** vlastnost k vyřešení problému. Pokud nastavíte hodnotu **Ano**, systém projektu ignoruje existenci nebo neexistenci tohoto souboru LIB a způsobí, že všechny projekt, který závisí na tomto projektu není propojení s neexistující soubor LIB.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Výstup registrace

Spustí `regsvr32.exe /s $(TargetPath)` na výstupu sestavení, který je platný pouze u projektů knihovny DLL. Pro projekty .exe tato vlastnost je ignorována. Výstup .exe zaregistrovat, nastavte konfiguraci událost v konfiguraci na provede vlastní registraci, který je vždy vyžadován pro soubory .exe registrované.

Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Přesměrování na uživatele

Registrace v sadě Visual Studio tradičně byla provedena v HKEY_CLASSES_ROOT (HKCR). Windows Vista a novějších operačních systémech pro přístup k HKCR musíte spustit Visual Studio v režimu zvýšených oprávnění. Vývojáři vždy nechcete spustit v režimu zvýšených oprávnění, ale musí i nadále fungovat s registrací. Přesměrování na uživatele umožňuje zaregistrovat bez nutnosti spuštění v tomto režimu.

Přesměrování na uživatele vynutí všech zápisu do HKCR přesměrovat na HKEY\_aktuální\_uživatele (HKCU). Pokud je vypnutý přesměrování na uživatele, může to způsobit [chyby pro sestavení projektu PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) při pokusu zapsat do HKCR program.

### <a name="link-library-dependencies"></a>Propojení závislosti knihoven

Určuje, zda propojení .lib souborů, které jsou vytvářeny závislé projekty. Obvykle můžete propojit v soubory .lib, ale nemusí být případ určité knihovny DLL.

Můžete také určit soubor .obj zadáním názvu souboru a relativní cestu, například ".. \\.. \MyLibProject\MyObjFile.obj". Pokud zdrojový kód souboru .obj #includes předkompilovaných hlaviček, například pch.h pch.obj soubor je umístěný ve stejné složce jako MyObjFile.obj a pch.obj musíte taky přidat jako další závislosti.

### <a name="use-library-dependency-inputs"></a>Použití vstupů závislosti knihovny

Ve velkých projektech když závislé projektu vytvoří soubor LIB přírůstkové propojování zakázáno. Pokud existují mnoha závislé projektů, které vytvářejí soubory LIB, vytváření aplikace může trvat dlouhou dobu. Pokud je tato vlastnost nastavená na **Ano**, propojení projektu systému v souborech OBJ pro soubory LIB vyprodukované závislé projekty, čímž umožní přírůstkové propojení.

Informace o tom, jak získat přístup **Obecné** stránky vlastností linkeru, najdete v části [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Viz také:

[Nastavení projektu VC ++, projekty a řešení, dialogové okno Možnosti](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[Stránky vlastností](../ide/property-pages-visual-cpp.md)  