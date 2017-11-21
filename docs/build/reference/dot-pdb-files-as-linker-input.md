---
title: . Soubory PDB jako vstup Linkeru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2f99bef901a09298404eabfe36f39bd1dd2b6bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pdb-files-as-linker-input"></a>Soubory .Pdb jako vstup linkeru
Objekt, soubory (.obj) zkompilovat pomocí možnosti /Zi obsahovat název databáze programu (PDB). Nezadávejte název souboru PDB objektu linkeru; ODKAZ používá vložený název najít PDB, pokud je to potřeba. To platí také pro debuggable objekty obsažené v knihovně; PDB debuggable knihovny musí být k dispozici linkeru společně s knihovny.  
  
 Souboru PDB odkaz také používá k ukládání ladicí informace pro soubor .exe nebo .dll soubor. PDB programu je výstupní soubor a vstupní soubor, protože při znovu sestaví program aktualizuje odkaz PDB.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)