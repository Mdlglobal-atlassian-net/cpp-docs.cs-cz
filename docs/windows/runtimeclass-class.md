---
title: Runtimeclass – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/11/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db9476e225b19f76fb695063c9c5058e8d9b2871
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080023"
---
# <a name="runtimeclass-class"></a>RuntimeClass – třída

Představuje třídu WinRT nebo COM, která dědí zadaných rozhraní a poskytuje zadaného modulu Windows Runtime, klasické rozhraní COM a slabou podporu odkazu.

Tato třída poskytuje standardní implementace WinRT a com. tříd, poskytuje implementaci `QueryInterface`, `AddRef`, `Release` atd., spravuje referenčního počtu modulu a obsahuje podporu pro poskytuje objekt pro vytváření tříd pro aktivovatelné objekty.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parametry

*classFlags*<br/>
Volitelný parametr. Kombinace jedné nebo více [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnot výčtu. `__WRL_CONFIGURATION_LEGACY__` Makra lze definovat za účelem změnit výchozí hodnotu classFlags pro všechny třídy modulu runtime v projektu. Pokud definována, RuntimeClass instance jsou mimo agilní ve výchozím nastavení. Pokud není definován, RuntimeClass instance jsou agilní ve výchozím nastavení. Aby se zabránilo nejednoznačnosti vždy zadávat `Microsoft::WRL::FtmBase` v `TInterfaces` nebo `RuntimeClassType::InhibitFtmBase`. Poznámka: Pokud jsou obě používají objekt InhibitFtmBase a ftmbase – bude agile.

*TInterfaces*<br/>
Seznam rozhraní objekt implementuje nad rámec `IUnknown`, `IInspectable` nebo jiných rozhraní řídí [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md). Je také může seznam jiných tříd nelze odvodit z, zejména `Microsoft::WRL::FtmBase` vytvořit objekt agilní a způsobit, že k implementaci `IMarshal`.

## <a name="members"></a>Členové

`RuntimeClassInitialize`<br/>
Funkce, která inicializuje objekt, pokud `MakeAndInitialize` šablony funkce se používá ke konstrukci objektu. Vrátí hodnotu S_OK, pokud objekt byl úspěšně inicializován nebo kód chyby modelu COM. Pokud inicializace se nezdařila. Kód chyby modelu COM je postoupena jako návratovou hodnotu `MakeAndInitialize`. Všimněte si, že `RuntimeClassInitialize` metoda není volána, pokud `Make` šablony funkce se používá ke konstrukci objektu.

### <a name="public-constructors"></a>Veřejné konstruktory

| Název                                               | Popis                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [Runtimeclass::runtimeclass –](#runtimeclass)        | Inicializuje aktuální instanci aplikace `RuntimeClass` třídy.   |
| [RuntimeClass:: ~ runtimeclass –](#tilde-runtimeclass) | Zruší inicializaci aktuální instance `RuntimeClass` třídy. |

### <a name="public-methods"></a>Veřejné metody

| Název                                                      | Popis                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Runtimeclass::addref –](#addref)                           | Zvýší počet odkazů pro aktuální `RuntimeClass` objektu.                              |
| [Runtimeclass::decrementreference –](#decrementreference)   | Sníží počet odkaz pro aktuální `RuntimeClass` objektu.                              |
| [Runtimeclass::getiids –](#getiids)                         | Získává pole, která může obsahovat rozhraní implementované aktuální ID `RuntimeClass` objektu. |
| [Runtimeclass::getruntimeclassname –](#getruntimeclassname) | Získá název třídy runtime aktuálního `RuntimeClass` objektu.                                  |
| [Runtimeclass::gettrustlevel –](#gettrustlevel)             | Získá aktuální úroveň důvěryhodnosti `RuntimeClass` objektu.                                         |
| [Runtimeclass::getweakreference –](#getweakreference)       | Získá ukazatel na objekt nestálý odkaz pro aktuální `RuntimeClass` objektu.                 |
| [Runtimeclass::internaladdref –](#internaladdref)           | Zvýší počet odkazů na aktuální `RuntimeClass` objektu.                               |
| [Runtimeclass::QueryInterface –](#queryinterface)           | Načte ukazatel na ID zadané rozhraní.                                                 |
| [Runtimeclass::Release –](#release)                         | Provádí operaci vydání COM v aktuálním `RuntimeClass` objektu.                             |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

Toto je podrobnost implementace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="tilde-runtimeclass"></a>RuntimeClass:: ~ runtimeclass –

Zruší inicializaci aktuální instance `RuntimeClass` třídy.

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>Runtimeclass::addref –

Zvýší počet odkazů pro aktuální `RuntimeClass` objektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="decrementreference"></a>Runtimeclass::decrementreference –

Sníží počet odkaz pro aktuální `RuntimeClass` objektu.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="getiids"></a>Runtimeclass::getiids –

Získává pole, která může obsahovat rozhraní implementované aktuální ID `RuntimeClass` objektu.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Pokud tato operace dokončí, celkový počet prvků v poli *IID*.

*IID*<br/>
Když tato operace dokončí, ukazatel na pole ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_OUTOFMEMORY.

## <a name="getruntimeclassname"></a>Runtimeclass::getruntimeclassname –

Získá název třídy runtime aktuálního `RuntimeClass` objektu.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po dokončení této operace, název třídy runtime.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Chyba vyhodnocení je vygenerován, pokud `__WRL_STRICT__` nebo `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` není definován.

## <a name="gettrustlevel"></a>Runtimeclass::gettrustlevel –

Získá aktuální úroveň důvěryhodnosti `RuntimeClass` objektu.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*trustLvl*<br/>
Když tato operace dokončí, aktuální úroveň důvěryhodnosti `RuntimeClass` objektu.

### <a name="return-value"></a>Návratová hodnota

Vždy S_OK.

### <a name="remarks"></a>Poznámky

Chyba vyhodnocení je vygenerován, pokud `__WRL_STRICT__` nebo `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` není definován.

## <a name="getweakreference"></a>Runtimeclass::getweakreference –

Získá ukazatel na objekt nestálý odkaz pro aktuální `RuntimeClass` objektu.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parametry

*weakreference –*<br/>
Když tato operace dokončí, ukazatel na objekt nestálý odkaz.

### <a name="return-value"></a>Návratová hodnota

Vždy S_OK.

## <a name="internaladdref"></a>Runtimeclass::internaladdref –

Zvýší počet odkazů na aktuální `RuntimeClass` objektu.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Návratová hodnota

Výsledný počet odkazů.

## <a name="queryinterface"></a>Runtimeclass::QueryInterface –

Načte ukazatel na ID zadané rozhraní.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ppvObject*<br/>
Když tento opereation se dokončí, ukazatel na rozhraní určené typem *riid* parametru.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="release"></a>Runtimeclass::Release –

Provádí operaci vydání COM v aktuálním `RuntimeClass` objektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

### <a name="remarks"></a>Poznámky

Pokud klesne na nulu, počet odkazů `RuntimeClass` objekt odstranit.

## <a name="runtimeclass"></a>Runtimeclass::runtimeclass –

Inicializuje aktuální instanci aplikace `RuntimeClass` třídy.

```cpp
RuntimeClass();
```
