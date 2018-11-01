---
title: Soubory .Exp jako vstup linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 4f70aad2fa91431da771f8e5be47956ae2db45a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661927"
---
# <a name="exp-files-as-linker-input"></a>Soubory .Exp jako vstup linkeru

Soubory exportu (.exp) obsahují informace o položkách exportované funkce a data. Když LIB vytvoří knihovnu importu, také vytvoří soubor .exp. Souboru .exp se použít, když propojíte svůj program, který exportuje a importuje z jiné aplikace přímo nebo nepřímo. Pokud jste pomocí souboru .exp, odkaz nevytváří knihovnu importu, protože předpokládá, že LIB už nějakou vytvořili. Podrobnosti o soubory .exp a importu knihovny najdete v tématu [práce s knihovnami importovat a exportovat soubory](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)