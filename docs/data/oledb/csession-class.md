---
title: CSession – třída
ms.date: 11/04/2016
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
ms.openlocfilehash: 72797411b100480a06e27b71b000264070e57e32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211130"
---
# <a name="csession-class"></a>CSession – třída

Představuje jednu relaci přístupu k databázi.

## <a name="syntax"></a>Syntaxe

```cpp
class CSession
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Abort](#abort)|Zruší (ukončí) transakci.|
|[Uzavírací](#close)|Zavře relaci.|
|[Potvrzuj](#commit)|Potvrdí transakci.|
|[GetTransactionInfo](#gettransactioninfo)|Vrátí informace týkající se transakce.|
|[Otevírají](#open)|Otevře novou relaci pro objekt zdroje dat.|
|[StartTransaction](#starttransaction)|Zahájí novou transakci pro tuto relaci.|

## <a name="remarks"></a>Poznámky

Jednu nebo více relací lze přidružit ke každému připojení zprostředkovatele (zdroji dat), který je reprezentován objektem [CDataSource](../../data/oledb/cdatasource-class.md) . Chcete-li vytvořit nový `CSession` pro `CDataSource`, zavolejte [CSession:: Open](../../data/oledb/csession-open.md). Chcete-li zahájit databázovou transakci, `CSession` poskytuje metodu `StartTransaction`. Po spuštění transakce ji můžete potvrdit pomocí metody `Commit`, nebo ji zrušit pomocí metody `Abort`.

## <a name="csessionabort"></a><a name="abort"></a>CSession:: Abort

Ukončí transakci.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Abort(BOID* pboidReason = NULL,
   BOOL bRetaining = FALSE,
   BOOL bAsync = FALSE) const throw();
```

#### <a name="parameters"></a>Parametry

Viz téma [ITransaction:: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="csessionclose"></a><a name="close"></a>CSession:: Close

Zavře relaci, která byla otevřena pomocí [CSession:: Open](../../data/oledb/csession-open.md).

### <a name="syntax"></a>Syntaxe

```cpp
void Close() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní ukazatel `m_spOpenRowset`.

## <a name="csessioncommit"></a><a name="commit"></a>CSession:: Commit

Potvrdí transakci.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Commit(BOOL bRetaining = FALSE,
   DWORD grfTC = XACTTC_SYNC,
   DWORD grfRM = 0) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [ITransaction:: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85)).

## <a name="csessiongettransactioninfo"></a><a name="gettransactioninfo"></a>CSession:: GetTransactionInfo

Vrátí informace týkající se transakce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [ITransaction:: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [ITransaction:: GetTransactionInfo](/previous-versions/windows/desktop/ms714975(v=vs.85)) v *Referenční příručce programátora OLE DB*.

## <a name="csessionopen"></a><a name="open"></a>CSession:: Open

Otevře novou relaci pro objekt zdroje dat.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CDataSource& ds,
   DBPROPSET *pPropSet = NULL,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parametry

*služby*<br/>
pro Zdroj dat, pro který má být relace otevřena.

*pPropSet*<br/>
pro Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury obsahující vlastnosti a hodnoty, které mají být nastaveny. Viz [sady vlastností a skupiny vlastností](/previous-versions/windows/desktop/ms713696(v=vs.85)) v *referenci OLE DB programátora* v Windows SDK.

*ulPropSets*<br/>
pro Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktur předaných v argumentu *pPropSet* .

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Je nutné otevřít objekt zdroje dat pomocí [CDataSource:: Open](../../data/oledb/cdatasource-open.md) před předáním do `CSession::Open`.

## <a name="csessionstarttransaction"></a><a name="starttransaction"></a>CSession:: StartTransaction

Zahájí novou transakci pro tuto relaci.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,
   ULONG isoFlags = 0,
   ITransactionOptions* pOtherOptions = NULL,
   ULONG* pulTransactionLevel = NULL) const throw();
```

#### <a name="parameters"></a>Parametry

Viz [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [ITransactionLocal:: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[CatDB](../../overview/visual-cpp-samples.md)<br/>
[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
