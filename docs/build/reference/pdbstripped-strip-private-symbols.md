---
title: /PDBSTRIPPED (Odstranit privátní symboly)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: 3ed36eca727a15a3c70bc51a07cd3c143d7f66da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320133"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Odstranit privátní symboly)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Uživatelem zadaný název databáze odstraněnými příslušnými daty programu (PDB), který vytvoří linker.

## <a name="remarks"></a>Poznámky

Pdbstripped vytvoří druhý soubor databáze (PDB) programu při vytváření bitové kopie programu s žádným z kompilátoru nebo linkeru, které vytvářejí soubor PDB ([/DEBUG](debug-generate-debug-info.md), [/Z7](z7-zi-zi-debug-information-format.md), /Zd nebo /Zi). Tento druhý soubor PDB vynechává symboly, které není vhodné k odeslání vašich zákazníků. Druhý soubor PDB bude obsahovat pouze:

- Veřejné symboly

- Seznam souborů objektů a části spustitelný soubor, ke kterému přispívají

- Rámec ukazatel optimalizace (FPO) ladění záznamy, použít k procházení zásobníku

Neúplný soubor PDB nebude obsahovat:

- Informace o typu

- Informace o číslech řádků

- Podle objektu souboru CodeView symboly třeba kroky týkající se funkce, místní hodnoty a statická data

Úplný soubor PDB se bude i nadále vygenerována při použití /PDBSTRIPPED.

Pokud nevytvoříte soubor PDB, /PDBSTRIPPED se ignoruje.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **Odstranit privátní symboly** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
