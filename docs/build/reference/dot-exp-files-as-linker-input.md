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
ms.openlocfilehash: 0f2f5c22752d6d938700228fc208c21b8f32cc7b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822285"
---
# <a name="exp-files-as-linker-input"></a>Soubory .Exp jako vstup linkeru

Soubory exportu (.exp) obsahují informace o položkách exportované funkce a data. Když LIB vytvoří knihovnu importu, také vytvoří soubor .exp. Souboru .exp se použít, když propojíte svůj program, který exportuje a importuje z jiné aplikace přímo nebo nepřímo. Pokud jste pomocí souboru .exp, odkaz nevytváří knihovnu importu, protože předpokládá, že LIB už nějakou vytvořili. Podrobnosti o soubory .exp a importu knihovny najdete v tématu [práce s knihovnami importovat a exportovat soubory](working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](link-input-files.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
