---
title: "Třída CAxDialogImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
dev_langs:
- C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2db97c0de9f262936212cf7f38abddf7c91eb5a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl – třída
Tato třída implementuje dialogové okno (modální nebo nemodální), který je hostitelem – ovládací prvky ActiveX.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CAxDialogImpl`.  
  
 *TBase*  
 Okno základní třídu pro **CDialogImplBaseT**.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Volejte tuto metodu za účelem poradit nebo unadvise všechny položky v mapa událostí mapy jímek objektu.|  
|[CAxDialogImpl::Create](#create)|Volejte tuto metodu za účelem vytvoření dialogového okna bez režimu.|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Volejte tuto metodu zrušení dialogového okna bez režimu.|  
|[CAxDialogImpl::DoModal](#domodal)|Volejte tuto metodu za účelem modální dialogové okno vytvořit.|  
|[CAxDialogImpl::EndDialog](#enddialog)|Volejte tuto metodu zrušení modální dialogové okno.|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Volat tuto metodu za účelem získání ukazatel `DialogProc` funkce zpětného volání.|  
|[CAxDialogImpl::GetIDD](#getidd)|Volat tuto metodu za účelem získání ID prostředku šablony dialogu|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Voláním této metody lze určit, zda zpráva je určený pro toto dialogové okno a pokud se jedná, zpracování zprávy.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|Proměnné, která existuje pouze v ladění sestavení a je nastavený na hodnotu true, pokud je modální dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 `CAxDialogImpl`Umožňuje vytvořit modální nebo nemodální dialogové okno. `CAxDialogImpl`Poskytuje postup pole dialogu, který používá výchozí mapování zpráv směrovat zprávy do příslušné obslužné rutiny.  
  
 `CAxDialogImpl`odvozená z `CDialogImplBaseT`, která je zase odvozena z *TBase* (ve výchozím nastavení, `CWindow`) a `CMessageMap`.  
  
 Třídě musí definovat člena IDD, který určuje ID dialogové okno šablony prostředků. Například přidání ATL Dialog objekt pomocí **přidat třídu** dialogové okno automaticky přidá následující řádek na třídu:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 kde `MyDialog` je **krátký název** zadali v Průvodci ATL dialogové okno.  
  
 V tématu [implementace dialogové okno](../../atl/implementing-a-dialog-box.md) Další informace.  
  
 Všimněte si, že ovládacího prvku ActiveX ve modální dialogové okno vytvořit s `CAxDialogImpl` nebude podporovat klávesy akcelerátoru. Pro podporu klávesy akcelerátoru v dialogovém okně Vytvořit s `CAxDialogImpl`, nemodální dialogové okno vytvořit a pomocí vlastní zpráva smyčky, používat [CAxDialogImpl::IsDialogMessage](#isdialogmessage) po získání zprávu z fronty pro zpracování klávesa akcelerátoru.  
  
 Další informace o `CAxDialogImpl`, najdete v části [ATL řízení členství ve skupině – nejčastější dotazy](../../atl/atl-control-containment-faq.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap  
 Volejte tuto metodu za účelem poradit nebo unadvise všechny položky v mapa událostí mapy jímek objektu.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 `bAdvise`  
 Nastavte na hodnotu true, pokud všechny položky jímka mají být doporučila; položky false, pokud všechny jímka mají být unadvised.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
##  <a name="create"></a>CAxDialogImpl::Create  
 Volejte tuto metodu za účelem vytvoření dialogového okna bez režimu.  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [v] Popisovač okna vlastníka.  
  
 `dwInitParam`  
 [v] Určuje hodnotu, která mají být předána do dialogového okna aplikace `lParam` parametr **WM_INITDIALOG** zprávy.  
  
 **RECT – &**  
 Tento parametr není používán. Tento parametr se předává v `CComControl`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro nově vytvořený dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Toto dialogové okno se automaticky přiloží k `CAxDialogImpl` objektu. Chcete-li vytvořit modální dialogové okno, volejte [DoModal](#domodal).  
  
 Druhý přepsání je k dispozici pouze v proto, že dialogová okna lze použít s [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>CAxDialogImpl::DestroyWindow  
 Volejte tuto metodu zrušení dialogového okna bez režimu.  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud okno úspěšně zničeno; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte `DestroyWindow` zrušení modální dialogové okno. Volání [EndDialog](#enddialog) místo.  
  
##  <a name="domodal"></a>CAxDialogImpl::DoModal  
 Volejte tuto metodu za účelem modální dialogové okno vytvořit.  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [v] Popisovač okna vlastníka. Výchozí hodnota je vrácenou hodnotu [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) Win32 funkce.  
  
 `dwInitParam`  
 [v] Určuje hodnotu, která mají být předána do dialogového okna aplikace `lParam` parametr **WM_INITDIALOG** zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu se hodnota `nRetCode` parametr zadaný ve volání [EndDialog](#enddialog), jinak hodnota -1.  
  
### <a name="remarks"></a>Poznámky  
 Toto dialogové okno se automaticky přiloží k `CAxDialogImpl` objektu.  
  
 Chcete-li vytvořit nemodální dialogové okno, volejte [vytvořit](#create).  
  
##  <a name="enddialog"></a>CAxDialogImpl::EndDialog  
 Volejte tuto metodu zrušení modální dialogové okno.  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 [v] Hodnota, která má být vrácen [DoModal](#domodal).  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je zničení dialogových oken; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 `EndDialog`musí být voláno prostřednictvím procesu dialogové okno pole. Po zničení dialogových oken, Windows používá hodnotu `nRetCode` jako návratová hodnota pro `DoModal`, který vytvořili dialogové okno.  
  
> [!NOTE]
>  Nevolejte `EndDialog` zrušení dialogového okna bez režimu. Volání [destroywindow –](#destroywindow) místo.  
  
##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc  
 Volat tuto metodu za účelem získání ukazatel `DialogProc` funkce zpětného volání.  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel `DialogProc` funkce zpětného volání.  
  
### <a name="remarks"></a>Poznámky  
 `DialogProc` Funkce je funkce zpětného volání definované aplikací.  
  
##  <a name="getidd"></a>CAxDialogImpl::GetIDD  
 Volat tuto metodu za účelem získání ID dialogové okno šablony prostředků.  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ID dialogové okno šablony prostředků.  
  
##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage  
 Voláním této metody lze určit, zda zpráva je určený pro toto dialogové okno a pokud se jedná, zpracování zprávy.  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Ukazatel na [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) struktura, která obsahuje zpráva, která má být zaškrtnuto.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud zpráva byl zpracován, FALSE, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je určena k volání přímo z ve smyčce zpráv.  
  
##  <a name="m_bmodal"></a>CAxDialogImpl::m_bModal  
 Proměnné, která existuje pouze v ladění sestavení a je nastavený na hodnotu true, pokud je modální dialogové okno.  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>Viz také  
 [CDialogImpl – třída](../../atl/reference/cdialogimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
