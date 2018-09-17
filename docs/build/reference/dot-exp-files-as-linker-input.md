---
title: . Soubory Exp jako vstup Linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4badc93f38d5ce76dcc294ad4ae216c8e3f6454c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724006"
---
# <a name="exp-files-as-linker-input"></a>Soubory .Exp jako vstup linkeru

Soubory exportu (.exp) obsahují informace o položkách exportované funkce a data. Když LIB vytvoří knihovnu importu, také vytvoří soubor .exp. Souboru .exp se použít, když propojíte svůj program, který exportuje a importuje z jiné aplikace přímo nebo nepřímo. Pokud jste pomocí souboru .exp, odkaz nevytváří knihovnu importu, protože předpokládá, že LIB už nějakou vytvořili. Podrobnosti o soubory .exp a importu knihovny najdete v tématu [práce s knihovnami importovat a exportovat soubory](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Viz také

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)