---
title: -HIGHENTROPYVA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 122f524db9af10449ce809e5a8de78148d04d431
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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