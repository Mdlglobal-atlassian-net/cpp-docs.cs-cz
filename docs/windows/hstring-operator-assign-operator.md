---
title: HString::Operator = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e528bed14f3f6f3b35270975833bdd17fd777db
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422646"
---
# <a name="hstringoperator-operator"></a>HString::Operator= – operátor

Přesune hodnotu jiného **HString** objektů na aktuální **HString** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Existující **HString** objektu.

## <a name="remarks"></a>Poznámky

Hodnota existující *Další* objekt zkopírován do aktuální **HString** objektu a pak *Další* objekt zničen.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)