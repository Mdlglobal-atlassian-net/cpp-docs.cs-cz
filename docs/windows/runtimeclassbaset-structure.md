---
title: Runtimeclassbaset – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c46e89dc11f4c6fe216cfd61c3222a9c52d9e45
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789134"
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
Pole, která určuje jeden nebo více příznaků [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) enumerátory.

## <a name="remarks"></a>Poznámky

Poskytuje pomocné metody pro `QueryInterface` operace a získat ID rozhraní.

## <a name="members"></a>Členové

### <a name="protected-methods"></a>Chráněné metody

Název                                                         | Popis
------------------------------------------------------------ | -----------------------------------------------------------------------------
[Runtimeclassbaset::asiid –](#asiid)                           | Načte ukazatel na ID zadané rozhraní.
[Runtimeclassbaset::getimplementediids –](#getimplementediids) | Načte pole ID, které jsou implementovány pomocí zadaného typu rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`RuntimeClassBaseT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="asiid"></a>Runtimeclassbaset::asiid –

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

*Implementuje*<br/>
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

*Implementuje*<br/>
Ukazatel na typ určený parametrem *T*.

*iidCount*<br/>
Maximální počet rozhraní ID pro načtení.

*IID*<br/>
Pokud se tato operace dokončí úspěšně, pole rozhraní implementovaný tímto typem ID *T*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě popisující chybu HRESULT.

### <a name="remarks"></a>Poznámky

Načte pole ID, které jsou implementovány pomocí zadaného typu rozhraní.
