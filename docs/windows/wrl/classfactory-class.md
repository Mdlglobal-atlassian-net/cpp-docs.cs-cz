---
title: ClassFactory – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: ccc1c43e8c68053a773883c25704cdea086bd0b1
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334710"
---
# <a name="classfactory-class"></a>ClassFactory – třída

Implementuje základní funkce `IClassFactory` rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
ID nultého rozhraní.

*I1*<br/>
První rozhraní.

*I2*<br/>
Druhé síťové rozhraní.

## <a name="remarks"></a>Poznámky

Využívat `ClassFactory` poskytují implementace uživatelem definovaný objekt pro vytváření.

Následující programovací model popisuje způsob použití [implementuje](implements-structure.md) struktura určit více než tři rozhraní na objekt pro vytváření tříd.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                        | Popis
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>Veřejné metody

Název                                            | Popis
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | Zvýší počet odkazů pro aktuální `ClassFactory` objektu.
[ClassFactory::LockServer](#lockserver)         | Zvýší nebo sníží počet podkladových objektů, které jsou sledovány aktuální `ClassFactory` objektu.
[ClassFactory::QueryInterface](#queryinterface) | Načte ukazatel na rozhraní určené typem parametru.
[ClassFactory::Release](#release)               | Sníží počet odkaz pro aktuální `ClassFactory` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ClassFactory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** module.h

**Namespace:** Microsoft::WRL

## <a name="addref"></a>ClassFactory::addref –

Zvýší počet odkazů pro aktuální `ClassFactory` objektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.

## <a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="lockserver"></a>ClassFactory::LockServer

Zvýší nebo sníží počet podkladových objektů, které jsou sledovány aktuální `ClassFactory` objektu.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*fLock*<br/>
**Hodnota TRUE** se zvýší počet sledovaných objektů. **false** se sníží počet sledovaných objektů.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_FAIL.

### <a name="remarks"></a>Poznámky

`ClassFactory` uchovává informace o objekty v základní instance [modulu](module-class.md) třídy.

## <a name="queryinterface"></a>ClassFactory::QueryInterface

Načte ukazatel na rozhraní určené typem parametru.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ppvObject*<br/>
Když tato operace dokončí, ukazatel na rozhraní určené typem parametru *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.

## <a name="release"></a>ClassFactory::Release –

Sníží počet odkaz pro aktuální `ClassFactory` objektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.
