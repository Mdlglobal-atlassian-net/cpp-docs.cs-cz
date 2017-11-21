---
title: . Soubory Exp jako vstup Linkeru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 39e515cadf2930cdbe5ef600bcba4c86cb79a191
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exp-files-as-linker-input"></a>Soubory .Exp jako vstup linkeru
Export (.exp) soubory obsahují informace o exportovaných funkcí a datové položky. Když LIB vytvoří knihovnu importu, také vytvoří soubor .exp. Můžete použít soubor .exp při propojení program, který exportuje do i importuje z jiné aplikace, buď přímo nebo nepřímo. Pokud jste se souborem .exp, odkaz nevytváří knihovnu importu, protože předpokládá, že LIB již vytvořili. Podrobnosti o soubory .exp a knihoven importovat najdete v tématu [práce knihoven importovat a exportovat soubory](../../build/reference/working-with-import-libraries-and-export-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)