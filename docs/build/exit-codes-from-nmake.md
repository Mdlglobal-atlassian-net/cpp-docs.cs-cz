---
title: "Kódy ukončení příkazu NMAKE | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13cbe4806d8b3960cbf80df41c7cce6e7657ba7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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