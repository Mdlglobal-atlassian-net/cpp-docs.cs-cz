---
title: CAutoPtr – třída
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
ms.openlocfilehash: 7f15e16b075b9a5327723a7f081100313f14ea77
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167718"
---
# <a name="cautoptr-class"></a>CAutoPtr – třída

Tato třída reprezentuje objekt inteligentního ukazatele.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class CAutoPtr
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAutoPtr:: CAutoPtr](#cautoptr)|Konstruktor|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAutoPtr:: Attach](#attach)|Voláním této metody převezmete vlastnictví existujícího ukazatele.|
|[CAutoPtr::D etach](#detach)|Voláním této metody vydáte vlastnictví ukazatele.|
|[CAutoPtr:: Free](#free)|Voláním této metody odstraníte objekt, na který odkazoval `CAutoPtr`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAutoPtr:: operator T *](#operator_t_star)|Operátor přetypování.|
|[CAutoPtr:: operator =](#operator_eq)|Operátor přiřazení|
|[CAutoPtr:: operator->](#operator_ptr)|Operátor pointer-to-member.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAutoPtr:: m_p](#m_p)|Proměnná členu dat ukazatele.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu inteligentního ukazatele, které vám pomůžou chránit před nevracením paměti tím, že automaticky uvolňují prostředky, když spadají mimo rozsah.

Dále `CAutoPtr`je kopírovací konstruktor a operátor přiřazení přenáší vlastnictví ukazatele, zkopírování ukazatele source na cílový ukazatel a nastavení ukazatele na zdroj na hodnotu null. Proto není možné mít dva `CAutoPtr` objekty, z nichž každý ukládá stejný ukazatel, což snižuje možnost odstranit stejný ukazatel dvakrát.

`CAutoPtr`také zjednodušuje vytváření kolekcí ukazatelů. Namísto odvození třídy kolekce a přepsání destruktoru je jednodušší vytvořit kolekci `CAutoPtr` objektů. Když se kolekce odstraní, `CAutoPtr` objekty se přestanou z oboru a automaticky se odstraní.

[CHeapPtr](../../atl/reference/cheapptr-class.md) a varianty fungují stejným způsobem jako `CAutoPtr`s tím rozdílem, že přidělují a uvolňují paměť pomocí různých funkcí haldy namísto operátorů **New** a **Delete** jazyka C++. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) je podobná `CAutoPtr`, jediný rozdíl spočívá v tom, že používá **Vector New []** a **Vector DELETE []** k přidělení a uvolnění paměti.

Pokud se vyžadují pole nebo seznamy inteligentních ukazatelů, podívejte se také na [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) a [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

## <a name="cautoptrattach"></a><a name="attach"></a>CAutoPtr:: Attach

Voláním této metody převezmete vlastnictví existujícího ukazatele.

```cpp
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
`CAutoPtr` Objekt převezme vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

Když `CAutoPtr` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a veškerá přidělená data, když se dostane mimo rozsah. Pokud se volá [CAutoPtr::D etach](#detach) , programátor se znovu přenese zodpovědnost za uvolnění všech přidělených prostředků.

V sestavení ladění dojde k selhání kontrolního výrazu, pokud datový člen [CAutoPtr:: m_p](#m_p) aktuálně odkazuje na existující hodnotu; To znamená, že se nerovná hodnotě NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad v [přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="cautoptr"></a>CAutoPtr:: CAutoPtr

Konstruktor

```cpp
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<>
CAutoPtr(CAutoPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
Existující ukazatel.

*TSrc*<br/>
Typ, který je spravován jiným `CAutoPtr`objektem, který slouží k inicializaci aktuálního objektu.

### <a name="remarks"></a>Poznámky

`CAutoPtr` Objekt lze vytvořit pomocí existujícího ukazatele, v takovém případě přenáší vlastnictví ukazatele.

### <a name="example"></a>Příklad

Podívejte se na příklad v [přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrcautoptr"></a><a name="dtor"></a>CAutoPtr:: ~ CAutoPtr

Destruktor.

```cpp
~CAutoPtr() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky. Volá [CAutoPtr:: Free](#free).

## <a name="cautoptrdetach"></a><a name="detach"></a>CAutoPtr::D etach

Voláním této metody vydáte vlastnictví ukazatele.

```cpp
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví proměnnou datového členu [CAutoPtr:: m_p](#m_p) na hodnotu null a vrátí kopii ukazatele. Po volání `Detach`je až do programátora uvolněny všechny přidělené prostředky, u kterých mohl `CAutoPtr` objekt dříve předpokládat reponsibility.

### <a name="example"></a>Příklad

Podívejte se na příklad v [přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptrfree"></a><a name="free"></a>CAutoPtr:: Free

Voláním této metody odstraníte objekt, na který odkazoval `CAutoPtr`.

```cpp
void Free() throw();
```

### <a name="remarks"></a>Poznámky

Objekt, na který ukazuje, `CAutoPtr` je uvolněný a proměnná datového členu [CAutoPtr:: m_p](#m_p) je nastavená na hodnotu null.

## <a name="cautoptrm_p"></a><a name="m_p"></a>CAutoPtr:: m_p

Proměnná členu dat ukazatele.

```cpp
T* m_p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná obsahuje informace o ukazateli.

## <a name="cautoptroperator-"></a><a name="operator_eq"></a>CAutoPtr:: operator =

Operátor přiřazení

```cpp
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parametry

*trub*<br/>
Ukazatel.

*TSrc*<br/>
Typ třídy.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na **\< CAutoPtr T >**.

### <a name="remarks"></a>Poznámky

Operátor přiřazení odpojí `CAutoPtr` objekt od libovolného aktuálního ukazatele a připojí nový ukazatel *p*na místo.

### <a name="example"></a>Příklad

Podívejte se na příklad v [přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator--gt"></a><a name="operator_ptr"></a>CAutoPtr:: operator-&gt;

Operátor pointer-to-member.

```cpp
T* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu proměnné datového členu [CAutoPtr:: m_p](#m_p) .

### <a name="remarks"></a>Poznámky

Tento operátor použijte k volání metody ve třídě, na kterou ukazuje `CAutoPtr` objekt. V sestavení ladění dojde k selhání kontrolního výrazu, pokud `CAutoPtr` body odkazují na hodnotu null.

### <a name="example"></a>Příklad

Podívejte se na příklad v [přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="cautoptroperator-t"></a><a name="operator_t_star"></a>CAutoPtr:: operator T *

Operátor přetypování.

```cpp
operator T* () const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na datový typ objektu definovaný v šabloně třídy.

### <a name="example"></a>Příklad

Podívejte se na příklad v [přehledu CAutoPtr](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Viz také

[CHeapPtr – třída](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr – třída](../../atl/reference/cautovectorptr-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
