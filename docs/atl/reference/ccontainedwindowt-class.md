---
title: Třída CContainedWindowT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CContainedWindowT
- ATLWIN/ATL::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::CContainedWindowT
- ATLWIN/ATL::CContainedWindowT::Create
- ATLWIN/ATL::CContainedWindowT::DefWindowProc
- ATLWIN/ATL::CContainedWindowT::GetCurrentMessage
- ATLWIN/ATL::CContainedWindowT::RegisterWndSuperclass
- ATLWIN/ATL::CContainedWindowT::SubclassWindow
- ATLWIN/ATL::CContainedWindowT::SwitchMessageMap
- ATLWIN/ATL::CContainedWindowT::UnsubclassWindow
- ATLWIN/ATL::CContainedWindowT::WindowProc
- ATLWIN/ATL::CContainedWindowT::m_dwMsgMapID
- ATLWIN/ATL::CContainedWindowT::m_lpszClassName
- ATLWIN/ATL::CContainedWindowT::m_pfnSuperWindowProc
- ATLWIN/ATL::CContainedWindowT::m_pObject
dev_langs:
- C++
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f3f90e23eed3bd1eba80bbf90fe73de45eb7cfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366481"
---
# <a name="ccontainedwindowt-class"></a>CContainedWindowT – třída
Tato třída implementuje okno obsažené v rámci jiného objektu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>  
class CContainedWindowT : public TBase
```  
  
#### <a name="parameters"></a>Parametry  
 *TBase*  
 Základní třída nové třídy. Výchozí základní třída má `CWindow`.  
  
 `TWinTraits`  
 Vlastnosti třídy, která definuje styly pro okno. Výchozí hodnota je `CControlWinTraits`.  
  
> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) je specializované `CContainedWindowT`. Pokud chcete změnit základní třídu nebo vlastnosti, použijte `CContainedWindowT` přímo.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor Inicializuje datových členů k určení, které mapy zpráv zpracuje zprávy obsažené oken.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CContainedWindowT::Create](#create)|Vytvoří okno.|  
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zprávy.|  
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|  
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Zaregistruje třídu oken okna obsažené.|  
|[CContainedWindowT::SubclassWindow](#subclasswindow)|Podtřídy a okna.|  
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Změny, které mapy zpráv se používá ke zpracování zprávy obsažené oken.|  
|[CContainedWindowT::UnsubclassWindow](#unsubclasswindow)|Obnoví dříve rozčleněné okna.|  
|[CContainedWindowT::WindowProc](#windowproc)|(Statické) Zpracuje zprávy odeslané do okna obsažené.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Určuje, které mapy zpráv zpracuje zprávy obsažené oken.|  
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Určuje název existující třídy okno na kterém bude na základě novou třídu okna.|  
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Body procedury okna původní třídu okna.|  
|[CContainedWindowT::m_pObject](#m_pobject)|Odkazuje na objekt obsahující.|  
  
## <a name="remarks"></a>Poznámky  
 `CContainedWindowT` implementuje okno obsažené v rámci jiného objektu. `CContainedWindowT`je okno postup používá mapování zprávu obsahující objektu na přímé zprávy do příslušné obslužné rutiny. Při vytváření `CContainedWindowT` objekt, můžete zadat, které mapy zpráv má být použita.  
  
 `CContainedWindowT` Umožňuje vytvořit nové okno vytváření supertříd existující třídy oken. **Vytvořit** metoda registruje první okno třídu, která je založená na existující třídy, ale používá `CContainedWindowT::WindowProc`. **Vytvoření** poté vytvoří okno založené na tato nová třída okno. Každá instance `CContainedWindowT` můžete supertřídě třídu jiné časové období.  
  
 `CContainedWindowT` také podporuje vytváření podtříd okno. `SubclassWindow` Metoda připojí existující okna `CContainedWindowT` objektu a změní okno postup `CContainedWindowT::WindowProc`. Každá instance `CContainedWindowT` můžete podtřídami jiné časové období.  
  
> [!NOTE]
>  Pro všechny zadané `CContainedWindowT` objektu, buď volání **vytvořit** nebo `SubclassWindow`. Obě metody na stejný objekt nesmí vyvolat.  
  
 Při použití **přidání ovládacího prvku na základě** možnost v Průvodci projektu knihovny ATL průvodce automaticky přidá `CContainedWindowT` – datový člen třídy implementující ovládacího prvku. Následující příklad ukazuje, jak je deklarovaná okno omezením:  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]  
  
|Další informace o|Další informace naleznete v tématu|  
|--------------------------------|---------|  
|Vytváření ovládacích prvků|[ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md)|  
|Pomocí systému windows v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|  
|Průvodce projektem knihovny ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|  
|Windows|[Windows](http://msdn.microsoft.com/library/windows/desktop/ms632595) a dalších tématech v sadě Windows SDK|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `TBase`  
  
 `CContainedWindowT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="ccontainedwindowt"></a>  CContainedWindowT::CContainedWindowT  
 Konstruktor inicializuje datových členů.  
  
