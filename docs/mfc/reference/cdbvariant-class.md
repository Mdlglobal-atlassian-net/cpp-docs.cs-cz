---
title: CDBVariant – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27970a7d3854dca398943bfe13c67f6a4e1f92f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdbvariant-class"></a>CDBVariant – třída
Představuje je odlišný datový typ pro třídy MFC rozhraní ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDBVariant  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDBVariant::CDBVariant](#cdbvariant)|Vytvoří `CDBVariant` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDBVariant::Clear](#clear)|Vymaže `CDBVariant` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDBVariant::m_dwType](#m_dwtype)|Obsahuje datový typ aktuálně uložené hodnoty. Typ `DWORD`.|  
  
### <a name="public-union-members"></a>Veřejné členy sjednocení  
  
|Název|Popis|  
|----------|-----------------|  
|[CDBVariant::m_boolVal](#m_boolval)|Obsahuje hodnotu typu **BOOL**.|  
|[CDBVariant::m_chVal](#m_chval)|Obsahuje hodnotu typu `unsigned char`.|  
|[CDBVariant::m_dblVal](#m_dblval)|Obsahuje hodnotu typu **dvojité**.|  
|[CDBVariant::m_fltVal](#m_fltval)|Obsahuje hodnotu typu **float**.|  
|[CDBVariant::m_iVal](#m_ival)|Obsahuje hodnotu typu **krátké**.|  
|[CDBVariant::m_lVal](#m_lval)|Obsahuje hodnotu typu **dlouho**.|  
|[CDBVariant::m_pbinary](#m_pbinary)|Obsahuje ukazatel na objekt typu `CLongBinary`.|  
|[CDBVariant::m_pdate](#m_pdate)|Obsahuje ukazatel na objekt typu **TIMESTAMP_STRUCT z**.|  
|[CDBVariant::m_pstring](#m_pstring)|Obsahuje ukazatel na objekt typu `CString`.|  
|[CDBVariant::m_pstringA](#m_pstringa)|Ukládá ukazatel na ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.|  
|[CDBVariant::m_pstringW](#m_pstringw)|Ukládá ukazatel na široké [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CDBVariant` nemá základní třídu.  
  
 `CDBVariant` je podobná [COleVariant](../../mfc/reference/colevariant-class.md), nicméně `CDBVariant` nepoužívá OLE. `CDBVariant` Umožňuje ukládání hodnotu bez obav, hodnota datového typu. `CDBVariant` sleduje datový typ aktuální hodnota, která je uložena v spojení.  
  
 Třída [CRecordset](../../mfc/reference/crecordset-class.md) využívá `CDBVariant` objekty v tři členské funkce: `GetFieldValue`, `GetBookmark`, a `SetBookmark`. Například `GetFieldValue` umožňuje dynamicky načíst data ve sloupci. Vzhledem k tomu, že v době běhu, nemusí být známé datový typ sloupce `GetFieldValue` používá `CDBVariant` objekt pro uložení dat sloupce.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDBVariant`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant  
 Vytvoří hodnotu NULL `CDBVariant` objektu.  
  
```  
CDBVariant();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví [m_dwType](#m_dwtype) – datový člen k **DBVT_NULL**.  
  
##  <a name="clear"></a>  CDBVariant::Clear  
 Volání této funkce člen zrušte `CDBVariant` objektu.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud hodnota [m_dwType](#m_dwtype) – datový člen je **DBVT_DATE**, **DBVT_STRING**, nebo **DBVT_BINARY**, **vymazat**uvolní paměť spojených se členem union ukazatele. **Zrušte** nastaví `m_dwType` k **DBVT_NULL**.  
  
 `CDBVariant` Volání destruktoru **zrušte**.  
  
##  <a name="m_boolval"></a>  CDBVariant::m_boolVal  
 Ukládá hodnotu typu **BOOL**.  
  
### <a name="remarks"></a>Poznámky  
 **M_boolVal** – datový člen patří ke sjednocení. Před přístupem k **m_boolVal**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_BOOL**, pak **m_boolVal** bude obsahovat platnou hodnotu; jinak, přístup k **m_boolVal** způsobí nespolehlivé výsledky.  
  
##  <a name="m_chval"></a>  CDBVariant::m_chVal  
 Ukládá hodnotu typu `unsigned char`.  
  
### <a name="remarks"></a>Poznámky  
 **M_chVal** – datový člen patří ke sjednocení. Před přístupem k **m_chVal**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_UCHAR**, pak **m_chVal** obsahuje platnou hodnotu; jinak, přístup k **m_chVal** způsobí nespolehlivé výsledky.  
  
##  <a name="m_dblval"></a>  CDBVariant::m_dblVal  
 Ukládá hodnotu typu **dvojité**.  
  
### <a name="remarks"></a>Poznámky  
 **M_dblVal** – datový člen patří ke sjednocení. Před přístupem k **m_dblVal**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_DOUBLE**, pak **m_dblVal** obsahuje platnou hodnotu; jinak, přístup k **m_dblVal** způsobí nespolehlivé výsledky.  
  
##  <a name="m_dwtype"></a>  CDBVariant::m_dwType  
 Tento člen dat obsahuje typ dat pro hodnotu, která je aktuálně uloženo v `CDBVariant` objektu union datový člen.  
  
### <a name="remarks"></a>Poznámky  
 Před přístupem k této union, je nutné zkontrolovat hodnotu `m_dwType` za účelem zjištění, které union datový člen přístup. Následující tabulka uvádí možné hodnoty pro `m_dwType` a odpovídající union datových členů.  
  
|m_dwType|Union datový člen|  
|---------------|-----------------------|  
|**DBVT_NULL**|Žádné členů sjednocení je platný pro přístup.|  
|**DBVT_BOOL**|[m_boolVal](#m_boolval)|  
|**DBVT_UCHAR**|[m_chVal](#m_chval)|  
|**DBVT_SHORT**|[m_iVal](#m_ival)|  
|**DBVT_LONG**|[m_lVal](#m_lval)|  
|**DBVT_SINGLE**|[m_fltVal](#m_fltval)|  
|**DBVT_DOUBLE**|[m_dblVal](#m_dblval)|  
|**DBVT_DATE**|[m_pdate](#m_pdate)|  
|**DBVT_STRING**|[m_pstring](#m_pstring)|  
|**DBVT_BINARY**|[m_pbinary](#m_pbinary)|  
|**DBVT_ASTRING**|[m_pstringA](#m_pstringa)|  
|**DBVT_WSTRING**|[m_pstringW](#m_pstringw)|  
  
##  <a name="m_fltval"></a>  CDBVariant::m_fltVal  
 Ukládá hodnotu typu **float**.  
  
### <a name="remarks"></a>Poznámky  
 **M_fltVal** – datový člen patří ke sjednocení. Před přístupem k **m_fltVal**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_SINGLE**, pak **m_fltVal** obsahuje platnou hodnotu; jinak, přístup k **m_fltVal** způsobí nespolehlivé výsledky.  
  
##  <a name="m_ival"></a>  CDBVariant::m_iVal  
 Ukládá hodnotu typu **krátké**.  
  
### <a name="remarks"></a>Poznámky  
 **M_iVal** – datový člen patří ke sjednocení. Před přístupem k **m_iVal**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_SHORT**, pak **m_iVal** obsahuje platnou hodnotu; jinak, přístup k **m_iVal** způsobí nespolehlivé výsledky.  
  
##  <a name="m_lval"></a>  CDBVariant::m_lVal  
 Ukládá hodnotu typu **dlouho**.  
  
### <a name="remarks"></a>Poznámky  
 **M_lVal** – datový člen patří ke sjednocení. Před přístupem k **m_lVal**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_LONG**, pak **m_lVal** obsahuje platnou hodnotu; jinak, přístup k **m_lVal** způsobí nespolehlivé výsledky.  
  
##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary  
 Ukládá ukazatel na objekt typu [CLongBinary](../../mfc/reference/clongbinary-class.md).  
  
### <a name="remarks"></a>Poznámky  
 **M_pbinary** – datový člen patří ke sjednocení. Před přístupem k **m_pbinary**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_BINARY**, pak **m_pbinary** obsahuje neplatný ukazatel; jinak, přístup k **m_pbinary** způsobí nespolehlivé výsledky.  
  
##  <a name="m_pdate"></a>  CDBVariant::m_pdate  
 Ukládá ukazatel na objekt typu **TIMESTAMP_STRUCT z**.  
  
### <a name="remarks"></a>Poznámky  
 **M_pdate** – datový člen patří ke sjednocení. Před přístupem k **m_pdate**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_DATE**, pak **m_pdate** obsahuje neplatný ukazatel; jinak, přístup k **m_pdate** způsobí nespolehlivé výsledky.  
  
 Další informace o **TIMESTAMP_STRUCT z** datový typ, podívejte se na téma [C datové typy](https://msdn.microsoft.com/library/ms714556.aspx) v dodatku D *referenční informace pro programátory ODBC* ve Windows SDK.  
  
##  <a name="m_pstring"></a>  CDBVariant::m_pstring  
 Ukládá ukazatel na objekt typu [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 **M_pstring** – datový člen patří ke sjednocení. Před přístupem k **m_pstring**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_STRING**, pak **m_pstring** obsahuje neplatný ukazatel; jinak, přístup k **m_pstring** způsobí nespolehlivé výsledky.  
  
##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA  
 Ukládá ukazatel na ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 **M_pstringA** – datový člen patří ke sjednocení. Před přístupem k **m_pstringA**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_ASTRING**, pak **m_pstringA** obsahuje neplatný ukazatel; jinak, přístup k **m_pstringA** způsobí nespolehlivé výsledky.  
  
##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW  
 Ukládá ukazatel na široké [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 **M_pstringW** – datový člen patří ke sjednocení. Před přístupem k **m_pstringW**, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` je nastaven na **DBVT_WSTRING**, pak **m_pstringW** obsahuje neplatný ukazatel; jinak, přístup k **m_pstringW** způsobí nespolehlivé výsledky.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)
