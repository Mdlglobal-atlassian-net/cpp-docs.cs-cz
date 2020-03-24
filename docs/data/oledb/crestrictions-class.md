---
title: CRestrictions – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 4a4c86987ceff0f04986d32011ba941e0d2319fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211299"
---
# <a name="crestrictions-class"></a>CRestrictions – třída

Obecná třída, která umožňuje určit omezení pro sady řádků schématu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Třída použitá pro přistupující objekt

*nRestrictions*<br/>
Počet sloupců omezení pro sadu řádků schématu.

*pguid*<br/>
Ukazatel na identifikátor GUID schématu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldbsch. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Otevírají](#open)|Vrátí sadu výsledků dle omezení zadaných uživatelem.|

## <a name="crestrictionsopen"></a><a name="open"></a>CRestrictions –:: Open

Vrátí sadu výsledků dle omezení zadaných uživatelem.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>Parametry

*jednání*<br/>
pro Určuje existující objekt relace, který se používá pro připojení ke zdroji dat.

*lpszParam*<br/>
pro Určuje omezení pro sadu řádků schématu.

*bBind*<br/>
pro Určuje, jestli se má mapovat Mapa sloupce automaticky. Výchozí hodnota je **true**, což způsobí, že mapování sloupce bude automaticky svázáno. Nastavením *bBind* na **false** zabráníte automatické vazbě na mapě sloupce, abyste se mohli svázat ručně. (Ruční vazba je zvláště důležitá pro uživatele OLAP.)

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Můžete zadat maximálně sedm omezení pro sadu řádků schématu.

Informace o definovaných omezeních pro jednotlivé sady řádků schématu naleznete v sadě [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) .

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
