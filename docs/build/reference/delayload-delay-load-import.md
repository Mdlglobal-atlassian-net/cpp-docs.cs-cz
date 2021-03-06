---
title: /DELAYLOAD (import odloženého načtení)
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: e92b470b7b5e76b39371f333cbbda150e7f6e8c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273351"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (import odloženého načtení)

> **/ DELAYLOAD:**_názevsouboru_

## <a name="parameters"></a>Parametry

*NázevSouboru*<br/>
Název knihovny DLL, kterou chcete zpožděně načíst.

## <a name="remarks"></a>Poznámky

Možnost/delayload způsobí, že knihovna DLL, která je určená `dllname` načtení pouze při prvním volání funkce v této knihovně DLL programem. Další informace najdete v tématu [podpora Linkeru pro knihovny DLL Delay-Loaded](linker-support-for-delay-loaded-dlls.md). Tuto možnost můžete použít tolikrát, kolikrát podle potřeby k určení tolika knihoven DLL dle libosti. Delayimp.lib je třeba použít při propojení programu nebo můžete implementovat vlastní odloženě zaváděné pomocné funkce.

[/DELAY](delay-delay-load-import-settings.md) určuje možnost vazby a načítání pro každou knihovnu DLL načtené se zpožděním.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V **Linkeru** složky, vyberte **vstup** stránku vlastností.

1. Upravit **DLL s odloženým načtením** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
