---
title: Cwindowimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb99d0cb37fff5abe5a7eb54d3ba9c4226e5fd1c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197198"
---
# <a name="cwindowimpl-class"></a>Cwindowimpl – třída
Poskytuje metody pro vytváření nebo vytvoření podtřídy časového období.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```    
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše nová třída odvozena od `CWindowImpl`.  
  
 *Tčíslice*  
 Základní třída vaší třídy. Ve výchozím nastavení, základní třída je [cwindow –](../../atl/reference/cwindow-class.md).  
  
 *TWinTraits*  
 A [třída vlastností](../../atl/understanding-window-traits.md) , který definuje styly pro okno. Výchozí hodnota je `CControlWinTraits`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWindowImpl::Create](#create)|Vytvoří okno.|  
  
### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT metody  
  
|||  
|-|-|  
|[DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zpráv.|  
|[GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|  
|[GetWindowProc](#getwindowproc)|Vrátí aktuální proceduru okna.|  
|[OnFinalMessage](#onfinalmessage)|Volá se po přijetí poslední zprávy (obvykle WM_NCDESTROY).|  
|[SubclassWindow](#subclasswindow)|Podtřídy okno.|  
|[UnsubclassWindow](#unsubclasswindow)|Obnoví dříve rozčleněných do podtříd okna.|  
  
### <a name="static-methods"></a>Statické metody  
  
|||  
|-|-|  
|[GetWndClassInfo](#getwndclassinfo)|Vrátí instanci statické třídy [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md), který spravuje informace o třídě okna.|  
|[WindowProc](#windowproc)|Zpracovává zprávy odeslané do okna.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Odkazuje na třídu okna původní proceduru okna.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `CWindowImpl` k vytvoření okna nebo podtřídou existujícímu oknu. `CWindowImpl` okno postup používá mapy zpráv pro směrování zpráv do příslušné obslužné rutiny.  
  
 `CWindowImpl::Create` vytvoří okno na základě informací třídy okna, která jsou spravována [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` obsahuje [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) – makro, což znamená, že `CWndClassInfo` zaregistruje nové třídy okna. Pokud chcete supertřídě existující třídy okna, jsou odvozeny z vaší třídy `CWindowImpl` a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) – makro. V takovém případě `CWndClassInfo` zaregistruje třídu okna, která vychází z existující třídy, ale používá `CWindowImpl::WindowProc`. Příklad:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Protože `CWndClassInfo` spravuje informace o pouze jednu třídu okna, každé okno vytvořené prostřednictvím instance `CWindowImpl` je založena na stejnou třídu okna.  
  
 `CWindowImpl` podporuje také vytváření podtříd okna. `SubclassWindow` Metoda připojí k existujícímu oknu `CWindowImpl` objektu a změní proceduru okna k `CWindowImpl::WindowProc`. Každá instance `CWindowImpl` můžou podtřídy jiného okna.  
  
