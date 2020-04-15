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
ms.openlocfilehash: 3128b1ba459cb017d1cdb2321bc55d865aa4f8b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365780"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Funkce výměny dat dialogových oken pro třídy CRecordView a CDaoRecordView

Toto téma obsahuje seznam DDX_Field funkcí používaných k výměně dat mezi formulářem [CRecordset](../../mfc/reference/crecordset-class.md) a [CRecordView](../../mfc/reference/crecordview-class.md) nebo [cdaorecordset](../../mfc/reference/cdaorecordset-class.md) a [formulářem CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) DAO se používá s databázemi Accessu a je podporován prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé.

> [!NOTE]
> DDX_Field funkce jsou jako funkce DDX v tom, že si vyměňují data s ovládacími prvky ve formuláři. Na rozdíl od ddx usebe si však vyměňují data s poli přidruženého objektu sady záznamů zobrazení, nikoli s poli samotného zobrazení záznamu. Další informace naleznete `CRecordView` v `CDaoRecordView`tématu třídy a .

### <a name="ddx_field-functions"></a>DDX_Field funkce

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Přenáší celá data mezi datovým členem pole sady záznamů a indexem aktuálního výběru v poli se seznamem v [crecordview](../../mfc/reference/crecordview-class.md) nebo [cdaorecordview](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Přenáší `CString` data mezi datovým členem pole sady záznamů a ovládacím prvkem úprav pole se seznamem v a `CRecordView` nebo `CDaoRecordView`. Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce vybere položku v poli se seznamem, která začíná znaky v zadaném řetězci.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Přenáší `CString` data mezi datovým členem pole sady záznamů a ovládacím prvkem úprav pole se seznamem v a `CRecordView` nebo `CDaoRecordView`. Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce vybere položku v poli se seznamem, která přesně odpovídá zadanému řetězci.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Přenáší logická data mezi datovým členem pole sady `CRecordView` `CDaoRecordView`záznamů a zaškrtávacím políčkem v poli nebo .|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Přenáší celá data mezi datovým členem pole sady záznamů a indexem aktuálního výběru v seznamu v a `CRecordView` nebo `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Spravuje přenos dat [CString](../../atl-mfc-shared/reference/cstringt-class.md) mezi ovládacím prvkem seznamu a datovými členy pole sady záznamů. Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce vybere položku v seznamu, která začíná znaky v zadaném řetězci.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Spravuje přenos `CString` dat mezi ovládacím prvkem seznamu a datovými členy pole sady záznamů. Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce vybere první položku, která přesně odpovídá zadanému řetězci.|
|[DDX_FieldRadio](#ddx_fieldradio)|Přenáší celá data mezi datovým členem pole sady záznamů a `CRecordView` `CDaoRecordView`skupinou přepínacích tlačítek v a nebo .|
|[DDX_FieldScroll](#ddx_fieldscroll)|Nastaví nebo získá pozici posouvání ovládacího prvku posuvníku `CRecordView` v nebo `CDaoRecordView`. Volání z funkce [DoFieldExchange.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange)|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronizuje pozici palce ovládacího prvku jezdce v `int` zobrazení záznamu a datového člena pole sady záznamů. |
|[DDX_FieldText](#ddx_fieldtext)|Přetížené verze jsou k `int`dispozici pro přenos `DWORD`, **UINT**, **long**, , [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **short**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)a [COleCurrency](../../mfc/reference/colecurrency-class.md) data mezi datovým členem pole sady záznamů a editačním polem v `CRecordView` nebo `CDaoRecordView`.|

## <a name="ddx_fieldcbindex"></a><a name="ddx_fieldcbindex"></a>DDX_FieldCBIndex

Funkce `DDX_FieldCBIndex` synchronizuje index vybrané položky v ovládacím prvku pole se seznamem v `int` zobrazení záznamů a datového člena pole sady záznamů přidruženého k zobrazení záznamů.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Index*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce nastaví výběr v ovládacím prvku na základě hodnoty zadané v *indexu*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, knihovna MFC nastaví hodnotu indexu na hodnotu 0. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný nebo pokud není vybrána žádná položka, je pole sady záznamů nastaveno na hodnotu 0.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Příklad by byl `DDX_FieldCBIndex`podobný pro .

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="ddx_fieldcbstring"></a><a name="ddx_fieldcbstring"></a>DDX_FieldCBString

Funkce `DDX_FieldCBString` spravuje přenos dat [CString](../../atl-mfc-shared/reference/cstringt-class.md) mezi ovládacím prvkem úprav ovládacího prvku pole `CString` se seznamem v zobrazení záznamu a datovým členem pole sady záznamů přidružených k zobrazení záznamu.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který začíná znaky v řetězci zadaném v *hodnotě*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, bude z pole se seznamem odebrán libovolný výběr a ovládací prvek pro úpravy pole se seznamem je nastaven na prázdné. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je pole sady záznamů nastaveno na hodnotu Null, pokud toto pole umožňuje.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Příklad zahrnuje volání `DDX_FieldCBString`do .

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldcbstringexact"></a><a name="ddx_fieldcbstringexact"></a>DDX_FieldCBStringExact

Funkce `DDX_FieldCBStringExact` spravuje přenos dat [CString](../../atl-mfc-shared/reference/cstringt-class.md) mezi ovládacím prvkem úprav ovládacího prvku pole `CString` se seznamem v zobrazení záznamu a datovým členem pole sady záznamů přidružených k zobrazení záznamu.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce nastaví aktuální výběr v poli se seznamem na první řádek, který přesně odpovídá řetězci zadanému v *hodnotě*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů NULL, je libovolný výběr odebrán z pole se seznamem a textové pole pole se seznamem je nastaveno na prázdné. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je pole sady záznamů nastaveno na hodnotu NULL.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Volání `DDX_FieldCBStringExact` by bylo podobné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldcheck"></a><a name="ddx_fieldcheck"></a>DDX_FieldCheck

Funkce `DDX_FieldCheck` spravuje přenos **int** dat mezi ovládacím prvkem zaškrtávacího políčka v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku zaškrtávacího políčka přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_FieldCheck` volání je *hodnota* nastavena na aktuální stav ovládacího prvku zaškrtávacího políčka nebo je stav ovládacího prvku nastaven na *hodnotu*v závislosti na směru přenosu.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldlbindex"></a><a name="ddx_fieldlbindex"></a>DDX_FieldLBIndex

Funkce `DDX_FieldLBIndex` synchronizuje index vybrané položky v ovládacím prvku seznamu v zobrazení záznamu a datového člena **int** pole sady záznamů přidruženého k zobrazení záznamu.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Index*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce nastaví výběr v ovládacím prvku na základě hodnoty zadané v *indexu*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, knihovna MFC nastaví hodnotu indexu na hodnotu 0. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je pole sady záznamů nastaveno na hodnotu 0.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldlbstring"></a><a name="ddx_fieldlbstring"></a>DDX_FieldLBString

Zkopíruje `DDX_FieldLBString` aktuální výběr ovládacího prvku seznamu v zobrazení záznamu do datového člena pole [CString](../../atl-mfc-shared/reference/cstringt-class.md) sady záznamů přidružené k zobrazení záznamu.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

V opačném směru tato funkce nastaví aktuální výběr v seznamu na první řádek, který začíná znaky v řetězci určeném *hodnotou*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, bude ze seznamu odebrán libovolný výběr. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je pole sady záznamů nastaveno na hodnotu Null.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Volání `DDX_FieldLBString` by bylo podobné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldlbstringexact"></a><a name="ddx_fieldlbstringexact"></a>DDX_FieldLBStringExact

Funkce `DDX_FieldLBStringExact` zkopíruje aktuální výběr ovládacího prvku seznamu v zobrazení záznamu do datového člena pole [CString](../../atl-mfc-shared/reference/cstringt-class.md) sady záznamů přidružené k zobrazení záznamu.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

V opačném směru tato funkce nastaví aktuální výběr v seznamu na první řádek, který přesně odpovídá řetězci zadanému v *hodnotě*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, bude ze seznamu odebrán libovolný výběr. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je pole sady záznamů nastaveno na hodnotu Null.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Volání `DDX_FieldLBStringExact` by bylo podobné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldradio"></a><a name="ddx_fieldradio"></a>DDX_FieldRadio

Funkce `DDX_FieldRadio` přidruží nulovou **int** členskou proměnnou sady záznamů k aktuálně vybranému přepínacímu tlačítku ve skupině přepínacích tlačítek v zobrazení záznamu.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID první ve skupině (se stylem WS_GROUP) sousedních ovládacích prvků přepínacího tlačítka v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přenosu z pole sady záznamů do zobrazení tato funkce zapne *n-té* přepínací tlačítko (od nuly) a vypne ostatní tlačítka. V opačném směru tato funkce nastaví pole sady záznamů na pořadové číslo přepínače, které je aktuálně zapnuto (zaškrtnuto). Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, není vybráno žádné tlačítko. Při přenosu z ovládacího prvku do sady záznamů, pokud není vybrán žádný ovládací prvek, je pole sady záznamů nastaveno na hodnotu Null, pokud to pole umožňuje.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Volání `DDX_FieldRadio` by bylo podobné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldscroll"></a><a name="ddx_fieldscroll"></a>DDX_FieldScroll

Funkce `DDX_FieldScroll` synchronizuje polohu posouvání ovládacího prvku posuvníku v zobrazení záznamu a datového člena **int** pole sady záznamů přidruženého k zobrazení záznamu (nebo s jakoukoli buňkovou proměnnou, na kterou se rozhodnete mapovat).

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID první ve skupině (se stylem WS_GROUP) sousedních ovládacích prvků přepínacího tlačítka v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do ovládacího prvku tato funkce nastaví polohu posouvání ovládacího prvku posuvníku na hodnotu zadanou v *hodnotě*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, je ovládací prvek posuvníku nastaven na hodnotu 0. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je hodnota pole sady záznamů 0.

První verzi použijte, pokud pracujete s třídami založenými na rozhraní ODBC. Druhou verzi použijte, pokud pracujete s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Volání `DDX_FieldScroll` by bylo podobné.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="ddx_fieldslider"></a><a name="ddx_fieldslider"></a>DDX_FieldSlider

Funkce `DDX_FieldSlider` synchronizuje pozici palce ovládacího prvku jezdce v zobrazení záznamu a datového člena **int** pole sady záznamů přidruženého k zobrazení záznamu (nebo s jakoukoli buňkovou proměnnou, na kterou se rozhodnete mapovat).

### <a name="syntax"></a>Syntaxe

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvníku.

*Hodnotu*<br/>
Odkaz na hodnotu, která má být vyměněna. Tento parametr podrží nebo bude použit k nastavení aktuální polohy palce ovládacího prvku posuvníku.

*pSada záznamů*<br/>
Ukazatel na přidružený `CRecordset` `CDaoRecordset` nebo objekt, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při přesouvání dat ze sady záznamů do posuvníku tato funkce nastaví pozici jezdce na hodnotu zadanou v *hodnotě*. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, je pozice ovládacího prvku posuvníku nastavena na hodnotu 0. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je hodnota pole sady záznamů 0.

`DDX_FieldSlider`nevyměňuje informace o rozsahu pomocí posuvníku, které jsou schopny nastavit rozsah, nikoli pouze polohu.

Pokud pracujete s třídami založenými na rozhraní ODBC, použijte první přepsání funkce. Použijte druhé přepsání s třídami založenými na DAO.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../dialog-data-exchange-and-validation.md). Příklady a další informace o `CRecordView` ddx pro a `CDaoRecordView` pole, naleznete [v tématu Zobrazení záznamů](../../data/record-views-mfc-data-access.md). Informace o ovládacích prvcích jezdce naleznete [v tématu Použití kláves CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Příklad

Viz [DDX_FieldText](#ddx_fieldtext) obecný příklad DDX_Field. Volání `DDX_FieldSlider` by bylo podobné.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="ddx_fieldtext"></a><a name="ddx_fieldtext"></a>DDX_FieldText

Funkce `DDX_FieldText` spravuje přenos dat **int**, **short**, **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**nebo **BYTE** mezi ovládacím prvkem textového pole a datovými členy pole sady záznamů.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku v objektu [CRecordView](../../mfc/reference/crecordview-class.md) nebo [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md)

*Hodnotu*<br/>
Odkaz na datového člena pole `CRecordset` `CDaoRecordset` v přidruženém nebo objektu. Datový typ hodnoty závisí na tom, které `DDX_FieldText` z přetížených verzí používáte.

*pSada záznamů*<br/>
Ukazatel na objekt [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset,](../../mfc/reference/cdaorecordset-class.md) se kterým se vyměňují data. Tento ukazatel `DDX_FieldText` umožňuje rozpoznat a nastavit hodnoty Null.

### <a name="remarks"></a>Poznámky

Pro objekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) `DDX_FieldText` také spravuje přenos [cOleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)a [COleCurrency](../../mfc/reference/colecurrency-class.md) hodnoty. Prázdný ovládací prvek pole pro úpravy označuje hodnotu Null. Při přenosu ze sady záznamů do ovládacího prvku, pokud je pole sady záznamů Null, je textové pole nastaveno na prázdné. Při přenosu z ovládacího prvku do sady záznamů, pokud je ovládací prvek prázdný, je pole sady záznamů nastaveno na hodnotu Null.

Pokud pracujete s třídami založenými na rozhraní ODBC, použijte verze s parametry [CRecordset.](../../mfc/reference/crecordset-class.md) Pokud pracujete s třídami založenými na DAO, použijte verze s parametry [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Příklady a další informace o DDX pro pole [CRecordView](../../mfc/reference/crecordview-class.md) a [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) naleznete v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Příklad

Následující `DoDataExchange` funkce pro [CRecordView](../../mfc/reference/crecordview-class.md) obsahuje `DDX_FieldText` volání funkce `IDC_COURSELIST` pro tři datové typy: je pole se seznamem; další dva ovládací prvky jsou editační pole. Pro programování DAO je *parametrem m_pSet* ukazatel na [CRecordset](../../mfc/reference/crecordset-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)
