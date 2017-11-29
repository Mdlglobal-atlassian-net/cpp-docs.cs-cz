---
title: -DYNAMICBASE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /dynamicbase
dev_langs: C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8b5af34353db3c5b7cebaf02e8ce6b1bd9518cc8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dynamicbase"></a>/DYNAMICBASE
Určuje, zda spustitelné bitové kopie může být náhodně rebased během zatížení pomocí adres místo rozložení náhodné (technologie ASLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, nastaví linkeru **/DYNAMICBASE** možnost.  
  
 Tato možnost upravuje záhlaví spustitelné bitové kopie k označení, zda zavaděč můžete náhodně rebase bitovou kopii v okamžiku načtení.  
  
 Technologie ASLR je podporován v systému Windows Vista, Windows Server 2008, Windows 7, Windows 8 a Windows Server 2012.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [Obrany zabezpečení ISV softwaru Windows](http://msdn.microsoft.com/library/bb430720.aspx)