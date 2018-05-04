---
title: -SYMBOLS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /symbols
dev_langs:
- C++
helpviewer_keywords:
- symbols, dumping
- public symbols
- symbols, displaying COFF symbol table
- symbol tables
- SYMBOLS dumpbin option
- /SYMBOLS dumpbin option
- -SYMBOLS dumpbin option
ms.assetid: 34bcae90-4561-4c77-a80c-065508dec39a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a0cc59ee730fcfad47d758dec73cb8646210934
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="symbols"></a>/SYMBOLS
```  
/SYMBOLS  
```  
  
 Tato možnost zobrazuje tabulky symbolů COFF. Tabulky symbolů existují v všechny soubory objektu. Tabulky symbolů COFF se zobrazí v souboru bitové kopie, pouze v případě, že je propojena s/Debug.  
  
 Následuje popis výstup /SYMBOLS. Další informace o význam /SYMBOLS výstupu najdete tak, že vyhledá v souboru winnt.h (IMAGE_SYMBOL a IMAGE_AUX_SYMBOL) nebo COFF dokumentace.  
  
 Zadané výpisu následující ukázka:  
  
```  
Dump of file main.obj  
File Type: COFF OBJECT  
  
COFF    SYMBOL    TABLE  
000    00000000   DEBUG      notype      Filename      | .file  
      main.cpp  
002   000B1FDB   ABS      notype      Static      | @comp.id  
003   00000000   SECT1      notype      Static      | .drectve  
      Section length       26, #relocs   0, #linenums    0, checksum 722C964F  
005   00000000   SECT2      notype      Static      | .text  
      Section length      23, #relocs      1, #linenums    0, checksum 459FF65F, selection    1 (pick no duplicates)  
007   00000000   SECT2      notype ()   External      | _main  
008   00000000   UNDEF      notype ()   External      | ?MyDump@@YAXXZ (void __cdecl MyDump(void))  
  
String Table Size = 0x10 bytes  
  
Summary  
  
      26 .drectve  
      23 .text  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující popis, řádky, které začínají číslem symbol popisuje sloupce, které obsahují informace, které jsou relevantní pro uživatele:  
  
-   První tři číslice je index nebo číslo symbol.  
  
-   Pokud třetí sloupec obsahuje SECT*x*, symbol je definován v této části souboru objektu. Ale pokud se zobrazí UNDEF, není definován v objektu a musí se překládat jinde.  
  
-   Pátý sloupec (statické, externí) informuje, zda je symbol viditelná pouze v rámci tohoto objektu, nebo zda je veřejný (viditelné externě). Symbol statické _sym, nebude ho propojit s veřejné symbol _sym; Tyto dvě různé instance funkce s názvem _sym by.  
  
 Posledního sloupce v číslem řádku je názvu symbolu, dekorované i bez upraveného.  
  
 Pouze [/HEADERS](../../build/reference/headers.md) – možnost nástroje DUMPBIN je k dispozici pro použití na soubory vytvořené pomocí [/GL](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)