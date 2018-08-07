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
ms.openlocfilehash: 98bd73d2c067e6d5bbb4425782de594bbaa47bc1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606621"
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

Chyba vyhodnocení je vygenerován, pokud &#95; &#95;WRL_STRICT&#95; &#95; nebo &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; není definován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
 [RuntimeClass – třída](../windows/runtimeclass-class.md)