---
title: . Soubory PDB jako vstup Linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6b728903d2a270efc6b3eb736e45540651dae8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706183"
---
# <a name="pdb-files-as-linker-input"></a>Soubory .Pdb jako vstup linkeru

Objekt (.obj) soubory zkompilovány pomocí možnosti/zi obsahovat název databáze programu (PDB). Nezadávejte název souboru PDB objektu do propojovacího programu; ODKAZ používá vložený název najít soubor PDB, pokud je to potřeba. To platí i pro laditelné objekty obsažené v knihovně; soubor PDB pro knihovnu laditelné musí být k dispozici v linkeru spolu s knihovny.

ODKAZ také pomocí souboru PDB obsahovat informace o ladění pro soubor .exe nebo .dll. Programu PDB je výstupní soubor a vstupní soubor, protože když replikujícím program aktualizuje odkaz do souboru PDB.

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)