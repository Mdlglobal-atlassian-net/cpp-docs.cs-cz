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
ms.openlocfilehash: 528c66da24c4cbf6c22af5b1b5f8dd3afffff64f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604643"
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper – konstruktor

Inicializuje novou instanci třídy **RoInitializeWrapper** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>Parametry

*příznaky*  
Jeden z výčtů RO_INIT_TYPE, které určuje podporu poskytovaný modulem Windows Runtime.

## <a name="remarks"></a>Poznámky

**RoInitializeWrapper** třída vyvolá `Windows::Foundation::Initialize(flags)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HandleT – třída](../windows/handlet-class.md)