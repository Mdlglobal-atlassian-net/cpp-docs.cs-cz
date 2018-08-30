---
title: -MANIFEST (vytvoření manifestu sestavení vedle sebe) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
dev_langs:
- C++
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cdf0f5d1d736635af3d7bf1a853e9002e072ef5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199110"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (vytvoření manifestu souběžného sestavení)
```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## <a name="remarks"></a>Poznámky  
 Volba /MANIFEST určuje, že má linker vytvořit souběžný soubor manifestu. Další informace o souborech manifestu naleznete v tématu [referenční příručka souborů manifestu](/windows/desktop/SbsCs/manifest-files-reference).  
  
 Výchozí hodnota je /MANIFEST.  
  
 Volba /MANIFEST:EMBED určuje, že má linker vložit soubor manifestu do bitové kopie jako prostředek typu RT_MANIFEST. Volitelný parametr `ID` je ID prostředku, které se použije pro manifest. Pro spustitelný soubor použijte hodnotu 1. Pro knihovnu DLL použijte hodnotu 2, aby bylo možné určit soukromé závislosti. Pokud parametr `ID` není zadán, výchozí hodnota je 2, pokud je nastavena volba /DLL. Jinak je výchozí hodnota 1.  
  
 Od verze Visual Studio 2008, soubory manifestu spustitelných souborů obsahují oddíl, který určuje informace o řízení uživatelských účtů (UAC). Pokud zadáte volbu/manifest, ale nezadáte [/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ani [/dll](../../build/reference/dll-build-a-dll.md), výchozí fragment nástroje Řízení uživatelských účtů, které má nastavený úroveň nástroje Řízení uživatelských účtů na *asInvoker* se vloží do manifestu. Další informace o úrovních nástroje Řízení uživatelských účtů najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Chcete-li změnit výchozí chování nástroje Řízení uživatelských účtů, proveďte jeden z následujících kroků:  
  
-   Určete volbu /MANIFESTUAC a nastavte úroveň nástroje Řízení uživatelských účtů na požadovanou hodnotu.  
  
-   Nebo určete možnost /MANIFESTUAC:NO, pokud nechcete v manifestu generovat fragment nástroje Řízení uživatelských účtů.  
  
 Pokud nezadáte volbu/manifest, ale zadat [/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) komentáře, se vytvoří soubor manifestu. Soubor manifestu nebude vytvořen, pokud určíte volbu /MANIFEST:NO.  
  
 Pokud určíte volbu /MANIFEST, název souboru manifestu bude stejný jako název výstupního souboru, ale s příponou .manifest připojenou k názvu souboru. Například pokud bude název výstupního souboru MyFile.exe, název souboru manifestu bude MyFile.exe.manifest.  Pokud zadáte manifestfile:*název*, název manifestu je zadat v *název*.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **soubor manifestu** stránku vlastností.  
  
5.  Upravit **generovat Manifest** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)