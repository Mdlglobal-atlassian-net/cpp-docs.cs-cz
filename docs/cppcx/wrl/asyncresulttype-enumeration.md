---
title: AsyncResultType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: d3f99fa85a777ae8361ed6f7cb82fe97ddd8d667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398794"
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

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)