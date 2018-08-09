---
title: Runtimeclass::gettrustlevel – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: adcec3f4a531a6c48e0995468994900124746e4b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015128"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel – metoda

Získá aktuální úroveň důvěryhodnosti **RuntimeClass** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry
*trustLvl*  
Když tato operace dokončí, aktuální úroveň důvěryhodnosti **RuntimeClass** objektu.

## <a name="return-value"></a>Návratová hodnota

Vždy S_OK.

## <a name="remarks"></a>Poznámky

Chyba vyhodnocení je vygenerován, pokud `__WRL_STRICT__` nebo `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` není definován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
 [RuntimeClass – třída](../windows/runtimeclass-class.md)