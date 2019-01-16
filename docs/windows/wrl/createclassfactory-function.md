---
title: CreateClassFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: e7e213d1b0679f17ce070de85ee9410ff9546716
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334770"
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

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)