---
title: Tools.ini a příkaz NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 860a334274a3a1a4ac9e11c3e7b5e9a0f136ecc0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE
NMAKE přečte Tools.ini před přečte soubory pravidel, pokud se používá /R. Hledá Tools.ini nejprve v aktuálním adresáři a pak v adresáři zadaném proměnnou prostředí INIT. V části Nastavení NMAKE v souboru inicializace začíná `[NMAKE]` a může obsahovat žádné informace o souboru pravidel. Zadejte komentář na samostatné řádky začínající symbolem čísla (#).  
  
## <a name="see-also"></a>Viz také  
 [Spuštění příkazu NMAKE](../build/running-nmake.md)