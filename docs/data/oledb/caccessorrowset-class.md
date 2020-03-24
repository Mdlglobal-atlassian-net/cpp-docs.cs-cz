---
title: CAccessorRowset – třída
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
ms.openlocfilehash: efb5618c03b1f70a809bb2bafe9611474799e00b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212248"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset – třída

Zapouzdřuje sadu řádků a její přidružené přistupující objekty v jediné třídě.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
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
|[Bind](#bind)|Vytvoří vazby (používá se, když je `bBind` zadáno jako **false** v [CCommand:: Open](../../data/oledb/ccommand-open.md)).|
|[CAccessorRowset –](#caccessorrowset)|Konstruktor|
|[Uzavírací](#close)|Zavře sadu řádků a všechny přistupující objekty.|
|[FreeRecordMemory](#freerecordmemory)|Uvolní všechny sloupce v aktuálním záznamu, které je třeba uvolnit.|
|[GetColumnInfo –](#getcolumninfo)|Implementuje [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)).|

## <a name="remarks"></a>Poznámky

Třída `TAccessor` spravuje přistupující objekt. Třída *TRowset* spravuje sadu řádků.

## <a name="caccessorrowsetbind"></a><a name="bind"></a>CAccessorRowset –:: bind

Vytvoří vazby, pokud jste zadali `bBind` jako **false** v [CCommand:: Open](../../data/oledb/ccommand-open.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="caccessorrowsetcaccessorrowset"></a><a name="caccessorrowset"></a>CAccessorRowset –:: CAccessorRowset –

Inicializuje objekt `CAccessorRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CAccessorRowset();
```

## <a name="caccessorrowsetclose"></a><a name="close"></a>CAccessorRowset –:: Close

Uvolní všechny aktivní přistupující objekty a sadu řádků.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Uvolní jakoukoli přidruženou paměť.

## <a name="caccessorrowsetfreerecordmemory"></a><a name="freerecordmemory"></a>CAccessorRowset –:: FreeRecordMemory

Uvolní všechny sloupce v aktuálním záznamu, které je třeba uvolnit.

### <a name="syntax"></a>Syntaxe

```cpp
void FreeRecordMemory();
```

## <a name="caccessorrowsetgetcolumninfo"></a><a name="getcolumninfo"></a>CAccessorRowset –:: GetColumnInfo

Získá informace o sloupci z otevřené sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>Parametry

Viz [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenci OLE DB programátora*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Uživatel musí uvolnit vrácené informace o sloupci a vyrovnávací paměť řetězců. Druhou verzi této metody použijte, když použijete [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) a potřebujete přepsat vazby.

Další informace naleznete v tématu [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) v *referenci programátora OLE DB*.

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
