---
title: Stránky vlastností (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 6456a192a502a0fcc032eaefc667c90ecec86d42
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751136"
---
# <a name="property-pages-mfc"></a>Stránky vlastností (MFC)

Stránky vlastností zobrazují aktuální hodnoty specifických vlastností ovládacího prvku OLE v přizpůsobitelném grafickém rozhraní pro zobrazení a úpravy podporou mechanismu mapování dat založeného na výměně dat dialogu (DDX).

Tento mechanismus mapování dat mapuje ovládací prvky stránky vlastností na jednotlivé vlastnosti ovládacího prvku OLE. Hodnota vlastnosti ovládacího prvku odráží stav nebo obsah ovládacího prvku stránky vlastnosti. Mapování mezi ovládacími prvky stránky **DDP_** vlastností a vlastnostmi `DoDataExchange` je určeno DDP_ volání funkce v členské funkci stránky vlastností. Následuje seznam **DDP_** funkcí, které si vyměňují data zadaná pomocí stránky vlastností ovládacího prvku:

### <a name="property-page-data-transfer"></a>Přenos dat stránky vlastností

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Propojí index vybraného řetězce v poli se seznamem s vlastností ovládacího prvku.|
|[DDP_CBString](#ddp_cbstring)|Propojí vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec může začínat stejnými písmeny jako hodnota vlastnosti, ale nemusí se plně shodovat.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Propojí vybraný řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec a hodnota řetězce vlastnosti se musí přesně shodovat.|
|[DDP_Check](#ddp_check)|Propojí zaškrtávací políčko na stránce vlastností ovládacího prvku s vlastností ovládacího prvku.|
|[DDP_LBIndex](#ddp_lbindex)|Propojí index vybraného řetězce v seznamu s vlastností ovládacího prvku.|
|[DDP_LBString](#ddp_lbstring)|Propojí vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec může začínat stejnými písmeny jako hodnota vlastnosti, ale nemusí se plně shodovat.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Propojí vybraný řetězec v seznamu s vlastností ovládacího prvku. Vybraný řetězec a hodnota řetězce vlastnosti se musí přesně shodovat.|
|[DDP_PostProcessing](#ddp_postprocessing)|Dokončí přenos hodnot vlastností z ovládacího prvku.|
|[DDP_Radio](#ddp_radio)|Propojí skupinu přepínacích tlačítek na stránce vlastností ovládacího prvku s vlastností ovládacího prvku.|
|[DDP_Text](#ddp_text)|Propojí ovládací prvek na stránce vlastností ovládacího prvku s vlastností ovládacího prvku. Tato funkce zpracovává několik různých typů vlastností, například **double**, **short**, BSTR a **long**.|

Další informace o `DoDataExchange` stránkách funkcí a vlastností naleznete v článku [Ovládací prvky ActiveX: Stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

Následuje seznam maker použitých k vytvoření a správě stránek vlastností ovládacího prvku OLE:

### <a name="property-pages"></a>Stránky vlastností

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Začíná se seznam ID stránky vlastností.|
|[END_PROPPAGEIDS](#end_proppageids)|Ukončí seznam ID stránky vlastností.|
|[PROPPAGEID](#proppageid)|Deklaruje stránku vlastností třídy ovládacího prvku.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Volání této funkce ve `DoDataExchange` funkci stránky vlastností k synchronizaci hodnoty vlastnosti celé číslo s indexem aktuálního výběru v poli se seznamem na stránce vlastností.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna s ovládacím prvkem pole se seznamem určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_CBIndex` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Volání této funkce ve `DoDataExchange` funkci stránky vlastností k synchronizaci hodnoty vlastnosti řetězce s aktuálním výběrem v poli se seznamem na stránce vlastností.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna s řetězcem pole se seznamem určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_CBString` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Volání této funkce ve `DoDataExchange` funkci stránky vlastností k synchronizaci hodnoty vlastnosti řetězce, která přesně odpovídá aktuálnímu výběru v poli se seznamem na stránce vlastností.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna s řetězcem pole se seznamem určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_CBStringExact` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Volání této funkce ve `DoDataExchange` funkci stránky vlastností k synchronizaci hodnoty vlastnosti s přidruženým ovládacím prvkem stránky vlastností.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku zaškrtávacího políčka přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna s ovládacím prvkem zaškrtávacího políčka určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_Check` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Volání této funkce ve `DoDataExchange` funkci stránky vlastností k synchronizaci hodnoty vlastnosti celé číslo s indexem aktuálního výběru v seznamu na stránce vlastností.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna se řetězcem seznamu určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_LBIndex` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Volánítéto funkce ve `DoDataExchange` funkci stránky vlastností pro synchronizaci hodnoty vlastnosti řetězce s aktuálním výběrem v seznamu na stránce vlastností.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna se řetězcem seznamu určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_LBString` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Volání této funkce ve `DoDataExchange` funkci stránky vlastností k synchronizaci hodnoty vlastnosti řetězce, která přesně odpovídá aktuálnímu výběru v seznamu na stránce vlastností.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna se řetězcem seznamu určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_LBStringExact` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Volání této funkce ve `DoDataExchange` funkci stránky vlastností, dokončit převod hodnot vlastností ze stránky vlastností do ovládacího prvku při ukládání hodnot vlastností.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

### <a name="remarks"></a>Poznámky

Tato funkce by měla být volána po dokončení všech funkcí výměny dat. Příklad:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Volání této funkce ve `DoPropExchange` funkci ovládacího prvku pro synchronizaci hodnoty vlastnosti s ovládacím prvkem přidružené stránky stránky přepínacího tlačítka.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku přepínacího tlačítka přidruženého k vlastnosti ovládacího prvku určené *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna s ovládacím prvkem přepínacího tlačítka určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_Radio` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Volání této funkce ve `DoDataExchange` funkci ovládacího prvku synchronizovat hodnotu vlastnosti s přidruženým ovládacím prvkem stránky vlastností.

```cpp
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

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Id*<br/>
ID prostředku ovládacího prvku přidruženého k vlastnosti ovládacího prvku zadané *pszPropName*.

*Členské*<br/>
Členská proměnná přidružená k ovládacímu prvku stránky vlastností určenému *id* a vlastností určenou *pszPropName*.

*pszPropName*<br/>
Název vlastnosti control, která má být vyměněna s ovládacím prvkem určeným *id*.

### <a name="remarks"></a>Poznámky

Tato funkce by měla `DDX_Text` být volána před voláním odpovídající funkce.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Začíná definice seznamu id stránky vlastností ovládacího prvku.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku, pro kterou jsou určeny stránky vlastností.

*Počet*<br/>
Počet stránek vlastností používaných třídou ovládacího prvku.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce pro vaši třídu, spusťte seznam stránek vlastností pomocí BEGIN_PROPPAGEIDS makra, přidejte položky maker pro každou stránku vlastností a dokončete seznam stránek vlastností END_PROPPAGEIDS makra.

Další informace o stránkách vlastností naleznete v článku [Ovládací prvky ActiveX: Stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Ukončí definici seznamu ID stránky vlastností.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku, která vlastní stránku vlastností.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID

Přidá stránku vlastností pro použití ovládacím prvkem OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
Jedinečné ID třídy stránky vlastností.

### <a name="remarks"></a>Poznámky

Všechna makra PROPPAGEID musí být umístěna mezi BEGIN_PROPPAGEIDS a END_PROPPAGEIDS makra v implementačním souboru ovládacího prvku.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxctl.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
