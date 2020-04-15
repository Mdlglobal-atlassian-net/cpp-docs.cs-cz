---
title: Třída CHandle
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 7c72ded75298ed69efe73c1a81abf404545ea9b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326926"
---
# <a name="chandle-class"></a>Třída CHandle

Tato třída poskytuje metody pro vytváření a používání objektu popisovače.

## <a name="syntax"></a>Syntaxe

```
class CHandle
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Konstruktor|
|[CHandle::~CHandle](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CHandle::Připojit](#attach)|Volání této metody `CHandle` připojit objekt k existující muško.|
|[CHandle::Zavřít](#close)|Volání této metody `CHandle` zavřít objekt.|
|[CHandle::Detach](#detach)|Volání této metody odpojit `CHandle` popisovač od objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CHandle::POPISOVAČ operátora](#operator_handle)|Vrátí hodnotu uloženého popisovače.|
|[CHandle::operátor =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CHandle::m_h](#m_h)|Členská proměnná, která ukládá popisovač.|

## <a name="remarks"></a>Poznámky

Objekt `CHandle` lze použít vždy, když je požadován popisovač: hlavní rozdíl je, že `CHandle` objekt bude automaticky odstraněn.

> [!NOTE]
> Některé funkce rozhraní API budou používat hodnotu NULL jako prázdný nebo neplatný popisovač, zatímco jiné používají INVALID_HANDLE_VALUE. `CHandle`používá pouze null a bude považovat INVALID_HANDLE_VALUE jako skutečný popisovač. Pokud zavoláte rozhraní API, které může vrátit INVALID_HANDLE_VALUE, měli byste zkontrolovat tuto hodnotu před [voláním CHandle::Attach](#attach) nebo passing to `CHandle` konstruktoru a místo toho předat NULL.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>CHandle::Připojit

Volání této metody `CHandle` připojit objekt k existující muško.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*H*<br/>
`CHandle`převezme vlastnictví rukojeti *h*.

### <a name="remarks"></a>Poznámky

Přiřadí `CHandle` objekt popisovači *h* a potom zavolá **h.Detach()**. V sestaveních debugs bude aktivovánat ATLASSERT, pokud *h* je NULL. Není provedena žádná jiná kontrola platnosti rukojeti.

## <a name="chandlechandle"></a><a name="chandle"></a>CHandle::CHandle

Konstruktor

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*H*<br/>
Existující popisovač `CHandle`nebo .

### <a name="remarks"></a>Poznámky

Vytvoří nový `CHandle` objekt, volitelně pomocí `CHandle` existujícího úchytu nebo objektu.

## <a name="chandlechandle"></a><a name="dtor"></a>CHandle::~CHandle

Destruktor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní `CHandle` objekt voláním [CHandle::Close](#close).

## <a name="chandleclose"></a><a name="close"></a>CHandle::Zavřít

Volání této metody `CHandle` zavřít objekt.

```
void Close() throw();
```

### <a name="remarks"></a>Poznámky

Zavře úchyt otevřeného objektu. Pokud je popisovač NULL, což `Close` bude případ, pokud již byla volána, ATLASSERT bude aktivována v sestavení ladění.

## <a name="chandledetach"></a><a name="detach"></a>CHandle::Detach

Volání této metody odpojit `CHandle` popisovač od objektu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí úchyt, který je odpojen.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví popisovače.

## <a name="chandlem_h"></a><a name="m_h"></a>CHandle::m_h

Členská proměnná, která ukládá popisovač.

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>CHandle::operátor =

Operátor přiřazení.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parametry

*H*<br/>
`CHandle`převezme vlastnictví rukojeti *h*.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CHandle` nový objekt.

### <a name="remarks"></a>Poznámky

Pokud `CHandle` objekt aktuálně obsahuje popisovač, bude uzavřen. Předávaný `CHandle` objekt bude mít jeho popisovač odkaz nastaven na NULL. Tím je zajištěno, že dva `CHandle` objekty nikdy nebudou obsahovat stejný aktivní popisovač.

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>CHandle::POPISOVAČ operátora

Vrátí hodnotu uloženého popisovače.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu uloženou v [chandle::m_h](#m_h).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
