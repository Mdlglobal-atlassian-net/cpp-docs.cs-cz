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
ms.openlocfilehash: 933d332ce2653fd8ea907a5fafda524ae0220906
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408996"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator= – operátor

Přesune hodnotu jiného **HStringReference** objektů na aktuální **HStringReference** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HStringReference& operator=(HStringReference&& other) throw()  
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Existující **HStringReference** objektu.

## <a name="remarks"></a>Poznámky

Hodnota existující *Další* objekt zkopírován do aktuální **HStringReference** objektu a pak *Další* objekt zničen.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HStringReference – třída](../windows/hstringreference-class.md)