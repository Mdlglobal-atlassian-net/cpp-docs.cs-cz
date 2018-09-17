---
title: -DRIVER (ovladač režimu jádra Windows NT) | Dokumentace Microsoftu
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
ms.openlocfilehash: 8ae096c502cdc94d47a516caf4c29ac4f3eceb4b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705546"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (ovladač režimu jádra Windows NT)

>/ DRIVER [: UPONLY |: WDM]

## <a name="remarks"></a>Poznámky

Použití **Driver/Driver** – možnost linkeru sestavit ovladač režimu jádra Windows NT.

**/DRIVER:UPONLY** přikazuje linkeru, které chcete přidat **při použití** bit do charakteristik výstupní hlavičky k určení, že se jedná Jednoprocesorový ovladač. Operační systém bude odmítnout zavést JEDNOPROCESOROVÝ ovladač systému s více procesory (PP).

**/DRIVER:WDM** způsobí, že nastaví linker **při použití** v poli DllCharacteristics nepovinné hlavičky bit.

Pokud **Driver/Driver** není zadán, tyto bity nejsou nastavené linkerem.

Pokud **Driver/Driver** určena:

- **/ Fixed: No** je v platnosti. Další informace najdete v tématu [/fixed (pevná základní adresa)](../../build/reference/fixed-fixed-base-address.md).

- Rozšíření výstupního souboru je nastavena na Sys. Použití **/OUT** Chcete-li změnit výchozí název souboru a rozšíření. Další informace najdete v tématu [/OUT (název výstupního souboru)](../../build/reference/out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **systému** stránku vlastností.

1. Upravit **ovladač** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit [VCLinkerTool.driver vlastnost](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
