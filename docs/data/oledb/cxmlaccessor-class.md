---
title: CXMLAccessor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 71922df2b4d94d06b21ade32b4d8c4ca22fa50c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065418"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor – třída

Umožňuje přístup ke zdrojům dat jako řetězce dat, když nemají žádné informace o schématu úložiště dat (podkladová struktura).

## <a name="syntax"></a>Syntaxe

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Požadavky

**Hlavička**: také atldbcli.h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetXMLColumnData –](#getxmlcolumndata)|Načte informace o sloupci.|
|[GetXMLRowData](#getxmlrowdata)|Načte celý obsah tabulky po řádcích.|

## <a name="remarks"></a>Poznámky

Ale `CXMLAccessor` se liší od `CDynamicStringAccessorW` , převede všechna data z úložiště dat jako ve formátu XML (označené) data. To je užitečné zejména pro výstup do webových stránek s ohledem na XML. Názvy značek XML se co nejpřesněji odpovídají názvy sloupců dat úložiště.

Použití `CDynamicAccessor` metody získat informace o sloupci. Informace o tomto sloupci použijete k vytvoření přistupující objekt dynamicky za běhu.

Informace o sloupci je uložená do vyrovnávací paměti, vytvářet a spravovat touto třídou. Získání informací pomocí sloupce [GetXMLColumnData](#getxmlcolumndata) nebo získat sloupce dat podle řádků pomocí [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Příklad

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="getxmlcolumndata"></a> CXMLAccessor::GetXMLColumnData

Načte informace o typu sloupců tabulky jako řetězec ve formátu XML data podle sloupce.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
[out] Odkaz na vyrovnávací paměti řetězce obsahující informace o typu sloupce, který se má načíst. Řetězec je formátováno s názvy značek XML, které odpovídají názvy sloupců dat úložiště.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Následuje ukázka, jak informace o typu sloupce je ve formátu XML. `type` Určuje datový typ sloupce. Všimněte si, že datové typy, které jsou založeny na typech dat OLE DB, nejsou u databáze, ke kterému přistupujete.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="getxmlrowdata"></a> CXMLAccessor::GetXMLRowData

Načte celý obsah tabulky jako řetězec ve formátu XML dat po řádku.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput, 
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
[out] Odkaz na vyrovnávací paměť obsahující data tabulky, který se má načíst. Jeho data formátovaná jako data řetězce s názvy značek XML, které odpovídají názvy sloupců dat úložiště.

*bAppend*<br/>
[in] Logická hodnota určující, jestli se má připojit řetězec za účelem výstupní data.

### <a name="return-value"></a>Návratová hodnota

Jeden standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Následuje ukázka, jak data řádku je ve formátu XML. `DATA` níže představuje data řádku. Použití přesunutí metody pro přechod na požadovaný řádek.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA – třída](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW – třída](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)