---
title: -APPCONTAINER | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /APPCONTAINER
dev_langs: C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 62b23ed04783971bf37442237e4db770b7427a8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="appcontainer"></a>/APPCONTAINER
Označí spustitelné soubory, které musí být spuštěný v kontejnerem aplikace – například [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] nebo aplikaci pro univerzální Windows.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Spustitelný soubor, který má **/APPCONTAINER** sadu možností může spustit pouze v kontejnerem aplikace, což je proces izolace prostředí byla zavedená v systému Windows 8. Pro [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] a univerzální aplikace pro Windows, musí být nastavena tato možnost.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [Co je aplikace pro univerzální Windows?](http://go.microsoft.com/fwlink/p/?LinkID=522074)