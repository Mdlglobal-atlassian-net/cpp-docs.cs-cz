---
title: "Stránka vlastností adresářů VC ++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs: C++
helpviewer_keywords: VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30a54b1d90585e6433f059acf30991ca53948d60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vc-directories-property-page"></a>Stránka vlastností adresářů VC++
Určuje adresáře, které aplikace Visual Studio použije k sestavení projektu. Pro přístup k této stránky vlastností v **Průzkumníku řešení**, otevřete místní nabídku pro projekt a vyberte možnost **vlastnosti**a potom v levém podokně **stránky vlastností** Dialogové okno, rozbalte seznam **vlastnosti konfigurace** a vyberte **adresáře VC ++**.  
  
 Při vytvoření projektu pomocí aplikace Visual Studio zdědí projekt určité adresáře. Mnohé z nich jsou uvedeny jako makra. K prozkoumání aktuální hodnotu makra, v pravém podokně **adresáře VC ++** vyberte řádek – například **adresáře Include**– zvolte tlačítko šipky dolů na pravé straně a potom vyberte  **Upravit**a potom v dialogovém okně, které se zobrazí, vyberte **makra** tlačítko. Další informace najdete v tématu tyto příspěvky blogu: [adresáře VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [zděděné vlastnosti a seznam vlastností](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), a [Visual Studio 2010 C++ projektu průvodci upgradem](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Typy adresářů  
 Můžete zadat také další adresáře, a to následujícím způsobem.  
  
 **Spustitelný soubor adresáře**  
 Adresáře, ve kterých se mají vyhledávat spustitelné soubory. Odpovídá **cesta** proměnné prostředí.  
  
 **Zahrnout adresáře**  
 Adresáře, ve kterých se mají vyhledávat vkládané soubory, na něž je odkazováno ze zdrojového kódu. Odpovídá **zahrnout** proměnné prostředí.  
  
 **Referenční dokumentace adresáře**  
 Adresáře, ve kterém se má hledat sestavení a soubory modulu (metadata), které jsou odkazované ve zdrojovém kódu pomocí [#using](../preprocessor/hash-using-directive-cpp.md) – direktiva. Odpovídá **LIBPATH** proměnné prostředí.  
  
 **Adresáře knihovny**  
 Adresáře, ve kterých se mají vyhledávat soubory knihoven (.lib), včetně knihoven prostředí runtime. Odpovídá **LIB** proměnné prostředí. Toto nastavení se nevztahuje na soubory .obj; pro odkaz na soubor .obj na [Linkeru](../ide/linker-property-pages.md)**Obecné** stránka vlastností, vyberte **Další závislosti knihovny** a pak zadejte relativní cesta k souboru.  
  
 **Zdrojové adresáře**  
 Adresáře, ve kterých se mají vyhledávat zdrojové soubory pro IntelliSense.  
  
 **Vyloučit adresáře**  
 Adresáře, ve kterých se během vytváření závislostí nemá vyhledávat.  
  
#### <a name="to-specify-or-modify-directory-settings"></a>Specifikace a změna nastavení adresáře  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro projekt, kterou chcete změnit a potom zvolte **vlastnosti**.  
  
2.  V levém podokně **stránky vlastností** dialogové okno, rozbalte seznam **vlastnosti konfigurace** a pak vyberte **adresáře VC ++**.  
  
3.  Na jednom ze seznamů directory upravit, vyberte ho, zvolte tlačítko šipky dolů na pravé straně a pak zvolte **upravit**.  
  
     V rozevíracím seznamu dialogového okna, které se objeví, můžete přidat nebo odebrat hodnoty a změnit pořadí, v jakém se hodnoty zobrazují. Můžete také změnit zda projektu dědí nastavení zaškrtnutím nebo zrušením zaškrtnutí **zděděné z nadřazené nebo produktu project výchozí**.  
  
## <a name="sharing-the-settings"></a>Sdílení nastavení  
 Vlastnosti projektu můžete sdílet s dalšími uživateli nebo napříč počítači. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
