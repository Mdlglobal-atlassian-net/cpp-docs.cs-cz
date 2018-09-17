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
ms.openlocfilehash: 3d8e19724183963329b959286a996b4f21d18b4c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709175"
---
# <a name="appcontainer"></a>/APPCONTAINER

Označí spustitelný soubor, který se musí spustit v kontejneru aplikace, například Microsoft Store nebo Universal Windows app.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Poznámky

Spustitelný soubor, který má **/appcontainer** sady možností lze spustit pouze v aplikačním kontejneru, což je prostředí izolace procesu zavedené v systému Windows 8. Tato možnost musí být nastavena pro aplikace pro Microsoft Store a Windows Universal.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)<br/>
[Co je aplikace Universal Windows?](/windows/uwp/get-started/universal-application-platform-guide)