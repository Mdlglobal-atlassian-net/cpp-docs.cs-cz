---
title: Handlet::Attach – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: a8783a18-bbf6-456c-98a3-e2048a10d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cfb8249d228b5a8e609952e1118bc23a75b9c98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426442"
---
# <a name="handletattach-method"></a>HandleT::Attach – metoda

Přidruží Zadaný popisovač s aktuálním **HandleT** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

#### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HandleT – třída](../windows/handlet-class.md)