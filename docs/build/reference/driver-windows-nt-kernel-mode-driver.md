---
title: -DRIVER (ovladač režimu jádra systému Windows NT) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
dev_langs:
- C++
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66291391ed38c27ce7446eccc6fca227c7c2c2d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373111"
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
