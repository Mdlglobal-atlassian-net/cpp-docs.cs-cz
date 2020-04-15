---
title: Třída CAutoVectorPtr
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
ms.openlocfilehash: 573446256aa89423837ebf73176a73f72054911b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318766"
---
# <a name="cautovectorptr-class"></a>Třída CAutoVectorPtr

Tato třída představuje inteligentní ukazatel objekt pomocí vektorové nové a odstranit operátory.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CAutoVectorPtr
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ ukazatele.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Konstruktor|
|[CAutoVectorPtr::~CAutoVectorPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoVectorPtr::Přidělit](#allocate)|Volání této metody přidělit paměť vyžadované pole objektů, na které `CAutoVectorPtr`se vztahuje .|
|[CAutoVectorPtr::Připojit](#attach)|Volání této metody převzít vlastnictví existující ukazatel.|
|[CAutoVectorPtr::Detach](#detach)|Volání této metody uvolnit vlastnictví ukazatele.|
|[CAutoVectorPtr::Volný](#free)|Volání této metody odstranit objekt ukázal `CAutoVectorPtr`.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoVectorPtr::operátor T *](#operator_t__star)|Operátor obsazení.|
|[CAutoVectorPtr::operátor =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CAutoVectorPtr::m_p](#m_p)|Proměnná datového prvku ukazatele.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu inteligentní ukazatel, který pomůže chránit před nevracením paměti tím, že automaticky uvolní prostředky, když spadá mimo rozsah. `CAutoVectorPtr`je podobný `CAutoPtr`, jediný rozdíl `CAutoVectorPtr` je, že používá [vektornové&#91;&#93;](../../standard-library/new-operators.md#op_new_arr) a [vektoru odstranit&#91;&#93;](../../standard-library/new-operators.md#op_delete_arr) přidělit a uvolnit paměť namísto C++ **nové** a **odstranit** operátory. Viz [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) pokud `CAutoVectorPtr` jsou požadovány třídy kolekce.

Viz [CAutoPtr](../../atl/reference/cautoptr-class.md) příklad použití třídy inteligentní ukazatel.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="cautovectorptrallocate"></a><a name="allocate"></a>CAutoVectorPtr::Přidělit

Volání této metody přidělit paměť vyžadované pole objektů, na které `CAutoVectorPtr`se vztahuje .

```
bool Allocate(size_t nElements) throw();
```

### <a name="parameters"></a>Parametry

*nPrvky*<br/>
Počet prvků v poli.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je paměť úspěšně přidělena, false při selhání.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud proměnná [CAutoVectorPtr::m_p](#m_p) člen aktuálně odkazuje na existující hodnotu; to znamená, že se nerovná hodnotě NULL.

## <a name="cautovectorptrattach"></a><a name="attach"></a>CAutoVectorPtr::Připojit

Volání této metody převzít vlastnictví existující ukazatel.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Objekt `CAutoVectorPtr` převezme vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

Když `CAutoVectorPtr` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a všechna přidělená data, když přejde mimo rozsah. Pokud [CAutoVectorPtr::Detach](#detach) se nazývá, programátor je opět uvedena odpovědnost za uvolnění všech přidělených prostředků.

V sestaveních ladění dojde k selhání kontrolního výrazu, pokud proměnná [CAutoVectorPtr::m_p](#m_p) člen aktuálně odkazuje na existující hodnotu; to znamená, že se nerovná hodnotě NULL.

## <a name="cautovectorptrcautovectorptr"></a><a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr

Konstruktor

```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Existující ukazatel.

### <a name="remarks"></a>Poznámky

Objekt `CAutoVectorPtr` lze vytvořit pomocí existující ukazatel, v takovém případě přenese vlastnictví ukazatele.

## <a name="cautovectorptrcautovectorptr"></a><a name="dtor"></a>CAutoVectorPtr::~CAutoVectorPtr

Destruktor.

```
~CAutoVectorPtr() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje. Volání [CAutoVectorPtr::Free](#free).

## <a name="cautovectorptrdetach"></a><a name="detach"></a>CAutoVectorPtr::Detach

Volání této metody uvolnit vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví proměnnou [CAutoVectorPtr::m_p](#m_p) na hodnotu NULL a vrátí kopii ukazatele. Po `Detach`volání je na programátorovi, aby uvolnil všechny `CAutoVectorPtr` přidělené prostředky, za které objekt dříve převzal odpovědnost.

## <a name="cautovectorptrfree"></a><a name="free"></a>CAutoVectorPtr::Volný

Volání této metody odstranit objekt ukázal `CAutoVectorPtr`.

```
void Free() throw();
```

### <a name="remarks"></a>Poznámky

Objekt, na který `CAutoVectorPtr` se vztahuje odkaz, je uvolněn a proměnná [CAutoVectorPtr::m_p](#m_p) člen je nastavena na hodnotu NULL.

## <a name="cautovectorptrm_p"></a><a name="m_p"></a>CAutoVectorPtr::m_p

Proměnná datového prvku ukazatele.

```
T* m_p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná obsahuje informace o ukazateli.

## <a name="cautovectorptroperator-"></a><a name="operator_eq"></a>CAutoVectorPtr::operátor =

Operátor přiřazení.

```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazatel.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na **\< cautovectorptr t >**.

### <a name="remarks"></a>Poznámky

Operátor přiřazení odpojí `CAutoVectorPtr` objekt od libovolného aktuálního ukazatele a připojí nový ukazatel *p*na jeho místo.

## <a name="cautovectorptroperator-t-"></a><a name="operator_t__star"></a>CAutoVectorPtr::operátor T *

Operátor obsazení.

```
operator T*() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí ukazatel na datový typ objektu definovaný v šabloně třídy.

## <a name="see-also"></a>Viz také

[Třída CAutoPtr](../../atl/reference/cautoptr-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
