---
title: CAccessorRowset – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: adb59e553565d9886cf27b55f2cfffb4cd0e7aa9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060153"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset – třída

Zapouzdřuje sadu řádků a jejich přidružené přístupových objektů v jedné třídě.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Třídu přistupujícího objektu.

*TRowset*<br/>
Třídy sady řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Bind](#bind)|Vytvoří vazbu (nepoužívá, pokud `bBind` je zadán jako **false** v [CCommand::Open](../../data/oledb/ccommand-open.md)).|
|[CAccessorRowset](#caccessorrowset)|Konstruktor|
|[Zavřít](#close)|Zavře sadu řádků a všechny přistupující objekty.|
|[Freerecordmemory –](#freerecordmemory)|Uvolní všechny sloupce v aktuální záznam, který musí být uvolněna.|
|[GetColumnInfo –](#getcolumninfo)|Implementuje [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704).|

## <a name="remarks"></a>Poznámky

Třída `TAccessor` spravuje přistupujícího objektu. Třída *TRowset* spravuje v sadě řádků.

## <a name="bind"></a> CAccessorRowset::Bind

Vytvoří vazbu, pokud jste zadali `bBind` jako **false** v [CCommand::Open](../../data/oledb/ccommand-open.md).

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

## <a name="caccessorrowset"></a> CAccessorRowset::CAccessorRowset

Inicializuje `CAccessorRowset` objektu.

### <a name="syntax"></a>Syntaxe

```cpp
CAccessorRowset();
```

## <a name="close"></a> CAccessorRowset::Close

Uvolní všechny aktivní přístupové objekty a sady řádků.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidružené paměti.

## <a name="freerecordmemory"></a> CAccessorRowset::FreeRecordMemory

Uvolní všechny sloupce v aktuální záznam, který musí být uvolněna.

### <a name="syntax"></a>Syntaxe

```cpp
void FreeRecordMemory();
```

## <a name="getcolumninfo"></a> CAccessorRowset::GetColumnInfo

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

Zobrazit [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *referenční informace pro OLE DB programátory*.

### <a name="return-value"></a>Návratová hodnota

Standardní HRESULT.

### <a name="remarks"></a>Poznámky

Uživatel musí uvolnit informace vrácené sloupce a vyrovnávací paměti pro řetězec. Druhá verze tuto metodu použijte, když používáte [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) a je nutné přepsat vazbách.

Další informace najdete v tématu [IColumnsInfo::GetColumnInfo](/previous-versions/windows/desktop/ms722704) v *OLE DB referenční informace pro programátory*.

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)