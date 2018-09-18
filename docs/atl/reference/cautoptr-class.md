---
title: Cautoptr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3066f4586d34c4742cc03511d7f8739b642ccbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066242"
---
# <a name="cautoptr-class"></a>Cautoptr – třída

Tato třída reprezentuje objekt inteligentního ukazatele.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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

|Název|Popis|
|----------|-----------------|
|[CAutoPtr::CAutoPtr](#cautoptr)|Konstruktor|
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAutoPtr::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.|
|[CAutoPtr::Detach](#detach)|Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.|
|[CAutoPtr::Free](#free)|Volejte tuto metodu za účelem odstranění objektu, na které odkazují `CAutoPtr`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAutoPtr::operator T *](#operator_t_star)|Operátor přetypování.|
|[CAutoPtr::operator =](#operator_eq)|Operátor přiřazení.|
|[CAutoPtr::operator ->](#operator_ptr)|Operátor pointer-to-member.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CAutoPtr::m_p](#m_p)|Členské proměnné ukazatele data.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro vytváření a správu inteligentního ukazatele, která pomůže zajistit ochranu před nevracení paměti, že automaticky uvolnění prostředků při spadá mimo rozsah.

Další, `CAutoPtr`konstruktor kopie a přiřazení operátoru převodu vlastnictví ukazatele, kopírování zdroje ukazatel na ukazatel cílový a nastavení zdroje ukazatel na hodnotu NULL. Proto není možné mít dvě `CAutoPtr` objekty každý ukládání stejný ukazatel, a to snižuje možnost odstranění stejný ukazatel dvakrát.

`CAutoPtr` také zjednodušuje vytváření kolekcí ukazatelů. Místo odvození třídy kolekce a přepisování destruktoru, je jednodušší, aby kolekce `CAutoPtr` objekty. Při odstranění kolekce `CAutoPtr` objekty dostanou mimo rozsah, který se automaticky odstranit sami.

[Cheapptr –](../../atl/reference/cheapptr-class.md) a varianty fungovat stejným způsobem jako `CAutoPtr`, s tím rozdílem, že se přidělují a uvolňují paměť pomocí funkce různé haldy místo C++ **nové** a **odstranit** operátory. [Cautovectorptr –](../../atl/reference/cautovectorptr-class.md) je podobný `CAutoPtr`, jediným rozdílem je, že používá **vektorové new []** a **vektoru delete []** k přidělují a uvolňují paměť.

Viz také [cautoptrarray –](../../atl/reference/cautoptrarray-class.md) a [cautoptrlist –](../../atl/reference/cautoptrlist-class.md) když pole nebo seznamy inteligentních ukazatelů jsou povinné.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]

##  <a name="attach"></a>  CAutoPtr::Attach

Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.

```
void Attach(T* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
`CAutoPtr` Objektu bude převzít vlastnictví tohoto ukazatele.

### <a name="remarks"></a>Poznámky

Když `CAutoPtr` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a jakékoli přiděleného objemu dat při dostane mimo rozsah. Pokud [CAutoPtr::Detach](#detach) je volána, programátor je znovu daný odpovědnost za žádné uvolnění při přidělování prostředků.

V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud [CAutoPtr::m_p](#m_p) datový člen aktuálně odkazuje na existující hodnotu; to znamená, že není rovna hodnotě NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).

##  <a name="cautoptr"></a>  CAutoPtr::CAutoPtr

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

*p*<br/>
Stávajícího ukazatele.

*TSrc*<br/>
Typ spravované jiným `CAutoPtr`, která slouží k inicializaci aktuální objekt.

### <a name="remarks"></a>Poznámky

`CAutoPtr` Objektu lze vytvořit pomocí stávajícího ukazatele, v takovém případě ji převede vlastnictví ukazatele.

### <a name="example"></a>Příklad

Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).

##  <a name="dtor"></a>  CAutoPtr:: ~ CAutoPtr

Destruktor.

```
~CAutoPtr() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky. Volání [CAutoPtr::Free](#free).

##  <a name="detach"></a>  CAutoPtr::Detach

Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.

```
T* Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí kopii ukazatele.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví ukazatele, nastaví [CAutoPtr::m_p](#m_p) data členskou proměnnou na hodnotu NULL a vrátí kopii ukazatele. Po volání `Detach`, ho je až programátorovi, aby uvolněte všechny přidělené prostředky nad tím, které `CAutoPtr` objekt může mít dříve předpokládá, že reponsibility.

### <a name="example"></a>Příklad

Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).

##  <a name="free"></a>  CAutoPtr::Free

Volejte tuto metodu za účelem odstranění objektu, na které odkazují `CAutoPtr`.

```
void Free() throw();
```

### <a name="remarks"></a>Poznámky

Objekt, který odkazuje `CAutoPtr` je uvolněn a [CAutoPtr::m_p](#m_p) data členská proměnná je nastavena na hodnotu NULL.

##  <a name="m_p"></a>  CAutoPtr::m_p

Členské proměnné ukazatele data.

```
T* m_p;
```

### <a name="remarks"></a>Poznámky

Tato členská proměnná uchovává informace o ukazatel.

##  <a name="operator_eq"></a>  CAutoPtr::operator =

Operátor přiřazení.

```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```

### <a name="parameters"></a>Parametry

*p*<br/>
Ukazatel.

*TSrc*<br/>
Typ třídy.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na **CAutoPtr\< T >**.

### <a name="remarks"></a>Poznámky

Operátor přiřazení odpojí `CAutoPtr` objekt z jakékoli aktuální ukazatel a připojí nový ukazatel *p*, na příslušné místo.

### <a name="example"></a>Příklad

Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).

##  <a name="operator_ptr"></a>  CAutoPtr::operator-&gt;

Operátor pointer-to-member.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu [CAutoPtr::m_p](#m_p) data členské proměnné.

### <a name="remarks"></a>Poznámky

Operátor volání metody ve třídě, na které odkazují `CAutoPtr` objektu. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud `CAutoPtr` odkazuje na hodnotu NULL.

### <a name="example"></a>Příklad

Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).

##  <a name="operator_t_star"></a>  CAutoPtr::operator T *

Operátor přetypování.

```
operator T* () const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na objekt typu dat definovanému v šabloně třídy.

### <a name="example"></a>Příklad

Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).

## <a name="see-also"></a>Viz také

[CHeapPtr – třída](../../atl/reference/cheapptr-class.md)<br/>
[CAutoVectorPtr – třída](../../atl/reference/cautovectorptr-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
