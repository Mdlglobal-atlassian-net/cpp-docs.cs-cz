---
title: . Soubory ilk jako vstup Linkeru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01fea585b86114373017b6d73948cb1438b7185e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371681"
---
# <a name="ilk-files-as-linker-input"></a>Soubory .Ilk jako vstup linkeru
Při propojování postupně, aktualizuje odkaz stavový soubor .ilk vytvořený během první přírůstkové odkaz. Tento soubor má stejné základní název jako soubor .exe nebo .dll soubor a má .ilk rozšíření. Při následné přírůstkové odkazy aktualizuje odkaz .ilk soubor. Pokud chybí soubor .ilk, odkaz provede úplné odkaz a vytvoří nový soubor .ilk. Pokud je soubor .ilk nepoužitelný, provede odkaz nonincremental odkaz. Podrobnosti o přírůstkové propojování najdete v tématu [přírůstkově odkaz (/ PŘÍRŮSTKOVÉ)](../../build/reference/incremental-link-incrementally.md) možnost.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)