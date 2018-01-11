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
ms.workload: cplusplus
ms.openlocfilehash: 0dc8c053181eda8535eb101352e9aa50053a28f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="testing-for-extraction-errors"></a>Testování pro nalezení chyb extrakce
Výstupní chyba zpracování funkce popsané v [chyba zpracování funkce](../standard-library/output-file-stream-member-functions.md), platí pro vstupní datové proudy. Testování pro nalezení chyb při extrakci je důležité. Vezměte v úvahu tento příkaz:  
  
```  
cin>> n;  
```  
  
 Pokud `n` je podepsaná hodnota typu integer, hodnotu větší než 32 767 (maximální povolenou hodnotu, nebo MAX_INT) nastaví datový proud `fail` bit a `cin` objekt nepoužitelný. Všechny následné extrakce za následek okamžitou vrátit se žádná hodnota uložena.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

