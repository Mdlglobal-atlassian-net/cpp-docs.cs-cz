---
title: -APPCONTAINER | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08966cd2b9da434c45750edb57644c182a14baf2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="appcontainer"></a>/APPCONTAINER
Označí spustitelné soubory, které musí být spuštěný v kontejnerem aplikace, například Microsoft Store nebo Windows univerzální aplikace.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Spustitelný soubor, který má **/APPCONTAINER** sadu možností může spustit pouze v kontejnerem aplikace, což je proces izolace prostředí byla zavedená v systému Windows 8. Pro aplikace Microsoft Store a Universal Windows musí být tato možnost nastavena.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [Co je aplikace pro univerzální Windows?](http://go.microsoft.com/fwlink/p/?LinkID=522074)