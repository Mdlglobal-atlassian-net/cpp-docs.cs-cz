---
title: Activationfactorycallback – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7979dd21d68c5b1e2606573a5271fc8deafdfb07
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604177"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback – funkce

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parametry

*activationid –*  
Zpracování na řetězec, který určuje název třídy runtime.

*ppFactory*  
Pokud tato operace dokončí, objekt factory pro aktivaci, který odpovídá parametru *activationid –*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby. HRESULT – selhání pravděpodobně jsou CLASS_E_CLASSNOTAVAILABLE a E_INVALIDARG.

## <a name="remarks"></a>Poznámky

Získá objekt factory aktivace pro ID zadaná aktivace.

Modul Windows Runtime volá tuto funkci zpětného volání pro žádost o objekt, který má název třídy runtime.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)