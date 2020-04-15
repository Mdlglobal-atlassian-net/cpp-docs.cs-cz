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
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375723"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT – struktura

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parametry

*RuntimeClassTypeT*<br/>
Pole příznaků, které určuje jeden nebo více čítačů výčtu [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="remarks"></a>Poznámky

Poskytuje pomocné `QueryInterface` metody pro operace a získání ID rozhraní.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                                                         | Popis
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Načte ukazatel na zadané ID rozhraní.
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | Načte pole ID rozhraní, které jsou implementovány zadaným typem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassBaseT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>RuntimeClassBaseT::AsIID

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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
Typ, který implementuje ID rozhraní určené parametrem *riid*.

*Implementuje*<br/>
Proměnná typu určeného parametrem šablony *T*.

*riid řekl:*<br/>
ID rozhraní načíst.

*ppvObjekt*<br/>
Pokud je tato operace úspěšná, ukazatel na ukazatel na rozhraní určené parametrem *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje chybu.

### <a name="remarks"></a>Poznámky

Načte ukazatel na zadané ID rozhraní.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementedIIDS

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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
Typ *implements* parametru.

*Implementuje*<br/>
Ukazatel na typ určený parametrem *T*.

*iidCount*<br/>
Maximální počet ID rozhraní načíst.

*IIDs*<br/>
Pokud se tato operace úspěšně dokončí, pole ID rozhraní implementované typem *T*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje chybu.

### <a name="remarks"></a>Poznámky

Načte pole ID rozhraní, které jsou implementovány zadaným typem.
