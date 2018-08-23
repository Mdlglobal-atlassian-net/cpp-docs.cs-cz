---
title: Simpleactivationfactory::getruntimeclassname – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: e66c6791a55debeb411fd6058d4bbe44cb6637e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575869"
---
# <a name="simpleactivationfactorygetruntimeclassname-method"></a>SimpleActivationFactory::GetRuntimeClassName – metoda

Získá název třídy runtime instance třídy určené `Base` parametr šablony třídy.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*  
Po dokončení této operace, název třídy runtime.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definován, chybu kontrolní výraz je vygenerován, pokud třída určená `Base` parametr šablony třídy není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo nemá nakonfigurovanou WinRt nebo WinRtClassicComMix [Runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)