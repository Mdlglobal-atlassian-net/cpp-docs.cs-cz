---
title: CreateActivationFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: ca3469128cf3d412138d5d39a1587cbc20150699
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398625"
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

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)