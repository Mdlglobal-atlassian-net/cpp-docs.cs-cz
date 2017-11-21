---
title: "Simpleclassfactory::CreateInstance – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs: C++
helpviewer_keywords: CreateInstance method
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aaffaf02c7db9c311f3f06e18e0194089d79e430
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
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

Pokud &#95; &#95; WRL_STRICT &#95; &#95; je definován, chybu assert je vygenerované, pokud základní třída zadaná v parametru šablony třída není odvozen od [RuntimeClass](../windows/runtimeclass-class.md), nebo není konfigurován s ClassicCom nebo WinRtClassicComMix [RuntimeClassType ](../windows/runtimeclasstype-enumeration.md) hodnota výčtu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[SimpleClassFactory – třída](../windows/simpleclassfactory-class.md)