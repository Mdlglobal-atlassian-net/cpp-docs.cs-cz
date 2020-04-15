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
ms.openlocfilehash: d3d82ea09b7ed2c1cbaf325906b4f9b480e1eb4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359325"
---
# <a name="cbookmark-class"></a>CBookmark – třída

Obsahuje hodnotu záložky v jeho vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Parametry

*nVelikost*<br/>
Velikost vyrovnávací paměti záložky v bajtech. Když *nSize* je nula, vyrovnávací paměť záložky bude dynamicky vytvořena v době běhu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CBookmark](#cbookmark)|Konstruktor|
|[Getbuffer](#getbuffer)|Načte ukazatel do vyrovnávací paměti.|
|[GetSize](#getsize)|Načte velikost vyrovnávací paměti v bajtů.|
|[Značka SetBookmark](#setbookmark)|Nastaví hodnotu záložky.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator)|Přiřadí `CBookmark` jednu třídu do jiné třídy.|

## <a name="remarks"></a>Poznámky

`CBookmark<0>`je šablona specializace `CBookmark`; jeho vyrovnávací paměť je dynamicky vytvořena za běhu.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBookmark::CBookmark

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parametry

*nVelikost*<br/>
[v] Velikost vyrovnávací paměti záložky v bajtech.

### <a name="remarks"></a>Poznámky

První funkce nastaví vyrovnávací paměť na hodnotu NULL a velikost vyrovnávací paměti na hodnotu 0. Druhá funkce nastaví velikost vyrovnávací paměti na *nSize*a vyrovnávací paměť na bajtou pole *bajtů nSize.*

> [!NOTE]
> Tato funkce je `CBookmark<0>`k dispozici pouze v aplikaci .

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBookmark::GetBuffer

Načte ukazatel do vyrovnávací paměti záložky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť záložky.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBookmark::GetSize

Načte velikost vyrovnávací paměti záložky.

### <a name="syntax"></a>Syntaxe

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Velikost vyrovnávací paměti v bajtů.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBookmark:SetBookmark

Zkopíruje hodnotu záložky, na `CBookmark` kterou *pBuffer* odkazuje, do vyrovnávací paměti a nastaví velikost vyrovnávací paměti na *nSize*.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parametry

*nVelikost*<br/>
[v] Velikost vyrovnávací paměti záložky.

*pVyrovnávací paměť*<br/>
[v] Ukazatel na bajtové pole obsahující hodnotu záložky.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Tato funkce je `CBookmark<0>`k dispozici pouze v aplikaci .

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBookmark::operátor =

Přiřadí `CBookmark` objekt jinému objektu.

### <a name="syntax"></a>Syntaxe

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor je `CBookmark<0>`potřeba pouze v .

## <a name="see-also"></a>Viz také

[Šablony spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Odkaz na šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
