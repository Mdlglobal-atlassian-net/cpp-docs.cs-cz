---
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: 0805393990070a10caed8208138e31ab9084bdf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482548"
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