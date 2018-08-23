---
title: Handlet::detach – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b66d5c65dd084da564067cd62242b315f6da182
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591371"
---
# <a name="handletdetach-method"></a>HandleT::Detach – metoda

Zruší přidružení aktuální **HandleT** objekt z jeho základní popisovač.

## <a name="syntax"></a>Syntaxe

```cpp
typename HandleTraits::Type Detach();
```

## <a name="return-value"></a>Návratová hodnota

Základní popisovač.

## <a name="remarks"></a>Poznámky

Když tato operace dokončí, aktuální **HandleT** je nastavena na neplatný stav.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HandleT – třída](../windows/handlet-class.md)