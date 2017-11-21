---
title: "Stránky vlastností linkeru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs: C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c958b0bce27effc5362d107a3b6abe9fcc761d39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-property-pages"></a>Stránky vlastností linkeru
Toto téma popisuje následující vlastnosti na **Obecné** stránky vlastností linkeru:  
  
 **Ignorovat knihovny importu**  
 Informuje linkeru nechcete pokusí se propojit veškerý výstup lib generovaný z tohoto buildu do jakékoli závislé projektu. To umožňuje systému projektu zpracování souborů .dll, které nevytváří soubor LIB při sestavení. Když na projekt závisí na jiného projektu, který vytváří knihovny DLL, systém projektu odkaz automaticky soubor LIB vytvářený podřízeným projektem. Toto nemusí být nezbytné pro projekty, které jsou vytváření knihovny DLL modelu COM nebo pouze prostředky; Tyto knihovny DLL nemají žádný smysluplný export. Pokud žádné Export knihovny DLL, nebudou se generovat soubor LIB linkeru. Pokud žádný soubor LIB se nachází na disku a systému projektu říká linkeru pro propojení této knihovny DLL (chybějící), odkaz se nezdaří.  
  
 Použití **ignorovat knihovny importu** k vyřešení problému. Pokud nastavíte hodnotu `Yes`, bude systém projektu ignorovat existenci nebo neexistenci tohoto souboru LIB a způsobit, že všechny projekt, který závisí na tomto projektu není propojení s neexistující soubor LIB.  
  
 Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.  
  
 **Výstup registrace**  
 Spusťte regsvr32.exe /s $(TargetPath), která je platná pouze u projektů knihovny DLL. Pro projekty .exe tato vlastnost je ignorována. Pokud chcete zaregistrovat výstup .exe, nastavte konfiguraci událost na provede vlastní registrace, který je vždy vyžadován pro soubory .exe registrované.  
  
 Programový přístup, najdete v tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.  
  
 **Přesměrování na uživatele**  
 Registrace v sadě Visual Studio tradičně byla provedena v HKEY_CLASSES_ROOT (HKCR). S [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)]pro přístup k HKCR musíte Visual Studio spustit v režimu zvýšených oprávnění. Vývojáři vždy nechcete spustit v režimu zvýšených oprávnění, ale musí i nadále fungovat s registrací. Přesměrování na uživatele umožňuje zaregistrovat bez nutnosti spuštění v tomto režimu.  
  
 Přesměrování na uživatele vynutí všech zápisu do HKCR přesměrovat HKEY_CURRENT_USER (HKCU). Pokud je vypnutý přesměrování na uživatele, může to způsobit [chyby pro sestavení projektu PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) při pokusu zapsat do HKCR program.  
  
 **Propojení závislosti knihoven**  
 Umožňuje výběr propojení v .lib souborů, které jsou vytvářeny závislé projekty. Obvykle který chcete propojit v souboru LIB.  
  
 Můžete také určit soubor .obj zadáním názvu souboru a relativní cestu, například **... \\.. \MyLibProject\MyObjFile.obj**. Pokud zdrojový kód souboru .obj #includes předkompilovaných hlaviček, například pch.h, pak pch.obj soubor je umístěný ve stejné složce jako **MyObjFile.obj** a musíte taky přidat **pch.obj** jako další závislost.  
  
 **Použití vstupů závislosti knihovny**  
 Ve velkých projektech když závislé projektu vytvoří soubor LIB přírůstkové propojování zakázáno. Pokud existují mnoha závislé projektů, které vytvářejí soubory LIB, vytváření aplikace může trvat dlouhou dobu. Pokud je tato vlastnost nastavená na `Yes`, propojení projektu systému v souborech OBJ pro soubory LIB vyprodukované závislé projekty, čímž umožní přírůstkové propojení.  
  
 Informace o tom, jak získat přístup **Obecné** stránky vlastností linkeru, najdete v části [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
## <a name="see-also"></a>Viz také  
 [Adresáře VC ++, projekty a řešení, dialogové okno Možnosti](http://msdn.microsoft.com/en-us/e027448b-c811-4c3d-8531-4325ad3f6e02)   
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)