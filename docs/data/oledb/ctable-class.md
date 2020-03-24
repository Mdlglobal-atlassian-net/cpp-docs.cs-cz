---
title: CTable – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: 47c9899889bbbf9b09300779691085786db0e088
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211143"
---
# <a name="ctable-class"></a>CTable – třída

Poskytuje způsob, jak přímý přístup k jednoduché sadě řádků (jedna bez parametrů).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
            template <typename T> class TRowset = CRowset>
class CTable :
   public CAccessorRowset <TAccessor, TRowset>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Přístupová třída.

*TRowset*<br/>
Třída sady řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Otevírají](#open)|Otevře tabulku.|

## <a name="remarks"></a>Poznámky

Informace o tom, jak spustit příkaz pro přístup k sadě řádků, naleznete v tématu [CCommand](../../data/oledb/ccommand-class.md) .

## <a name="ctableopen"></a><a name="open"></a>CTable:: Open

Otevře tabulku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   LPCSTR szTableName,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();

HRESULT Open(const CSession& session,
   DBID& dbid,
   DBPROPSET* pPropSet = NULL,
   ULONG ulPropSets = 0) throw ();
```

#### <a name="parameters"></a>Parametry

*jednání*<br/>
pro Relace, pro kterou je tabulka otevřená

*wszTableName*<br/>
pro Název tabulky, která se má otevřít, předaná jako řetězec Unicode

*szTableName*<br/>
pro Název tabulky, která se má otevřít, předaná jako řetězec ANSI.

*dbid*<br/>
pro `DBID` tabulky, která se má otevřít

*pPropSet*<br/>
pro Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury obsahující vlastnosti a hodnoty, které mají být nastaveny. Viz [sady vlastností a skupiny vlastností](/previous-versions/windows/desktop/ms713696(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK. Výchozí hodnota NULL neurčuje žádné vlastnosti.

*ulPropSets*<br/>
pro Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur předaných v argumentu *pPropSet* .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další podrobnosti naleznete v tématu [IOpenRowset:: OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
