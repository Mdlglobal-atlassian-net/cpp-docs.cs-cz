---
title: CreateClassFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 323fce053707d6d00d1e17b641613d15607ab6f8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040751"
---
# <a name="createclassfactory-function"></a>CreateClassFactory – funkce

Vytvoří objekt factory, který vytvoří instance dané třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>Parametry

*příznaky*<br/>
Kombinace jedné nebo více [runtimeclasstype –](runtimeclasstype-enumeration.md) hodnot výčtu.

*entry*<br/>
Ukazatel [creatormap –](creatormap-structure.md) , který obsahuje informace o parametru inicializace a registraci *riid*.

*riid*<br/>
Odkaz na identifikátor rozhraní.

*ppFactory*<br/>
Pokud se tato operace dokončí úspěšně, ukazatel na objekt pro vytváření tříd.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Chyba vyhodnocení je vygenerován, pokud parametr šablony *Factory* není odvozen z rozhraní `IClassFactory`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)