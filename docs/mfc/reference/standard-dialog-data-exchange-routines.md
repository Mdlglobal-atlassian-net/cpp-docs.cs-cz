---
title: "Rutiny výměny dat standardního dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca598a9ac6a146457d24bcc80e54d003123d7dd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutiny výměny dat standardního dialogového okna
Toto téma uvádí rutiny exchange (DDX) dat standardního dialogového okna použít pro běžné ovládací prvky MFC dialogové okno.  
  
> [!NOTE]
>  Rutiny výměny dat standardního dialogového okna jsou definovány v afxdd_.h soubor hlavičky. Aplikace by měla obsahovat však afxwin.h.  
  
### <a name="ddx-functions"></a>DDX – funkce  
  
|||  
|-|-|  
|[Ddx_cbindex –](#ddx_cbindex)|Inicializuje nebo načte index aktuální výběr ovládacího prvku pole se seznamem.|  
|[Ddx_cbstring –](#ddx_cbstring)|Inicializuje nebo načte aktuální obsah pole upravit ovládacího prvku pole se seznamem.|  
|[Ddx_cbstringexact –](#ddx_cbstringexact)|Inicializuje nebo načte aktuální obsah pole upravit ovládacího prvku pole se seznamem.|  
|[Ddx_check –](#ddx_check)|Inicializuje nebo načte aktuální stav ovládací prvek zaškrtávací políčko.|  
|[Ddx_control –](#ddx_control)|Podtřídy daný ovládací prvek v rámci dialogového okna.|  
|[Ddx_datetimectrl –](#ddx_datetimectrl)|Inicializuje nebo načte datum a čas data ovládacího prvku pro výběr data a času.|  
|[Ddx_ipaddress –](#ddx_ipaddress)|Inicializuje nebo načte aktuální hodnotu ovládací prvek adresy IP.|  
|[Ddx_lbindex –](#ddx_lbindex)|Inicializuje nebo načte index aktuální výběr ovládací prvek seznam.|  
|[Ddx_lbstring –](#ddx_lbstring)|Inicializuje nebo načte aktuální výběr v rámci ovládací prvek seznam.|  
|[Ddx_lbstringexact –](#ddx_lbstringexact)|Inicializuje nebo načte aktuální výběr v rámci ovládací prvek seznam.|
|[DDX_ManagedControl –](#ddx_managedcontrol)|Vytvoří ovládacího prvku .NET odpovídající ID ovládacího prvku prostředku.|  
|[Ddx_monthcalctrl –](#ddx_monthcalctrl)|Inicializuje nebo načte aktuální hodnotu ovládací prvek měsíční kalendář.|  
|[Ddx_radio –](#ddx_radio)|Inicializuje nebo načte index na základě 0 ovládací prvek přepínač, který je právě rezervována vrátit v rámci skupiny ovládací prvek přepínač.|  
|[Ddx_scroll –](#ddx_scroll)|Inicializuje nebo načte aktuální umístění ovládacího prvku posuňte jezdec.|  
|[Ddx_slider –](#ddx_slider)|Inicializuje nebo načte aktuální pozici prvku posuvník jezdce.|  
|[DDX_Text –](#ddx_text)|Inicializuje nebo načte aktuální hodnotu ovládacích prvků pro úpravy.|  
  
##  <a name="ddx_cbindex"></a>Ddx_cbindex –  
 `DDX_CBIndex` Funkce spravuje přenos `int` formuláři dat mezi prvek pole se seznamem v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `int` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládacího prvku pole se seznamem přidružená vlastnost ovládacího prvku.  
  
 *index*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_CBIndex` je volána, *index* je nastaven na index aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *index* je nastaven na hodnotu 0.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_cbstring"></a>Ddx_cbstring –  
 `DDX_CBString` Funkce spravuje přenos `CString` formuláři dat mezi ovládacího prvku úprav ovládacího prvku pole se seznamem v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `CString` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_CBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládacího prvku pole se seznamem přidružená vlastnost ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_CBString` je volána, *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastaven na řetězec nulové délky.  
  
> [!NOTE]
>  Pokud pole se seznamem rozevíracího seznamu, hodnota vyměňují je omezená na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_cbstringexact"></a>Ddx_cbstringexact –  
 `DDX_CBStringExact` Funkce spravuje přenos `CString` formuláři dat mezi ovládacího prvku úprav ovládacího prvku pole se seznamem v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `CString` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládacího prvku pole se seznamem přidružená vlastnost ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_CBStringExact` je volána, *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastaven na řetězec nulové délky.  
  
> [!NOTE]
>  Pokud pole se seznamem rozevíracího seznamu, hodnota vyměňují je omezená na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_check"></a>Ddx_check –  
 `DDX_Check` Funkce spravuje přenos `int` formuláři dat mezi ovládací prvek zaškrtávací políčko v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `int` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_Check(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládací prvek zaškrtávací políčko, které jsou spojené s vlastností ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Check` je volána, *hodnota* nastavena na aktuální stav ovládací prvek zaškrtávací políčko. Seznam hodnot možné stavu najdete v tématu [BM_GETCHECK](http://msdn.microsoft.com/library/windows/desktop/bb775986) ve Windows SDK.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_control"></a>Ddx_control –  
 `DDX_Control` Funkce podtřídy ovládacího prvku, určeného `nIDC`, dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_Control(
    CDataExchange* pDX,  
    int nIDC,  
    CWnd& rControl);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `nIDC`  
 ID prostředku pro být rozčlenění ovládacího prvku.  
  
 *rControl*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení související s daný ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 `pDX` Objekt poskytl rozhraní při `DoDataExchange` funkce je volána. Proto `DDX_Control` by měla být volána pouze v rámci vaší přepsání `DoDataExchange`.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_datetimectrl"></a>Ddx_datetimectrl –  
 `DDX_DateTimeCtrl` Funkce spravuje přenos dat datum nebo čas mezi ovládací prvek pro výběr data a času ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) v objekt zobrazení nebo formuláře dialogové okno a buď [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) – datový člen objektu dialogové okno pole nebo formátu zobrazení.  
  
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
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr. Nemusíte odstranit tento objekt.  
  
 `nIDC`  
 ID prostředku ovládacího prvku datum a čas výběr přidružený k proměnné členů.  
  
 *value*  
 V první dva verzí, odkaz na `CTime` nebo `COleDateTime` členské proměnné, dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data. Ve třetí verzi, odkaz na `CString` objekt zobrazení ovládacího prvku data člena.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_DateTimeCtrl` je volána, *hodnotu* je nastavena na aktuální stav datum a čas ovládací prvek pro výběr nebo ovládací prvek je nastavený na *hodnotu*, v závislosti na směru exchange.  
  
 Ve výše uvedené, třetí verzi `DDX_DateTimeCtrl` spravuje přenos `CString` dat mezi datum čas řízení a [CString](../../atl-mfc-shared/reference/cstringt-class.md) – datový člen objektu zobrazení ovládacího prvku. Řetězec je naformátován pomocí pravidel aktuální národní prostředí pro formátování data a časy.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  

   

 
## <a name="ddx_managedcontrol"></a>DDX_ManagedControl –
Vytvoří ovládacího prvku .NET odpovídající ID ovládacího prvku prostředku.  
   
### <a name="syntax"></a>Syntaxe  
  ```  
template <typename T>  
void DDX_ManagedControl(  
     CDataExchange* pDX,   
     int nIDC,   
     CWinFormsControl<T>& control );  
```
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel [CDataExchange – třída](cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládací prvek související s vlastností ovládacího prvku.  
  
 `control`  
 Odkaz na [CWinFormsControl třída](cwinformscontrol-class.md) objektu.  
   
### <a name="remarks"></a>Poznámky  
 `DDX_ManagedControl`volání [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) k vytvoření ovládacího prvku odpovídající ID prostředku ovládacího prvku. Použití `DDX_ManagedControl` k vytvoření ovládacích prvků z ID prostředků v [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Pro data systému exchange není potřeba použít funkce DDX/DDV s Windows Forms – ovládací prvky.  
  
 Další informace najdete v tématu [postup: provést vazby dat k DDX/DDV s modelem Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h  
   
### <a name="see-also"></a>Viz také  
 [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)   
 [CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
 

  
##  <a name="ddx_ipaddress"></a>Ddx_ipaddress –  
 `DDX_IPAddress` Funkce spravuje přenos dat mezi ovládací prvek adresy IP a členem data objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,  
    int nIDC,  
    DWORD& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku IP adresu ovládací prvek související s vlastností ovládacího prvku.  
  
 *value*  
 Odkaz na `DWORD` obsahující hodnotu pole čtyři ovládací prvek adresy IP. Pole jsou vyplněna nebo tímto.  
  
|Pole|Služba BITS obsahující hodnota pole|  
|-----------|-------------------------------------|  
|3|0 až 7|  
|2|8 až 15|  
|1|16 až 23|  
|0|24 do 31|  
  
 Použít Win32 [IPM_GETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761378) načíst hodnotu, nebo použijte [IPM_SETADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb761380) k vyplnění hodnota. Tyto zprávy jsou popsány v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_IPAddress` je volána, *hodnotu* je buď pro čtení z ovládacího prvku IP adresu nebo *hodnota* je zapsán do ovládacího prvku, v závislosti na směru exchange.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_lbindex"></a>Ddx_lbindex –  
 `DDX_LBIndex` Funkce spravuje přenos `int` formuláři dat mezi ovládací prvek seznamu v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `int` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,  
    int nIDC,  
    int& index);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládací prvek seznam přidružená vlastnost ovládacího prvku.  
  
 *index*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_LBIndex` je volána, *index* je nastaven na index aktuální výběr pole v seznamu. Pokud není vybrána žádná položka, *index* je nastaven na hodnotu -1.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_lbstring"></a>Ddx_lbstring –  
 `DDX_LBString` Funkce spravuje přenos `CString` formuláři dat mezi ovládací prvek seznamu v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `CString` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_LBString(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládací prvek seznam přidružená vlastnost ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_LBString` je volána k přenosu dat do ovládací prvek seznamu, první položky v ovládacím prvku, jehož počáteční odpovídá *hodnota* je vybrána. (Vyhledat celou položku, nikoli pouze předponu, použijte [ddx_lbstringexact –](#ddx_lbstringexact).) Pokud nejsou nalezeny žádné shody, nejsou vybrány žádné položky. Porovnání se velká a malá písmena.  
  
 Když `DDX_LBString` je volána k přenosu dat z ovládací prvek seznamu, *hodnota* nastavena na aktuální výběr pole v seznamu. Pokud není vybrána žádná položka, *hodnota* je nastaven na řetězec nulové délky.  
  
> [!NOTE]
>  Pokud pole se seznamem je rozevíracího seznamu, hodnota vyměňují je omezená na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_lbstringexact"></a>Ddx_lbstringexact –  
 `DDX_CBStringExact` Funkce spravuje přenos `CString` formuláři dat mezi úpravy kontrolu nad ovládací prvek seznamu v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `CString` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,  
    int nIDC,  
    CString& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládací prvek seznam přidružená vlastnost ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_LBStringExact` je volána k přenosu dat do ovládací prvek seznamu, první položky v ovládacím prvku, který odpovídá *hodnota* je vybrána. (Vyhledat pouze předponu spíš než celý položek, použijte [ddx_lbstring –](#ddx_lbstring).) Pokud nejsou nalezeny žádné shody, nejsou vybrány žádné položky. Porovnání se velká a malá písmena.  
  
 Když `DDX_CBStringExact` je volána k přenosu dat z ovládací prvek seznamu, *hodnota* nastavena na aktuální výběr pole v seznamu. Pokud není vybrána žádná položka, *hodnota* je nastaven na řetězec nulové délky.  
  
> [!NOTE]
>  Pokud pole se seznamem je rozevíracího seznamu, hodnota vyměňují je omezená na 255 znaků.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_monthcalctrl"></a>Ddx_monthcalctrl –  
 `DDX_MonthCalCtrl` Funkce spravuje přenosu dat data mezi ovládací prvek měsíční kalendář ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) v dialogového okna, formátu zobrazení, nebo objekt zobrazení ovládacího prvku a buď [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
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
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr. Nemusíte odstranit tento objekt.  
  
 `nIDC`  
 ID prostředku ovládací prvek měsíční kalendář přidružený k proměnné členů.  
  
 *value*  
 Odkaz na `CTime` nebo `COleDateTime` členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek spravuje hodnotu data. Pole čas v objektu času jsou sady tak, aby odrážela čas vytvoření okna pro ovládací prvek nebo libovolnou dobu nebyl nastaven v ovládacím prvku pomocí volání `CMonthCalCtrl::SetCurSel`.  
  
 Když `DDX_MonthCalCtrl` je volána, *hodnota* nastavena na aktuální stav ovládací prvek měsíční kalendář.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_radio"></a>Ddx_radio –  
 `DDX_Radio` Funkce spravuje přenos `int` data mezi skupinou přepínačů ovládacího prvku v dialogovém okně, tvoří zobrazení, nebo objekt zobrazení ovládacího prvku a `int` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku. Hodnota `int` – datový člen je určen podle přepínačů, které je vybráno tlačítko ve skupině.  
  
```  
void AFXAPI DDX_Radio(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku první prvek přepínač ve skupině.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo objekt ovládacího prvku zobrazení, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Radio` je volána, *hodnota* nastavena na aktuální stav skupiny ovládacích prvků přepínačů. Hodnota je nastavená na index ovládací prvek přepínač, který je právě rezervována vrátit na základě 0 nebo -1, pokud žádný přepínač ovládací prvky jsou zaškrtnutá políčka.  
  
 Například v případě, že první přepínač ve skupině je zaškrtnuta možnost (tlačítko s ws_group – styl) hodnotu `int` člen je 0 a tak dále.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_scroll"></a>Ddx_scroll –  
 `DDX_Scroll` Funkce spravuje přenos `int` formuláři dat mezi ovládací prvek typu posuvník v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `int` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku ovládací prvek typu posuvník související s vlastností ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Scroll` je volána, *hodnota* je nastavena na aktuální pozici ovládacího prvku jezdec. Další informace o hodnoty související s aktuálním umístěním ovládacího prvku jezdec najdete v tématu [GetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787585) ve Windows SDK.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_slider"></a>Ddx_slider –  
 `DDX_Slider` Funkce spravuje přenos `int` dat mezi ovládací prvek typu jezdec v dialogovém okně zobrazení pole nebo formuláře a `int` data členem objektu zobrazení nebo formuláře dialogového okna.  
  
```  
void AFXAPI DDX_Slider(
    CDataExchange* pDX,  
    int nIDC,  
    int& value);  
```  
  
### <a name="parameters"></a>Parametry  
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID prostředku v ovládacím prvku posuvník.  
  
 *value*  
 Odkaz na hodnotu výměnu. Tento parametr obsahuje nebo nastaví aktuální pozici v ovládacím prvku posuvník.  
  
### <a name="remarks"></a>Poznámky  
 Když `DDX_Slider` je volána, *hodnota* je nastavena na aktuální pozici ovládacího prvku jezdec, nebo hodnota přijme pozice, v závislosti na směru exchange.  
  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích posuvníku najdete v tématu [pomocí CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  
  
##  <a name="ddx_text"></a>DDX_Text –  
 `DDX_Text` Funkce spravuje přenos `int`, **Celé_číslo**, **dlouho**, `DWORD`, `CString`, **float**, nebo  **dvojité** dat mezi ovládací prvek upravit v dialogovém okně, zobrazení formuláře nebo řízení zobrazení a [CString](../../atl-mfc-shared/reference/cstringt-class.md) – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
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
 `pDX`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 `nIDC`  
 ID ovládací prvek upravit v dialogovém okně, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *value*  
 Odkaz na člena dat v dialogovém okně, zobrazení formuláře nebo objekt zobrazení ovládacího prvku. Datový typ *hodnotu* závisí na kterém přetížené verze `DDX_Text` používáte.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdd_.h  

## <a name="see-also"></a>Viz také  
 [Rutiny ověřování dat standardního dialogového okna](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
