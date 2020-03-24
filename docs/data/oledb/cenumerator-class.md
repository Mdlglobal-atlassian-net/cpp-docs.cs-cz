---
title: CEnumerator – třída
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: d0fa5f381dba4f67934007d59dbdaf4450bcfb60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211793"
---
# <a name="cenumerator-class"></a>CEnumerator – třída

Používá objekt čítače OLE DB, který zpřístupňuje rozhraní [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) , aby vrátil sadu řádků popisující všechny zdroje dat a enumerátory.

## <a name="syntax"></a>Syntaxe

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Hledání](#find)|Vyhledá přes dostupné zprostředkovatele (zdroje dat), který hledá jeden se zadaným názvem.|
|[GetMoniker](#getmoniker)|Načte rozhraní `IMoniker` pro aktuální záznam.|
|[Otevírají](#open)|Otevře enumerátor.|

## <a name="remarks"></a>Poznámky

Data `ISourcesRowset` můžete načíst nepřímo z této třídy.

## <a name="cenumeratorfind"></a><a name="find"></a>CEnumerator –:: Find

Vyhledá zadaný název mezi dostupnými poskytovateli.

### <a name="syntax"></a>Syntaxe

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Parametry

*szSearchName*<br/>
pro Název, který chcete vyhledat.

### <a name="return-value"></a>Návratová hodnota

**hodnota true** , pokud byl nalezen název. V opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento název se mapuje na `SOURCES_NAME` člen rozhraní [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) .

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a>CEnumerator –:: GetMoniker

Analyzuje zobrazovaný název pro extrakci komponenty řetězce, který lze převést na moniker.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Parametry

*ppMoniker*<br/>
mimo Moniker se analyzuje z zobrazovaného názvu ([CEnumeratorAccessor:: m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) aktuálního řádku.

*lpszDisplayName*<br/>
pro Zobrazovaný název, který se má analyzovat

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="cenumeratoropen"></a><a name="open"></a>CEnumerator –:: Open

Váže moniker pro enumerátor, pokud je zadán, a načte sadu řádků pro enumerátor voláním [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Parametry

*pMoniker*<br/>
pro Ukazatel na moniker pro enumerátor.

*pClsid*<br/>
pro Ukazatel na `CLSID` výčtu.

*čítače*<br/>
pro Odkaz na enumerátor.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="see-also"></a>Viz také

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
