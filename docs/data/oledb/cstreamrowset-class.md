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
ms.openlocfilehash: ad4987422fd200faef141150908d4df0722f669a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366275"
---
# <a name="cstreamrowset-class"></a>CStreamRowset – třída

Používá se `CCommand` `CTable` v deklaraci nebo.

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parametry

*TPřipis*<br/>
Třída přistupujícího objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Cstreamrowset](#cstreamrowset)|Konstruktor Instance objektu `CStreamRowset` inicializuje a inicializuje.|
|[Zavřít](#close)|Uvolní ukazatel rozhraní [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) ve třídě.|

## <a name="remarks"></a>Poznámky

Použijte `CStreamRowset` ve `CCommand` `CTable` svém prohlášení nebo prohlášení, například:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

– nebo –

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute`vrátí `ISequentialStream` ukazatel, který je `m_spStream`uložen v aplikaci . Poté použijete `Read` metodu k načtení dat (řetězce Unicode) ve formátu XML. Příklad:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 provede formátování XML a vrátí všechny sloupce a všechny řádky sady řádků jako jeden řetězec XML.

> [!NOTE]
> Tato funkce funguje pouze se serverem SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset::CStreamRowset

Instance objektu `CStreamRowset` inicializuje a inicializuje.

### <a name="syntax"></a>Syntaxe

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset::Zavřít

Uvolní ukazatel rozhraní [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) ve třídě.

### <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

## <a name="see-also"></a>Viz také

[Šablony spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Odkaz na šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