> [!NOTE]
>  Pro všechny uvedené `CWindowImpl` objektu, volejte buď `Create` nebo `SubclassWindow`. Není vyvolání obou metod na stejný objekt.  
  
 Kromě `CWindowImpl`, knihovna ATL poskytuje [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vytvoření okna, který je obsažen v jiném objektu.  
  
 Destruktor základní třídy (~ `CWindowImplRoot`) zajišťuje, že v okně je pryč předtím, než je objekt zničen.  
  
 `CWindowImpl` je odvozen od `CWindowImplBaseT`, která je odvozena z `CWindowImplRoot`, která je odvozena z `TBase` a [cmessagemap –](../../atl/reference/cmessagemap-class.md).  
  
|Další informace o|Další informace naleznete v tématu|  
|--------------------------------|---------|  
|Vytváření ovládacích prvků|[ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md)|  
|Pomocí systému windows v knihovně ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|  
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Cmessagemap –](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="create"></a>  CWindowImpl::Create  
 Vytvoří okno založené na nové třídě okna.  
  
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
 *hWndParent*  
 [in] Popisovač okna nadřazené nebo vlastníka.  
  
 *Rect*  
 [in] A [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující pozici okna. `RECT` Je možné předat ukazatelem nebo odkazem.  
  
 *szWindowName*  
 [in] Určuje název okna. Výchozí hodnota je NULL.  
  
 *dwStyle*  
 [in] Styl okna. Tato hodnota je kombinovat s styl poskytovaný třídou osobnostní rysy pro okno. Výchozí hodnota poskytuje jsou vlastnosti třídy plnou kontrolu nad styl. Seznam možných hodnot najdete v tématu [CreateWindow](https://msdn.microsoft.com/library/windows/desktop/ms632679) v sadě Windows SDK.  
  
 *dwExStyle*  
 [in] Styl rozšířené okna. Tato hodnota je kombinovat s styl poskytovaný třídou osobnostní rysy pro okno. Výchozí hodnota poskytuje jsou vlastnosti třídy plnou kontrolu nad styl. Seznam možných hodnot najdete v tématu [CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680) v sadě Windows SDK.  
  
 *MenuOrID*  
 [in] Pro podřízené okno identifikátor okna. Pro okno nejvyšší úrovně, nabídky popisovač okna. Výchozí hodnota je **0U**.  
  
 *lpCreateParam*  
 [in] Ukazatel na data vytvoření okna. Úplný popis naleznete v popisu pro poslední parametr [CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač do nově vytvořeného okna. V opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 `Create` nejprve zaregistruje třídu okna, pokud ho ještě není zaregistrovaný. Nově vytvořený okno je automaticky připojen k `CWindowImpl` objektu.  
  
> [!NOTE]
>  Nevolejte `Create` Pokud už jste volali [SubclassWindow](#subclasswindow).  
  
 Použití třídy okna, která je založena na existující třídy okna, jsou odvozeny z vaší třídy `CWindowImpl` a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) – makro. Proceduru okna existující třídu okna se uloží do [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Další informace najdete v tématu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Přehled.  
  
> [!NOTE]
>  Pokud se použije jako hodnota 0 *MenuOrID* parametru, musí být zadán jako 0U (výchozí hodnota), aby chybu kompilátoru.  
  
##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc  
 Volané [WindowProc](#windowproc) zpracování zpráv není zpracována v mapování zprávy.  
  
```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```  
  
### <a name="parameters"></a>Parametry  
 *uMsg*  
 [in] Zpráva odeslaná do okna.  
  
 *wParam*  
 [in] Další informace specifické pro zprávy.  
  
 *lParam*  
 [in] Další informace specifické pro zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `DefWindowProc` volání [CallWindowProc](https://msdn.microsoft.com/library/windows/desktop/ms633571) funkci Win32 k odeslání informací zprávu do okna postupem uvedeným v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
 Funkce bez parametrů automaticky načte potřebné parametry z aktuální zprávu.  
  
##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage  
 Vrátí aktuální zprávu zabalen do `MSG` struktury.  
  
```
const MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zprávu.  
  
##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc  
 Vrátí `WindowProc`, aktuální proceduru okna.  
  
```
virtual WNDPROC GetWindowProc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální proceduru okna.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem proceduru okna nahradit svojí vlastní.  
  
##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo  
 Volané [vytvořit](#create) pro přístup k informacím o třídě okna.  
  
```
static CWndClassInfo& GetWndClassInfo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Statické instance [cwndclassinfo –](../../atl/reference/cwndclassinfo-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CWindowImpl` získá prostřednictvím této metody [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra, která určuje nové třídy okna.  
  
 K nadřazené třídu existující okno odvodit třídu z `CWindowImpl` a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) – makro přepsat `GetWndClassInfo`. Další informace najdete v tématu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Přehled.  
  
 Kromě použití maker DECLARE_WND_CLASS a DECLARE_WND_SUPERCLASS, můžete přepsat `GetWndClassInfo` s vlastní implementaci.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc  
 V závislosti na okně odkazuje na jednu z následujících postupů okna.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Poznámky  
  
|Typ okna|Proceduru okna|  
|--------------------|----------------------|  
|Okno založené na nové třídy okna, zadaná pomocí [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) – makro.|[DefWindowProc](https://msdn.microsoft.com/library/windows/desktop/ms633572) funkci Win32.|  
|Okno podle třídy okna, která upravuje existující třídu, zadaná pomocí [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) – makro.|Existující třídu okna proceduru okna.|  
|Okno rozčleněných do podtříd.|Rozčleněné okno původní proceduru okna.|  
  
 [CWindowImpl::DefWindowProc](#defwindowproc) odešle zprávy informace pro proceduru okna, které jsou uloženy v `m_pfnSuperWindowProc`.  
  
##  <a name="onfinalmessage"></a>  CWindowImpl::OnFinalMessage  
 Volá se po přijetí poslední zprávy (obvykle WM_NCDESTROY).  
  
```
virtual void OnFinalMessage(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 [in] Popisovač okna zničen.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace `OnFinalMessage` nemá žádný účinek, ale můžete přepsat tuto funkci pro zpracování vyčištění před zničení časového období. Pokud chcete automaticky odstranit objekt při odstraňování oken, můžete volat **odstranit tento;** této funkce.  
  
##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow  
 Podtřídy třídy okna identifikovaný *hWnd* a připojí ho k `CWindowImpl` objektu.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 [in] Popisovač okna se rozčlenit do podtříd.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud v okně se úspěšně rozčlenit do podtříd; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Nyní používá rozčleněných do podtříd okno [CWindowImpl::WindowProc](#windowproc). Původní proceduru okna se uloží do [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  Nevolejte `SubclassWindow` Pokud už jste volali [vytvořit](#create).  
  
##  <a name="unsubclasswindow"></a>  CWindowImpl::UnsubclassWindow  
 Odpojí okno rozčleněný z `CWindowImpl` objektu a obnoví původní proceduru okna uložené v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna dříve rozčlenit do podtříd.  
  
##  <a name="windowproc"></a>  CWindowImpl::WindowProc  
 Tato statická funkce implementuje proceduru okna.  
  
```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 *hWnd*  
 [in] Popisovač okna.  
  
 *uMsg*  
 [in] Zpráva odeslaná do okna.  
  
 *wParam*  
 [in] Další informace specifické pro zprávy.  
  
 *lParam*  
 [in] Další informace specifické pro zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek zpracování zprávy.  
  
### <a name="remarks"></a>Poznámky  
 `WindowProc` používá výchozí mapování zpráv (deklarované pomocí [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) ke směrování zpráv do příslušné obslužné rutiny. V případě potřeby `WindowProc` volání [DefWindowProc](#defwindowproc) pro zpracování další zprávy. Pokud se závěrečná zpráva není zpracována, `WindowProc` provede následující akce:  
  
-   Provádí unsubclassing, pokud byl unsubclassed okna.  
  
-   Vymaže `m_hWnd`.  
  
-   Volání [OnFinalMessage](#onfinalmessage) zničen okna.  
  
 Můžete přepsat `WindowProc` jiný mechanismus pro zpracování zpráv.  
  
## <a name="see-also"></a>Viz také  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Ccomcontrol – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
