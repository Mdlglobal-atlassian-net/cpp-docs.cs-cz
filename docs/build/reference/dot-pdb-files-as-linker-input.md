---
title: Soubory .Pdb jako vstup linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 23974a9e20f8259c3a38af15664d328ded7ff7d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628891"
---
# <a name="pdb-files-as-linker-input"></a>Soubory .Pdb jako vstup linkeru

Objekt (.obj) soubory zkompilovány pomocí možnosti/zi obsahovat název databáze programu (PDB). Nezadávejte název souboru PDB objektu do propojovacího programu; ODKAZ používá vložený název najít soubor PDB, pokud je to potřeba. To platí i pro laditelné objekty obsažené v knihovně; soubor PDB pro knihovnu laditelné musí být k dispozici v linkeru spolu s knihovny.

ODKAZ také pomocí souboru PDB obsahovat informace o ladění pro soubor .exe nebo .dll. Programu PDB je výstupní soubor a vstupní soubor, protože když replikujícím program aktualizuje odkaz do souboru PDB.

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)