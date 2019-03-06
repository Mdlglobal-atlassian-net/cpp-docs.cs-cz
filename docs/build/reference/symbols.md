---
title: /SYMBOLS
ms.date: 09/05/2018
f1_keywords:
- /symbols
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
ms.openlocfilehash: 4aa6702cfa13523d64553041af4a18270d9babb3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421469"
---
# <a name="symbols"></a>/SYMBOLS

```
/SYMBOLS
```

Tato možnost zobrazí tabulka symbolů COFF. Existují tabulky symbolů do všech objektových souborů. Pouze v případě, že je propojený s/Debug, zobrazí se v souboru bitové kopie tabulkou symbolů COFF.

Následuje popis výstup /SYMBOLS. Další informace na významu /SYMBOLS výstupu lze najít hledáním v souboru winnt.h (IMAGE_SYMBOL a IMAGE_AUX_SYMBOL), nebo v dokumentaci COFF.

Daný následující výpis vzorku:

```
Dump of file main.obj
File Type: COFF OBJECT

COFF SYMBOL TABLE
000 00000000 DEBUG    notype       Filename     | .file
    main.cpp
002 000B1FDB ABS      notype       Static       | @comp.id
003 00000000 SECT1    notype       Static       | .drectve
    Section length     26, #relocs    0, #linenums    0, checksum 722C964F
005 00000000 SECT2    notype       Static       | .text
    Section length     23, #relocs    1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)
007 00000000 SECT2    notype ()    External     | _main
008 00000000 UNDEF    notype ()    External     | ?MyDump@@YAXXZ (void __cdecl MyDump(void))

String Table Size = 0x10 bytes

  Summary

         26 .drectve
         23 .text
```

## <a name="remarks"></a>Poznámky

Následující popis pro řádky, které začínají znakem čísla symbol, který popisuje sloupce, které obsahují informace související s uživateli:

- První tři číslice, je číslo/indexu symbol.

- Pokud třetí sloupec obsahuje SECT*x*, je definován symbol v této části souboru objektu. Ale pokud se zobrazí UNDEF, není definována v objektu a musejí být vyřešeny jinde.

- Pátý sloupec (statické, externí) řekne, jestli je viditelný pouze v rámci daného objektu symbol, nebo zda je veřejné (viditelné externě). Statický symbol _sym, nebude propojené s veřejnými symboly _sym; Tyto dvě různé instance funkce s názvem _sym by.

Poslední sloupec číslem řádku je název symbolu, dekorovaných i nedekorovaných.

Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití se soubory vytvořenými pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)
