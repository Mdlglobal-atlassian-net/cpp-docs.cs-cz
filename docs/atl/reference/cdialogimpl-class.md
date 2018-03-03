---
title: "CDialogImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab4bb1e04bd21900cdf8d8122af51547e79aea22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdialogimpl-class"></a>CDialogImpl – třída
Tato třída poskytuje metody pro vytváření modální nebo nemodální dialogového okna.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CDialogImpl`.  
  
 *TBase*  
 Základní třída nové třídy. Výchozí základní třída má [CWindow](../../atl/reference/cwindow-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Vytvoření](#create)|Vytvoří dialogového okna bez režimu.|  
|[Destroywindow –](#destroywindow)|Zničí dialogového okna bez režimu.|  
|[DoModal](#domodal)|Vytvoří modální dialogové okno.|  
|[EndDialog](#enddialog)|Zničí modální dialogové okno.|  
  
### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT metody  
  
|||  
|-|-|  
|[GetDialogProc](#getdialogproc)|Vrátí aktuální procedury dialogové okno pole.|  
|[MapDialogRect](#mapdialogrect)|Mapuje jednotky dialogového určeného obdélníku na obrazovce jednotek (v pixelech).|  
|[OnFinalMessage](#onfinalmessage)|Volá se po přijetí poslední zprávy, obvykle `WM_NCDESTROY`.|  
  
### <a name="static-functions"></a>Statické funkce  
  
|||  
|-|-|  
|[DialogProc](#dialogproc)|Zpracuje zprávy odeslané do dialogového okna.|  
|[StartDialogProc](#startdialogproc)|Volá se při přijetí první zprávu zpracovat zprávy odeslané do dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 S `CDialogImpl` můžete vytvořit modální nebo nemodální dialogové okno. `CDialogImpl`Poskytuje postup pole dialogu, který používá výchozí mapování zpráv směrovat zprávy do příslušné obslužné rutiny.  
  
 Základní třída destruktor **~ CWindowImplRoot** zajistí, že okno zmizel před zničení objektu.  
  
 `CDialogImpl`odvozená z **CDialogImplBaseT**, která je zase odvozena z **CWindowImplRoot**.  
  
> [!NOTE]
>  Musí definovat vlastní třídy **IDD** člena, který určuje ID dialogové okno šablony prostředků. Průvodce projektem ATL například automaticky přidá následující řádek na třídu:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 kde `MyDlg` je **krátký název** zadali v průvodci na **názvy** stránky.  
  
|Další informace o|Další informace naleznete v tématu|  
|--------------------------------|---------|  
|Vytváření ovládacích prvků|[ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md)|  
|Pomocí dialogových oken v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|  
|Průvodce projektem knihovny ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|  
|Dialogová okna|[Dialogová okna](http://msdn.microsoft.com/library/windows/desktop/ms632588) a dalších tématech v sadě Windows SDK|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="create"></a>CDialogImpl::Create  
 Vytvoří dialogového okna bez režimu.  
  
```  
HWND Create(
    HWND hWndParent,  
    LPARAM dwInitParam = NULL );  

