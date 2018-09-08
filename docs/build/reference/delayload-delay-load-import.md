---
title: -DELAYLOAD (Import odloženého načtení) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b140aed55bb1a83224bbe1698ff40695c306a693
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103733"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (import odloženého načtení)

> **/ DELAYLOAD:**_názevsouboru_

## <a name="parameters"></a>Parametry

*NázevSouboru*<br/>
Název knihovny DLL, kterou chcete zpožděně načíst.

## <a name="remarks"></a>Poznámky

Možnost/delayload způsobí, že knihovna DLL, která je určená `dllname` načtení pouze při prvním volání funkce v této knihovně DLL programem. Další informace najdete v tématu [podpora Linkeru pro knihovny DLL Delay-Loaded](../../build/reference/linker-support-for-delay-loaded-dlls.md). Tuto možnost můžete použít tolikrát, kolikrát podle potřeby k určení tolika knihoven DLL dle libosti. Delayimp.lib je třeba použít při propojení programu nebo můžete implementovat vlastní odloženě zaváděné pomocné funkce.

[/DELAY](../../build/reference/delay-delay-load-import-settings.md) určuje možnost vazby a načítání pro každou knihovnu DLL načtené se zpožděním.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

2. V **Linkeru** složky, vyberte **vstup** stránku vlastností.

3. Upravit **DLL s odloženým načtením** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
[Možnosti linkeru](../../build/reference/linker-options.md)