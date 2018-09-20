---
title: Roinitializewrapper::roinitializewrapper – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b5cf858ae3fb3974898428b8437784ac3ce324e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416276"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper – konstruktor

Inicializuje novou instanci třídy **RoInitializeWrapper** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Jeden z výčtů RO_INIT_TYPE, které určuje podporu poskytovaný modulem Windows Runtime.

## <a name="remarks"></a>Poznámky

**RoInitializeWrapper** třída vyvolá `Windows::Foundation::Initialize(flags)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HandleT – třída](../windows/handlet-class.md)