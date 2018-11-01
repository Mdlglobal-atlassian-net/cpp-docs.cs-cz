---
title: /PDB (Použít databázi programu)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: c7d3b571a429d780c0c5eea0ad498499c615245f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589540"
---
# <a name="pdb-use-program-database"></a>/PDB (Použít databázi programu)

```
/PDB:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Uživatelem zadaný název databáze programu (PDB), který vytvoří linker. Nahradí výchozí název.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení když [/DEBUG](../../build/reference/debug-generate-debug-info.md) není zadán, linker vytvoří databázi programu (PDB), který obsahuje informace o ladění. Výchozí název souboru PDB má základní název programu a příponou PDB.

Pomocí/pdb:*filename* zadat název souboru PDB. Pokud není zadán/Debug, / PDB možnost je ignorována.

Soubor PDB může být až 2GB.

Další informace najdete v tématu [soubory .pdb jako vstup Linkeru](../../build/reference/dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **generovat soubor databáze programu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)