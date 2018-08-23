---
title: Handlet::internalclose – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc3f01227cb37285f11ef8256d0b101f156871b5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605513"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose – metoda

Zavře aktuální **HandleT** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
virtual bool InternalClose();
```

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud aktuální **handlet –** zavření úspěšně; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

**InternalClose()** je **chráněné**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HandleT – třída](../windows/handlet-class.md)