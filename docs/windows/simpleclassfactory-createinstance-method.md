---
title: Simpleclassfactory::CreateInstance – metoda | Microsoft Docs
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
ms.openlocfilehash: 8a31d364a6464962b8243cfaced03131a20f9324
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892745"
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
Musí být `nullptr`, jinak hodnota vrácená hodnota je CLASS_E_NOAGGREGATION.

SimpleClassFactory nepodporuje agregace. Pokud byly podporované agregace a vytvářený objekt byl součástí agregace, `pUnkOuter` by ukazatel na rozhraní IUnknown řízení agregace.

*riid*  
ID objektu k vytvoření rozhraní.

*ppvObject*  
Když tato operace dokončí, ukazatel na instanci objektu určeného `riid` parametr.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.

## <a name="remarks"></a>Poznámky

Pokud &#95; &#95;WRL_STRICT&#95; &#95; je definován, chybu assert je vygenerované, pokud základní třída zadaná v parametru šablony třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo není nakonfigurovaný ClassicCom nebo WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)