---
title: "proveďte-při Statement (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- do
- while
dev_langs: C++
helpviewer_keywords: do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40f86574e849bae8c1defafcfeab46fced2d77b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C)
`do-while` Příkaz umožňuje opakujte příkaz nebo složený příkaz, dokud zadaného výrazu se změní na hodnotu false.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz iterace*:  
 **proveďte***příkaz***při (***výraz***);**   
  
 *Výraz* v `do-while` vyhodnotí po provedení do těla smyčky. Do těla smyčky, proto je vždy alespoň jednou spustit.  
  
 *Výraz* musí mít typ aritmetické nebo ukazatel. Provádění pokračuje následujícím způsobem:  
  
1.  Provede se tělo příkaz.  
  
2.  Dále *výraz* vyhodnotí. Pokud *výraz* je nastavena hodnota false, `do-while` příkaz ukončí a předá řízení další příkaz v programu. Pokud *výraz* hodnotu true (nenulové hodnoty), tento proces se opakuje, počínaje z kroku 1.  
  
 `do-while` Příkaz můžete také při ukončení **zalomení**, `goto`, nebo `return` do těla příkazu je spustit příkaz.  
  
 Zde je příklad příkazu `do-while`:  
  
```  
do   
{  
    y = f( x );  
    x--;  
} while ( x > 0 );  
```  
  
 V tomto `do-while` prohlášení, dvou příkazů `y = f( x );` a `x--;` provedení, bez ohledu na počáteční hodnotu `x`. Potom `x > 0` vyhodnotí. Pokud `x` je větší než 0, těla příkazu se znovu spustí a `x > 0` je již znovu. Text příkazu se spustí opakovaně, dokud `x` zůstane větší než 0. Provádění `do-while` příkaz ukončí při `x` se změní na 0 nebo záporné. Alespoň jednou je proveden těla smyčky.  
  
## <a name="see-also"></a>Viz také  
 [Proveďte-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)