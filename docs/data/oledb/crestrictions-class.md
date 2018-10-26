---
title: CRestrictions – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a4ea0536a8af87927521f88d888e19aa145f2c04
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072067"
---
# <a name="crestrictions-class"></a>CRestrictions – třída

Obecná třída, která vám umožní zadat omezení pro sad řádků schématu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Parametry

*T*<br/>
Třída použitá pro přistupující objekt.

*nRestrictions*<br/>
Počet sloupců omezení pro sadu řádků schématu.

*pguid*<br/>
Ukazatel na identifikátor GUID schématu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbsch.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Otevřít](#open)|Vrací sadu podle uživatelem zadané omezení výsledků.|

## <a name="open"></a> CRestrictions::Open

Vrací sadu podle uživatelem zadané omezení výsledků.

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

*Relace*<br/>
[in] Určuje existující relaci objekt používaný pro připojení ke zdroji dat.

*lpszParam*<br/>
[in] Určuje omezení na sadu řádků schématu.

*bBind*<br/>
[in] Určuje, jestli se má svázat mapy sloupce automaticky. Výchozí hodnota je **true**, což způsobí, že mapování sloupce vázat automaticky. Nastavení *bBind* k **false** brání automatické vazby mapy sloupce tak, aby mohl vytvořit vazbu ručně. (Ruční vazba je zajímavé především uživatelům OLAP).

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Můžete zadat maximálně sedm omezení pro sadu řádků schématu.

Zobrazit [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686) informace o definovaných omezení na jednotlivých řádků schématu.

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)