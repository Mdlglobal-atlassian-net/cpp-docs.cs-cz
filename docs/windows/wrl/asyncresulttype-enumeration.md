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
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334696"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType – výčet

Určuje typ výsledku vrácený `GetResults()` metody.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`MultipleResults`|Sada více výsledků, které jsou uvedeny postupně mezi `Start` stavu a před `Close()` je volána.|
|`SingleResult`|Jeden výsledek, který se zobrazí po `Complete` dojde k události.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)