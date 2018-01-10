---
title: "-DRIVER (ovladač režimu jádra systému Windows NT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs: C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29234e3c0e368c7710f9071c753422bc4e6ef2b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (ovladač režimu jádra Windows NT)

>/ DRIVER [: UPONLY |: WDM]

## <a name="remarks"></a>Poznámky

Použití **/Driver** – možnost linkeru pro sestavení ovladač režimu jádra systému Windows NT.

**/DRIVER:UPONLY** způsobí, že linkeru přidat **IMAGE_FILE_UP_SYSTEM_ONLY** bit vlastnostmi v hlavičce výstup k určení, zda je počítač s jedním procesorem (UP) ovladače. Operační systém odmítne o načtení ovladače, až na víceprocesorový systém (PP).

**/DRIVER:WDM** způsobí, že linkeru nastavit **IMAGE_DLLCHARACTERISTICS_WDM_DRIVER** bitů v hlavičce volitelné DllCharacteristics poli.

Pokud **/Driver** není zadán, tyto bity nejsou nastaveny podle linkeru.

Pokud **/Driver** je zadán:

- **/FIXED:NO** je v platnosti. Další informace najdete v tématu [/FIXED (pevné základní adresa)](../../build/reference/fixed-fixed-base-address.md).

- Rozšíření výstupního souboru je nastavena na .sys. Použití **/OUT** Chcete-li změnit výchozí název souboru a rozšíření. Další informace najdete v tématu [/OUT (název výstupního souboru)](../../build/reference/out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte **Linkeru** složky.

1. Klikněte **systému** stránku vlastností.

1. Změnit **ovladač** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu [VCLinkerTool.driver vlastnost](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Viz také

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)
