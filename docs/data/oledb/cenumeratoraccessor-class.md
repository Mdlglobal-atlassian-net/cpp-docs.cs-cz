---
title: CEnumeratorAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: e94f7a5d34a134d4b05211bd5fa03f7c498fa45a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646482"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor – třída

Používá [CEnumerator](../../data/oledb/cenumerator-class.md) pro přístup k datům z enumerátor sady řádků.

## <a name="syntax"></a>Syntaxe

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="members"></a>Členové

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_bIsParent](#bisparent)|Proměnná označující, zda je čítač nadřazené čítače, pokud je řádek enumerátor.|
|[m_nType](#ntype)|Proměnná označující, zda řádek popisuje zdroje dat nebo enumerátor.|
|[m_szDescription](#szdescription)|Popis zdroje dat nebo enumerátor.|
|[m_szName](#szname)|Název zdroje dat nebo enumerátor.|
|[m_szParseName](#szparsename)|Řetězec pro [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) získat monikeru pro zdroj dat nebo enumerátor.|

## <a name="remarks"></a>Poznámky

Tato sada řádků se skládá z zdroje dat a enumerátory viditelné z aktuálního výčtu.

## <a name="bisparent"></a> CEnumeratorAccessor::m_bIsParent

Proměnná označující, zda je čítač nadřazené čítače, pokud je řádek enumerátor.

### <a name="syntax"></a>Syntaxe

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200) v *OLE DB referenční informace pro programátory* Další informace.

## <a name="ntype"></a> CEnumeratorAccessor::m_nType

Proměnná označující, zda řádek popisuje zdroje dat nebo enumerátor.

### <a name="syntax"></a>Syntaxe

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200) v *OLE DB referenční informace pro programátory* Další informace.

## <a name="szdescription"></a> CEnumeratorAccessor::m_szDescription

Popis zdroje dat nebo enumerátor.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200) v *OLE DB referenční informace pro programátory* Další informace.

## <a name="szname"></a> CEnumeratorAccessor::m_szName

Název zdroje dat nebo enumerátor.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200) v *OLE DB referenční informace pro programátory* Další informace.

## <a name="szparsename"></a> CEnumeratorAccessor::m_szParseName

Řetězec pro [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) získat monikeru pro zdroj dat nebo enumerátor.

### <a name="syntax"></a>Syntaxe

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200) v *OLE DB referenční informace pro programátory* Další informace.

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)