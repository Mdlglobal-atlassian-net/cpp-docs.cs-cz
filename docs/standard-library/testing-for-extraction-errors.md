---
title: "Testování pro nalezení chyb extrakce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 088cc150513d593aff5d4250c899eb3712c5fe39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="testing-for-extraction-errors"></a>Testování pro nalezení chyb extrakce
Výstupní chyba zpracování funkce popsané v [chyba zpracování funkce](../standard-library/output-file-stream-member-functions.md), platí pro vstupní datové proudy. Testování pro nalezení chyb při extrakci je důležité. Vezměte v úvahu tento příkaz:  
  
```  
cin>> n;  
```  
  
 Pokud `n` je podepsaná hodnota typu integer, hodnotu větší než 32 767 (maximální povolenou hodnotu, nebo MAX_INT) nastaví datový proud `fail` bit a `cin` objekt nepoužitelný. Všechny následné extrakce za následek okamžitou vrátit se žádná hodnota uložena.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní datové proudy](../standard-library/input-streams.md)

