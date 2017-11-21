---
title: "-MANIFEST (vytvoření manifestu souběžně sdílená sestavení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.GenerateManifest
dev_langs: C++
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2067b0eb3cedb924c906e77bb549611bf8e8ed01
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (vytvoření manifestu souběžného sestavení)
```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## <a name="remarks"></a>Poznámky  
 Volba /MANIFEST určuje, že má linker vytvořit souběžný soubor manifestu. Další informace o souborů manifestu najdete v tématu [Manifest soubory – referenční dokumentace](http://msdn.microsoft.com/library/aa375632).  
  
 Výchozí hodnota je /MANIFEST.  
  
 Volba /MANIFEST:EMBED určuje, že má linker vložit soubor manifestu do bitové kopie jako prostředek typu RT_MANIFEST. Volitelný parametr `ID` je ID prostředku, které se použije pro manifest. Pro spustitelný soubor použijte hodnotu 1. Pro knihovnu DLL použijte hodnotu 2, aby bylo možné určit soukromé závislosti. Pokud parametr `ID` není zadán, výchozí hodnota je 2, pokud je nastavena volba /DLL. Jinak je výchozí hodnota 1.  
  
 Počínaje verzí Visual Studio 2008, manifestu soubory pro spustitelné soubory obsahují část, která určuje informace o řízení uživatelských účtů (UAC). Pokud zadáte /MANIFEST, ale ani jeden z nich zadejte [/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ani [/dll](../../build/reference/dll-build-a-dll.md), fragment výchozí nástroje Řízení uživatelských účtů, která má úroveň nastavení nástroje Řízení uživatelských účtů do *asInvoker* je vložen do manifestu. Další informace o úrovních nástroje Řízení uživatelských účtů najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Chcete-li změnit výchozí chování nástroje Řízení uživatelských účtů, proveďte jeden z následujících kroků:  
  
-   Určete volbu /MANIFESTUAC a nastavte úroveň nástroje Řízení uživatelských účtů na požadovanou hodnotu.  
  
-   Nebo určete možnost /MANIFESTUAC:NO, pokud nechcete v manifestu generovat fragment nástroje Řízení uživatelských účtů.  
  
 Pokud není zadán /MANIFEST, ale nezadávejte [/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) komentáře, se vytvoří soubor manifestu. Soubor manifestu nebude vytvořen, pokud určíte volbu /MANIFEST:NO.  
  
 Pokud určíte volbu /MANIFEST, název souboru manifestu bude stejný jako název výstupního souboru, ale s příponou .manifest připojenou k názvu souboru. Například pokud bude název výstupního souboru MyFile.exe, název souboru manifestu bude MyFile.exe.manifest.  Pokud zadáte /MANIFESTFILE:*název*, název manifestu je zadáte v *název*.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **souboru Manifest** stránku vlastností.  
  
5.  Změnit **generovat Manifest** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)