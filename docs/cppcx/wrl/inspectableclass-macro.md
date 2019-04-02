---
title: InspectableClass – makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: cedf395ae98a423e0335851327b5fdda1a4bc7d6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787031"
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

## <a name="see-also"></a>Viz také

[RuntimeClass – třída](runtimeclass-class.md)