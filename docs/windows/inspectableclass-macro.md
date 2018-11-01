---
title: InspectableClass – makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 55d5aed96ff7c8b01142f8d4de81a431fdfcc2d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631592"
---
# <a name="inspectableclass-macro"></a>InspectableClass – makro

Nastaví runtime název a vztah důvěryhodnosti na úrovni třídy.

## <a name="syntax"></a>Syntaxe

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parametry

*runtimeClassName*<br/>
Úplný textový název třídy runtime.

*trustLevel*<br/>
Jeden z [TrustLevel](https://msdn.microsoft.com/library/br224625.aspx) hodnot výčtu.

## <a name="remarks"></a>Poznámky

**InspectableClass** – makro jde použít jenom s typy prostředí Windows Runtime.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[RuntimeClass – třída](../windows/runtimeclass-class.md)