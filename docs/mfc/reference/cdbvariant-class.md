---
title: CDBVariant – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: e1c3ccdba1de9191079630989facf154ccf62d7f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465317"
---
# <a name="cdbvariant-class"></a>CDBVariant – třída
Představuje je odlišný datový typ pro třídy knihovny MFC rozhraní ODBC.  
  
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
  
### <a name="public-union-members"></a>Veřejné členy sjednocení.  
  
|Název|Popis|  
|----------|-----------------|  
|[CDBVariant::m_boolVal](#m_boolval)|Obsahuje hodnotu typu **BOOL**.|  
|[CDBVariant::m_chVal](#m_chval)|Obsahuje hodnotu typu **unsigned char**.|  
|[CDBVariant::m_dblVal](#m_dblval)|Obsahuje hodnotu typu **double**.|  
|[CDBVariant::m_fltVal](#m_fltval)|Obsahuje hodnotu typu **float**.|  
|[CDBVariant::m_iVal](#m_ival)|Obsahuje hodnotu typu **krátký**.|  
|[CDBVariant::m_lVal](#m_lval)|Obsahuje hodnotu typu **dlouhé**.|  
|[CDBVariant::m_pbinary](#m_pbinary)|Obsahuje ukazatel na objekt typu `CLongBinary`.|  
|[CDBVariant::m_pdate](#m_pdate)|Obsahuje ukazatel na objekt typu **TIMESTAMP_STRUCT z**.|  
|[CDBVariant::m_pstring](#m_pstring)|Obsahuje ukazatel na objekt typu `CString`.|  
|[CDBVariant::m_pstringA](#m_pstringa)|Uchovává ukazatel na ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.|  
|[CDBVariant::m_pstringW](#m_pstringw)|Uchovává ukazatel na široké [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CDBVariant` nemá základní třídu.  
  
 `CDBVariant` je podobný [COleVariant](../../mfc/reference/colevariant-class.md), nicméně `CDBVariant` nepoužívá OLE. `CDBVariant` Umožňuje uložit hodnotu bez starostí o datový typ hodnoty. `CDBVariant` sleduje datový typ aktuální hodnotu, která je uložena ve sjednocení.  
  
 Třída [CRecordset](../../mfc/reference/crecordset-class.md) využívá `CDBVariant` objekty ve třech členské funkce: `GetFieldValue`, `GetBookmark`, a `SetBookmark`. Například `GetFieldValue` umožňuje dynamicky načíst data ve sloupci. Vzhledem k tomu, že datový typ sloupce nemusí být známá v době běhu `GetFieldValue` používá `CDBVariant` objekt pro uložení dat sloupce.  
  
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
 Nastaví [m_dwType](#m_dwtype) datový člen do DBVT_NULL.  
  
##  <a name="clear"></a>  CDBVariant::Clear  
 Voláním této členské funkce zrušte `CDBVariant` objektu.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud hodnota [m_dwType](#m_dwtype) datový člen je DBVT_DATE, DBVT_STRING nebo DBVT_BINARY, `Clear` uvolní paměť spojených se členem Unie ukazatele. `Clear` Nastaví `m_dwType` k DBVT_NULL.  
  
 `CDBVariant` Volání destruktoru `Clear`.  
  
##  <a name="m_boolval"></a>  CDBVariant::m_boolVal  
 Uloží hodnotu typu BOOL.  
  
### <a name="remarks"></a>Poznámky  
 `m_boolVal` Patří datový člen sjednocení. Před použitím `m_boolVal`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_BOOL, pak `m_boolVal` bude obsahovat platnou hodnotu; v opačném případě přístupu k `m_boolVal` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_chval"></a>  CDBVariant::m_chVal  
 Ukládá hodnotu typu **unsigned char**.  
  
### <a name="remarks"></a>Poznámky  
 `m_chVal` Patří datový člen sjednocení. Před použitím `m_chVal`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_UCHAR, pak `m_chVal` obsahuje platnou hodnotu; v opačném případě přístupu k `m_chVal` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_dblval"></a>  CDBVariant::m_dblVal  
 Ukládá hodnotu typu **double**.  
  
### <a name="remarks"></a>Poznámky  
 `m_dblVal` Patří datový člen sjednocení. Před použitím `m_dblVal`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_DOUBLE, pak `m_dblVal` obsahuje platnou hodnotu; v opačném případě přístupu k `m_dblVal` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_dwtype"></a>  CDBVariant::m_dwType  
 Tomuto datovému členu obsahuje typ dat pro hodnotu, která je aktuálně uloženo v `CDBVariant` sjednocení datový člen objektu.  
  
### <a name="remarks"></a>Poznámky  
 Před použitím této sjednocení, musíte zkontrolovat hodnoty `m_dwType` aby bylo možné určit, které sjednocení datový člen pro přístup k. V následující tabulce jsou uvedeny možné hodnoty pro `m_dwType` a odpovídající sjednocení datových členů.  
  
|m_dwType|Sjednocení datový člen|  
|---------------|-----------------------|  
|DBVT_NULL|Žádný člen sjednocení je platný pro přístup.|  
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
  
##  <a name="m_fltval"></a>  CDBVariant::m_fltVal  
 Ukládá hodnotu typu **float**.  
  
### <a name="remarks"></a>Poznámky  
 `m_fltVal` Patří datový člen sjednocení. Před použitím `m_fltVal`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_SINGLE, pak `m_fltVal` obsahuje platnou hodnotu; v opačném případě přístupu k `m_fltVal` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_ival"></a>  CDBVariant::m_iVal  
 Ukládá hodnotu typu **krátký**.  
  
### <a name="remarks"></a>Poznámky  
 `m_iVal` Patří datový člen sjednocení. Před použitím `m_iVal`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_SHORT, pak `m_iVal` obsahuje platnou hodnotu; v opačném případě přístupu k `m_iVal` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_lval"></a>  CDBVariant::m_lVal  
 Ukládá hodnotu typu **dlouhé**.  
  
### <a name="remarks"></a>Poznámky  
 `m_lVal` Patří datový člen sjednocení. Před použitím `m_lVal`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_LONG, pak `m_lVal` obsahuje platnou hodnotu; v opačném případě přístupu k `m_lVal` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary  
 Uchovává ukazatel na objekt typu [CLongBinary](../../mfc/reference/clongbinary-class.md).  
  
### <a name="remarks"></a>Poznámky  
 `m_pbinary` Patří datový člen sjednocení. Před použitím `m_pbinary`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_BINARY, pak `m_pbinary` obsahuje platný ukazatel; v opačném případě přístupu k `m_pbinary` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_pdate"></a>  CDBVariant::m_pdate  
 Uchovává ukazatel na objekt typu TIMESTAMP_STRUCT z.  
  
### <a name="remarks"></a>Poznámky  
 `m_pdate` Patří datový člen sjednocení. Před použitím `m_pdate`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_DATE, pak `m_pdate` obsahuje platný ukazatel; v opačném případě přístupu k `m_pdate` vytvoří nespolehlivé výsledky.  
  
 Další informace o typu TIMESTAMP_STRUCT z dat, naleznete v tématu [datové typy jazyka C](/previous-versions/windows/desktop/ms714556\(v=vs.85\)) v dodatku D *ODBC programátora* v sadě Windows SDK.  
  
##  <a name="m_pstring"></a>  CDBVariant::m_pstring  
 Uchovává ukazatel na objekt typu [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Poznámky  
 `m_pstring` Patří datový člen sjednocení. Před použitím `m_pstring`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_STRING, pak `m_pstring` obsahuje platný ukazatel; v opačném případě přístupu k `m_pstring` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA  
 Uchovává ukazatel na ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `m_pstringA` Patří datový člen sjednocení. Před použitím `m_pstringA`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_ASTRING, pak `m_pstringA` obsahuje platný ukazatel; v opačném případě přístupu k `m_pstringA` vytvoří nespolehlivé výsledky.  
  
##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW  
 Uchovává ukazatel na široké [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `m_pstringW` Patří datový člen sjednocení. Před použitím `m_pstringW`, nejprve zkontrolujte hodnotu [CDBVariant::m_dwType](#m_dwtype). Pokud `m_dwType` nastavena na DBVT_WSTRING, pak `m_pstringW` obsahuje platný ukazatel; v opačném případě přístupu k `m_pstringW` vytvoří nespolehlivé výsledky.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)
