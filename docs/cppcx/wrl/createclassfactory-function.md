---
title: CreateClassFactory – funkce
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214055"
---
# <a name="createclassfactory-function"></a>CreateClassFactory – funkce

Vytvoří objekt pro vytváření, který vytváří instance zadané třídy.

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

*Flag*<br/>
Kombinace jedné nebo více hodnot výčtu [RuntimeClassType –](runtimeclasstype-enumeration.md) .

*entry*<br/>
Ukazatel na [CreatorMap](creatormap-structure.md) , který obsahuje inicializační a registrační informace o parametru *riid*.

*riid*<br/>
Odkaz na ID rozhraní.

*ppFactory*<br/>
Pokud se tato operace úspěšně dokončí, ukazatel na objekt pro vytváření tříd.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="remarks"></a>Poznámky

Pokud *objekt pro vytváření* parametrů není odvozen od rozhraní `IClassFactory`, je vyvolána chyba kontrolního výrazu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** modul. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Wrappers::Details – obor názvů](microsoft-wrl-wrappers-details-namespace.md)
