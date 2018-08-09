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
ms.openlocfilehash: f25e85e59769f822a6c732cc0911c564c0104f96
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651077"
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

Pokud &#95; &#95;WRL_STRICT&#95; &#95; je definován, chybu kontrolní výraz je vygenerován, pokud zadaná v parametru šablony třídy základní třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo nemá nakonfigurovanou ClassicCom nebo WinRtClassicComMix [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také
 [SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)