---
title: "Testování pro nalezení chyb extrakce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 232dbd4312bbb8a0f16b6095622680f070ff2905
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="testing-for-extraction-errors"></a>Testování pro nalezení chyb extrakce
Výstupní chyba zpracování funkce popsané v [chyba zpracování funkce](../standard-library/output-file-stream-member-functions.md), platí pro vstupní datové proudy. Testování pro nalezení chyb při extrakci je důležité. Vezměte v úvahu tento příkaz:  
  
```  
cin>> n;  
```  
  
 Pokud `n` je podepsaná hodnota typu integer, hodnotu větší než 32 767 (maximální povolenou hodnotu, nebo MAX_INT) nastaví datový proud `fail` bit a `cin` objekt nepoužitelný. Všechny následné extrakce za následek okamžitou vrátit se žádná hodnota uložena.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

