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
ms.openlocfilehash: 3b738cc8f439e6653162ab99b0a26e87aa8fee36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372670"
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
Nultý rozhraní.

*I1*<br/>
První rozhraní.

*I2*<br/>
Druhé rozhraní.

## <a name="remarks"></a>Poznámky

Využijte `ClassFactory` k poskytování uživatelem definované implementace výroby.

Následující programovací vzor ukazuje, jak použít [Implements](implements-structure.md) struktury k určení více než tři rozhraní na factory třídy.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                        | Popis
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                            | Popis
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::Addref](#addref)                 | Zintáží počet odkazů `ClassFactory` pro aktuální objekt.
[ClassFactory::LockServer](#lockserver)         | Zkružní nebo sníží počet podkladových objektů, které jsou `ClassFactory` sledovány aktuální objekt.
[ClassFactory::QueryInterface](#queryinterface) | Načte ukazatel na rozhraní určené parametrem.
[ClassFactory::Vydání](#release)               | Sníží počet odkazů pro aktuální `ClassFactory` objekt.

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

**Obor názvů:** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory::Addref

Zintáží počet odkazů `ClassFactory` pro aktuální objekt.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory::LockServer

Zkružní nebo sníží počet podkladových objektů, které jsou `ClassFactory` sledovány aktuální objekt.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stádo*<br/>
**true** to increment the number of tracked objects. **false** zmenšit počet sledovaných objektů.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_FAIL.

### <a name="remarks"></a>Poznámky

`ClassFactory`sleduje objekty v základní instanci třídy [Module.](module-class.md)

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory::QueryInterface

Načte ukazatel na rozhraní určené parametrem.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*ppvObjekt*<br/>
Po dokončení této operace ukazatel na rozhraní určené parametrem *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory::Vydání

Sníží počet odkazů pro aktuální `ClassFactory` objekt.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání.
