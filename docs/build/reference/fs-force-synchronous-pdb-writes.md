---
title: /FS (Vynutit synchronní zápisy do souboru PDB)
ms.date: 11/04/2016
f1_keywords:
- /FS
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
ms.openlocfilehash: 97ffb9529087329cf327ba704523b93d5d9b99b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270976"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (Vynutit synchronní zápisy do souboru PDB)

Vynutí zápisy do souboru databáze (PDB) programu – vytvořil [/zi](z7-zi-zi-debug-information-format.md) nebo [/zi](z7-zi-zi-debug-information-format.md)– k serializaci pomocí MSPDBSRV. SOUBOR EXE.

## <a name="syntax"></a>Syntaxe

```
/FS
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení když **/zi** nebo **/zi** není zadán, kompilátor uzamkne soubory PDB, zaznamená se informace o typech a symbolickém ladění. To může výrazně snížit čas potřebný kompilátoru generovat informace o typu, když je velký počet typů. Pokud jiný proces dočasně uzamkne soubor PDB – například antivirový program – zápisy kompilátor může dojít k selhání a může dojít k závažné chybě. Tento problém může taky dojít v případě více kopií cl.exe přístup ke stejnému souboru PDB – například pokud má vaše řešení nezávislé projekty, které používají stejné zprostředkující adresáře nebo výstupní adresáře, a paralelní sestavení jsou povolená. **/FS** zabrání kompilátoru zamykání souborů PDB – možnost kompilátoru a vynutí zápisy do projít MSPDBSRV. Exe souboru, který serializuje přístup. To může být výrazně delší dobu sestavení a nezabrání všechny chyby, které mohou nastat při více instancí cl.exe přístup k souboru PDB ve stejnou dobu. Doporučujeme změnit vaše řešení tak, aby nezávislé projekty zápisu do samostatných zprostředkující a výstupní umístění nebo které jste proveďte jeden z projektů závislá na druhé sestavování projektu platnost serializovat.

[/MP](mp-build-with-multiple-processes.md) možnost umožňuje **/FS** ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala `/FS` a klikněte na tlačítko **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
