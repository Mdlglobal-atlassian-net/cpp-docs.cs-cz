---
title: -HIGHENTROPYVA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /HIGHENTROPYVA
dev_langs: C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 189344645cff785b2957131303cabbe1946954ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="highentropyva"></a>/HIGHENTROPYVA
Určuje, jestli spustitelné bitové kopie podporuje vysokou entropií 64-bit adresu místa rozložení náhodné (technologie ASLR).  
  
```  
  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost upravuje hlavičku souboru .dll nebo .exe indikující, zda je podporováno technologie ASLR s adresami 64-bit. Pokud je tato možnost nastavená na spustitelný soubor a všechny moduly, které závisí na, operační systém, který podporuje 64bitové technologie ASLR rebase segmentů spustitelné bitové kopie v době zatížení pomocí náhodnou adres v 64-bit virtuálního adresového prostoru. Tento velký adresní prostor je obtížnější pro útočníka tak snadno uhodnout umístění paměti konkrétní oblasti.  
  
 Ve výchozím nastavení nastaví linkeru tuto možnost pro 64bitové spustitelné bitové kopie. Chcete-li nastavit tuto možnost, [/DYNAMICBASE](../../build/reference/dynamicbase.md) musí být také nastavena možnost.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [/ DYNAMICBASE](../../build/reference/dynamicbase.md)   
 [Obrany zabezpečení ISV softwaru Windows](http://msdn.microsoft.com/library/bb430720.aspx)