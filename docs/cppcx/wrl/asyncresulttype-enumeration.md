---
title: AsyncResultType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: 309ed876c71f453336ecc2ed10eedc07f2a80be8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786646"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType – výčet

Určuje typ výsledku vrácený `GetResults()` metody.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Name|Popis|
|----------|-----------------|
|`MultipleResults`|Sada více výsledků, které jsou uvedeny postupně mezi `Start` stavu a před `Close()` je volána.|
|`SingleResult`|Jeden výsledek, který se zobrazí po `Complete` dojde k události.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)