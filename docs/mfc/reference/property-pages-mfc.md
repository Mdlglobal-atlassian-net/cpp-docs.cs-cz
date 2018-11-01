---
title: Stránky vlastností (MFC)
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 4f8e56ed4be6bf4c7a5283894493ee46c4ed2ff4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620906"
---
# <a name="property-pages-mfc"></a>Stránky vlastností (MFC)

Stránky vlastností zobrazí aktuální hodnoty konkrétní vlastnosti ovládacích prvků OLE v přizpůsobitelné grafické rozhraní pro prohlížení a úpravy díky podpoře mechanismu mapování dat podle výměna dat dialogových oken (DDX).

Tento mechanismus mapování dat mapuje ovládací prvky stránky vlastností pro jednotlivé vlastnosti ovládacího prvku OLE. Hodnota vlastnosti ovládacího prvku odráží stav nebo obsah ovládacího prvku vlastnosti stránky. Mapování mezi ovládací prvky stránky vlastností a vlastností je určená **ddp_ –** funkce se volá na stránce vlastností `DoDataExchange` členskou funkci. Tady je seznam **ddp_ –** funkce, které výměnu dat zadané na stránce vlastností ovládacího prvku:

### <a name="property-page-data-transfer"></a>Přenos dat stránky vlastností

