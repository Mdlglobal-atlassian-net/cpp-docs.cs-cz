---
title: Runtimeclass::gettrustlevel – metoda | Microsoft Docs
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
ms.openlocfilehash: bc588950cc8752a7c2b8e1ddf00b2193aaf0f395
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892628"
---
# <a name="runtimeclassgettrustlevel-method"></a>RuntimeClass::GetTrustLevel – metoda

Získá aktuální objekt RuntimeClass úroveň důvěryhodnosti.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*trustLvl*  
Když tato operace dokončí, úroveň důvěryhodnosti aktuálního objektu RuntimeClass.

## <a name="return-value"></a>Návratová hodnota

Vždy S_OK.

## <a name="remarks"></a>Poznámky

Chybu assert je vygenerované Pokud &#95; &#95;WRL_STRICT&#95; &#95; nebo &#95; &#95;WRL_FORCE_INSPECTABLE_CLASS_MACRO&#95; &#95; není definován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[RuntimeClass – třída](../windows/runtimeclass-class.md)