---
title: "Tools.ini a příkaz NMAKE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4516c3206a08c2b9ee32aea4bbb669ce4cdf0d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE
NMAKE přečte Tools.ini před přečte soubory pravidel, pokud se používá /R. Hledá Tools.ini nejprve v aktuálním adresáři a pak v adresáři zadaném proměnnou prostředí INIT. V části Nastavení NMAKE v souboru inicializace začíná `[NMAKE]` a může obsahovat žádné informace o souboru pravidel. Zadejte komentář na samostatné řádky začínající symbolem čísla (#).  
  
## <a name="see-also"></a>Viz také  
 [Spuštění příkazu NMAKE](../build/running-nmake.md)