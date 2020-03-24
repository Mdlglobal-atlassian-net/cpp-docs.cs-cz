---
title: ActivationFactoryCallback – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
ms.openlocfilehash: 0be4bebcc561cdf1df3f2502c8cc1927bdc65564
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214211"
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback – funkce

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(
   HSTRING activationId,
   IActivationFactory **ppFactory
);
```

### <a name="parameters"></a>Parametry

*activationId –*<br/>
Popisovač na řetězec, který určuje název běhové třídy.

*ppFactory*<br/>
Po dokončení této operace bude továrna aktivace, která odpovídá parametru *activationId –* .

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, který popisuje chybu. Pravděpodobná selhání: HRESULTs CLASS_E_CLASSNOTAVAILABLE a E_INVALIDARG.

## <a name="remarks"></a>Poznámky

Získá továrnu aktivace pro zadané ID aktivace.

Prostředí Windows Runtime volá tuto funkci zpětného volání, aby požadovala objekt určený jeho názvem běhové třídy.

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)
