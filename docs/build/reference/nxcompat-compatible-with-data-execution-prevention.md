---
title: / NXCOMPAT (kompatibilní s předcházením spuštění dat) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /NXCOMPAT
dev_langs:
- C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb4f8a91545a196bc92fdc0ec44e89a7d5680185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (kompatibilní s předcházením spuštění dat)

Označuje, že spustitelný soubor je kompatibilní s funkcí Zabránění spuštění dat systému Windows.

## <a name="syntax"></a>Syntaxe

> **/ NXCOMPAT**[**: NE**]

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **/NXCOMPAT** zapnutý.

**/NXCOMPAT:No** lze použít jako kompatibilní s předcházením spuštění dat explicitně zadat spustitelný soubor.

Další informace o zabránění spuštění dat najdete v těchto článcích:

- [Podrobný popis funkce Zabránění spuštění dat (DEP)](http://go.microsoft.com/fwlink/p/?linkid=157771)

- [Zabránění spuštění dat](http://go.microsoft.com/fwlink/p/?linkid=157770)

- [Zabránění spuštění dat (Windows Embedded)](http://go.microsoft.com/fwlink/p/?linkid=157768)

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost v **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
