---
title: ComPtrRef – třída
ms.date: 10/03/2018
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
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372626"
---
# <a name="comptrref-class"></a>ComPtrRef – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ>nebo typ odvozený od [společnosti\<ComPtr T,](comptr-class.md) `ComPtr`nikoli pouze rozhraní reprezentované rozhraním .

## <a name="remarks"></a>Poznámky

Představuje odkaz na objekt `ComPtr<T>`typu .

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                               | Popis
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef::ComPtrRef](#comptrref) | Inicializuje novou instanci `ComPtrRef` třídy ze `ComPtrRef` zadaného ukazatele na jiný objekt.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                         | Popis
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::GetAddressOf](#getaddressof)                     | Načte adresu ukazatele na rozhraní reprezentované aktuálním `ComPtrRef` objektem.
[ComPtrRef::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel na rozhraní, které `ComPtrRef` bylo reprezentováno objektem.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                                                     | Popis
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::operátor InterfaceType**](#operator-interfacetype-star-star) | Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel na rozhraní, které `ComPtrRef` bylo reprezentováno objektem.
[ComPtrRef::operátor T*](#operator-t-star)                               | Vrátí hodnotu [datového](comptrrefbase-class.md#ptr) člena ptr_ aktuálního objektu ComPtrRef.
[ComPtrRef::operátor void**](#operator-void-star-star)                   | Odstraní aktuální `ComPtrRef` objekt, převrátí ukazatel na rozhraní, které `ComPtrRef` bylo reprezentováno objektem `void`jako ukazatel na ukazatel na , a potom vrátí ukazatel přetypádka.
[ComPtrRef::operátor*](#operator-star)                                   | Načte ukazatel na rozhraní reprezentované aktuálním `ComPtrRef` objektem.
[ComPtrRef::operátor==](#operator-equality)                              | Označuje, `ComPtrRef` zda jsou dva objekty stejné.
[ComPtrRef::operátor!=](#operator-inequality)                            | Označuje, `ComPtrRef` zda dva objekty nejsou stejné.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef::ComPtrRef

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*Ptr*<br/>
Základní hodnota jiného `ComPtrRef` objektu.

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci `ComPtrRef` třídy ze `ComPtrRef` zadaného ukazatele na jiný objekt.

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef::GetAddressOf

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>Návratová hodnota

Adresa ukazatele na rozhraní reprezentované aktuálním `ComPtrRef` objektem.

### <a name="remarks"></a>Poznámky

Načte adresu ukazatele na rozhraní reprezentované aktuálním `ComPtrRef` objektem.

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef::operátor==

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

*A*<br/>
Odkaz na `ComPtrRef` objekt.

*B*<br/>
Odkaz na `ComPtrRef` jiný objekt nebo ukazatel na`void*`anonymní typ ( ).

### <a name="return-value"></a>Návratová hodnota

První operátor dává **true,** pokud je objekt *a* rovna objektu *b*; jinak **false**.

Druhý a třetí operátor poskytují **hodnotu true,** pokud se objekt *a* rovná **hodnotě nullptr**; jinak **false**.

Čtvrtý a pátý operátor yield **true,** pokud je objekt *a* rovna objektu *b*; jinak **false**.

### <a name="remarks"></a>Poznámky

Označuje, `ComPtrRef` zda jsou dva objekty stejné.

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef::operátor!=

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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

*A*<br/>
Odkaz na `ComPtrRef` objekt.

*B*<br/>
Odkaz na `ComPtrRef` jiný objekt nebo ukazatel na`void*`anonymní objekt ( ).

### <a name="return-value"></a>Návratová hodnota

První operátor dává **true,** pokud objekt *a* není rovna *objektu b*; jinak **false**.

Druhý a třetí operátor poskytují **hodnotu true,** pokud se objekt *a* nerovná **hodnotě nullptr**; jinak **false**.

Čtvrtý a pátý operátor poskytují **hodnotu true,** pokud se objekt *a* nerovná objektu *b*; jinak **false**.

### <a name="remarks"></a>Poznámky

Označuje, `ComPtrRef` zda dva objekty nejsou stejné.

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef::operátor InterfaceType**

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>Poznámky

Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel na rozhraní, které `ComPtrRef` bylo reprezentováno objektem.

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef::operátor*

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní reprezentované aktuálním `ComPtrRef` objektem.

### <a name="remarks"></a>Poznámky

Načte ukazatel na rozhraní reprezentované aktuálním `ComPtrRef` objektem.

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef::operátor T*

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
operator T*();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu [datového](comptrrefbase-class.md#ptr) prvku ptr_ `ComPtrRef` aktuálního objektu.

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef::operátor void\*\*

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
operator void**() const;
```

### <a name="remarks"></a>Poznámky

Odstraní aktuální `ComPtrRef` objekt, převrátí ukazatel na rozhraní, které `ComPtrRef` bylo reprezentováno objektem `void`jako ukazatel na ukazatel na , a potom vrátí ukazatel přetypádka.

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef::ReleaseAndGetAddressOf

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které bylo `ComPtrRef` reprezentováno odstraněným objektem.

### <a name="remarks"></a>Poznámky

Odstraní aktuální `ComPtrRef` objekt a vrátí ukazatel na ukazatel na rozhraní, které `ComPtrRef` bylo reprezentováno objektem.
