---
title: ActivationFactoryCallback – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 4743e7724c5aba4171cb017654267afaac676f24
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59021602"
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

*activationId*<br/>
Zpracování na řetězec, který určuje název třídy runtime.

*ppFactory*<br/>
Pokud tato operace dokončí, objekt factory pro aktivaci, který odpovídá parametru *activationid –*.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby. HRESULT – selhání pravděpodobně jsou CLASS_E_CLASSNOTAVAILABLE a E_INVALIDARG.

## <a name="remarks"></a>Poznámky

Získá objekt factory aktivace pro ID zadaná aktivace.

Modul Windows Runtime volá tuto funkci zpětného volání pro žádost o objekt, který má název třídy runtime.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)