|||
|-|-|
|[Ddp_cbindex –](#ddp_cbindex)|Propojí vybrané řetězcového indexu pole se seznamem s vlastností ovládacího prvku.|
|[Ddp_cbstring –](#ddp_cbstring)|Propojí vybrané řetězec v poli se seznamem s vlastností ovládacího prvku. Vybrané řetězce mohou začínat stejná písmena jako hodnotu vlastnosti, ale nemusí odpovídat plně.|
|[Ddp_cbstringexact –](#ddp_cbstringexact)|Propojí vybrané řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|
|[Ddp_check –](#ddp_check)|Obsahuje odkazy na stránce vlastností ovládacího prvku s vlastností ovládacího prvku zaškrtávací políčko.|
|[Ddp_lbindex –](#ddp_lbindex)|Propojí vybrané řetězcového indexu v seznamu pomocí ovládacího prvku.|
|[Ddp_lbstring –](#ddp_lbstring)|Propojí vybrané řetězec v seznamu pomocí ovládacího prvku. Vybrané řetězce mohou začínat stejná písmena jako hodnotu vlastnosti, ale nemusejí odpovídat plně.|
|[Ddp_lbstringexact –](#ddp_lbstringexact)|Propojí vybrané řetězec v seznamu pomocí ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|
|[Ddp_postprocessing –](#ddp_postprocessing)|Dokončení převodu hodnoty vlastnosti z ovládacího prvku.|
|[Ddp_radio –](#ddp_radio)|Odkazy skupině přepínacích tlačítek na stránce vlastností ovládacího prvku s vlastností ovládacího prvku.|
|[Ddp_text –](#ddp_text)|Obsahuje odkazy ovládací prvek na stránce vlastností ovládacího prvku s vlastností ovládacího prvku. Tato funkce zpracovává několik různých typů vlastností, jako například **double**, **krátký**, BSTR, a **dlouhé**.|

Další informace o `DoDataExchange` funkce a vlastnosti stránky, najdete v článku [ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

Následuje seznam makra použitá k vytvoření a správě stránek vlastností pro ovládací prvek OLE:

### <a name="property-pages"></a>Stránky vlastností

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Začne seznam ID stránek vlastností.|
|[END_PROPPAGEIDS](#end_proppageids)|Konec seznamu ID stránek vlastností.|
|[PROPPAGEID](#proppageid)|Deklaruje stránky vlastností třídy ovládacího prvku.|

##  <a name="ddp_cbindex"></a>  Ddp_cbindex –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce pro synchronizaci se index aktuálního výběru v poli se seznamem na stránce vlastností hodnota celočíselnou vlastnost.

```
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku se seznamem pole ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za prvek pole se seznamem určené *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_CBIndex` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_cbstring"></a>  Ddp_cbstring –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce synchronizace hodnotu vlastnosti řetězce pomocí aktuálního výběru v poli se seznamem na stránce vlastností.

```
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku se seznamem pole ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za řetězec pole se seznamem určený *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_CBString` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_cbstringexact"></a>  Ddp_cbstringexact –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce synchronizace se změní hodnota vlastnosti řetězce, který přesně odpovídá aktuální výběr v poli se seznamem na stránce vlastností.

```
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku se seznamem pole ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za řetězec pole se seznamem určený *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_CBStringExact` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_check"></a>  Ddp_check –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce pro synchronizaci hodnoty vlastnosti se ovládací prvek zaškrtávací políčko přidružené vlastnosti stránky.

```
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku v ovládacím prvku zaškrtávací políčko přidružené vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za ovládací prvek zaškrtávací políčko určené *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_Check` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_lbindex"></a>  Ddp_lbindex –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce pro synchronizaci se index aktuálně vybrané položky v seznamu na stránce vlastností hodnota celočíselnou vlastnost.

```
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku v seznamu pole ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za seznam pole řetězec určený *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_LBIndex` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_lbstring"></a>  Ddp_lbstring –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce synchronizace hodnotu vlastnosti řetězce pomocí aktuálního výběru v rozevíracím seznamu na stránce vlastností.

```
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku v seznamu pole ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za seznam pole řetězec určený *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_LBString` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_lbstringexact"></a>  Ddp_lbstringexact –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce synchronizace se změní hodnota vlastnosti řetězce, který přesně odpovídá aktuální výběr v seznamu na stránce vlastností.

```
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku v seznamu pole ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za seznam pole řetězec určený *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_LBStringExact` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_postprocessing"></a>  Ddp_postprocessing –

Voláním této funkce na stránce vlastností `DoDataExchange` funkce, dokončete převod hodnoty vlastností na stránce vlastností do ovládacího prvku při uložení hodnoty vlastnosti.

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

### <a name="remarks"></a>Poznámky

Tuto funkci lze volat po dokončení všechny funkce výměny dat. Příklad:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_radio"></a>  Ddp_radio –

Voláním této funkce ve vašem ovládacím prvku `DoPropExchange` funkce pro synchronizaci hodnoty vlastnosti se přidružené vlastnosti stránky ovládací prvek přepínač.

```
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku přepínače tlačítko ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za ovládacího prvku tlačítko přepínače určené *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_Radio` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="ddp_text"></a>  Ddp_text –

Voláním této funkce ve vašem ovládacím prvku `DoDataExchange` funkce synchronizace hodnoty vlastnosti pomocí ovládacího prvku přidružené vlastnosti stránky.

```
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*id*<br/>
ID prostředku ovládacího prvku přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Člen*<br/>
Členské proměnné přidružené k ovládacímu prvku stránka vlastnosti určené *id* a vlastnost určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti ovládacího prvku, který bude vyměněn za ovládací prvek určený *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána před odpovídajícími `DDX_Text` volání funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS

Začíná definice ovládacího prvku seznam ID stránek vlastností.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku pro vlastnosti, které jsou určené stránky.

*Počet*<br/>
Číslo stránky vlastností, které používá třída ovládacího prvku.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce třídy seznam vlastností stránky začínat BEGIN_PROPPAGEIDS – makro pak přidat makro položky pro každý z vašich stránky vlastností a dokončení seznamu vlastností stránky pomocí END_PROPPAGEIDS makra.

Další informace na stránkách vlastností, najdete v článku [ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="end_proppageids"></a>  END_PROPPAGEIDS

Ukončí definici seznamu ID stránky vlastností.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku, který vlastní stránky vlastností.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

##  <a name="proppageid"></a>  PROPPAGEID

Přidá stránky vlastností pro použití ovládacího prvku OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parametry

*identifikátor CLSID*<br/>
ID jedinečné třídy stránky vlastností.

### <a name="remarks"></a>Poznámky

Všechna makra PROPPAGEID musí být umístěn mezi BEGIN_PROPPAGEIDS a END_PROPPAGEIDS makra v souboru implementace ovládacího prvku.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxctl.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
