---
title: Simpleactivationfactory::getruntimeclassname – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
dev_langs:
- C++
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e001d0269c21026bdd00abcdd4d257f11d601cf6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889030"
---
# <a name="simpleactivationfactorygetruntimeclassname-method"></a>SimpleActivationFactory::GetRuntimeClassName – metoda

Získá název třídy runtime instance třídy určeného `Base` – třída parametru šablony.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*  
Po dokončení této operace, název modulu runtime třídy.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.

## <a name="remarks"></a>Poznámky

Pokud &#95; &#95;WRL_STRICT&#95; &#95; je definován, chybu assert je vygenerované, pokud třída určeného `Base` parametr šablony třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo není konfigurován s WinRt nebo WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)