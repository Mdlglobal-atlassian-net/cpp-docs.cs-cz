---
title: Třída CAutoPtr
ms.date: 11/04/2016
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
ms.openlocfilehash: cb8e3d6b71db6ab60b3b246bd8c5bf4f2c9aaa34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321259"
---
# <a name="cautoptr-class"></a>Třída CAutoPtr

Tato třída představuje inteligentní ukazatel objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CAutoPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Konstruktor|
|[CAutoPtr::~CAutoPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtr::Připojit](#attach)|Volání této metody převzít vlastnictví existující ukazatel.|
|[CAutoPtr::Detach](#detach)|Volání této metody uvolnit vlastnictví ukazatele.|
|[CAutoPtr::Zdarma](#free)|Volání této metody odstranit objekt ukázal `CAutoPtr`.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtr::operátor T*](#operator_t_star)|Operátor obsazení.|
|[CAutoPtr::operátor =](#operator_eq)|Operátor přiřazení.|
|[CAutoPtr::operátor ->](#operator_ptr)|Operátor ukazatele na člen.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|Proměnná datového prvku ukazatele.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu inteligentní ukazatel, který pomůže chránit před nevracením paměti tím, že automaticky uvolní prostředky, když spadá mimo rozsah.

Dále `CAutoPtr`'s copy konstruktor a operátor přiřazení převod vlastnictví ukazatele, kopírování zdrojukazatel cílového ukazatele a nastavení zdrojový ukazatel null. Proto je nemožné mít `CAutoPtr` dva objekty každý ukládání stejného ukazatele, a to snižuje možnost odstranění stejného ukazatele dvakrát.

`CAutoPtr`také zjednodušuje vytváření kolekcí ukazatelů. Místo odvození třídy kolekce a přepsání destruktoru je jednodušší vytvořit `CAutoPtr` kolekci objektů. Při odstranění kolekce objekty `CAutoPtr` přejdou mimo rozsah a automaticky odstranit sami.

[CHeapPtr](../../atl/reference/cheapptr-class.md) a varianty fungují stejným `CAutoPtr`způsobem jako , s tím rozdílem, že přidělují a volné paměti pomocí různých funkcí haldy namísto C++ **nové** a **odstranit** operátory. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) je `CAutoPtr`podobný , jediný rozdíl je, že používá **vektor nové []** a **vektor delete []** přidělit a uvolnit paměť.

Viz také [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) a [CAutoPtrList,](../../atl/reference/cautoptrlist-class.md) pokud jsou vyžadována pole nebo seznamy inteligentních ukazatelů.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr::Připojit

Volání této metody převzít vlastnictví existující ukazatel.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Objekt `CAutoPtr` převezme vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

Když `CAutoPtr` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a všechna přidělená data, když přejde mimo rozsah. Pokud [CAutoPtr::Detach](#detach) se nazývá, programátor je opět pověřen odpovědnost za uvolnění všech přidělených prostředků.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud datový člen [CAutoPtr:::m_p](#m_p) aktuálně odkazuje na existující hodnotu; to znamená, že se nerovná hodnotě NULL.

### <a name="example"></a>Příklad

Viz příklad v [Přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr::CAutoPtr

Konstruktor

```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Existující ukazatel.

*TSrc (TSrc)*<br/>
Typ, který je `CAutoPtr`spravován jiným , slouží k inicializaci aktuálního objektu.

### <a name="remarks"></a>Poznámky

Objekt `CAutoPtr` lze vytvořit pomocí existující ukazatel, v takovém případě přenese vlastnictví ukazatele.

### <a name="example"></a>Příklad

Viz příklad v [Přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr::~CAutoPtr

Destruktor.

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje. Volání [CAutoPtr::Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::Detach

Volání této metody uvolnit vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví proměnnou [CAutoPtr::m_p](#m_p) datového člena na HODNOTU NULL a vrátí kopii ukazatele. Po `Detach`volání je na programátorovi, aby uvolnil všechny `CAutoPtr` přidělené prostředky, přes které objekt mohl dříve předpokládat reponsibility.

### <a name="example"></a>Příklad

Viz příklad v [Přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr::Zdarma

Volání této metody odstranit objekt ukázal `CAutoPtr`.

```
void Free() throw();
```

### <a name="remarks"></a>Poznámky

Objekt, na který `CAutoPtr` se vztahuje odkaz, je uvolněn a proměnná [CAutoPtr::m_p](#m_p) datový člen je nastavena na hodnotu NULL.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr::m_p

Proměnná datového prvku ukazatele.

```
T* m_p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná obsahuje informace o ukazateli.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr::operátor =

Operátor přiřazení.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel.

*TSrc (TSrc)*<br/>
Typ třídy.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na **cautoptr\< t >**.

### <a name="remarks"></a>Poznámky

Operátor přiřazení odpojí `CAutoPtr` objekt od libovolného aktuálního ukazatele a připojí nový ukazatel *p*na jeho místo.

### <a name="example"></a>Příklad

Viz příklad v [Přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr::operátor -&gt;

Operátor ukazatele na člen.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné [CAutoPtr::m_p](#m_p) datového člena.

### <a name="remarks"></a>Poznámky

Tento operátor slouží k volání metody ve `CAutoPtr` třídě, na kterou objekt ukazuje. V sestaveních ladění dojde k selhání `CAutoPtr` kontrolního výrazu, pokud odkazuje na HODNOTU NULL.

### <a name="example"></a>Příklad

Viz příklad v [Přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr::operátor T*

Operátor obsazení.

```
operator T* () const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na datový typ objektu definovaný v šabloně třídy.

### <a name="example"></a>Příklad

Viz příklad v [Přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Viz také

[Třída CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Třída CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
