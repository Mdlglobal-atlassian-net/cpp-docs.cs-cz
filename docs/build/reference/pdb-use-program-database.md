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
ms.openlocfilehash: ddcf83cafd5f499158f3116f04e40397b7f8d0a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320081"
---
# <a name="pdb-use-program-database"></a>/PDB (Použít databázi programu)

```
/PDB:filename
```

## <a name="arguments"></a>Arguments

*Název souboru*<br/>
Uživatelem zadaný název databáze programu (PDB), který vytvoří linker. Nahradí výchozí název.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení když [/DEBUG](debug-generate-debug-info.md) není zadán, linker vytvoří databázi programu (PDB), který obsahuje informace o ladění. Výchozí název souboru PDB má základní název programu a příponou PDB.

Pomocí/pdb:*filename* zadat název souboru PDB. Pokud není zadán/Debug, / PDB možnost je ignorována.

Soubor PDB může být až 2GB.

Další informace najdete v tématu [soubory .pdb jako vstup Linkeru](dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **generovat soubor databáze programu** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
