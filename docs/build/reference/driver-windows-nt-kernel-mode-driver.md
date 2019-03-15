---
title: /DRIVER (ovladač režimu jádra Windows NT)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.driver
- /driver
helpviewer_keywords:
- kernel mode driver
- -DRIVER linker option
- DRIVER linker option
- /DRIVER linker option
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
ms.openlocfilehash: ab7253d7e386bf385bcb3a586c5e0e1c1e860694
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811677"
---
# <a name="driver-windows-nt-kernel-mode-driver"></a>/DRIVER (ovladač režimu jádra Windows NT)

>/ DRIVER [: UPONLY |: WDM]

## <a name="remarks"></a>Poznámky

Použití **Driver/Driver** – možnost linkeru sestavit ovladač režimu jádra Windows NT.

**/DRIVER:UPONLY** přikazuje linkeru, které chcete přidat **při použití** bit do charakteristik výstupní hlavičky k určení, že se jedná Jednoprocesorový ovladač. Operační systém bude odmítnout zavést JEDNOPROCESOROVÝ ovladač systému s více procesory (PP).

**/DRIVER:WDM** způsobí, že nastaví linker **při použití** v poli DllCharacteristics nepovinné hlavičky bit.

Pokud **Driver/Driver** není zadán, tyto bity nejsou nastavené linkerem.

Pokud **Driver/Driver** určena:

- **/ Fixed: No** je v platnosti. Další informace najdete v tématu [/fixed (pevná základní adresa)](fixed-fixed-base-address.md).

- Rozšíření výstupního souboru je nastavena na Sys. Použití **/OUT** Chcete-li změnit výchozí název souboru a rozšíření. Další informace najdete v tématu [/OUT (název výstupního souboru)](out-output-file-name.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **systému** stránku vlastností.

1. Upravit **ovladač** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit [VCLinkerTool.driver vlastnost](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.driver?view=visualstudiosdk-2017#Microsoft_VisualStudio_VCProjectEngine_VCLinkerTool_driver).

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
