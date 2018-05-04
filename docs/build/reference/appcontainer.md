---
title: -APPCONTAINER | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c47154d7a5eddd26573612708462c0352da30ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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