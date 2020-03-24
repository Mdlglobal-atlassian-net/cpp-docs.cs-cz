---
title: CXMLAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211039"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor – třída

Umožňuje přístup ke zdrojům dat jako řetězcová data, pokud nemáte žádné znalosti schématu úložiště dat (základní struktura).

## <a name="syntax"></a>Syntaxe

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Požadavky

**Záhlaví**: atldbcli. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Načte informace o sloupci.|
|[GetXMLRowData](#getxmlrowdata)|Načte celý obsah tabulky podle řádků.|

## <a name="remarks"></a>Poznámky

`CXMLAccessor` se ale liší od `CDynamicStringAccessorW` v tom, že převádí všechna data, která jsou dostupná z úložiště dat, jako data ve formátu XML (označená). To je užitečné hlavně pro výstup na webové stránky podporující XML. Názvy značek XML budou odpovídat názvům sloupců úložiště dat co nejpřesněji.

K získání informací o sloupci použijte `CDynamicAccessor` metody. Tyto informace o sloupci slouží k vytvoření přístupového objektu dynamicky v době běhu.

Informace o sloupci jsou uloženy ve vyrovnávací paměti vytvořené a spravované touto třídou. Získat informace o sloupci pomocí [GetXMLColumnData](#getxmlcolumndata) nebo získat data sloupce podle řádků pomocí [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Příklad

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor –:: GetXMLColumnData

Načte informace o typu sloupce tabulky jako řetězcová data ve formátu XML, podle sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
mimo Odkaz na vyrovnávací paměť řetězců obsahující informace o typu sloupce, které mají být načteny. Řetězec je formátován názvy značek XML, které odpovídají názvům sloupců v úložišti dat.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak jsou informace o typu sloupce formátovány v XML. `type` Určuje datový typ sloupce. Všimněte si, že datové typy jsou založené na OLE DB datových typů, nikoli na tom, jaká databáze je k dispozici.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor –:: GetXMLRowData

Načte celý obsah tabulky jako řetězcová data ve formátu XML, podle řádku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
mimo Odkaz na vyrovnávací paměť obsahující data tabulky, která mají být načtena. Data jsou formátována jako řetězcová data s názvy značek XML, které odpovídají názvům sloupců v úložišti dat.

*bAppend*<br/>
pro Logická hodnota určující, zda se má řetězec připojit k konci výstupních dat.

### <a name="return-value"></a>Návratová hodnota

Jedna ze standardních hodnot HRESULT.

### <a name="remarks"></a>Poznámky

Následující příklad ukazuje, jak jsou data řádků formátována v jazyce XML. `DATA` níže představuje data řádku. K přesunu na požadovaný řádek použijte metody Move.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA – třída](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW – třída](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)
