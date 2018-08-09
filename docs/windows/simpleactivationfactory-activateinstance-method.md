---
title: Simpleactivationfactory::activateinstance – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 260d7e2993bd92297167c23458d37ba80919306f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013382"
---
# <a name="simpleactivationfactoryactivateinstance-method"></a>SimpleActivationFactory::ActivateInstance – metoda

Vytvoří instanci zadaného rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry
*ppvObject*  
Když tato operace dokončí, ukazatel na instanci objektu určeného parametrem `Base` parametr šablony třídy.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definován, chybu kontrolní výraz je vygenerován, pokud zadaná v parametru šablony třídy základní třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo nemá nakonfigurovanou WinRt nebo WinRtClassicComMix [ Runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
 [SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)