HWND Create(
    HWND hWndParent,  
    RECT&, 
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [v] Popisovač okna vlastníka.  
  
 **RECT – &**`rect`  
 [v] A [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující velikost a umístění dialogovém okně.  
  
 `dwInitParam`  
 [v] Určuje hodnotu, která mají být předána do dialogového okna aplikace **lParam** parametr **WM_INITDIALOG** zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro nově vytvořený dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Toto dialogové okno se automaticky přiloží k `CDialogImpl` objektu. Chcete-li vytvořit modální dialogové okno, volejte [DoModal](#domodal). Druhý výše uvedené přepsání se používá jenom s [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>CDialogImpl::DestroyWindow  
 Zničí dialogového okna bez režimu.  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud dialogové okno byla úspěšně zničení jinak **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí **TRUE** Pokud dialogové okno byla úspěšně zničení jinak **FALSE**.  
  
##  <a name="dialogproc"></a>CDialogImpl::DialogProc  
 Tato statická funkce implementuje postup pole dialogové okno.  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač pro dialogové okno.  
  
 `uMsg`  
 [v] Zpráva odeslaná do dialogového okna.  
  
 `wParam`  
 [v] Další informace specifické pro zprávy.  
  
 `lParam`  
 [v] Další informace specifické pro zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud zpráva je zpracován; v opačném **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 `DialogProc`používá výchozí mapování zpráv směrovat zprávy do příslušné obslužné rutiny.  
  
 Můžete přepsat `DialogProc` zajistit jiný mechanismus pro zpracování zpráv.  
  
##  <a name="domodal"></a>CDialogImpl::DoModal  
 Vytvoří modální dialogové okno.  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [v] Popisovač okna vlastníka. Výchozí hodnota je vrácenou hodnotu [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) Win32 funkce.  
  
 `dwInitParam`  
 [v] Určuje hodnotu, která mají být předána do dialogového okna aplikace **lParam** parametr **WM_INITDIALOG** zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu se hodnota `nRetCode` parametr zadaný ve volání [EndDialog](#enddialog). Jinak hodnota -1.  
  
### <a name="remarks"></a>Poznámky  
 Toto dialogové okno se automaticky přiloží k `CDialogImpl` objektu.  
  
 Chcete-li vytvořit nemodální dialogové okno, volejte [vytvořit](#create).  
  
##  <a name="enddialog"></a>CDialogImpl::EndDialog  
 Zničí modální dialogové okno.  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 [v] Hodnota, která má být vrácen [CDialogImpl::DoModal](#domodal).  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud dialogové okno je zničení, jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 `EndDialog`musí být voláno prostřednictvím procesu dialogové okno. Po zničení dialogových oken, Windows používá hodnotu `nRetCode` jako návratová hodnota pro `DoModal`, který vytvořili dialogové okno.  
  
> [!NOTE]
>  Nevolejte `EndDialog` zrušení dialogového okna bez režimu. Volání [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) místo.  
  
##  <a name="getdialogproc"></a>CDialogImpl::GetDialogProc  
 Vrátí `DialogProc`, aktuální procedury dialogové okno pole.  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální procedury dialogové okno pole.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu nahradit postup dialogové okno Vlastní.  
  
##  <a name="mapdialogrect"></a>CDialogImpl::MapDialogRect  
 Převede jednotky (map) – dialogové okno jednotky zadaný rámeček na obrazovku (v pixelech).  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `CRect` objekt nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura, která je pro příjem souřadnice klienta aktualizace, která obklopuje oblasti aktualizace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud aktualizace úspěšně. 0, pokud se aktualizace nezdaří. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce nahrazuje souřadnice v zadané `RECT` struktury s převedený souřadnice, což umožňuje strukturu, který se má použít k vytvoření dialogového nebo umístit ovládacího prvku v dialogovém okně.  
  
##  <a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage  
 Volá se po přijetí poslední zprávy (obvykle `WM_NCDESTROY`).  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač pro okno bude zrušeno.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že pokud chcete automaticky odstraňovat objektu při odstraňování oken, můžete volat `delete this;` sem.  
  
##  <a name="startdialogproc"></a>CDialogImpl::StartDialogProc  
 Volat pouze jednou, když je obdržena první zprávu zpracovat zprávy odeslané do dialogového okna.  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač pro dialogové okno.  
  
 `uMsg`  
 [v] Zpráva odeslaná do dialogového okna.  
  
 `wParam`  
 [v] Další informace specifické pro zprávy.  
  
 `lParam`  
 [v] Další informace specifické pro zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Procedura okna.  
  
### <a name="remarks"></a>Poznámky  
 Po počáteční volání `StartDialogProc`, `DialogProc` není nastaven jako dialogové okno postupu a další volání tam.  
  
## <a name="see-also"></a>Viz také  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Přehled třídy](../../atl/atl-class-overview.md)