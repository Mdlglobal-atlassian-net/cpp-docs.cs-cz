---
title: -PDBSTRIPPED (odstranění privátních symbolů) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
dev_langs:
- C++
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0680f265214849c2e46c4ceb23dcb71bdff61c3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710837"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Odstranit privátní symboly)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Uživatelem zadaný název databáze odstraněnými příslušnými daty programu (PDB), který vytvoří linker.

## <a name="remarks"></a>Poznámky

Pdbstripped vytvoří druhý soubor databáze (PDB) programu při vytváření bitové kopie programu s žádným z kompilátoru nebo linkeru, které vytvářejí soubor PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), /Zd nebo /Zi). Tento druhý soubor PDB vynechává symboly, které není vhodné k odeslání vašich zákazníků. Druhý soubor PDB bude obsahovat pouze:

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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **ladění** stránku vlastností.

1. Upravit **Odstranit privátní symboly** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)