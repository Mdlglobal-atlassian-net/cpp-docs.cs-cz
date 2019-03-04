---
title: Chandle – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 19e761ea8eb133db55b4d24600f2a1fd01ac3e34
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292897"
---
# <a name="chandle-class"></a>Chandle – třída

Tato třída poskytuje metody pro vytváření a používání popisovač objektu.

## <a name="syntax"></a>Syntaxe

```
class CHandle
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHandle::CHandle](#chandle)|Konstruktor|
|[Chandle –:: ~ chandle –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHandle::Attach](#attach)|Voláním této metody lze připojit `CHandle` objektů pro existující popisovač.|
|[CHandle::Close](#close)|Volejte tuto metodu za účelem Zavřít `CHandle` objektu.|
|[CHandle::Detach](#detach)|Volejte tuto metodu za účelem odpojení popisovač z `CHandle` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CHandle::operator POPISOVAČ](#operator_handle)|Vrací hodnotu uloženou popisovač.|
|[CHandle::operator =](#operator_eq)|Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CHandle::m_h](#m_h)|Členské proměnné, která uloží popisovač.|

## <a name="remarks"></a>Poznámky

A `CHandle` objekt lze použít vždy, když je povinný popisovač: Hlavní rozdíl je, že `CHandle` objekt bude automaticky odstraněno.

> [!NOTE]
>  Některé funkce rozhraní API budete používat jako prázdný nebo neplatný popisovač, NULL, zatímco v jiných INVALID_HANDLE_VALUE. `CHandle` využívá pouze hodnotu NULL a bude považovat INVALID_HANDLE_VALUE skutečné popisovač. Při volání rozhraní API, která může vrátit INVALID_HANDLE_VALUE, by měla vyhledávat tuto hodnotu před voláním [CHandle::Attach](#attach) nebo jejich předání do `CHandle` konstruktoru a místo toho předat hodnotu NULL.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="attach"></a>  CHandle::Attach

Voláním této metody lze připojit `CHandle` objektů pro existující popisovač.

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*h*<br/>
`CHandle` převezme vlastnictví popisovač *h*.

### <a name="remarks"></a>Poznámky

Přiřazuje `CHandle` objektu *h* zpracovat. V sestaveních ladí, bude-li vyvolána ATLASSERT *h* má hodnotu NULL. Žádné další typové kontroly za jako platnosti popisovače.

##  <a name="chandle"></a>  CHandle::CHandle

Konstruktor

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>Parametry

*h*<br/>
Existující popisovač nebo `CHandle`.

### <a name="remarks"></a>Poznámky

Vytvoří novou `CHandle` objektu, případně můžete použít existující popisovač nebo `CHandle` objektu.

##  <a name="dtor"></a>  Chandle –:: ~ chandle –

Destruktor.

```
~CHandle() throw();
```

### <a name="remarks"></a>Poznámky

Uvolňuje `CHandle` objektu voláním [CHandle::Close](#close).

##  <a name="close"></a>  CHandle::Close

Volejte tuto metodu za účelem Zavřít `CHandle` objektu.

```
void Close() throw();
```

### <a name="remarks"></a>Poznámky

Zavře otevřený objekt popisovače. Pokud je popisovač je NULL, což bude v případě, pokud `Close` již byla volána, ATLASSERT, bude vyvolána v sestaveních ladění.

##  <a name="detach"></a>  CHandle::Detach

Volejte tuto metodu za účelem odpojení popisovač z `CHandle` objektu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač budou tímto odpojeny.

### <a name="remarks"></a>Poznámky

Uvolní vlastnictví objektu popisovač.

##  <a name="m_h"></a>  CHandle::m_h

Členské proměnné, která uloží popisovač.

```
HANDLE m_h;
```

##  <a name="operator_eq"></a>  CHandle::operator =

Operátor přiřazení.

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>Parametry

*h*<br/>
`CHandle` převezme vlastnictví popisovač *h*.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na nové `CHandle` objektu.

### <a name="remarks"></a>Poznámky

Pokud `CHandle` objekt aktuálně obsahuje popisovač, bude uzavřeno. `CHandle` Objektu předávaný bude mít odkaz na jeho popisovač nastavena na hodnotu NULL. To zajistí, že dvě `CHandle` objekty, nikdy neobsahuje stejné aktivní zpracování.

##  <a name="operator_handle"></a>  CHandle::operator POPISOVAČ

Vrací hodnotu uloženou popisovač.

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>Poznámky

Vrací hodnotu uloženou v [CHandle::m_h](#m_h).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
