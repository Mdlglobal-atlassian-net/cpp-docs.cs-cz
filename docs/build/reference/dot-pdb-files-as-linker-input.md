---
title: . Soubory PDB jako vstup Linkeru | Microsoft Docs
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
ms.openlocfilehash: f6707be955b5c4a332d1162f53b1cb854391a2ce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370173"
---
# <a name="pdb-files-as-linker-input"></a>Soubory .Pdb jako vstup linkeru
Objekt, soubory (.obj) zkompilovat pomocí možnosti /Zi obsahovat název databáze programu (PDB). Nezadávejte název souboru PDB objektu linkeru; ODKAZ používá vložený název najít PDB, pokud je to potřeba. To platí také pro debuggable objekty obsažené v knihovně; PDB debuggable knihovny musí být k dispozici linkeru společně s knihovny.  
  
 Souboru PDB odkaz také používá k ukládání ladicí informace pro soubor .exe nebo .dll soubor. PDB programu je výstupní soubor a vstupní soubor, protože při znovu sestaví program aktualizuje odkaz PDB.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)