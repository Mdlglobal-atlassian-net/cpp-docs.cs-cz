---
title: Simpleclassfactory::CreateInstance – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aa0d48ba96c550ff6ee1248dccd0b4c8e3021212
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020301"
---
# <a name="simpleclassfactorycreateinstance-method"></a>SimpleClassFactory::CreateInstance – metoda

Vytvoří instanci zadaného rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

### <a name="parameters"></a>Parametry
*pUnkOuter*  
Musí být **nullptr**; v opačném případě je vrácená hodnota CLASS_E_NOAGGREGATION.

Simpleclassfactory – nepodporuje agregace. Pokud byly podporovány agregace a součást agregace, byl tento objekt vytváří *pUnkOuter* bude ukazatel řízení `IUnknown` rozhraní agregace.

*riid*  
ID objektu pro vytváření rozhraní.

*ppvObject*  
Když tato operace dokončí, ukazatel na instanci objektu určeného parametrem *riid* parametru.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Pokud `__WRL_STRICT__` je definován, chybu kontrolní výraz je vygenerován, pokud zadaná v parametru šablony třídy základní třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo nemá nakonfigurovanou ClassicCom nebo WinRtClassicComMix [ Runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
 [SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)