```
CContainedWindowT(
    LPTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);

CContainedWindowT(
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0)
    CContainedWindowT();
```     
  
### <a name="parameters"></a>Parametry  
 `lpszClassName`  
 [v] Název existující třídy okno na kterém bude na základě okno obsažené.  
  
 `pObject`  
 [v] Ukazatel na objekt obsahující, který deklaruje mapy zpráv. Tento objekt třídy musí být odvozeny od [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [v] Identifikuje mapy zpráv, která zpracuje zprávy obsažené oken. Výchozí hodnota 0, určuje výchozí mapování zpráv deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Použít alternativní zpráva mapování deklarovat s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předat `msgMapID`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit nové okno prostřednictvím [vytvořit](#create), je nutné předat název existující třídy okna pro `lpszClassName` parametr. Příklad, naleznete v části [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) Přehled.  
  
 Existují tři konstruktory:  
  
-   Konstruktor s tři argumenty se obvykle nazývá.  
  
-   Konstruktor s dva argumenty používá název třídy z **TBase::GetWndClassName**.  
  
-   Pokud chcete zadat argumenty později, použije se konstruktor bez argumentů. Pokud později zavoláte musíte zadat název třídy oken, objekt map zpráv a mapy ID zprávy **vytvořit**.  
  
 Pokud podtřídami existujícího okna prostřednictvím [SubclassWindow](#subclasswindow), `lpszClassName` nebude použita hodnota; proto můžete předat **NULL** tohoto parametru.  
  
##  <a name="create"></a>  CContainedWindowT::Create  
 Volání [RegisterWndSuperclass](#registerwndsuperclass) k registraci okno třídu, která je založená na existující třídy, ale používá [CContainedWindowT::WindowProc](#windowproc).  
  
```
HWND Create(  
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);

HWND Create(
    LPCTSTR lpszClassName,
    CMessageMap* pObject,
    DWORD dwMsgMapID,
    HWND hWndParent,
    _U_RECT rect,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClassName`  
 [v] Název existující třídy okno na kterém bude na základě okno obsažené.  
  
 `pObject`  
 [v] Ukazatel na objekt obsahující, který deklaruje mapy zpráv. Tento objekt třídy musí být odvozeny od [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
 `dwMsgMapID`  
 [v] Identifikuje mapy zpráv, která zpracuje zprávy obsažené oken. Výchozí hodnota 0, určuje výchozí mapování zpráv deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Použít alternativní zpráva mapování deklarovat s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předat `msgMapID`.  
  
 `hWndParent`  
 [v] Popisovač okna nadřazené nebo vlastníka.  
  
 `rect`  
 [v] A [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující pozici okna. `RECT` Lze předat ukazatel nebo odkazem.  
  
 `szWindowName`  
 [v] Určuje název okna. Výchozí hodnota je **NULL**.  
  
 `dwStyle`  
 [v] Styl okna. Výchozí hodnota je **ws_child – &#124; ws_visible –**. Seznam možných hodnot najdete v tématu [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK.  
  
 `dwExStyle`  
 [v] Styl delší okno. Výchozí hodnota je 0 – žádný rozšířené styl. Seznam možných hodnot najdete v tématu [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `MenuOrID`  
 [v] Pro podřízeného okna identifikátor okno. Pro nejvyšší úrovně okno popisovač nabídky pro okno. Výchozí hodnota je **0U**.  
  
 `lpCreateParam`  
 [v] Ukazatel na vytvoření oken data. Úplný popis naleznete v popisu pro parametr konečné [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu popisovač okna nově vytvořený; v opačném **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Název existující třídy okna je uložen v [m_lpszClassName](#m_lpszclassname). **Vytvoření** poté vytvoří okno založené na tato nová třída. Nově vytvořený okna se automaticky přiloží k `CContainedWindowT` objektu.  
  
> [!NOTE]
>  Nevolejte **vytvořit** Pokud již máte volána [SubclassWindow](#subclasswindow).  
  
> [!NOTE]
>  Pokud se používá jako hodnota 0 `MenuOrID` parametr, musí být zadán jako 0U (výchozí hodnota) aby se zabránilo chybě kompilátoru.  
  
##  <a name="defwindowproc"></a>  CContainedWindowT::DefWindowProc  
 Voláno rozhraním [WindowProc](#windowproc) zpracování zpráv není zpracována mapy zpráv.  
  
```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
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
  
##  <a name="getcurrentmessage"></a>  CContainedWindowT::GetCurrentMessage  
 Vrátí aktuální zprávu ( **m_pCurrentMsg**).  
  
```
const _ATL_MSG* GetCurrentMessage();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zprávu, součástí `MSG` struktura.  
  
##  <a name="m_dwmsgmapid"></a>  CContainedWindowT::m_dwMsgMapID  
 Obsahuje identifikátor mapy zpráv, které jsou právě používány pro okno obsažené.  
  
```
DWORD m_dwMsgMapID;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato zpráva mapa musí být deklarován v obsahující objektu.  
  
 Mapa zpráv výchozí deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), je vždy identifikována nula. Mapování zpráv alternativní deklarovat s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), je identifikovaný `msgMapID`.  
  
 `m_dwMsgMapID` Nejprve se inicializuje pomocí konstruktoru a může být změněn voláním [SwitchMessageMap](#switchmessagemap). Příklad, naleznete v části [CContainedWindowT přehled](../../atl/reference/ccontainedwindowt-class.md).  
  
##  <a name="m_lpszclassname"></a>  CContainedWindowT::m_lpszClassName  
 Určuje název existující třídy oken.  
  
```
LPTSTR m_lpszClassName;
```  
  
### <a name="remarks"></a>Poznámky  
 Při vytváření okna, [vytvořit](#create) zaregistruje novou třídu okna, která je založená na existující třída ale používá [CContainedWindowT::WindowProc](#windowproc).  
  
 `m_lpszClassName` se inicializuje pomocí konstruktoru. Příklad, naleznete v části [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) Přehled.  
  
##  <a name="m_pfnsuperwindowproc"></a>  CContainedWindowT::m_pfnSuperWindowProc  
 Pokud okno obsažené podtřídou, `m_pfnSuperWindowProc` odkazuje na původní procedury okna okno třídy.  
  
```
WNDPROC m_pfnSuperWindowProc;
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je okno obsažené superclassed, znamená ho pracuje na okno třídu, která upraví stávající třídě, `m_pfnSuperWindowProc` body procedury okna existující třídy oken.  
  
 [DefWindowProc](#defwindowproc) metoda odesílá informace zprávy procedury okna Uložit v `m_pfnSuperWindowProc`.  
  
##  <a name="m_pobject"></a>  CContainedWindowT::m_pObject  
 Odkazuje na objekt obsahující `CContainedWindowT` objektu.  
  
```
CMessageMap* m_pObject;
```  
  
### <a name="remarks"></a>Poznámky  
 Tento kontejner, jehož třída musí být odvozeny od [CMessageMap](../../atl/reference/cmessagemap-class.md), deklaruje mapy zpráv používané okno obsažené.  
  
 `m_pObject` se inicializuje pomocí konstruktoru. Příklad, naleznete v části [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md) Přehled.  
  
##  <a name="registerwndsuperclass"></a>  CContainedWindowT::RegisterWndSuperclass  
 Voláno rozhraním [vytvořit](#create) registrace třídy okna okna obsažené.  
  
```
ATOM RegisterWndSuperClass();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného atom který jednoznačně identifikuje třídu oken registrované; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Tato třída okno je založená na existující třídy, ale používá [CContainedWindowT::WindowProc](#windowproc). Existující třída okna okno a název procedury jsou uloženy ve [m_lpszClassName](#m_lpszclassname) a [m_pfnSuperWindowProc](#m_pfnsuperwindowproc), v uvedeném pořadí.  
  
##  <a name="subclasswindow"></a>  CContainedWindowT::SubclassWindow  
 Podtřídy okno identifikovaný `hWnd` a připojí jej k `CContainedWindowT` objektu.  
  
```
BOOL SubclassWindow(HWND hWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [v] Popisovač okna se rozčlenění.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je okno úspěšně rozčleněné; v opačném **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Rozčleněné okno teď používá [CContainedWindowT::WindowProc](#windowproc). Původní procedury okna je uložen v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
> [!NOTE]
>  Nevolejte `SubclassWindow` Pokud již máte volána [vytvořit](#create).  
  
##  <a name="switchmessagemap"></a>  CContainedWindowT::SwitchMessageMap  
 Změny, které mapy zpráv se používá ke zpracování zprávy obsažené oken.  
  
```
void SwitchMessageMap(DWORD dwMsgMapID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwMsgMapID`  
 [v] Identifikátor mapy zpráv. Chcete-li použít výchozí mapování zpráv deklarovat s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), předat nula. Použít alternativní zpráva mapování deklarovat s [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), předat `msgMapID`.  
  
### <a name="remarks"></a>Poznámky  
 Mapy zpráv musí být definován v obsahující objektu.  
  
 Nejdřív zadejte identifikátor mapy zpráv v konstruktoru.  
  
##  <a name="unsubclasswindow"></a>  CContainedWindowT::UnsubclassWindow  
 Odpojí okno rozčleněné od `CContainedWindowT` objektu a obnoví původní procedury okna Uložit v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).  
  
```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bForce`  
 [v] Nastavte na **TRUE** vynutit původní okno postup obnovit i v případě okno postup `CContainedWindowT` objekt není aktuálně aktivní. Pokud `bForce` je nastaven na **FALSE** a postup okno `CContainedWindowT` objekt není aktuálně aktivní, původní procedury okna neobnoví.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna dříve rozčlenění. Pokud `bForce` je nastaven na **FALSE** a postup okno `CContainedWindowT` objekt není aktuálně aktivní, vrátí **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pouze v případě, že chcete obnovit původní procedury okna zničen okna. V opačném [WindowProc](#windowproc) automaticky a to při okno zničena.  
  
##  <a name="windowproc"></a>  CContainedWindowT::WindowProc  
 Tato metoda statické implementuje proceduru okna.  
  
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
 `WindowProc` přesměruje zprávy a pokuste se identifikovanou pomocí mapy zpráv [m_dwMsgMapID](#m_dwmsgmapid). V případě potřeby `WindowProc` volání [DefWindowProc](#defwindowproc) pro zpracování další zprávy.  
  
## <a name="see-also"></a>Viz také  
 [CWindow – třída](../../atl/reference/cwindow-class.md)   
 [CWindowImpl – třída](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap – třída](../../atl/reference/cmessagemap-class.md)   
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)   
 [Přehled třídy](../../atl/atl-class-overview.md)
