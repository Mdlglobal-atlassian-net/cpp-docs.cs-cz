---
title: "Simpleactivationfactory::activateinstance – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance method
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bbe9d8c215674f087c6e0fa4ca7f3439fb89b78
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
Když tato operace dokončí, ukazatel na instanci objektu určeného `Base` – třída parametru šablony.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.

## <a name="remarks"></a>Poznámky

Pokud &#95; &#95; WRL_STRICT &#95; &#95; je definován, chybu assert je vygenerované, pokud základní třída zadaná v parametru šablony třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo není konfigurován s WinRt nebo WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[SimpleActivationFactory – třída](../windows/simpleactivationfactory-class.md)