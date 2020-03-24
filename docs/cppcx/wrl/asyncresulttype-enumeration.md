---
title: AsyncResultType – výčet
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: b8a2a9ec803fba1be0012fcb58bf3b42e78f9071
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214159"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType – výčet

Určuje typ výsledku vrácený metodou `GetResults()`.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Členové

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`MultipleResults`|Sada více výsledků, které jsou postupně zobrazovány mezi `Start`m stavem a před zavoláním `Close()`.|
|`SingleResult`|Jeden výsledek, který se zobrazí po výskytu události `Complete`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** Async. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
