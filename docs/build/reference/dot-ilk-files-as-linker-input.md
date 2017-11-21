---
title: . Soubory ilk jako vstup Linkeru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e7d801992beb75ccc14e185fc062dc4c51f8433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ilk-files-as-linker-input"></a>Soubory .Ilk jako vstup linkeru
Při propojování postupně, aktualizuje odkaz stavový soubor .ilk vytvořený během první přírůstkové odkaz. Tento soubor má stejné základní název jako soubor .exe nebo .dll soubor a má .ilk rozšíření. Při následné přírůstkové odkazy aktualizuje odkaz .ilk soubor. Pokud chybí soubor .ilk, odkaz provede úplné odkaz a vytvoří nový soubor .ilk. Pokud je soubor .ilk nepoužitelný, provede odkaz nonincremental odkaz. Podrobnosti o přírůstkové propojování najdete v tématu [přírůstkově odkaz (/ PŘÍRŮSTKOVÉ)](../../build/reference/incremental-link-incrementally.md) možnost.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)