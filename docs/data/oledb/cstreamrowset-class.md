---
title: CStreamRowset – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
ms.openlocfilehash: 4a0e67ff1e800ff0f838b863eaaf839d4456ed82
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441079"
---
# <a name="cstreamrowset-class"></a>CStreamRowset – třída

Používá se v deklaraci `CCommand` nebo `CTable`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Přístupová třída.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Konstruktor Vytvoří instanci a inicializuje objekt `CStreamRowset`.|
|[Uzavírací](#close)|Uvolní ukazatel rozhraní [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) ve třídě.|

## <a name="remarks"></a>Poznámky

V deklaraci `CCommand` nebo `CTable` použijte `CStreamRowset`, například:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

nebo

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` vrátí ukazatel `ISequentialStream`, který je uložen v `m_spStream`. Pak použijte metodu `Read` k načtení dat (řetězce Unicode) ve formátu XML. Příklad:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 provádí formátování XML a vrátí všechny sloupce a všechny řádky sady řádků jako jeden řetězec XML.

> [!NOTE]
>  Tato funkce funguje jenom s SQL Server 2000.

## <a name="cstreamrowset"></a>CStreamRowset:: CStreamRowset

Vytvoří instanci a inicializuje objekt `CStreamRowset`.

### <a name="syntax"></a>Syntaxe

```cpp
CStreamRowset();
```

## <a name="close"></a>CStreamRowset:: Close

Uvolní ukazatel rozhraní [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) ve třídě.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)