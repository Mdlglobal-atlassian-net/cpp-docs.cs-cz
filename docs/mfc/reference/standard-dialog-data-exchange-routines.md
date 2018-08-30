---
title: Rutiny výměny dat standardního dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 770d110a5acd66b307e675d8c71a7de108bae6b5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198494"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutiny výměny dat standardního dialogového okna
Toto téma uvádí rutiny exchange (DDX) dat standardního dialogového okna pro běžné ovládací prvky dialogového okna knihovny MFC.  
  
> [!NOTE]
>  Rutiny výměny dat standardního dialogového okna jsou definovány v souboru afxdd_.h záhlaví. Ale aplikace by měla obsahovat afxwin.h.  
  
### <a name="ddx-functions"></a>DDX – funkce  
  
|||  
|-|-|  
|[Ddx_cbindex –](#ddx_cbindex)|Inicializuje nebo načte index aktuálního výběru ovládacího prvku pole se seznamem.|  
|[Ddx_cbstring –](#ddx_cbstring)|Inicializuje nebo načte aktuální obsah upravit pole ovládacího prvku pole se seznamem.|  
|[Ddx_cbstringexact –](#ddx_cbstringexact)|Inicializuje nebo načte aktuální obsah upravit pole ovládacího prvku pole se seznamem.|  
|[Ddx_check –](#ddx_check)|Inicializuje nebo načte aktuální stav ovládací prvek zaškrtávací políčko.|  
|[Ddx_control –](#ddx_control)|Podtřídy daný ovládací prvek v rámci dialogového okna.|  
|[Ddx_datetimectrl –](#ddx_datetimectrl)|Inicializuje nebo načte datum a čas data ovládací prvek pro výběr data a času.|  
|[Ddx_ipaddress –](#ddx_ipaddress)|Inicializuje nebo načte aktuální hodnota ovládacího prvku IP adresu.|  
|[Ddx_lbindex –](#ddx_lbindex)|Inicializuje nebo načte index aktuálního výběru ovládacího prvku seznamu.|  
|[Ddx_lbstring –](#ddx_lbstring)|Inicializuje nebo načte aktuální výběr v rámci ovládacího prvku seznamu pole.|  
|[Ddx_lbstringexact –](#ddx_lbstringexact)|Inicializuje nebo načte aktuální výběr v rámci ovládacího prvku seznamu pole.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Vytvoří ovládací prvek .NET odpovídající ID ovládacího prvku prostředku.|  
|[Ddx_monthcalctrl –](#ddx_monthcalctrl)|Inicializuje nebo načte aktuální hodnotu ovládací prvek měsíční kalendář.|  
|[Ddx_radio –](#ddx_radio)|Inicializuje nebo načte index založený na 0 v ovládacím prvku přepínač, který je aktuálně zaškrtnutých v rámci skupiny ovládacích prvků přepínačů.|  
|[Ddx_scroll –](#ddx_scroll)|Inicializuje nebo načte aktuální pozice posuvníku ovládacího prvku thumb.|  
|[Ddx_slider –](#ddx_slider)|Inicializuje nebo načte aktuální pozice posuvníku ovládacího prvku thumb.|  
|[DDX_Text –](#ddx_text)|Inicializuje nebo načte aktuální hodnota ovládacího prvku pro úpravy.|  
  
##  <a name="ddx_cbindex"></a>  Ddx_cbindex –  
 `DDX_CBIndex` Funkce spravuje přenos **int** data mezi ovládací prvek pole se seznamem v dialogovém okně formuláře, zobrazení, nebo objekt zobrazení ovládacího prvku a **int** datový člen dialogové okno, zobrazení formuláře nebo ovládacího prvku objekt zobrazení.  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku prvek pole se seznamem, který je přidružený k vlastnosti ovládacího prvku.  
  
 *index*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_CBIndex` se nazývá *index* je nastavena na index aktuálního výběru pole se seznamem. Pokud není vybrána žádná položka *index* je nastavena na hodnotu 0.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_cbstring"></a>  Ddx_cbstring –  
 `DDX_CBString` Funkce spravuje přenos `CString` zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi ovládacího prvku pro úpravy prvku pole se seznamem v dialogovém okně a `CString` datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku prvek pole se seznamem, který je přidružený k vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_CBString` se nazývá *hodnotu* je nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka *hodnotu* nastavený na řetězec o nulové délce.  
  
> [!NOTE]
>  Pokud rozevírací seznam pole se seznamem se hodnota vyměňují je omezena na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>  Ddx_cbstringexact –  
 `DDX_CBStringExact` Funkce spravuje přenos `CString` zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi ovládacího prvku pro úpravy prvku pole se seznamem v dialogovém okně a `CString` datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku prvek pole se seznamem, který je přidružený k vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_CBStringExact` se nazývá *hodnotu* je nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka *hodnotu* nastavený na řetězec o nulové délce.  
  
> [!NOTE]
>  Pokud rozevírací seznam pole se seznamem se hodnota vyměňují je omezena na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_check"></a>  Ddx_check –  
 `DDX_Check` Funkce spravuje přenos **int** data mezi ovládací prvek zaškrtávací políčko v dialogovém okně, formuláře, zobrazení, nebo objekt zobrazení ovládacího prvku a **int** datový člen dialogové okno, zobrazení formuláře nebo ovládacího prvku objekt zobrazení.  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládací prvek zaškrtávací políčko, které jsou přidružené k vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Check` se nazývá *hodnotu* je nastavena na aktuální stav ovládací prvek zaškrtávací políčko. Seznam stav možné hodnoty najdete v tématu [BM_GETCHECK](/windows/desktop/Controls/bm-getcheck) v sadě Windows SDK.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_control"></a>  Ddx_control –  
 `DDX_Control` Funkce podtřídy ovládacího prvku určené *nIDC*, dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [cdataexchange –](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 *nIDC*  
 ID prostředku ovládacího prvku na má rozčlenit do podtříd.  
  
 *rControl*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládací prvek objekt zobrazení související s zadaný ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 *PDX* objektu je poskytnut pomocí rozhraní framework při `DoDataExchange` funkce je volána. Proto `DDX_Control` by měla být volána pouze v rámci přepsání metody `DoDataExchange`.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>  Ddx_datetimectrl –  
 `DDX_DateTimeCtrl` Funkce spravuje přenos dat Datum a čas mezi ovládací prvek pro výběr data a času ( [atributu CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) v objektu pole nebo formuláře dialogového okna zobrazení a buď [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) datový člen objektu zobrazení nebo formuláře dialogového okna.  
  
```  
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [cdataexchange –](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr. Není nutné odstranit tento objekt.  
  
 *nIDC*  
 ID prostředku datum a čas pro výběr ovládacího prvku přidruženého k členské proměnné.  
  
 *value*  
 V prvních dvou verzí, odkaz na `CTime` nebo `COleDateTime` členské proměnné, dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data. Ve třetí verzi odkaz na `CString` datový člen ovládací prvek zobrazení objekt.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_DateTimeCtrl` je volána, *hodnotu* je nastavena na aktuální stav datu a ovládacího prvku pro výběr času nebo ovládací prvek je nastaven na *hodnota*, v závislosti na směru exchange.  
  
 Ve třetí verzi výše uvedeného `DDX_DateTimeCtrl` spravuje přenos `CString` data mezi datum čas ovládacího prvku a [CString](../../atl-mfc-shared/reference/cstringt-class.md) datový člen objektu ovládacího prvku zobrazení. Řetězec je formátovaný pomocí pravidel pro aktuální národní prostředí pro formátování data a času.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  

## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl
Vytvoří ovládací prvek .NET odpovídající ID ovládacího prvku prostředku.  
   
### <a name="syntax"></a>Syntaxe  
```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [cdataexchange – třída](cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládacího prvku přidruženého k vlastnosti ovládacího prvku.  
  
 *control*  
 Odkaz na [CWinFormsControl – třída](cwinformscontrol-class.md) objektu.  
   
### <a name="remarks"></a>Poznámky  
 `DDX_ManagedControl` volání [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) vytvořit ovládací prvek s odpovídajícím ID prostředku ovládacího prvku. Použití `DDX_ManagedControl` k vytvoření ovládacích prvků z ID prostředku v [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Pro data systému exchange není potřeba používat funkce DDX/DDV s ovládacími prvky Windows Forms.  
  
 Další informace najdete v tématu [jak: proveďte DDX/DDV datové vazby pomocí Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h  
   
### <a name="see-also"></a>Viz také  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>  Ddx_ipaddress –  
 `DDX_IPAddress` Funkce spravuje přenos dat mezi ovládací prvek adresy IP a datový člen objektu ovládacího prvku zobrazení.  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládací prvek adresy IP, které jsou přidružené k vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na DWORD obsahující pole čtyř hodnotu ovládací prvek adresy IP. Pole jsou vyplněna nebo trochu odlišná.  
  
|Pole|Služba BITS obsahující hodnotu pole|  
|-----------|-------------------------------------|  
|3|0 až 7|  
|2|8 až 15|  
|1|16 až 23|  
|0|24 do 31.|  
  
 Použití rozhraní Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress) načíst hodnotu nebo použijte [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress) tak, aby vyplnil hodnotu. Tyto zprávy jsou popsány v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_IPAddress` je volána, *hodnotu* je buď čtení ze správy IP adres nebo *hodnotu* se zapisují do ovládacího prvku, v závislosti na směru exchange.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_lbindex"></a>  Ddx_lbindex –  
 `DDX_LBIndex` Funkce spravuje přenos **int** data mezi ovládací prvek seznam v dialogovém okně formuláře, zobrazení, nebo objekt zobrazení ovládacího prvku a **int** datový člen dialogové okno, zobrazení formuláře nebo ovládacího prvku objekt zobrazení.  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládací prvek seznam přidružené vlastnosti ovládacího prvku.  
  
 *index*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_LBIndex` se nazývá *index* je nastavena na index aktuální výběr v seznamu. Pokud není vybrána žádná položka *index* je nastavena na hodnotu -1.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_lbstring"></a>  Ddx_lbstring –  
 `DDX_LBString` Funkce spravuje přenos `CString` data mezi ovládací prvek seznam v dialogovém okně formuláře, zobrazení, nebo objekt zobrazení ovládacího prvku a `CString` datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládací prvek seznam přidružené vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_LBString` je volána k přenosu dat do seznamu ovládacího prvku pole, první položky v ovládacím prvku, jehož začátku odpovídá *hodnotu* zaškrtnuto. (Tak, aby odpovídaly celé položky, ne jenom předpony, použijte [ddx_lbstringexact –](#ddx_lbstringexact).) Pokud neexistují žádné odpovídající položky, nejsou vybrané žádné položky. Porovnání se velká a malá písmena.  
  
 Když `DDX_LBString` je volána k přenosu dat z ovládacího prvku seznamu pole *hodnotu* je nastavena na aktuální výběr v seznamu. Pokud není vybrána žádná položka *hodnotu* nastavený na řetězec o nulové délce.  
  
> [!NOTE]
>  Pokud rozevírací seznam pole se seznamem se hodnota vyměňují je omezena na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>  Ddx_lbstringexact –  
 `DDX_CBStringExact` Funkce spravuje přenos `CString` zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi úprav ovládací prvek seznam v dialogovém okně a `CString` datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku ovládací prvek seznam přidružené vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_LBStringExact` je volána k přenosu dat do seznamu ovládacího prvku pole, první položky v ovládacím prvku, který odpovídá *hodnotu* zaškrtnuto. (Vyhledání pouze předponu místo celé položky [ddx_lbstring –](#ddx_lbstring).) Pokud neexistují žádné odpovídající položky, nejsou vybrané žádné položky. Porovnání se velká a malá písmena.  
  
 Když `DDX_CBStringExact` je volána k přenosu dat z ovládacího prvku seznamu pole *hodnotu* je nastavena na aktuální výběr v seznamu. Pokud není vybrána žádná položka *hodnotu* nastavený na řetězec o nulové délce.  
  
> [!NOTE]
>  Pokud rozevírací seznam pole se seznamem se hodnota vyměňují je omezena na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>  Ddx_monthcalctrl –  
 `DDX_MonthCalCtrl` Funkce spravuje přenos dat mezi ovládací prvek měsíční kalendář ( [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) dialogové okno, formulářové zobrazení, nebo objekt zobrazení ovládacího prvku a buď [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [cdataexchange –](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr. Není nutné odstranit tento objekt.  
  
 *nIDC*  
 ID prostředku v ovládacím prvku měsíční kalendář přidružený k proměnné členů.  
  
 *value*  
 Odkaz na `CTime` nebo `COleDateTime` členskou proměnnou dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek slouží ke správě hodnotu data. Čas pole v objektu čas jsou sady tak, aby odrážely čas vytvoření okna ovládacího prvku nebo jakýkoli čas byla nastavena v ovládacím prvku pomocí volání `CMonthCalCtrl::SetCurSel`.  
  
 Když `DDX_MonthCalCtrl` se nazývá *hodnotu* je nastavena na aktuální stav ovládací prvek měsíční kalendář.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_radio"></a>  Ddx_radio –  
 `DDX_Radio` Funkce spravuje přenos **int** zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi skupinu přepínačů ovládacího prvku v dialogovém okně a **int** datový člen dialogové okno, zobrazení formuláře nebo ovládacího prvku objekt zobrazení. Hodnota **int** datový člen se určuje podle přepínačů, které se vybere tlačítko v rámci skupiny.  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku první ovládací prvek přepínač v skupině.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Radio` se nazývá *hodnotu* je nastavena na aktuální stav skupiny ovládacích prvků přepínačů. Tato hodnota nastavená jako ovládacím prvku přepínač, který je nyní ověřen index založený na 0 nebo -1, pokud žádné ovládací prvky přepínače nebyly zvoleny.  
  
 Například v případě, že je první přepínací tlačítko ve skupině checked (tlačítka se stylem WS_GROUP) hodnotu **int** člen je 0 a tak dále.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_scroll"></a>  Ddx_scroll –  
 `DDX_Scroll` Funkce spravuje přenos **int** zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi posuvníku ovládacího prvku v dialogovém okně a **int** datový člen dialogové okno, zobrazení formuláře nebo ovládacího prvku objekt zobrazení.  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku posuvníku ovládacího prvku přidruženého k vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Scroll` se nazývá *hodnotu* je nastavena na aktuální pozici ovládacího prvku thumb. Další informace o hodnoty přidružené k aktuální pozici ovládacího prvku thumb, naleznete v tématu [GetScrollPos](/windows/desktop/api/winuser/nf-winuser-getscrollpos) v sadě Windows SDK.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_slider"></a>  Ddx_slider –  
 `DDX_Slider` Funkce spravuje přenos **int** data mezi ovládací prvek posuvník v zobrazení dialogového okna nebo formuláře a **int** datový člen objektu zobrazení nebo formuláře dialogového okna.  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [cdataexchange –](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID prostředku v ovládacím prvku posuvník.  
  
 *value*  
 Odkaz na hodnotu, která bude vyměněn. Tento parametr obsahuje nebo nastaví aktuální pozici v ovládacím prvku posuvník.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Slider` je volána, *hodnotu* je nastavena na aktuální pozici ovládacího prvku thumb, nebo hodnota přijímá pozice, v závislosti na směru exchange.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích posuvníku, naleznete v tématu [používání atributu CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  
  
##  <a name="ddx_text"></a>  DDX_Text –  
 `DDX_Text` Funkce spravuje přenos **int**, **UINT**, **dlouhé**, DWORD, `CString`, **float**, nebo **double** data mezi ovládacího prvku pro úpravy v dialogovém okně zobrazení formuláře nebo ovládací prvek zobrazení a [CString](../../atl-mfc-shared/reference/cstringt-class.md) datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.  
  
```  
void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,  
    int nIDC,  
    COleDateTime& value);  
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel [cdataexchange –](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení pro úpravy.  
  
 *value*  
 Odkaz na datový člen v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení. Datový typ *hodnotu* závisí na kterém přetížené verze `DDX_Text` použijete.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Požadavky  
  **Hlavička** afxdd_.h  

## <a name="see-also"></a>Viz také  
 [Rutiny ověřování dat standardního dialogového okna](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
