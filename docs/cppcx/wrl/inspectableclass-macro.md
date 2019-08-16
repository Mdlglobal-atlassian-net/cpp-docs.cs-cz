---
title: InspectableClass – makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500480"
---
# <a name="inspectableclass-macro"></a>InspectableClass – makro

Nastaví název třídy modulu runtime a úroveň důvěryhodnosti.

## <a name="syntax"></a>Syntaxe

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parametry

*runtimeClassName*<br/>
Úplný textový název běhové třídy.

*trustLevel*<br/>
Jedna z hodnot výčtu [TrustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel) .

## <a name="remarks"></a>Poznámky

Makro **InspectableClass –** lze použít pouze s typy prostředí Windows Runtime.

## <a name="requirements"></a>Požadavky

**Hlavička:** Implements. h

**Hosting** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[RuntimeClass – třída](runtimeclass-class.md)