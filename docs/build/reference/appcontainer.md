---
title: -APPCONTAINER | Dokumentace Microsoftu
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
ms.openlocfilehash: ea6f08a141d48183d96dba6cb02fcf31909af0ae
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686250"
---
# <a name="appcontainer"></a>/APPCONTAINER
Označí spustitelný soubor, který se musí spustit v kontejneru aplikace, například Microsoft Store nebo Universal Windows app.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Spustitelný soubor, který má **/appcontainer** sady možností lze spustit pouze v aplikačním kontejneru, což je prostředí izolace procesu zavedené v systému Windows 8. Tato možnost musí být nastavena pro aplikace pro Microsoft Store a Windows Universal.  
  
## <a name="see-also"></a>Viz také  
 [– Možnosti nástroje EDITBIN](../../build/reference/editbin-options.md)   
 [Co je aplikace Universal Windows?](/windows/uwp/get-started/universal-application-platform-guide)