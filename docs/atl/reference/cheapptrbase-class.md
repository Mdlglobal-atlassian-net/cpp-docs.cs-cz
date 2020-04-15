---
title: Třída CHeapPtrBase
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: 62cabf281473cdf21fe260fa23082bc55f339849
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326902"
---
# <a name="cheapptrbase-class"></a>Třída CHeapPtrBase

Tato třída tvoří základ pro několik tříd ukazatelů inteligentní haldy.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu, který má být uložen na haldě.

*Přidělování*<br/>
Třída přidělení paměti, která má být používána. Ve výchozím nastavení CRT rutiny se používají k přidělení a uvolnění paměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtrBase::~CHeapPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtrBase::Přidělit bajty](#allocatebytes)|Volání této metody přidělit paměť.|
|[CHeapPtrBase::Připojit](#attach)|Volání této metody převzít vlastnictví existující ukazatel.|
|[CHeapPtrBase::Detach](#detach)|Volání této metody uvolnit vlastnictví ukazatele.|
|[CHeapPtrBase::Zdarma](#free)|Volání této metody odstranit objekt ukázal `CHeapPtrBase`.|
|[CHeapPtrBase::Přerozdělení bajtů](#reallocatebytes)|Volání této metody přerozdělit paměti.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtrBase::operátor T*](#operator_t_star)|Operátor obsazení.|
|[CHeapPtrBase::operátor &](#operator_amp)|Operátor &.|
|[CHeapPtrBase::operátor ->](#operator_ptr)|Operátor ukazatele na člen.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|Proměnná datového prvku ukazatele.|

## <a name="remarks"></a>Poznámky

Tato třída tvoří základ pro několik tříd ukazatelů inteligentní haldy. Odvozené třídy, například [CHeapPtr](../../atl/reference/cheapptr-class.md) a [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), přidejte vlastní konstruktory a operátory. Viz tyto třídy pro příklady implementace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>CHeapPtrBase::Přidělit bajty

Volání této metody přidělit paměť.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Počet bajtů paměti přidělit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je paměť úspěšně přidělena, false otherwise.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud proměnná [CHeapPtrBase::m_pData](#m_pdata) člen aktuálně odkazuje na existující hodnotu; to znamená, že se nerovná hodnotě NULL.

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase::Připojit

Volání této metody převzít vlastnictví existující ukazatel.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Objekt `CHeapPtrBase` převezme vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

Když `CHeapPtrBase` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a všechna přidělená data, když přejde mimo rozsah.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud proměnná [CHeapPtrBase::m_pData](#m_pdata) člen aktuálně odkazuje na existující hodnotu; to znamená, že se nerovná hodnotě NULL.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>CHeapPtrBase::~CHeapPtrBase

Destruktor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase::Detach

Volání této metody uvolnit vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví proměnnou [CHeapPtrBase::m_pData](#m_pdata) člena na HODNOTU NULL a vrátí kopii ukazatele.

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase::Zdarma

Volání této metody odstranit objekt ukázal `CHeapPtrBase`.

```
void Free() throw();
```

### <a name="remarks"></a>Poznámky

Objekt, na který `CHeapPtrBase` se vztahuje odkaz, je uvolněn a proměnná [CHeapPtrBase::m_pData](#m_pdata) člen je nastavena na hodnotu NULL.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase::m_pData

Proměnná datového prvku ukazatele.

```
T* m_pData;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná obsahuje informace o ukazateli.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase::operátor&amp;

Operátor &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu objektu, na `CHeapPtrBase` který objekt ukazuje.

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase::operátor -&gt;

Operátor ukazatele na člen.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné [CHeapPtrBase::m_pData](#m_pdata) člen.

### <a name="remarks"></a>Poznámky

Tento operátor slouží k volání metody ve `CHeapPtrBase` třídě, na kterou objekt ukazuje. V sestaveních ladění dojde k selhání `CHeapPtrBase` kontrolního výrazu, pokud odkazuje na HODNOTU NULL.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase::operátor T*

Operátor obsazení.

```
operator T*() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí [cheapptrbase::m_pData](#m_pdata).

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>CHeapPtrBase::Přerozdělení bajtů

Volání této metody přerozdělit paměti.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Nové množství paměti přidělit, v bajtů.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je paměť úspěšně přidělena, false otherwise.

## <a name="see-also"></a>Viz také

[Třída CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Třída CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
