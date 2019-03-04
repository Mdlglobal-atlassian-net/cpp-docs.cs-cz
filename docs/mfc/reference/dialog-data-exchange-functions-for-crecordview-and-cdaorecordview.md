---
title: Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView
ms.date: 11/04/2016
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
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
ms.openlocfilehash: 2a794d16b2f94bf8ba66b6c0398dec262d8829e5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269887"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView

Toto téma obsahuje seznam funkce DDX_Field používané k výměně dat mezi [CRecordset](../../mfc/reference/crecordset-class.md) a [CRecordView](../../mfc/reference/crecordview-class.md) formuláře nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) a [ CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formuláře.

> [!NOTE]
>  DDX_Field – funkce jsou podobné funkce DDX v tom, že si vyměňují dat s ovládacími prvky ve formuláři. Ale na rozdíl od DDX, si vyměňují data s poli typu objektu přidružené sady záznamů v zobrazení, nikoli s poli typu samotném zobrazení záznamu. Další informace najdete v tématu třídy `CRecordView` a `CDaoRecordView`.

### <a name="ddxfield-functions"></a>DDX_Field – funkce

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Přenosy dat celé číslo mezi datový člen polí záznamů a index aktuálního výběru v poli se seznamem [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Přenosy `CString` poli data mezi datový člen záznamů pole a ovládacího prvku pro úpravy pole se seznamem `CRecordView` nebo `CDaoRecordView`. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere položku v poli se seznamem, který začíná znaky v zadaném řetězci.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Přenosy `CString` poli data mezi datový člen záznamů pole a ovládacího prvku pro úpravy pole se seznamem `CRecordView` nebo `CDaoRecordView`. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere položku v poli se seznamem, který se přesně shoduje se zadaný řetězec.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Boolean – datový přenos mezi datový člen polí záznamů a zaškrtněte políčko v `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Přenosy dat celé číslo mezi datový člen polí záznamů a index aktuálně vybrané položky v seznamu v `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Spravuje přenos [CString](../../atl-mfc-shared/reference/cstringt-class.md) data mezi ovládací prvek pole se seznamem a datové členy polí sady záznamů. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere položku v seznamu, který začíná znaky v zadaném řetězci.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Spravuje přenos `CString` data mezi ovládací prvek pole se seznamem a datové členy polí sady záznamů. Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce vybere první položka, která se přesně shoduje se zadaný řetězec.|
|[DDX_FieldRadio](#ddx_fieldradio)|Přenosy dat celé číslo mezi datový člen polí záznamů a skupinu přepínačů v `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Nastaví nebo získá pozici posunutí ovládací prvek posuvníku v `CRecordView` nebo `CDaoRecordView`. Volání z vaší [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkce.|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronizuje thumb pozice posuvníku v zobrazení záznamu a `int` pole datového člena sady záznamů. |
|[DDX_FieldText](#ddx_fieldtext)|Přetížené verze jsou k dispozici pro přenos `int`, **UINT**, **dlouhé**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float** , **double**, **krátký**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), a [COleCurrency](../../mfc/reference/colecurrency-class.md) dat mezi datový člen polí záznamů a úpravy poli `CRecordView` nebo `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

`DDX_FieldCBIndex` Funkce synchronizuje index vybrané položky v rozevírací seznam ovládacího prvku pole se seznamem v zobrazení záznamů a `int` pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*index*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví výběr v ovládacím prvku v závislosti na hodnotě zadané v *index*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, MFC nastaví hodnotu indexu na 0. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný nebo pokud není vybrána žádná položka sady záznamů pole je nastaveno na hodnotu 0.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. V příkladu by měl vypadat přibližně pro `DDX_FieldCBIndex`.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

`DDX_FieldCBString` Funkce spravuje přenos [CString](../../atl-mfc-shared/reference/cstringt-class.md) data mezi ovládacího prvku pro úpravy prvku pole se seznamem v zobrazení záznamu a `CString` pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který začíná znaky v řetězci zadanému v *hodnota*. Na přenos ze sady záznamů do ovládacího prvku, pokud sada záznamů pole má hodnotu Null, nic se odebere z pole se seznamem a ovládacího prvku pro úpravy pole se seznamem je nastavena na prázdnou. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null pokud pole povolí.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Tento příklad obsahuje volání `DDX_FieldCBString`.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

`DDX_FieldCBStringExact` Funkce spravuje přenos [CString](../../atl-mfc-shared/reference/cstringt-class.md) data mezi ovládacího prvku pro úpravy prvku pole se seznamem v zobrazení záznamu a `CString` pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který přesně odpovídá řetězci zadanému v *hodnota*. Na přenos ze sady záznamů do ovládacího prvku, pokud sada záznamů pole má hodnotu NULL, nic se odebere z pole se seznamem a pole pro úpravy pole se seznamem je nastavena na prázdnou. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu NULL.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldCBStringExact` by se měl podobat.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="ddx_fieldcheck"></a>  Ddx_fieldcheck –

`DDX_FieldCheck` Funkce spravuje přenos **int** data mezi ovládací prvek zaškrtávací políčko v dialogovém okně, formuláře, zobrazení, nebo objekt zobrazení ovládacího prvku a **int** datový člen dialogové okno, zobrazení formuláře nebo ovládacího prvku objekt zobrazení.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID prostředku ovládací prvek zaškrtávací políčko, které jsou přidružené k vlastnosti ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_FieldCheck` se nazývá *hodnotu* je nastavena na aktuální stav ovládací prvek zaškrtávací políčko nebo stav ovládacího prvku nastavená na *hodnota*, v závislosti na směru přenosu.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex

`DDX_FieldLBIndex` Funkce synchronizuje index vybrané položky v ovládacím prvku seznamu pole v zobrazení záznamu a **int** pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*index*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví výběr v ovládacím prvku v závislosti na hodnotě zadané v *index*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, MFC nastaví hodnotu indexu na 0. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu 0.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString

`DDX_FieldLBString` Zkopíruje v zobrazení záznamu do aktuálního výběru ovládacího prvku seznam [CString](../../atl-mfc-shared/reference/cstringt-class.md) pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

V opačném směru, tato funkce nastaví aktuální výběr v seznamu na první řádek, který začíná znaky v řetězci určené *hodnota*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, nic odebrán ze seznamu. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldLBString` by se měl podobat.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact

`DDX_FieldLBStringExact` Funkce zkopíruje aktuální výběr ovládacího prvku seznam v zobrazení záznamu k [CString](../../atl-mfc-shared/reference/cstringt-class.md) pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

V opačném směru, tato funkce nastaví aktuální výběr v seznamu na první řádek, který přesně odpovídá řetězci zadanému v *hodnota*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, nic odebrán ze seznamu. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldLBStringExact` by se měl podobat.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio

`DDX_FieldRadio` Funkce přidruží nulovým základem **int** členskou proměnnou záznamů zobrazení záznamu s aktuálně vybraného přepínače ve skupině přepínacích tlačítek v zobrazení záznamů.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID prvního ve skupině (stylem WS_GROUP) vedle ovládacích prvků přepínačů v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přenosu ze záznamů pole k zobrazení, tato funkce Zapne *n-tý* přepínací tlačítko (počítáno od nuly) a vypne další tlačítka. V opačném směru tato funkce nastaví pole záznamů řadová číslovka přepínač, který je aktuálně v (čtverečkovaný). Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, se neobjeví tlačítko zaškrtnuto. Na přenos z ovládacího prvku do sady záznamů, pokud je vybraný žádný ovládací prvek, záznamů pole je nastaveno na hodnotu Null pokud pole, která povoluje.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldRadio` by se měl podobat.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

`DDX_FieldScroll` Funkce synchronizuje pozici posunutí ovládací prvek posuvníku v zobrazení záznamu a **int** pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu (nebo libovolné celočíselná proměnná rozhodnete ji namapovat na) .

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID prvního ve skupině (stylem WS_GROUP) vedle ovládacích prvků přepínačů v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku, tato funkce nastaví na hodnotu zadanou v pozici posunutí ovládací prvek posuvníku *hodnota*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, je ovládací prvek posuvníku. nastavte na hodnotu 0. Na přenos z ovládacího prvku do sady záznamů Pokud ovládací prvek je prázdný, hodnota pole sady záznamů je 0.

Používejte první verze, pokud pracujete s třídy založené na rozhraní ODBC. Pokud pracujete s třídy založené na rozhraní DAO, použijte druhou verzi.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldScroll` by se měl podobat.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

  ## <a name="ddx_fieldslider"></a>  Ddx_fieldslider –
`DDX_FieldSlider` Funkce synchronizuje thumb pozice posuvníku v zobrazení záznamu a **int** pole datový člen třídy sadu záznamů spojenou se zobrazením záznamu (nebo libovolné celočíselná proměnná rozhodnete ji namapovat na).

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

*pDX*<br/>
Ukazatel [CDataExchange](cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID prostředku v ovládacím prvku posuvník.

*value*<br/>
Odkaz na hodnotu, která bude vyměněn. Tento parametr obsahuje nebo bude používat nastavení aktuální pozici thumb ovládacího prvku posuvník.

*pRecordset*<br/>
Ukazatel na přidruženou `CRecordset` nebo `CDaoRecordset` objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů posuvníku, tato funkce nastaví na hodnotu zadanou v pozice posuvníku *hodnota*. Na přenos ze sady záznamů do ovládacího prvku Pokud sada záznamů pole má hodnotu Null, umístění v ovládacím prvku posuvník nastaven na hodnotu 0. Na přenos z ovládacího prvku do sady záznamů Pokud ovládací prvek je prázdný, hodnota pole sady záznamů je 0.

`DDX_FieldSlider` není vyměňovat informace rozsahu pomocí ovládacích prvků posuvník dokáže nastavit rozsah než jednoduše pozici.

První přepsat funkci použijte, pokud pracujete s třídy založené na rozhraní ODBC. Druhý přepsat pomocí třídy založené na rozhraní DAO.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro `CRecordView` a `CDaoRecordView` pole, naleznete v tématu [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Informace o ovládacích prvcích posuvníku, naleznete v tématu [používání atributu CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Příklad

Zobrazit [DDX_FieldText](#ddx_fieldtext) obecné DDX_Field – příklad. Volání `DDX_FieldSlider` by se měl podobat.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="ddx_fieldtext"></a>  DDX_FieldText

`DDX_FieldText` Funkce spravuje přenos **int**, **krátký**, **dlouhé**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**, nebo **BAJTŮ** data mezi ovládací prvek úprav a datové členy polí sady záznamů.

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

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku v [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objektu.

*value*<br/>
Odkaz na pole datového člena v přidruženém `CRecordset` nebo `CDaoRecordset` objektu. Datový typ hodnoty, závisí na kterém přetížené verze `DDX_FieldText` použijete.

*pRecordset*<br/>
Ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objektu, pomocí kterého se vyměňují data. This – ukazatel umožňuje `DDX_FieldText` ke zjišťování a nastavte hodnoty Null.

### <a name="remarks"></a>Poznámky

Pro [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objekty, `DDX_FieldText` také spravuje přenos [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), a [COleCurrency](../../mfc/reference/colecurrency-class.md) hodnoty. Ovládací prvek úprav prázdný označuje hodnotu Null. Na přenos ze sady záznamů do ovládacího prvku, pokud sada záznamů pole má hodnotu Null, pole pro úpravy je nastavena na prázdnou. Na přenos z ovládacího prvku do sady záznamů, pokud ovládací prvek je prázdný, sada záznamů pole je nastaveno na hodnotu Null.

Použití verze s [CRecordset](../../mfc/reference/crecordset-class.md) parametry při práci s třídy založené na rozhraní ODBC. Použití verze s [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) parametry při práci s tříd založených na DAO.

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o rozhraní DDX pro [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) pole, najdete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Následující `DoDataExchange` fungovat [CRecordView](../../mfc/reference/crecordview-class.md) obsahuje `DDX_FieldText` funkce se volá pro tři datové typy: `IDC_COURSELIST` je pole se seznamem; další dva ovládací prvky jsou textových polí. Pro programování v rozhraní DAO, *m_pSet* parametru je ukazatel [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](mfc-macros-and-globals.md)
