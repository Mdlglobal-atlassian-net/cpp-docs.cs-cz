---
title: Kódy ukončení příkazu NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e71442e1e36dbd69afa65051cbf08f403bf8b31
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="exit-codes-from-nmake"></a>Kódy ukončení příkazu NMAKE
NMAKE vrátí následující ukončovací kód:  
  
|Kód|Význam|  
|----------|-------------|  
|0|Žádná chyba (pravděpodobně upozornění)|  
|1|Nedokončené sestavení (vydala, jenom když se použije /K)|  
|2|Chyba programu, pravděpodobně kvůli jednomu z následujících akcí:|  
||-Chyby syntaxe v souboru pravidel|  
||-Zadání kódu chyby nebo ukončení příkazu|  
||-Přerušení uživatelem.|  
|4|Systémová chyba – nedostatek paměti|  
|255|Cíl není aktuální (vydala, jenom když se použije /Q)|  
  
## <a name="see-also"></a>Viz také  
 [Spuštění příkazu NMAKE](../build/running-nmake.md)