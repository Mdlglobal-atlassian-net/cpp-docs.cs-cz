---
title: InspectableClass – makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 9d194f5a87ac4a142301bc896cb3ed172f119473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398186"
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
Jeden z [TrustLevel](/windows/desktop/api/inspectable/ne-inspectable-trustlevel) hodnot výčtu.

## <a name="remarks"></a>Poznámky

**InspectableClass** – makro jde použít jenom s typy prostředí Windows Runtime.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[RuntimeClass – třída](runtimeclass-class.md)