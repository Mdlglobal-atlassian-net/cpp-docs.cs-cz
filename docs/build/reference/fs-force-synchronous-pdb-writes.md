---
title: -FS (vynucení synchronních PDB zápisů) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b332782cb9bcd929bcd67d4d81b7a7d0259f53cc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714594"
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (Vynutit synchronní zápisy do souboru PDB)

Vynutí zápisy do souboru databáze (PDB) programu – vytvořil [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) nebo [/zi](../../build/reference/z7-zi-zi-debug-information-format.md)– k serializaci pomocí MSPDBSRV. SOUBOR EXE.

## <a name="syntax"></a>Syntaxe

```
/FS
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení když **/zi** nebo **/zi** není zadán, kompilátor uzamkne soubory PDB, zaznamená se informace o typech a symbolickém ladění. To může výrazně snížit čas potřebný kompilátoru generovat informace o typu, když je velký počet typů. Pokud jiný proces dočasně uzamkne soubor PDB – například antivirový program – zápisy kompilátor může dojít k selhání a může dojít k závažné chybě. Tento problém může taky dojít v případě více kopií cl.exe přístup ke stejnému souboru PDB – například pokud má vaše řešení nezávislé projekty, které používají stejné zprostředkující adresáře nebo výstupní adresáře, a paralelní sestavení jsou povolená. **/FS** zabrání kompilátoru zamykání souborů PDB – možnost kompilátoru a vynutí zápisy do projít MSPDBSRV. Exe souboru, který serializuje přístup. To může být výrazně delší dobu sestavení a nezabrání všechny chyby, které mohou nastat při více instancí cl.exe přístup k souboru PDB ve stejnou dobu. Doporučujeme změnit vaše řešení tak, aby nezávislé projekty zápisu do samostatných zprostředkující a výstupní umístění nebo které jste proveďte jeden z projektů závislá na druhé sestavování projektu platnost serializovat.

[/MP](../../build/reference/mp-build-with-multiple-processes.md) možnost umožňuje **/FS** ve výchozím nastavení.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala `/FS` a klikněte na tlačítko **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)