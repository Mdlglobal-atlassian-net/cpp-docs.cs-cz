---
title: Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView
ms.date: 09/17/2019
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
ms.openlocfilehash: 8b216941837cd79492aa6cb707481073b5321bce
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421357"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView

Toto téma obsahuje seznam funkcí DDX_Field používaných k výměně dat mezi formulářem [CRecordset](../../mfc/reference/crecordset-class.md) [a](../../mfc/reference/cdaorecordview-class.md) formulářem v tabulce [CRecordView](../../mfc/reference/crecordview-class.md) [nebo z formuláře](../../mfc/reference/cdaorecordset-class.md) . Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

> [!NOTE]
>  DDX_Field funkce jsou jako funkce DDX v tom, že vyměňují data s ovládacími prvky ve formuláři. Ale na rozdíl od DDX, vyměňují data s poli přidruženého objektu sady záznamů zobrazení a nikoli s poli samotného zobrazení záznamu. Další informace naleznete v tématu třídy `CRecordView` a `CDaoRecordView`.

### <a name="ddx_field-functions"></a>Funkce DDX_Field

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Převádí celočíselná data mezi datovým členem pole sady záznamů a indexem aktuálního výběru v poli se seznamem v oblasti [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Přenáší `CString` data mezi datovým členem pole sady záznamů a ovládacím prvkem pro úpravy pole se seznamem v `CRecordView` nebo `CDaoRecordView`. Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce vybere položku v poli se seznamem, která začíná znaky v zadaném řetězci.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Přenáší `CString` data mezi datovým členem pole sady záznamů a ovládacím prvkem pro úpravy pole se seznamem v `CRecordView` nebo `CDaoRecordView`. Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce vybere položku v poli se seznamem, která přesně odpovídá zadanému řetězci.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Přenáší logická data mezi datovým členem pole sady záznamů a zaškrtávacím políčkem v `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Přenáší celočíselná data mezi datovým členem pole sady záznamů a indexem aktuálního výběru v seznamu v `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Spravuje přenos dat [CString](../../atl-mfc-shared/reference/cstringt-class.md) mezi ovládací prvek seznamu a datovými členy pole sady záznamů. Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce vybere položku v seznamu, která začíná znaky v zadaném řetězci.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Spravuje přenos dat `CString` mezi ovládacím prvkem seznamu a datovými členy pole sady záznamů. Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce vybere první položku, která přesně odpovídá zadanému řetězci.|
|[DDX_FieldRadio](#ddx_fieldradio)|Přenáší celočíselná data mezi datovým členem pole sady záznamů a skupinou přepínačů v `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Nastaví nebo získá pozici posunutí ovládacího prvku posuvníku v `CRecordView` nebo `CDaoRecordView`. Zavolejte funkci [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) .|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronizuje polohu jezdce ovládacího prvku posuvník v zobrazení záznamu a datového členu `int` pole sady záznamů. |
|[DDX_FieldText](#ddx_fieldtext)|Přetížené verze jsou k dispozici pro přenos `int`, **uint**, **Long**, `DWORD`[, CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **Double**, **short**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)a [COleCurrency](../../mfc/reference/colecurrency-class.md) dat mezi polem sady záznamů a polem pro úpravy v `CRecordView` nebo `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

Funkce `DDX_FieldCBIndex` synchronizuje index vybrané položky v ovládacím prvku seznamu ovládacího prvku pole se seznamem v zobrazení záznamu a datového členu `int` pole sady záznamů, která je přidružena k zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*indexovacím*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce nastaví výběr v ovládacím prvku na základě hodnoty zadané v *indexu*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, sada MFC nastaví hodnotu indexu na 0. Pokud je ovládací prvek v přenosu od ovládacího prvku do sady záznamů prázdný nebo pokud není vybrána žádná položka, je pole sada záznamů nastaveno na hodnotu 0.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Příklad by byl podobný `DDX_FieldCBIndex`.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="ddx_fieldcbstring"></a>DDX_FieldCBString

Funkce `DDX_FieldCBString` spravuje přenos dat [CString](../../atl-mfc-shared/reference/cstringt-class.md) mezi ovládacím prvkem pro úpravy ovládacího prvku pole se seznamem v zobrazení záznamu a datovým členem `CString` pole sady záznamů, která je přidružena k zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který začíná znaky v řetězci zadaném v poli *hodnota*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, je z pole se seznamem odstraněn libovolný výběr a ovládací prvek pro úpravy pole se seznamem je nastaven na hodnotu Empty. Pokud je ovládací prvek v rámci převodu na sadu záznamů prázdný, je pole sada záznamů nastaveno na hodnotu null, pokud to pole povoluje.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Příklad obsahuje volání `DDX_FieldCBString`.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

## <a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

Funkce `DDX_FieldCBStringExact` spravuje přenos dat [CString](../../atl-mfc-shared/reference/cstringt-class.md) mezi ovládacím prvkem pro úpravy ovládacího prvku pole se seznamem v zobrazení záznamu a datovým členem `CString` pole sady záznamů, která je přidružena k zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který přesně odpovídá řetězci zadanému v poli *hodnota*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu NULL, je z pole se seznamem odstraněn libovolný výběr a pole pro úpravy pole se seznamem je nastaveno na hodnotu prázdné. V případě, že je ovládací prvek prázdný, je pole sada záznamů nastaveno na hodnotu NULL a na přenos z ovládacího prvku do sady záznamů.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Volání `DDX_FieldCBStringExact` by byla podobná.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="ddx_fieldcheck"></a>DDX_FieldCheck

Funkce `DDX_FieldCheck` spravuje přenos dat typu **int** mezi ovládacím prvkem zaškrtávací políčko v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku zaškrtávací políčko přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když je volána `DDX_FieldCheck`, *hodnota* je nastavena na aktuální stav ovládacího prvku zaškrtávací políčko nebo je stav ovládacího prvku nastaven na *hodnotu*v závislosti na směru přenosu.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

Funkce `DDX_FieldLBIndex` synchronizuje index vybrané položky v ovládacím prvku seznamu v zobrazení záznamu a datovém členovi pole **int** objektu Recordset přidruženého k zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*indexovacím*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce nastaví výběr v ovládacím prvku na základě hodnoty zadané v *indexu*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, sada MFC nastaví hodnotu indexu na 0. V případě, že je ovládací prvek prázdný, je pole sada záznamů nastaveno na hodnotu 0 na přenos od ovládacího prvku do sady záznamů.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) .

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="ddx_fieldlbstring"></a>DDX_FieldLBString

`DDX_FieldLBString` zkopíruje aktuální výběr ovládacího prvku seznamu v zobrazení záznamu do datového členu pole [CString](../../atl-mfc-shared/reference/cstringt-class.md) sady záznamů přidruženého k zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

V opačném směru Tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který začíná znaky v řetězci zadaném *hodnotou*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, je libovolný výběr odebrán ze seznamu. V případě, že je ovládací prvek prázdný, je pole sada záznamů nastaveno na hodnotu null a na přenos z ovládacího prvku do sady záznamů.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Volání `DDX_FieldLBString` by byla podobná.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

Funkce `DDX_FieldLBStringExact` zkopíruje aktuální výběr ovládacího prvku seznamu v zobrazení záznamu do datového členu pole [CString](../../atl-mfc-shared/reference/cstringt-class.md) v sadě záznamů, která je přidružena k zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

V opačném směru Tato funkce nastaví aktuální výběr v seznamu na první řádek, který přesně odpovídá řetězci zadanému v poli *hodnota*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, je libovolný výběr odebrán ze seznamu. V případě, že je ovládací prvek prázdný, je pole sada záznamů nastaveno na hodnotu null a na přenos z ovládacího prvku do sady záznamů.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Volání `DDX_FieldLBStringExact` by byla podobná.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="ddx_fieldradio"></a>DDX_FieldRadio

Funkce `DDX_FieldRadio` přidružuje členskou proměnnou **int** na základě nuly v zobrazení záznamu sady záznamů s aktuálně vybraným přepínačem ve skupině přepínačů v zobrazení záznamu.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prvního ve skupině (se stylem WS_GROUP) sousedících ovládacích prvků přepínačů v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při převodu z pole Recordset do zobrazení Tato funkce zapne přepínač *n-tý* (založený na nule) a vypne ostatní tlačítka. V opačném směru Tato funkce nastaví pole sady záznamů na pořadové číslo přepínacího tlačítka, které je aktuálně zapnuto (zaškrtnuto). Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, není vybráno žádné tlačítko. Při přenosu z ovládacího prvku do sady záznamů, pokud není vybrán žádný ovládací prvek, je pole sada záznamů nastaveno na hodnotu null, pokud to toto pole povoluje.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Volání `DDX_FieldRadio` by byla podobná.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="ddx_fieldscroll"></a>DDX_FieldScroll

Funkce `DDX_FieldScroll` synchronizuje pozici posunutí ovládacího prvku posuvníku v zobrazení záznamu a datovém členovi pole **int** objektu Recordset přidruženého k zobrazení záznamu (nebo pomocí libovolné celočíselné proměnné, ke které jste se rozhodli namapovat).

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prvního ve skupině (se stylem WS_GROUP) sousedících ovládacích prvků přepínačů v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) .

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při přesunu dat ze sady záznamů do ovládacího prvku Tato funkce nastaví pozici posunutí ovládacího prvku posuvníku na hodnotu zadanou v poli *hodnota*. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, je ovládací prvek posuvníku nastaven na hodnotu 0. Pokud je ovládací prvek prázdný, je při přenosu z ovládacího prvku do sady záznamů hodnota pole sada záznamů 0.

Pokud pracujete se třídami založenými na rozhraní ODBC, použijte první verzi. Pokud pracujete s třídami založenými na rozhraní DAO, použijte druhou verzi.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Volání `DDX_FieldScroll` by byla podobná.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

  ## <a name="ddx_fieldslider"></a>DDX_FieldSlider
Funkce `DDX_FieldSlider` synchronizuje polohu jezdce ovládacího prvku posuvníku v zobrazení záznamu a datový člen pole **int** objektu Recordset přidruženého k zobrazení záznamu (nebo s libovolnou celočíselnou proměnnou, na kterou jste se rozhodli namapovat).

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
Ukazatel na objekt [CDataExchange –](cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvník

*value*<br/>
Odkaz na hodnotu, která má být vyměněna. Tento parametr má nebo bude použit k nastavení aktuálního umístění souřadnic ovládacího prvku posuvník.

*pRecordset*<br/>
Ukazatel na přidružený objekt `CRecordset` nebo `CDaoRecordset`, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při přesunu dat ze sady záznamů do posuvníku Tato funkce nastaví pozici posuvníku na hodnotu zadanou v poli *hodnota*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů null, pozice ovládacího prvku posuvník je nastavena na hodnotu 0. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, hodnota pole Recordset je 0.

`DDX_FieldSlider` neměňuje informace o rozsahu s ovládacími prvky posuvníku, které umožňují nastavit rozsah místo pouhého umístění.

Pokud pracujete s třídami založenými na rozhraní ODBC, použijte první přepsání funkce. Použijte druhé přepsání s třídami založenými na rozhraní DAO.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro `CRecordView` a `CDaoRecordView` pole naleznete v tématu [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Informace o ovládacích prvcích posuvníku naleznete v tématu [using atributu CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Příklad

Obecné DDX_Field příklad najdete v tématu [DDX_FieldText](#ddx_fieldtext) . Volání `DDX_FieldSlider` by byla podobná.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="ddx_fieldtext"></a>DDX_FieldText

Funkce `DDX_FieldText` spravuje přenos **int**, **krátká**, **dlouhá**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **Double**, **bool**nebo **Byte** dat mezi ovládacím prvkem pole pro úpravy a datovými členy pole sady záznamů.

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
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)

*value*<br/>
Odkaz na datový člen pole v objektu přidruženého `CRecordset` nebo `CDaoRecordset`. Datový typ hodnota závisí na tom, které z přetížených verzí `DDX_FieldText` používáte.

*pRecordset*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) , se kterým se data vyměňují. Tento ukazatel umožňuje `DDX_FieldText` detekovat a nastavovat hodnoty null.

### <a name="remarks"></a>Poznámky

Pro objekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) `DDX_FieldText` také spravuje přenos hodnot [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)a [COleCurrency](../../mfc/reference/colecurrency-class.md) . Prázdný ovládací prvek textové pole indikuje hodnotu null. Při přenosu ze sady záznamů do ovládacího prvku, pokud má pole sady záznamů hodnotu null, je pole pro úpravy nastaveno na hodnotu prázdné. V případě, že je ovládací prvek prázdný, je pole sada záznamů nastaveno na hodnotu null a na přenos z ovládacího prvku do sady záznamů.

Použijte verze s parametry [CRecordset](../../mfc/reference/crecordset-class.md) , pokud pracujete se třídami založenými na rozhraní ODBC. Pokud pracujete s třídami založenými na rozhraní DAO, použijte verze s parametry [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Následující funkce `DoDataExchange` pro funkci [CRecordView](../../mfc/reference/crecordview-class.md) obsahuje `DDX_FieldText` volání funkcí pro tři datové typy: `IDC_COURSELIST` je pole se seznamem; Další dva ovládací prvky jsou pole pro úpravy. Pro programování DAO je parametr *m_pSet* ukazatel na [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)
