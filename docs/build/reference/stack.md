---
title: -STACK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /stack
dev_langs: C++
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae6696123ffa016a1c3f64ed2310efe571b55978
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stack"></a>/STACK
```  
/STACK:reserve[,commit]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost nastaví velikost zásobníku v bajtech a přijímá argumenty notaci desítkový nebo jazyka C. Možnost /STACK se vztahuje pouze na spustitelný soubor.  
  
 *Rezervovat* argument určuje přidělení celkový zásobníku v virtuální paměti. Editbin – zaokrouhlí na nejbližší 4 bajtů zadanou hodnotu.  
  
 Volitelné `commit` argument podléhá interpretace v operačním systému. V systému Windows NT, Windows 95 a Windows 98 `commit` určuje množství fyzické paměti k přidělení najednou. Potvrzená virtuální paměť rezervuje místo ve stránkovacím souboru. A vyšší `commit` hodnota šetří čas, pokud aplikace vyžaduje více místa v zásobníku, ale zvyšuje požadavky na paměť a případně čas spuštění.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)