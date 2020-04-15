---
title: RuntimeClass – třída
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376237"
---
# <a name="runtimeclass-class"></a>RuntimeClass – třída

Představuje třídu WinRT nebo COM, která dědí zadaná rozhraní a poskytuje zadanou modul Windows Runtime, klasickou podporu com a slabé reference.

Tato třída poskytuje často používané implementace WinRT a COM `QueryInterface` `AddRef`třídy, poskytující implementaci , , atd., `Release` spravuje počet odkazů modulu a má podporu pro poskytování factory třídy pro aktivovatelné objekty.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parametry

*classFlags*<br/>
Volitelný parametr. Kombinace jedné nebo více hodnot výčtu [Typu RuntimeClassType.](runtimeclasstype-enumeration.md) Makro `__WRL_CONFIGURATION_LEGACY__` lze definovat pro změnu výchozí hodnoty classFlags pro všechny runtime třídy v projektu. Pokud je definováno, instance RuntimeClass jsou ve výchozím nastavení neagilní. Pokud není definována, RuntimeClass instance jsou agilní ve výchozím nastavení. Chcete-li se vyhnout `Microsoft::WRL::FtmBase` nejednoznačnosti, vždy zadejte v `TInterfaces` nebo `RuntimeClassType::InhibitFtmBase`. Všimněte si, pokud InhibitFtmBase a FtmBase jsou použity objekt bude agilní.

*TRozhraní*<br/>
Seznam rozhraní, které objekt implementuje mimo , `IUnknown` `IInspectable` nebo jiná rozhraní řízená [typem RuntimeClassType](runtimeclasstype-enumeration.md). Může také seznam dalších tříd, které `Microsoft::WRL::FtmBase` mají být odvozeny z, zejména `IMarshal`aby objekt agilní a způsobit jeho implementaci .

## <a name="members"></a>Členové

`RuntimeClassInitialize`<br/>
Funkce, která inicializuje objekt, `MakeAndInitialize` pokud je funkce šablony použita k vytvoření objektu. Vrátí S_OK, pokud byl objekt úspěšně inicializován, nebo kód chyby COM, pokud se inicializace nezdařila. Kód chyby COM je rozšířen jako vrácená hodnota . `MakeAndInitialize` Všimněte `RuntimeClassInitialize` si, že metoda `Make` není volána, pokud je funkce šablony použita k vytvoření objektu.

### <a name="public-constructors"></a>Veřejné konstruktory

| Name (Název)                                               | Popis                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | Inicializuje aktuální instanci třídy. `RuntimeClass`   |
| [RuntimeClass::~RuntimeClass](#tilde-runtimeclass) | Deinitializes aktuální instance `RuntimeClass` třídy. |

### <a name="public-methods"></a>Veřejné metody

| Name (Název)                                                      | Popis                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | Zintáží počet odkazů `RuntimeClass` pro aktuální objekt.                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | Sníží počet odkazů pro aktuální `RuntimeClass` objekt.                              |
| [RuntimeClass::GetIIds](#getiids)                         | Získá pole, které může obsahovat ID `RuntimeClass` rozhraní implementované aktuálním objektem. |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | Získá název třídy runtime `RuntimeClass` aktuálního objektu.                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | Získá úroveň důvěryhodnosti `RuntimeClass` aktuálního objektu.                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | Získá ukazatel na slabý referenční objekt `RuntimeClass` pro aktuální objekt.                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | Zintáží počet odkazů `RuntimeClass` na aktuální objekt.                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | Načte ukazatel na zadané ID rozhraní.                                                 |
| [RuntimeClass::Vydání](#release)                         | Provede operaci vydání com `RuntimeClass` na aktuální objekt.                             |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

Toto je detail implementace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>RuntimeClass::~RuntimeClass

Deinitializes aktuální instance `RuntimeClass` třídy.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>RuntimeClass::AddRef

Zintáží počet odkazů `RuntimeClass` pro aktuální objekt.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>RuntimeClass::DecrementReference

Sníží počet odkazů pro aktuální `RuntimeClass` objekt.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>RuntimeClass::GetIIds

Získá pole, které může obsahovat ID `RuntimeClass` rozhraní implementované aktuálním objektem.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Po dokončení této operace, celkový počet prvků v poli *IID .*

*IIDs*<br/>
Po dokončení této operace ukazatel na pole ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak E_OUTOFMEMORY.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

Získá název třídy runtime `RuntimeClass` aktuálního objektu.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po dokončení této operace název třídy runtime.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Chyba assert je emitován, pokud `__WRL_STRICT__` nebo `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` není definována.

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

Získá úroveň důvěryhodnosti `RuntimeClass` aktuálního objektu.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*důvěraLvl*<br/>
Po dokončení této operace úroveň důvěryhodnosti `RuntimeClass` aktuálního objektu.

### <a name="return-value"></a>Návratová hodnota

Vždycky S_OK.

### <a name="remarks"></a>Poznámky

Chyba assert je emitován, pokud `__WRL_STRICT__` nebo `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` není definována.

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>RuntimeClass::GetWeakReference

Získá ukazatel na slabý referenční objekt `RuntimeClass` pro aktuální objekt.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parametry

*slabýReference*<br/>
Po dokončení této operace ukazatel na slabý referenční objekt.

### <a name="return-value"></a>Návratová hodnota

Vždycky S_OK.

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>RuntimeClass::InternalAddRef

Zintáží počet odkazů `RuntimeClass` na aktuální objekt.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>RuntimeClass::QueryInterface

Načte ukazatel na zadané ID rozhraní.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*ppvObjekt*<br/>
Po dokončení tohoto opereation, ukazatel na rozhraní určené *riid* parametr.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="runtimeclassrelease"></a><a name="release"></a>RuntimeClass::Vydání

Provede operaci vydání com `RuntimeClass` na aktuální objekt.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud se počet odkazů `RuntimeClass` stane nulou, objekt se odstraní.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>RuntimeClass::RuntimeClass

Inicializuje aktuální instanci třídy. `RuntimeClass`

```cpp
RuntimeClass();
```
