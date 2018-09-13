---
title: Implementuje strukturu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/11/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18616b1010dfe6a23861c512b1113c30fe5251ce
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535350"
---
# <a name="implements-structure"></a>Implementuje strukturu

Implementuje `QueryInterface` a `GetIid` pro zadaných rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename I0,
   typename I1 = Details::Nil,
   typename I2 = Details::Nil,
   typename I3 = Details::Nil,
   typename I4 = Details::Nil,
   typename I5 = Details::Nil,
   typename I6 = Details::Nil,
   typename I7 = Details::Nil,
   typename I8 = Details::Nil,
   typename I9 = Details::Nil
>
struct __declspec(novtable) Implements : Details::ImplementsHelper<RuntimeClassFlags<WinRt>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT>, Details::ImplementsBase;
template <
   int flags,
   typename I0,
   typename I1,
   typename I2,
   typename I3,
   typename I4,
   typename I5,
   typename I6,
   typename I7,
   typename I8
>
struct __declspec(novtable) Implements<RuntimeClassFlags<flags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : Details::ImplementsHelper<RuntimeClassFlags<flags>, typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT>, Details::ImplementsBase;
```

### <a name="parameters"></a>Parametry

*I0*  
ID nultého rozhraní. (Povinné)

*I1*  
ID prvního rozhraní. (Volitelné)

*I2*  
Druhé ID rozhraní. (Volitelné)

*I3*  
ID třetího rozhraní. (Volitelné)

*TYP I4*  
ID čtvrtého rozhraní. (Volitelné)

*I5*  
ID pátého rozhraní. (Volitelné)

*I6*  
ID šestého rozhraní. (Volitelné)

*I7*  
ID sedmého rozhraní. (Volitelné)

*I8*  
ID osmého rozhraní. (Volitelné)

*I9*  
ID devátého rozhraní. (Volitelné)

*příznaky*  
Konfigurace příznaky pro třídu. Jeden nebo více [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) výčty, které jsou určené v [runtimeclassflags –](../windows/runtimeclassflags-structure.md) struktury.

## <a name="remarks"></a>Poznámky

Je odvozen ze seznamu zadaných rozhraní a implementuje šablony pomocné rutiny pro `QueryInterface` a `GetIid`.

Každý *I0* prostřednictvím *I9* rozhraní parametr musí být odvozen z rozhraní `IUnknown`, `IInspectable`, nebo [chaininterfaces –](../windows/chaininterfaces-structure.md) šablony. *Příznaky* parametr určuje, zda podpory je vygenerován pro `IUnknown` nebo `IInspectable`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

| Název        | Popis                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonymum pro `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Chráněné metody

| Název                                              | Popis                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::cancastto –](#cancastto)               | Získá ukazatel na rozhraní zadané.                                                                    |
| [Implements::casttounknown –](#casttounknown)       | Získá ukazatel na základní `IUnknown` rozhraní.                                                        |
| [Implements::fillarraywithiid –](#fillarraywithiid) | Vloží ID rozhraní určené parametrem aktuální ID nultého šablona do určeného pole elementu. |

### <a name="protected-constants"></a>Chráněné konstanty

| Název                              | Popis                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | Obsahuje počet implementovaných rozhraní ID. |

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="cancastto"></a>Implements::cancastto –

Získá ukazatel na rozhraní zadané.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*  
Odkaz na identifikátor rozhraní.

*ppv*  
Pokud úspěšná, ukazatel na rozhraní určené *riid*.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu, například E_NOINTERFACE.

### <a name="remarks"></a>Poznámky

Toto je interní pomocné funkce, který provádí operace QueryInterface.

## <a name="casttounknown"></a>Implements::casttounknown –

Získá ukazatel na základní `IUnknown` rozhraní.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Tato operace je vždy úspěšné a vrátí `IUnknown` ukazatele.

### <a name="remarks"></a>Poznámky

Interní pomocné funkce.

## <a name="fillarraywithiid"></a>Implements::fillarraywithiid –

Vloží ID rozhraní určené parametrem aktuální ID nultého šablona do určeného pole elementu.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*  
Z nuly vycházející index určující počáteční prvek pole pro tuto operaci. Po dokončení této operace *index* zvyšuje o 1.

*IID*  
Pole typu IID.

### <a name="remarks"></a>Poznámky

Interní pomocné funkce.

## <a name="iidcount"></a>Implements::IidCount

Obsahuje počet implementovaných rozhraní ID.

```cpp
static const unsigned long IidCount;
```
