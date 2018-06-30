---
title: Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faa94f14461ed41229d11857125a317b00c27abd
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123029"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView
Toto téma obsahuje seznam DDX_Field – funkce, které slouží pro výměnu dat mezi [CRecordset](../../mfc/reference/crecordset-class.md) a [CRecordView](../../mfc/reference/crecordview-class.md) formuláře nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) a [ CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formuláře.  
  
> [!NOTE]
>  DDX_Field – funkce jsou jako funkce DDX v tom, že si vyměňují dat s ovládacími prvky ve formuláři. Ale na rozdíl od DDX, jejich vyměňovat data s poli objekt přidružené sady záznamů zobrazení a nikoli s poli samotném zobrazení záznamu. Další informace najdete v tématu třídy `CRecordView` a `CDaoRecordView`.  
  
### <a name="ddxfield-functions"></a>DDX_Field – funkce  
  
|||  
|-|-|  
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Přenosy dat celé číslo mezi členem sady záznamů pole data a index aktuální výběr v poli se seznamem v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|  
|[Ddx_fieldcbstring –](#ddx_fieldcbstring)|Přenosy `CString` dat mezi pole datových členů sady záznamů a upravit ovládacího prvku pole se seznamem pole `CRecordView` nebo `CDaoRecordView`. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere položku do pole se seznamem, který začíná znaky v zadaném řetězci.|  
|[Ddx_fieldcbstringexact –](#ddx_fieldcbstringexact)|Přenosy `CString` dat mezi pole datových členů sady záznamů a upravit ovládacího prvku pole se seznamem pole `CRecordView` nebo `CDaoRecordView`. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere položku do pole se seznamem, který přesně odpovídá zadaný řetězec.|  
|[Ddx_fieldcheck –](#ddx_fieldcheck)|Boolean – datový přenos mezi členem sady záznamů pole data a zaškrtněte políčko v `CRecordView` nebo `CDaoRecordView`.|  
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Přenosy dat celé číslo mezi členem sady záznamů pole data a index aktuální výběr v seznamu v `CRecordView` nebo `CDaoRecordView`.|  
|[Ddx_fieldlbstring –](#ddx_fieldlbstring)|Spravuje přenos [CString](../../atl-mfc-shared/reference/cstringt-class.md) dat mezi ovládacího prvku pole se seznamem a pole datových členů sady záznamů. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere položka v seznamu, který začíná znaky v zadaném řetězci.|  
|[Ddx_fieldlbstringexact –](#ddx_fieldlbstringexact)|Spravuje přenos `CString` dat mezi ovládacího prvku pole se seznamem a pole datových členů sady záznamů. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere první položka, který přesně odpovídá zadaný řetězec.|  
|[DDX_FieldRadio](#ddx_fieldradio)|Přenosy dat celé číslo mezi pole datových členů sady záznamů a skupinu přepínačů v `CRecordView` nebo `CDaoRecordView`.|  
|[Ddx_fieldscroll –](#ddx_fieldscroll)|Nastaví nebo získá pozici posunutí ovládací prvek posuvníku v `CRecordView` nebo `CDaoRecordView`. Volání z vaší [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkce.|  
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronizuje jezdec pozice ovládací prvek typu jezdec v zobrazení záznamů a `int` pole datových členů sady záznamů. |
|[DDX_FieldText](#ddx_fieldtext)|Přetížené verze jsou k dispozici pro přenos `int`, **Celé_číslo**, **dlouho**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float** , **dvojité**, **krátké**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), a [COleCurrency](../../mfc/reference/colecurrency-class.md) dat mezi pole datových členů sady záznamů a upravíte pole `CRecordView` nebo `CDaoRecordView`.|  
  
##  <a name="ddx_fieldcbindex"></a>  Ddx_fieldcbindex –  
 `DDX_FieldCBIndex` Funkce synchronizuje index vybrané položky v ovládacím prvku seznamu pole ovládacího prvku pole se seznamem v zobrazení záznamu a `int` pole datových členů sady záznamů přidružené zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *index*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví výběru v ovládacím prvku na základě hodnoty zadané v *index*. Na přenos ze sady záznamů do ovládacího prvku Pokud je sada záznamů pole hodnotu Null, MFC nastaví hodnotu indexu na hodnotu 0. Přenos z ovládacího prvku do sady záznamů Pokud ovládací prvek je prázdný nebo pokud není vybrána žádná položka, pole Sada záznamů nastavena na hodnotu 0.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. V příkladu by podobné pro `DDX_FieldCBIndex`.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  

##  <a name="ddx_fieldcbstring"></a>  Ddx_fieldcbstring –  
 `DDX_FieldCBString` Funkce spravuje přenos [CString](../../atl-mfc-shared/reference/cstringt-class.md) dat mezi ovládacího prvku úprav ovládacího prvku pole se seznamem v zobrazení záznamu a `CString` pole datových členů sady záznamů přidružené zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který začíná znaky v zadaném v řetězci *hodnotu*. Na přenos ze sady záznamů do ovládacího prvku, pokud je sada záznamů pole hodnotu Null, všechny výběru se odebere z pole se seznamem a upravit ovládacího prvku pole se seznamem je nastavena na prázdnou. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null pokud umožňuje pole.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. V příkladu obsahuje volání `DDX_FieldCBString`.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
## <a name="ddx_fieldcbstringexact"></a>  Ddx_fieldcbstringexact –  
 `DDX_FieldCBStringExact` Funkce spravuje přenos [CString](../../atl-mfc-shared/reference/cstringt-class.md) dat mezi ovládacího prvku úprav ovládacího prvku pole se seznamem v zobrazení záznamu a `CString` pole datových členů sady záznamů přidružené zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který přesně odpovídá řetězec zadaný v *hodnotu*. Na přenos ze sady záznamů do ovládacího prvku, pokud je sada záznamů pole hodnotu NULL, všechny výběru se odebere z pole se seznamem a pole pro úpravy pole se seznamem nastavena na prázdnou. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu NULL.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldCBStringExact` podobat.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="ddx_fieldcheck"></a>  Ddx_fieldcheck –  
 `DDX_FieldCheck` Funkce spravuje přenos **int** formuláři dat mezi ovládací prvek zaškrtávací políčko v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a **int** dialogové okno, zobrazení formuláře nebo ovládacího prvku – datový člen objekt zobrazení.  
  
```  
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládací prvek zaškrtávací políčko, které jsou spojené s vlastností ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_FieldCheck` je volána, *hodnotu* nastavena na aktuální stav ovládací prvek zaškrtávací políčko, nebo je nastavena do stavu ovládacího prvku *hodnotu*, v závislosti na směru přenosu.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="ddx_fieldlbindex"></a>  Ddx_fieldlbindex –  
 `DDX_FieldLBIndex` Funkce synchronizuje index vybrané položky v ovládacím prvku seznamu pole v zobrazení záznamu a **int** pole datových členů sady záznamů přidružené zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,    
    int nIDC,   
    int& index,  
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *index*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví výběru v ovládacím prvku na základě hodnoty zadané v *index*. Na přenos ze sady záznamů do ovládacího prvku Pokud je sada záznamů pole hodnotu Null, MFC nastaví hodnotu indexu na hodnotu 0. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu 0.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="ddx_fieldlbstring"></a>  Ddx_fieldlbstring –  
 `DDX_FieldLBString` Zkopíruje v zobrazení záznamu pro aktuální výběr ovládacího prvku seznam [CString](../../atl-mfc-shared/reference/cstringt-class.md) pole datových členů sady záznamů přidružené zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 V opačném směru, tato funkce nastaví aktuální výběr v seznamu na první řádek, který začíná znaky v řetězci určeného *hodnotu*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, všechny výběr odeberou se z pole se seznamem. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldLBString` podobat.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="ddx_fieldlbstringexact"></a>  Ddx_fieldlbstringexact –  
 `DDX_FieldLBStringExact` Funkce zkopíruje v zobrazení záznamu pro aktuální výběr ovládacího prvku seznam [CString](../../atl-mfc-shared/reference/cstringt-class.md) pole datových členů sady záznamů přidružené zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 V opačném směru, tato funkce nastaví aktuální výběr v seznamu na první řádek, který přesně odpovídá řetězec zadaný v *hodnotu*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, všechny výběr odeberou se z pole se seznamem. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldLBStringExact` podobat.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="ddx_fieldradio"></a>  Ddx_fieldradio –  
 `DDX_FieldRadio` Funkce přidruží nulovým základem **int** členské proměnné sady záznamů zobrazení záznamu s aktuálně vybraného přepínače ve skupině přepínacích tlačítek v zobrazení záznamu.  
  
```  
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID první ve skupině (s styl ws_group –) prvků sousedících přepínačů v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Při přenosu ze sady záznamů pole do zobrazení, tato funkce se změní *n-tou* přepínač (počítáno od nuly) a vypne zobrazování jiných tlačítek. V opačném směru tato funkce nastaví pole Sada záznamů na řadová číslovka přepínač, který je aktuálně na (zaškrtnuto). Přenos ze sady záznamů do ovládacího prvku Pokud je sada záznamů pole hodnotu Null, žádné tlačítko je zapnutá. Přenos z ovládacího prvku do sady záznamů Pokud je vybraný žádný ovládací prvek, pole Sada záznamů nastavena na hodnotu Null pokud umožňuje pole, která.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldRadio` podobat.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="ddx_fieldscroll"></a>  Ddx_fieldscroll –  
 `DDX_FieldScroll` Funkce synchronizuje pozici posunutí ovládací prvek posuvníku v zobrazení záznamu a **int** pole datových členů sady záznamů přidružené zobrazení záznamu (nebo s jakoukoli proměnná s celým číslem rozhodnete namapovat je na) .  
  
```  
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID první ve skupině (s styl ws_group –) prvků sousedících přepínačů v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví pozici posunutí ovládacího panelu přejděte na hodnotu zadanou v *hodnotu*. Přenos ze sady záznamů do ovládacího prvku Pokud je sada záznamů pole hodnotu Null, ovládacích prvků posuv panelu nastavena na hodnotu 0. Na přenos z ovládacího prvku do sady záznamů Pokud ovládací prvek je prázdné, hodnota pole Sada záznamů je 0.  
  
 První verzi použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhá verze použijte, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldScroll` podobat.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  

  ## <a name="nameddxfieldslidera--ddxfieldslider"></a>name="ddx_fieldslider"></a>  DDX_FieldSlider
`DDX_FieldSlider` Funkce synchronizuje jezdec pozice ovládací prvek typu jezdec v zobrazení záznamů a **int** pole datových členů sady záznamů přidružené zobrazení záznamu (nebo s jakoukoli proměnná s celým číslem rozhodnete namapovat je na).  
   
### <a name="syntax"></a>Syntaxe  
  ```
   void AFXAPI DDX_FieldSlider(  
       CDataExchange* pDX,  
       int nIDC,  
       int& value,  
       CRecordset* pRecordset );  

void AFXAPI DDX_FieldSlider(  
     CDataExchange* pDX,  
     int nIDC,  
     int& value,  
     CDaoRecordset* pRecordset );  
```
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku v ovládacím prvku posuvník.  
  
 *value*  
 Odkaz na hodnotu výměnu. Tento parametr obsahuje nebo se použije k nastavení ovládacího prvku posuvník aktuální pozici jezdce.  
  
 *pRecordset*  
 Ukazatel na přidruženého `CRecordset` nebo `CDaoRecordset` objekt, ke které se vyměňují data.  
   
### <a name="remarks"></a>Poznámky  
 Při přesunu dat ze sady záznamů na posuvníku, tato funkce nastavuje pozici jezdec na hodnotu zadanou v *hodnotu*. Přenos ze sady záznamů do ovládacího prvku Pokud je sada záznamů pole hodnotu Null, umístění v ovládacím prvku posuvník nastavena na hodnotu 0. Na přenos z ovládacího prvku do sady záznamů Pokud ovládací prvek je prázdné, hodnota pole Sada záznamů je 0.  
  
 `DDX_FieldSlider` není výměna informací o rozsahu s podporou nastavení rozsahu než jednoduše pozice ovládací prvky posuvníku.  
  
 Pokud pracujete s třídy založené na rozhraní ODBC, použijte první přepsání funkce. Pomocí třídy založené na rozhraní DAO druhý přepsání.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro `CRecordView` a `CDaoRecordView` pole, najdete v části [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Informace o ovládacích prvcích posuvníku najdete v tématu [pomocí CSliderCtrl](../using-csliderctrl.md).  
   
### <a name="example"></a>Příklad  
 V tématu [DDX_FieldText –](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldSlider` podobat.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
  
##  <a name="ddx_fieldtext"></a>  DDX_FieldText –  
 `DDX_FieldText` Funkce spravuje přenos **int**, **krátké**, **dlouho**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **dvojité**, **BOOL**, nebo **BAJTŮ** dat mezi prvek upravit a pole datových členů sady záznamů.  
  
```  
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BYTE& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    int& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    UINT& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    long& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    DWORD& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    float& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    double& value,   
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    short& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BOOL& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    BYTE& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    long& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    DWORD& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    CString& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    float& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    double& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    COleDateTime& value,   
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,    
    int nIDC,   
    COleCurrency& value,   
    CDaoRecordset* pRecordset);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.  
  
 *value*  
 Odkaz na pole datových členů v přidruženém `CRecordset` nebo `CDaoRecordset` objektu. Datový typ hodnoty závisí na kterém přetížené verze `DDX_FieldText` používáte.  
  
 *pRecordset*  
 Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekt, ke které se vyměňují data. Umožňuje tento ukazatel `DDX_FieldText` ke zjišťování a nastavit hodnoty Null.  
  
### <a name="remarks"></a>Poznámky  
 Pro [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekty, `DDX_FieldText` také spravuje přenos [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), a [COleCurrency](../../mfc/reference/colecurrency-class.md) hodnoty. Prvek prázdný upravit označuje hodnotu Null. Přenos ze sady záznamů do ovládacího prvku, pokud je sada záznamů pole hodnotu Null, textové pole nastavena na prázdnou. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null.  
  
 Použijte verzi pomocí [CRecordset](../../mfc/reference/crecordset-class.md) parametry, pokud pracujete s třídy založené na rozhraní ODBC. Použijte verzi pomocí [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) parametry, pokud pracujete s třídy založené na rozhraní DAO.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).  
  
### <a name="example"></a>Příklad  
 Následující `DoDataExchange` funkce pro [CRecordView](../../mfc/reference/crecordview-class.md) obsahuje `DDX_FieldText` volání funkce pro tři datové typy: `IDC_COURSELIST` je pole se seznamem; dvou ovládacích prvků jsou úpravy polí. Pro rozhraní DAO programování *m_pSet* parametr je ukazatel na [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 [!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]  

  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
