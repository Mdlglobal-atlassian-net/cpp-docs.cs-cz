---
title: HStringReference::Operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
dev_langs:
- C++
ms.assetid: ea100ed3-e566-4c9e-b6a8-f296088dea9c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7045229cc15304a88253f97e1ad3c9f171f139a0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597125"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= – operátor

Přesune hodnotu jiného **HStringReference** objektů na aktuální **HStringReference** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HStringReference& operator=(HStringReference&& other) throw()  
```

### <a name="parameters"></a>Parametry

*Ostatní*  
Existující **HStringReference** objektu.

## <a name="remarks"></a>Poznámky

Hodnota existující *Další* objekt zkopírován do aktuální **HStringReference** objektu a pak *Další* objekt zničen.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HStringReference – třída](../windows/hstringreference-class.md)