---
title: CDBVariant – třída
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 9bb70acb43f2e73ade86b753ebbb7949759ce88d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754596"
---
# <a name="cdbvariant-class"></a>CDBVariant – třída

Představuje typ dat varianty pro třídy Knihovny MFC ODBC.

## <a name="syntax"></a>Syntaxe

```
class CDBVariant
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Vytvoří `CDBVariant` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDBVariant::Vymazat](#clear)|Vymaže `CDBVariant` objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Obsahuje datový typ aktuálně uložené hodnoty. Zadejte `DWORD`.|

### <a name="public-union-members"></a>Členové veřejných odborů

|Název|Popis|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Obsahuje hodnotu typu **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Obsahuje hodnotu typu **nepodepsaný znak**.|
|[CDBVariant::m_dblVal](#m_dblval)|Obsahuje hodnotu typu **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Obsahuje hodnotu typu **float**.|
|[CDBVariant::m_iVal](#m_ival)|Obsahuje hodnotu typu **short**.|
|[CDBVariant::m_lVal](#m_lval)|Obsahuje hodnotu typu **long**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Obsahuje ukazatel na objekt `CLongBinary`typu .|
|[CDBVariant::m_pdate](#m_pdate)|Obsahuje ukazatel na objekt typu **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Obsahuje ukazatel na objekt `CString`typu .|
|[CDBVariant::m_pstringA](#m_pstringa)|Ukládá ukazatel na objekt ASCII [CString.](../../atl-mfc-shared/reference/cstringt-class.md)|
|[CDBVariant::m_pstringW](#m_pstringw)|Ukládá ukazatel na široký [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.|

## <a name="remarks"></a>Poznámky

`CDBVariant`nemá základní třídu.

`CDBVariant`je podobný [COleVariant](../../mfc/reference/colevariant-class.md); však `CDBVariant` nepoužívá OLE. `CDBVariant`umožňuje uložit hodnotu bez obav o datový typ hodnoty. `CDBVariant`sleduje datový typ aktuální hodnoty, která je uložena v unii.

Třída [CRecordset](../../mfc/reference/crecordset-class.md) `CDBVariant` využívá objekty ve `GetFieldValue` `GetBookmark`třech `SetBookmark`členských funkcích: , a . Umožňuje například `GetFieldValue` dynamicky načítat data ve sloupci. Vzhledem k tomu, že datový typ sloupce `GetFieldValue` nemusí `CDBVariant` být znám za běhu, používá objekt k uložení dat sloupce.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CDBVariant`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant::CDBVariant

Vytvoří objekt `CDBVariant` NULL.

```
CDBVariant();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen [m_dwType](#m_dwtype) na DBVT_NULL.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant::Vymazat

Volání této členské funkce `CDBVariant` vymazat objekt.

```cpp
void Clear();
```

### <a name="remarks"></a>Poznámky

Pokud je hodnota [datového](#m_dwtype) člena m_dwType DBVT_DATE, `Clear` DBVT_STRING nebo DBVT_BINARY, uvolní paměť přidruženou k členu ukazatele unie. `Clear`nastaví `m_dwType` na DBVT_NULL.

Destruktor `CDBVariant` `Clear`volá .

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant::m_boolVal

Ukládá hodnotu typu BOOL.

### <a name="remarks"></a>Poznámky

Datový `m_boolVal` člen patří do unie. Před přístupem `m_boolVal`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_boolVal` na DBVT_BOOL, pak bude obsahovat platnou hodnotu; v opačném `m_boolVal` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant::m_chVal

Ukládá hodnotu typu **nepodepsané char**.

### <a name="remarks"></a>Poznámky

Datový `m_chVal` člen patří do unie. Před přístupem `m_chVal`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_chVal` na DBVT_UCHAR, pak obsahuje platnou hodnotu; v opačném `m_chVal` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant::m_dblVal

Ukládá hodnotu typu **double**.

### <a name="remarks"></a>Poznámky

Datový `m_dblVal` člen patří do unie. Před přístupem `m_dblVal`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_dblVal` na DBVT_DOUBLE, pak obsahuje platnou hodnotu; v opačném `m_dblVal` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant::m_dwType

Tento datový člen obsahuje datový typ pro hodnotu, `CDBVariant` která je aktuálně uložena v datovém členu sjednocení objektu.

### <a name="remarks"></a>Poznámky

Před přístupem k této unie, je `m_dwType` nutné zkontrolovat hodnotu, aby bylo možné určit, který člen dat unie pro přístup. V následující tabulce jsou `m_dwType` uvedeny možné hodnoty pro a odpovídající datový člen unie.

|m_dwType|Datový člen Unie|
|---------------|-----------------------|
|DBVT_NULL|Žádný člen unie není platný pro přístup.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant::m_fltVal

Ukládá hodnotu typu **float**.

### <a name="remarks"></a>Poznámky

Datový `m_fltVal` člen patří do unie. Před přístupem `m_fltVal`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_fltVal` na DBVT_SINGLE, pak obsahuje platnou hodnotu; v opačném `m_fltVal` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant::m_iVal

Ukládá hodnotu typu **short**.

### <a name="remarks"></a>Poznámky

Datový `m_iVal` člen patří do unie. Před přístupem `m_iVal`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_iVal` na DBVT_SHORT, pak obsahuje platnou hodnotu; v opačném `m_iVal` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant::m_lVal

Ukládá hodnotu typu **long**.

### <a name="remarks"></a>Poznámky

Datový `m_lVal` člen patří do unie. Před přístupem `m_lVal`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_lVal` na DBVT_LONG, pak obsahuje platnou hodnotu; v opačném `m_lVal` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant::m_pbinary

Ukládá ukazatel na objekt typu [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Poznámky

Datový `m_pbinary` člen patří do unie. Před přístupem `m_pbinary`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_pbinary` na DBVT_BINARY, pak obsahuje platný ukazatel; v opačném `m_pbinary` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant::m_pdate

Uloží ukazatel na objekt typu TIMESTAMP_STRUCT.

### <a name="remarks"></a>Poznámky

Datový `m_pdate` člen patří do unie. Před přístupem `m_pdate`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_pdate` na DBVT_DATE, pak obsahuje platný ukazatel; v opačném `m_pdate` případě bude přístup k nespolehlivé výsledky.

Další informace o datovém typu TIMESTAMP_STRUCT naleznete v tématu [Datové typy C](/sql/odbc/reference/appendixes/c-data-types) v dodatku D odkazu *programátora ODBC* v sadě Windows SDK.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant::m_pstring

Ukládá ukazatel na objekt typu [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Poznámky

Datový `m_pstring` člen patří do unie. Před přístupem `m_pstring`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_pstring` na DBVT_STRING, pak obsahuje platný ukazatel; v opačném `m_pstring` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant::m_pstringA

Ukládá ukazatel na objekt ASCII [CString.](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>Poznámky

Datový `m_pstringA` člen patří do unie. Před přístupem `m_pstringA`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_pstringA` na DBVT_ASTRING, pak obsahuje platný ukazatel; v opačném `m_pstringA` případě bude přístup k nespolehlivé výsledky.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant::m_pstringW

Ukládá ukazatel na široký [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.

### <a name="remarks"></a>Poznámky

Datový `m_pstringW` člen patří do unie. Před přístupem `m_pstringW`nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastavena `m_pstringW` na DBVT_WSTRING, pak obsahuje platný ukazatel; v opačném `m_pstringW` případě bude přístup k nespolehlivé výsledky.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
