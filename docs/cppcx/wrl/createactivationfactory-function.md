---
title: CreateActivationFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: ab03b15a968c6aba3fa6df8c975fb98e873f8e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214068"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory – funkce

Vytvoří objekt pro vytváření, který vytváří instance zadané třídy, které mohou být aktivovány prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>Parametry

*Flag*<br/>
Kombinace jedné nebo více hodnot výčtu [RuntimeClassType –](runtimeclasstype-enumeration.md) .

*entry*<br/>
Ukazatel na [CreatorMap](creatormap-structure.md) , který obsahuje inicializační a registrační informace o parametru *riid*.

*riid*<br/>
Odkaz na ID rozhraní.

*ppFactory*<br/>
Pokud se tato operace úspěšně dokončí, ukazatel na továrnu aktivace.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Pokud *objekt pro vytváření* parametrů není odvozen od rozhraní `IActivationFactory`, je vyvolána chyba kontrolního výrazu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)
