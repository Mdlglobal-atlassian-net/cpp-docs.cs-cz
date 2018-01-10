---
title: "Třída CWindowImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::DefWindowProc
- ATLWIN/ATL::GetCurrentMessage
- ATLWIN/ATL::GetWindowProc
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::SubclassWindow
- ATLWIN/ATL::UnsubclassWindow
- ATLWIN/ATL::GetWndClassInfo
- ATLWIN/ATL::WindowProc
- ATLWIN/ATL::m_pfnSuperWindowProc
dev_langs: C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3aa14c3ae6c083cbf440d8b5b94fcb3754bd6fff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cwindowimpl-class"></a>CWindowImpl – třída
Poskytuje metody pro vytvoření nebo vytvoření podtřídy časového období.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Svou novou třídu odvozenou z `CWindowImpl`.  
  
 *TBase*  
 Základní třída třídě. Ve výchozím nastavení, je základní třída [CWindow](../../atl/reference/cwindow-class.md).  
  
 `TWinTraits`  
 A [vlastnosti třídy](../../atl/understanding-window-traits.md) , který definuje styly pro okno. Výchozí hodnota je `CControlWinTraits`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWindowImpl::Create](#create)|Vytvoří okno.|  
  
### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT metody  
  
|||  
|-|-|  
|[DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zprávy.|  
|[GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|  
|[GetWindowProc](#getwindowproc)|Vrátí aktuální procedury okna.|  
|[OnFinalMessage](#onfinalmessage)|Volá se po přijetí poslední zprávy (obvykle `WM_NCDESTROY`).|  
|[SubclassWindow](#subclasswindow)|Podtřídy a okna.|  
|[UnsubclassWindow](#unsubclasswindow)|Obnoví dříve rozčleněné okna.|  
  
### <a name="static-methods"></a>Statické metody  
  
|||  
|-|-|  
|[GetWndClassInfo](#getwndclassinfo)|Vrátí statický instanci [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), který spravuje informace o třídě okno.|  
|[WindowProc](#windowproc)|Zpracuje zprávy odeslané do okna.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Body procedury okna původní třídu okna.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `CWindowImpl` k vytvoření okna nebo podtřídou existující okna. `CWindowImpl` okno postup používá mapy zpráv pro přesměrování zprávy do příslušné obslužné rutiny.  
  
 `CWindowImpl::Create`vytvoří okno založené na informace o třídě okna, který je spravovaný nástrojem [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl`obsahuje [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makro, což znamená `CWndClassInfo` zaregistruje novou třídu okna. Pokud chcete supertřídě existující třídy oken, odvozena třídě z `CWindowImpl` a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro. V takovém případě `CWndClassInfo` zaregistruje okno třídu, která je založená na existující třídy, ale používá `CWindowImpl::WindowProc`. Příklad:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Protože `CWndClassInfo` spravuje informace třídy oken s jedním, každý okna vytvořeného prostřednictvím instance `CWindowImpl` je založena na stejnou třídu oken.  
  
 `CWindowImpl`také podporuje vytváření podtříd okno. `SubclassWindow` Metoda připojí existující okna `CWindowImpl` objektu a změní okno postup `CWindowImpl::WindowProc`. Každá instance `CWindowImpl` můžete podtřídami jiné časové období.  
  
> [!NOTE]
>  Pro všechny zadané `CWindowImpl` objektu, buď volání **vytvořit** nebo `SubclassWindow`. Nemáte vyvolání obě metody na stejný objekt.  
  
 Kromě `CWindowImpl`, poskytuje ATL [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vytvořit okno, které se nachází v jiném objektu.  
  
 Základní třída destruktor (~ **CWindowImplRoot**) zajišťuje, že okno pryč zničen objekt.  
  
 `CWindowImpl`odvozená z **CWindowImplBaseT**, která je odvozena z **CWindowImplRoot**, která je odvozena z **TBase** a [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
|Další informace o|Další informace naleznete v tématu|  
|--------------------------------|---------|  
|Vytváření ovládacích prvků|[ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md)|  
|Pomocí systému windows v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|  
|Průvodce projektem knihovny ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="create"></a>CWindowImpl::Create  
 Vytvoří okno založeno na třídě nové okno.  
  
```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [v] Popisovač okna nadřazené nebo vlastníka.  
  
 `rect`  
 [v] A [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující pozici okna. `RECT` Lze předat ukazatel nebo odkazem.  
  
 `szWindowName`  
 [v] Určuje název okna. Výchozí hodnota je **NULL**.  
  
 `dwStyle`  
 [v] Styl okna. Tato hodnota je kombinovat s styl poskytované vlastnosti třídy pro okno. Výchozí hodnota poskytuje jsou vlastnosti třídy plnou kontrolu nad styl. Seznam možných hodnot najdete v tématu [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK.  
  
 `dwExStyle`  
 [v] Styl delší okno. Tato hodnota je kombinovat s styl poskytované vlastnosti třídy pro okno. Výchozí hodnota poskytuje jsou vlastnosti třídy plnou kontrolu nad styl. Seznam možných hodnot najdete v tématu [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `MenuOrID`  
 [v] Pro podřízeného okna identifikátor okno. Pro nejvyšší úrovně okno popisovač nabídky pro okno. Výchozí hodnota je **0U**.  
  
 `lpCreateParam`  
 [v] Ukazatel na vytvoření oken data. Úplný popis naleznete v popisu pro parametr konečné [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač okna nově vytvořený. V opačném **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 **Vytvoření** poprvé registruje třídu oken, pokud ho ještě není zaregistrovaný. Nově vytvořený okna se automaticky přiloží k `CWindowImpl` objektu.  
  
> [!NOTE]
>  Nevolejte **vytvořit** Pokud již máte volána [SubclassWindow](#subclasswindow).  
  
 Pokud chcete použít okno třídu, která je založena na existující třídy oken, odvozena třídě z `CWindowImpl` a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro. Existující třída okna okno postup je uložen v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Další informace najdete v tématu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Přehled.  
  
> [!NOTE]
>  Pokud se používá jako hodnota 0 `MenuOrID` parametr, musí být zadán jako 0U (výchozí hodnota) aby se zabránilo chybě kompilátoru.  
  
##  <a name="defwindowproc"></a>CWindowImpl::DefWindowProc  
 Voláno rozhraním [WindowProc](#windowproc) zpracování zpráv není zpracována mapy zpráv.  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```  
  
### <a name="parameters"></a>Parametry  
 `uMsg`  
 [v] Zpráva odeslaná do okna.  
  
 `wParam`  
 [v] Další informace specifické pro zprávy.  
  
 `lParam`  
 [v] Další informace specifické pro zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `DefWindowProc` volání [CallWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633571) funkce Win32 k odeslání zprávy informací do okna postupem uvedeným v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
 Funkci bez parametrů automaticky načte potřebné parametry z aktuální zprávu.  
  
##  <a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage  
 Vrátí aktuální zprávu, součástí `MSG` struktura.  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zprávu.  
  
##  <a name="getwindowproc"></a>CWindowImpl::GetWindowProc  
 Vrátí `WindowProc`, aktuální procedury okna.  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální procedury okna.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu nahradit vlastní procedury okna.  
  
##  <a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo  
 Voláno rozhraním [vytvořit](#create) pro přístup k informacím třída okno.  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Statické instanci [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CWindowImpl` obdrží tato metoda prostřednictvím [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makro, který určuje třídu nové okno.  
  
 K supertřídě existující třídy oken, odvozena třídě z `CWindowImpl` a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro přepsat `GetWndClassInfo`. Další informace najdete v tématu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Přehled.  
  
 Kromě použití `DECLARE_WND_CLASS` a `DECLARE_WND_SUPERCLASS` makra, můžete přepsat `GetWndClassInfo` s vlastní implementaci.  
  
##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc  
 V závislosti na okno odkazuje na jednu z následujících postupů interval.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Poznámky  
  
|Typ okna|Procedury oken|  
|--------------------|----------------------|  
|Okno podle novou třídu okno zadaná pomocí [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makro.|[DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572) Win32 funkce.|  
|Okno podle okno třídu, která upraví stávající třídě, zadaná pomocí [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro.|Procedura okno existující třídy oken.|  
|Rozčleněné okno.|Rozčleněné okno původní procedury okna.|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc) zasílá zprávu informace k postupu okno Uložit v `m_pfnSuperWindowProc`.  
  
##  <a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage  
 Volá se po přijetí poslední zprávy (obvykle `WM_NCDESTROY`).  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač pro okno bude zrušeno.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementaci `OnFinalMessage` nic neprovádí, ale můžete přepsat tuto funkci pro zpracování čištění před likvidace okna. Pokud chcete automaticky odstraňovat objektu při odstraňování oken, můžete volat `delete this;` této funkce.  
  
##  <a name="subclasswindow"></a>CWindowImpl::SubclassWindow  
 Podtřídy okno identifikovaný `hWnd` a připojí jej k `CWindowImpl` objektu.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač okna se rozčlenění.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je okno úspěšně rozčleněné; v opačném **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Rozčleněné okno teď používá [CWindowImpl::WindowProc](#windowproc). Původní procedury okna je uložen v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  Nevolejte `SubclassWindow` Pokud již máte volána [vytvořit](#create).  
  
##  <a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow  
 Odpojí okno rozčleněné od `CWindowImpl` objektu a obnoví původní procedury okna Uložit v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna dříve rozčlenění.  
  
##  <a name="windowproc"></a>CWindowImpl::WindowProc  
 Tato statická funkce implementuje proceduru okna.  
  
```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač okna.  
  
 `uMsg`  
 [v] Zpráva odeslaná do okna.  
  
 `wParam`  
 [v] Další informace specifické pro zprávy.  
  
 `lParam`  
 [v] Další informace specifické pro zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy.  
  
### <a name="remarks"></a>Poznámky  
 `WindowProc`používá výchozí mapování zpráv (deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) směrovat zprávy do příslušné obslužné rutiny. V případě potřeby `WindowProc` volání [DefWindowProc](#defwindowproc) pro zpracování další zprávy. Pokud nejsou zpracovávány poslední zprávy, `WindowProc` provede následující akce:  
  
-   Provede unsubclassing, pokud byl unsubclassed okna.  
  
-   Vymaže `m_hWnd`.  
  
-   Volání [OnFinalMessage](#onfinalmessage) zničen okna.  
  
 Můžete přepsat `WindowProc` zajistit jiný mechanismus pro zpracování zpráv.  
  
## <a name="see-also"></a>Viz také  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
