---
title: CBookmark – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: 89c7e62e51adbe96bee870b4baa8a35784b61ac0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447252"
---
# <a name="cbookmark-class"></a>CBookmark – třída

Obsahuje hodnotu záložky ve své vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
Velikost vyrovnávací paměti pro záložky v bajtech Pokud je *nSize* nula, vyrovnávací paměť záložky se dynamicky vytvoří v době běhu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CBookmark](#cbookmark)|Konstruktor|
|[GetBuffer](#getbuffer)|Načte ukazatel na vyrovnávací paměť.|
|[GetSize](#getsize)|Načte velikost vyrovnávací paměti v bajtech.|
|[SetBookmark](#setbookmark)|Nastaví hodnotu záložky.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator)|Přiřadí jednu třídu `CBookmark` k druhé.|

## <a name="remarks"></a>Poznámky

`CBookmark<0>` je specializace šablony `CBookmark`; jeho vyrovnávací paměť je dynamicky vytvořena v době běhu.

## <a name="cbookmark"></a>CBookmark:: CBookmark

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parametry

*nSize*<br/>
pro Velikost vyrovnávací paměti pro záložky v bajtech

### <a name="remarks"></a>Poznámky

První funkce nastaví vyrovnávací paměť na NULL a velikost vyrovnávací paměti na 0. Druhá funkce nastaví velikost vyrovnávací paměti na *nSize*a vyrovnávací paměť na bajtové pole *nSize* bajtů.

> [!NOTE]
>  Tato funkce je k dispozici pouze v `CBookmark<0>`.

## <a name="getbuffer"></a>CBookmark:: GetBuffer

Načte ukazatel na vyrovnávací paměť záložky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť záložky.

## <a name="getsize"></a>CBookmark:: GetSize

Načte velikost vyrovnávací paměti záložky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Velikost vyrovnávací paměti v bajtech.

## <a name="setbookmark"></a>CBookmark:: SetBookmark

Zkopíruje hodnotu záložky, na kterou odkazuje *pBuffer* , do vyrovnávací paměti `CBookmark` a nastaví velikost vyrovnávací paměti na *nSize*.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*nSize*<br/>
pro Velikost vyrovnávací paměti záložky

*pBuffer*<br/>
pro Ukazatel na pole bajtů obsahující hodnotu záložky.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je k dispozici pouze v `CBookmark<0>`.

## <a name="operator"></a>CBookmark:: operator =

Přiřadí objekt `CBookmark` k druhému.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor je vyžadován pouze v `CBookmark<0>`.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)