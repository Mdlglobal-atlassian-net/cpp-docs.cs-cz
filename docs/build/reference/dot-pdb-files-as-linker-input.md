---
title: Soubory .Pdb jako vstup linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 365f2955f5bc9e8082221a070af454c820c665f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273284"
---
# <a name="pdb-files-as-linker-input"></a>Soubory .Pdb jako vstup linkeru

Objekt (.obj) soubory zkompilovány pomocí možnosti/zi obsahovat název databáze programu (PDB). Nezadávejte název souboru PDB objektu do propojovacího programu; ODKAZ používá vložený název najít soubor PDB, pokud je to potřeba. To platí i pro laditelné objekty obsažené v knihovně; soubor PDB pro knihovnu laditelné musí být k dispozici v linkeru spolu s knihovny.

ODKAZ také pomocí souboru PDB obsahovat informace o ladění pro soubor .exe nebo .dll. Programu PDB je výstupní soubor a vstupní soubor, protože když replikujícím program aktualizuje odkaz do souboru PDB.

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](link-input-files.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
