---
title: CreateActivationFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: 07bc0dceb8066faf9c1beab64d48245d8735aa64
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786965"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory – funkce

Vytvoří objekt factory, který vytvoří instance dané třídy, které mohou být aktivovány modulem Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Kombinace jedné nebo více [runtimeclasstype –](runtimeclasstype-enumeration.md) hodnot výčtu.

*entry*<br/>
Ukazatel [creatormap –](creatormap-structure.md) , který obsahuje informace o parametru inicializace a registraci *riid*.

*riid*<br/>
Odkaz na identifikátor rozhraní.

*ppFactory*<br/>
Pokud se tato operace dokončí úspěšně, ukazatel na objekt factory pro aktivaci.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Chyba vyhodnocení je vygenerován, pokud parametr šablony *Factory* není odvozen z rozhraní `IActivationFactory`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)