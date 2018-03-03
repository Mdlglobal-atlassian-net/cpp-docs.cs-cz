---
title: "Runtimeclass::gettrustlevel – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 89a00c052ec1191cd57057f52401954397169b88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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

Chybu assert je emitovaného Pokud &#95; &#95; WRL_STRICT &#95; &#95; nebo &#95; &#95; WRL_FORCE_INSPECTABLE_CLASS_MACRO &#95; &#95; není definován.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[RuntimeClass – třída](../windows/runtimeclass-class.md)