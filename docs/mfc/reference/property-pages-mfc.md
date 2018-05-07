---
title: Stránky vlastností (MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0895cd22870b3a4a266e9be12f0000fae7f7101a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="property-pages-mfc"></a>Stránky vlastností (MFC)
Stránky vlastností zobrazí aktuální hodnoty konkrétní vlastnosti ovládacích prvků OLE přizpůsobitelné, grafické rozhraní pro prohlížení a úpravy díky podpoře dat mapování mechanismus založený na výměna dialogových dat (DDX).  
  
 Tento mechanismus data mapování mapuje ovládací prvky stránky vlastností pro jednotlivé vlastnosti ovládacího prvku OLE. Hodnota vlastnosti ovládacího prvku odráží stav nebo obsah ovládacího prvku stránky vlastností. Je zadána mapování mezi ovládací prvky stránky vlastnosti a vlastnosti **ddp_ –** funkce volá na stránce vlastností `DoDataExchange` – členská funkce. Následuje seznam **ddp_ –** funkce, které vyměňovat data zadaný na stránce vlastností ovládacího prvku:  
  
### <a name="property-page-data-transfer"></a>Přenos dat stránky vlastností  
  
|||  
|-|-|  
|[Ddp_cbindex –](#ddp_cbindex)|Propojí vybrané řetězec index v poli se seznamem s vlastností ovládacího prvku.|  
|[Ddp_cbstring –](#ddp_cbstring)|Propojí vybrané řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec můžete začít s stejná písmena jako hodnotu vlastnosti, ale není potřeba plně shodná.|  
|[Ddp_cbstringexact –](#ddp_cbstringexact)|Propojí vybrané řetězec v poli se seznamem s vlastností ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|  
|[Ddp_check –](#ddp_check)|Odkazy zaškrtávacího políčka na stránce vlastností ovládacího prvku pomocí ovládacího prvku.|  
|[Ddp_lbindex –](#ddp_lbindex)|Propojí vybrané řetězec index v poli seznamu pomocí ovládacího prvku.|  
|[Ddp_lbstring –](#ddp_lbstring)|Propojí vybrané řetězec v seznamu pomocí ovládacího prvku. Vybraný řetězec můžete začít s stejná písmena jako hodnotu vlastnosti, ale nemusí odpovídat plně.|  
|[Ddp_lbstringexact –](#ddp_lbstringexact)|Propojí vybrané řetězec v seznamu pomocí ovládacího prvku. Vybraný řetězec a hodnotu vlastnosti řetězce musí přesně shodovat.|  
|[Ddp_postprocessing –](#ddp_postprocessing)|Dokončení přenosu hodnoty vlastnosti z ovládacího prvku.|  
|[Ddp_radio –](#ddp_radio)|Skupina přepínacích tlačítek na stránce vlastností ovládacího prvku pomocí ovládacího prvku odkazy.|  
|[Ddp_text –](#ddp_text)|Odkazy ovládacího prvku na stránce vlastností ovládacího prvku pomocí ovládacího prvku. Tato funkce zpracovává několika různých typů vlastností, jako například **dvojité**, **krátké**, `BSTR`, a **dlouho**.|  
  
 Další informace o `DoDataExchange` funkce a vlastnosti stránky, najdete v článku [– ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).  
  
 Následuje seznam makra umožňuje vytvářet a spravovat stránky vlastností pro ovládací prvky OLE:  
  
### <a name="property-pages"></a>Stránky vlastností  
  
|||  
|-|-|  
|[BEGIN_PROPPAGEIDS –](#begin_proppageids)|Zahájí seznam identifikátorů stránky vlastností.|  
|[END_PROPPAGEIDS –](#end_proppageids)|Ukončí seznam identifikátorů stránky vlastností.|  
|[PROPPAGEID –](#proppageid)|Deklaruje stránky vlastností třídy ovládacího prvku.|  
  
##  <a name="ddp_cbindex"></a>  Ddp_cbindex –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce synchronizovat hodnotu vlastnosti celé číslo s indexem aktuální výběr v poli se seznamem na stránce vlastností.  
  
```   
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 Pole ID prostředku se seznamem se ovládací prvek související s vlastností ovládacího prvku určeného `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně s ovládacím prvkem pole se seznamem určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_CBIndex` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_cbstring"></a>  Ddp_cbstring –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce k synchronizaci s aktuálním výběrem pole se seznamem na stránce vlastností hodnotu vlastnosti řetězce.  
  
```  
void AFXAPI DDP_CBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 Pole ID prostředku se seznamem se ovládací prvek související s vlastností ovládacího prvku určeného `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně řetězcem pole se seznamem určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_CBString` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_cbstringexact"></a>  Ddp_cbstringexact –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce synchronizace hodnotu vlastnosti řetězce, který přesně odpovídá aktuální výběr v poli se seznamem na stránce vlastností.  
  
```  
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 Pole ID prostředku se seznamem se ovládací prvek související s vlastností ovládacího prvku určeného `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně řetězcem pole se seznamem určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_CBStringExact` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_check"></a>  Ddp_check –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce synchronizace hodnotu vlastnosti s ovládací prvek zaškrtávací políčko stránky přidružené vlastnosti.  
  
```   
void AFXAPI DDP_Check(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 ID prostředku ovládací prvek zaškrtávací políčko přidružená vlastnost ovládacího prvku určeného `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně s ovládací prvek zaškrtávací políčko určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_Check` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_lbindex"></a>  Ddp_lbindex –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce synchronizovat hodnotu vlastnosti celé číslo s indexem aktuální výběr v seznamu na stránce vlastností.  
  
```   
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 Ovládací prvek související s určeného vlastností ovládacího prvku pole ID prostředku seznamu `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně řetězcem pole seznamu určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_LBIndex` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_lbstring"></a>  Ddp_lbstring –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce k synchronizaci s aktuálním výběrem v seznamu na stránce vlastností hodnotu vlastnosti řetězce.  
  
```   
void AFXAPI DDP_LBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 Ovládací prvek související s určeného vlastností ovládacího prvku pole ID prostředku seznamu `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně řetězcem pole seznamu určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_LBString` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_lbstringexact"></a>  Ddp_lbstringexact –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce synchronizace hodnotu vlastnosti řetězce, který přesně odpovídá aktuální výběr v seznamu na stránce vlastností.  
  
```   
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 Ovládací prvek související s určeného vlastností ovládacího prvku pole ID prostředku seznamu `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně řetězcem pole seznamu určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_LBStringExact` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_postprocessing"></a>  Ddp_postprocessing –  
 Volání této funkce na stránce vlastností `DoDataExchange` funkce ukončíte přenos hodnot vlastností na stránce vlastností do vlastního ovládacího prvku, pokud hodnoty vlastnosti jsou uloženy.  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána po dokončení všech funkce výměny dat. Příklad:  
  
 [!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_radio"></a>  Ddp_radio –  
 Volání této funkce ve vašem ovládacím prvku `DoPropExchange` funkce synchronizovat hodnotu vlastnosti se přidružené vlastnosti stránky ovládací prvek přepínač.  
  
```   
void AFXAPI DDP_Radio(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 ID prostředku přepínače tlačítko ovládací prvek související s vlastností ovládacího prvku určeného `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně s ovládací prvek přepínač určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_Radio` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="ddp_text"></a>  Ddp_text –  
 Volání této funkce ve vašem ovládacím prvku `DoDataExchange` funkce synchronizace hodnotu vlastnosti s ovládacím prvkem přidružené vlastnosti stránky.  
  
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
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `id`  
 ID prostředku ovládací prvek související s vlastností ovládacího prvku určeného `pszPropName`.  
  
 `member`  
 Členské proměnné přidruženého k ovládacímu prvku stránky vlastnost určeného `id` a vlastnost určeného `pszPropName`.  
  
 `pszPropName`  
 Název vlastnosti vlastnost ovládacího prvku k výměně pomocí ovládacího prvku určeného `id`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce by měla být volána před odpovídající `DDX_Text` volání funkce.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS –  
 Zahájí definici ovládacího prvku seznam identifikátorů stránky vlastností.  
  
```   
BEGIN_PROPPAGEIDS(class_name,  count)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku pro vlastností, které jsou určené stránky.  
  
 *Počet*  
 Počet stránek vlastností, které používá třída ovládacích prvků.  
  
### <a name="remarks"></a>Poznámky  
 V souboru implementace (sada), který definuje členské funkce pro třídu, spusťte seznamu vlastností stránky s `BEGIN_PROPPAGEIDS` makro, potom můžete přidat položky makro pro každou z vaší stránky vlastností a dokončení seznamu vlastností stránky s `END_PROPPAGEIDS` makro.  
  
 Další informace o stránky vlastností, najdete v článku [– ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="end_proppageids"></a>  END_PROPPAGEIDS –  
 Ukončí definici vašeho seznamu ID stránky vlastností.  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Název třídy ovládacího prvku, který vlastní stránky vlastností.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
  
##  <a name="proppageid"></a>  PROPPAGEID –  
 Stránky vlastností pro použití se přidá váš ovládací prvek OLE.  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Třída jedinečné ID stránky vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Všechny `PROPPAGEID` makra musí být umístěn mezi `BEGIN_PROPPAGEIDS` a `END_PROPPAGEIDS` makra v souboru implementaci ovládacího prvku.  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxctl.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
