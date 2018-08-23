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
ms.openlocfilehash: c714f37a53e111c90333352610fd73532ac86fe7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599829"
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