---
title: RuntimeClassBaseT – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 5d93b3e86e7ba105a42ccbedbbf44c51ada97bbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403162"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parametry

*RuntimeClassTypeT*<br/>
Pole, která určuje jeden nebo více příznaků [runtimeclasstype –](runtimeclasstype-enumeration.md) enumerátory.

## <a name="remarks"></a>Poznámky

Poskytuje pomocné metody pro `QueryInterface` operace a získat ID rozhraní.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Název                                                         | Popis
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Načte ukazatel na ID zadané rozhraní.
[Runtimeclassbaset::getimplementediids –](#getimplementediids) | Načte pole ID, které jsou implementovány pomocí zadaného typu rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassBaseT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="asiid"></a>RuntimeClassBaseT::AsIID

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který implementuje rozhraní ID určené parametrem *riid*.

*implements*<br/>
Proměnné určené parametrem šablony typu *T*.

*riid*<br/>
ID rozhraní, který se má načíst.

*ppvObject*<br/>
Pokud je tato operace úspěšná, ukazatel na ukazatel na rozhraní určené parametrem *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.

### <a name="remarks"></a>Poznámky

Načte ukazatel na ID zadané rozhraní.

## <a name="getimplementediids"></a>Runtimeclassbaset::getimplementediids –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ *implementuje* parametru.

*implements*<br/>
Ukazatel na typ určený parametrem *T*.

*iidCount*<br/>
Maximální počet rozhraní ID pro načtení.

*iids*<br/>
Pokud se tato operace dokončí úspěšně, pole rozhraní implementovaný tímto typem ID *T*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.

### <a name="remarks"></a>Poznámky

Načte pole ID, které jsou implementovány pomocí zadaného typu rozhraní.
