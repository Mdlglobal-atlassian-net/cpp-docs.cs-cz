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
ms.openlocfilehash: bb44af102f08e05edddc2fb692d1e30dd7e31717
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556670"
---
# <a name="cenumerator-class"></a>CEnumerator – třída

Používá objekt enumerátoru OLE DB, která zveřejní [ISourcesRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms715969(v=vs.85)) rozhraní vrátit sadu řádků s popisem všechny zdroje dat a enumerátory.

## <a name="syntax"></a>Syntaxe

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Najít](#find)|Hledá v rámci (zdroje dat) dostupných poskytovatelů vyhledávání pro jeden se zadaným názvem.|
|[GetMoniker](#getmoniker)|Načte `IMoniker` rozhraní pro požadovaný aktuální záznam.|
|[Otevřít](#open)|Otevře se enumerátor.|

## <a name="remarks"></a>Poznámky

Můžete načíst `ISourcesRowset` data nepřímo z této třídy.

## <a name="find"></a> CEnumerator::Find

Vyhledá zadaný název mezi dostupných zprostředkovatelů.

### <a name="syntax"></a>Syntaxe

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Parametry

*szSearchName*<br/>
[in] Název, který se má hledat.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud název nebyl nalezen. V opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tento název se mapuje `SOURCES_NAME` člena [ISourcesRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms715969(v=vs.85)) rozhraní.

## <a name="getmoniker"></a> CEnumerator::GetMoniker

Analyzuje zobrazovaný název na extrahuje komponentu řetězec, který lze převést na moniker.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Parametry

*ppMoniker*<br/>
[out] Moniker služby byl analyzován ze zobrazovaného jména ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) aktuálního řádku.

*lpszDisplayName*<br/>
[in] Zobrazovaný název analyzovat.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="open"></a> CEnumerator::Open

Vazeb zástupný název čítače, pokud jeden je zadán, pak načte sada řádků pro enumerátor voláním [ISourcesRowset::GetSourcesRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Parametry

*pMoniker*<br/>
[in] Ukazatel na moniker enumerátor.

*pClsid*<br/>
[in] Ukazatel `CLSID` čítače.

*Enumerátor*<br/>
[in] Odkaz na enumerátor.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="see-also"></a>Viz také

[DBViewer](../../visual-cpp-samples.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)