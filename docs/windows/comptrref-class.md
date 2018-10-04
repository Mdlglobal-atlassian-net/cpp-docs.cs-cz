---
title: Comptrref – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e19b8bb5ecf1215c3f9c4eb74cf36eb9d7fc7200
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235799"
---
# <a name="comptrref-class"></a>ComPtrRef – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T
>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
A [ComPtr\<T >](../windows/comptr-class.md) typ nebo z ní odvozené, nikoli pouze rozhraní, které jsou reprezentována `ComPtr`.

## <a name="remarks"></a>Poznámky

Představuje odkaz na objekt typu `ComPtr<T>`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                               | Popis
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[Comptrref::comptrref –](#comptrref) | Inicializuje novou instanci třídy `ComPtrRef` třídy z zadaný ukazatel na jiný `ComPtrRef` objektu.

### <a name="public-methods"></a>Veřejné metody

Název                                                         | Popis
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref::getaddressof –](#getaddressof)                     | Načte adresu ukazatel rozhraní reprezentované aktuální `ComPtrRef` objektu.
[Comptrref::releaseandgetaddressof –](#releaseandgetaddressof) | Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována `ComPtrRef` objektu.

### <a name="public-operators"></a>Veřejné operátory

Název                                                                     | Popis
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operator InterfaceType **](#operator-interfacetype-star-star) | Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována `ComPtrRef` objektu.
[ComPtrRef::operator T *](#operator-t-star)                               | Vrátí hodnotu [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) aktuálního objektu comptrref – datový člen.
[ComPtrRef::operator void **](#operator-void-star-star)                   | Odstraní aktuální `ComPtrRef` objektu, přetypování ukazatel na rozhraní, která je reprezentována `ComPtrRef` objektu jako ukazatel na ukazatel- `void`a vrátí ukazatel přetypování.
[ComPtrRef::operator *](#operator-star)                                   | Načte ukazatel na rozhraní reprezentované aktuální `ComPtrRef` objektu.
[ComPtrRef::operator ==](#operator-equality)                              | Určuje, zda dva `ComPtrRef` objekty rovnají.
[ComPtrRef::operator! =](#operator-inequality)                            | Určuje, zda dva `ComPtrRef` objekty nejsou stejné.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="comptrref"></a>Comptrref::comptrref –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Zadaná hodnota jiného `ComPtrRef` objektu.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `ComPtrRef` třídy z zadaný ukazatel na jiný `ComPtrRef` objektu.

## <a name="getaddressof"></a>Comptrref::getaddressof –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa ukazatele na rozhraní reprezentované aktuální `ComPtrRef` objektu.

### <a name="remarks"></a>Poznámky

Načte adresu ukazatel rozhraní reprezentované aktuální `ComPtrRef` objektu.

## <a name="operator-equality"></a>ComPtrRef::operator ==

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*a*<br/>
Odkaz na `ComPtrRef` objektu.

*b*<br/>
Odkaz na jiný `ComPtrRef` objekt nebo ukazatel na anonymního typu (`void*`).

### <a name="return-value"></a>Návratová hodnota

První operátor výnosy `true` Pokud objekt *a* rovná objektu *b*; v opačném případě `false`.

Druhý a třetí operátory yield `true` Pokud objekt *a* rovná `nullptr`; v opačném případě `false`.

Čtvrtý a pátý operátory yield `true` Pokud objekt *a* rovná objektu *b*; v opačném případě `false`.

### <a name="remarks"></a>Poznámky

Určuje, zda dva `ComPtrRef` objekty rovnají.

## <a name="operator-inequality"></a>ComPtrRef::operator! =

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*a*<br/>
Odkaz na `ComPtrRef` objektu.

*b*<br/>
Odkaz na jiný `ComPtrRef` objekt nebo ukazatel na anonymní objekt (`void*`).

### <a name="return-value"></a>Návratová hodnota

První operátor výnosy `true` Pokud objekt *a* není roven objektu *b*; v opačném případě `false`.

Druhý a třetí operátory yield `true` Pokud objekt *a* není roven `nullptr`; v opačném případě `false`.

Čtvrtý a pátý operátory yield `true` Pokud objekt *a* není roven objektu *b*; v opačném případě `false`.

### <a name="remarks"></a>Poznámky

Určuje, zda dva `ComPtrRef` objekty nejsou stejné.

## <a name="operator-interfacetype-star-star"></a>ComPtrRef::operator InterfaceType **

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Poznámky

Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována `ComPtrRef` objektu.

## <a name="operator-star"></a>ComPtrRef::operator *

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní reprezentované aktuální `ComPtrRef` objektu.

### <a name="remarks"></a>Poznámky

Načte ukazatel na rozhraní reprezentované aktuální `ComPtrRef` objektu.

## <a name="operator-t-star"></a>ComPtrRef::operator T *

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
operator T*();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) datový člen aktuálního `ComPtrRef` objektu.

## <a name="operator-void-star-star"></a>ComPtrRef::operator void\*\*

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Poznámky

Odstraní aktuální `ComPtrRef` objektu, přetypování ukazatel na rozhraní, která je reprezentována `ComPtrRef` objektu jako ukazatel na ukazatel- `void`a vrátí ukazatel přetypování.

## <a name="releaseandgetaddressof"></a>Comptrref::releaseandgetaddressof –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní, která je reprezentována pomocí odstraněným `ComPtrRef` objektu.

### <a name="remarks"></a>Poznámky

Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel rozhraní, která je reprezentována `ComPtrRef` objektu.
