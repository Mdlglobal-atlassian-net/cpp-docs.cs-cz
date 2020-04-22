---
title: Třída CContainedWindowT
ms.date: 11/04/2016
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
helpviewer_keywords:
- CContainedWindow class
- contained windows
- CContainedWindowT class
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
ms.openlocfilehash: 7b89346bbc62cdda808b193a199fdf121f052ebb
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747743"
---
# <a name="ccontainedwindowt-class"></a>Třída CContainedWindowT

Tato třída implementuje okno obsažené v jiném objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow, class TWinTraits = CControlWinTraits>
class CContainedWindowT : public TBase
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Základní třída vaší nové třídy. Výchozí základní třída `CWindow`je .

*TWinTraits*<br/>
Třída vlastností, která definuje styly pro vaše okno. Výchozí formát je `CControlWinTraits`.

> [!NOTE]
> [CContainedWindow](ccontainedwindowt-class.md) je specializace `CContainedWindowT`. Pokud chcete změnit základní třídu nebo `CContainedWindowT` vlastnosti, použijte přímo.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CContainedWindowT::CContainedWindowT](#ccontainedwindowt)|Konstruktor Inicializuje členy dat a určí, která mapa zpráv bude zpracovávat zprávy obsaženého okna.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CContainedWindowT::Vytvořit](#create)|Vytvoří okno.|
|[CContainedWindowT::DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zpráv.|
|[CContainedWindowT::GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|
|[CContainedWindowT::RegisterWndSuperclass](#registerwndsuperclass)|Registruje třídu okna obsaženého okna.|
|[CContainedWindowT::Okno podtřídy](#subclasswindow)|Podtřídy okna.|
|[CContainedWindowT::SwitchMessageMap](#switchmessagemap)|Změny, které mapa zpráv se používá ke zpracování zprávy obsažené okno.|
|[CContainedWindowT::UnsubclassWindow CContainedWindowT::UnsubclassWindow CContainedWindowT::UnsubclassWindow CContain](#unsubclasswindow)|Obnoví dříve podtřídy okna.|
|[CContainedWindowT::WindowProc](#windowproc)|(Statické) Zpracuje zprávy odeslané do uzavřeného okna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CContainedWindowT::m_dwMsgMapID](#m_dwmsgmapid)|Určuje, které mapování zpráv bude zpracovávat zprávy obsaženého okna.|
|[CContainedWindowT::m_lpszClassName](#m_lpszclassname)|Určuje název existující třídy okna, na které bude založena nová třída okna.|
|[CContainedWindowT::m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Odkazuje na původní okno třídy okna postup.|
|[CContainedWindowT::m_pObject](#m_pobject)|Odkazuje na obsahující objekt.|

## <a name="remarks"></a>Poznámky

`CContainedWindowT`implementuje okno obsažené v jiném objektu. `CContainedWindowT`Procedura okna společnosti používá mapu zpráv v objektu obsahujícím k přesměrování zpráv příslušným obslužným rutinám. Při vytváření `CContainedWindowT` objektu určíte, která mapa zpráv má být použita.

`CContainedWindowT`umožňuje vytvořit nové okno superclassing existující třídy okna. Metoda `Create` nejprve zaregistruje třídu okna, která je `CContainedWindowT::WindowProc`založena na existující třídě, ale používá . `Create`pak vytvoří okno založené na této nové třídy okna. Každá instance `CContainedWindowT` může nadtřídit jinou třídu okna.

`CContainedWindowT`podporuje také podtřídy oken. Metoda `SubclassWindow` připojí existující okno k `CContainedWindowT` objektu a změní `CContainedWindowT::WindowProc`proceduru okna na . Každá instance `CContainedWindowT` může podtřídy jiné okno.

> [!NOTE]
> Pro daný `CContainedWindowT` objekt volejte `Create` `SubclassWindow`buď nebo . Neměli byste vyvolat obě metody na stejný objekt.

Při použití **add ovládacíprvek založený na** v Průvodci projektem ATL, průvodce automaticky přidá `CContainedWindowT` datový člen do třídy implementující ovládací prvek. Následující příklad ukazuje, jak je deklarováno uzavřené okno:

[!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/cpp/ccontainedwindowt-class_1.h)]

[!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/cpp/ccontainedwindowt-class_2.h)]

[!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/cpp/ccontainedwindowt-class_3.h)]

|Další informace o|Seznamte se s |
|--------------------------------|---------|
|Vytváření ovládacích prvků|[Kurz ATL](../../atl/active-template-library-atl-tutorial.md)|
|Použití oken v atl|[Třídy oken ATL](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Windows|[Windows](/windows/win32/winmsg/windows) a další témata v sadě Windows SDK|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`CContainedWindowT`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="ccontainedwindowtccontainedwindowt"></a><a name="ccontainedwindowt"></a>CContainedWindowT::CContainedWindowT

Konstruktor inicializuje datové členy.

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

*název lpszClassName*<br/>
[v] Název existující třídy okna, na které bude založeno obsažené okno.

*pObjekt*<br/>
[v] Ukazatel na obsahující objekt, který deklaruje mapu zprávy. Třída tohoto objektu musí být odvozena z [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[v] Identifikuje mapu zpráv, která bude zpracovávat zprávy obsaženého okna. Výchozí hodnota 0 určuje výchozí mapu zpráv deklarovanou [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Chcete-li použít alternativní mapu zpráv deklarovanou s `msgMapID` [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)předaj .

### <a name="remarks"></a>Poznámky

Pokud chcete vytvořit nové okno prostřednictvím [vytvořit](#create), musíte předat název existující třídy okna pro parametr *lpszClassName.* Příklad naleznete v [přehledu CContainedWindow.](../../atl/reference/ccontainedwindowt-class.md)

Existují tři konstruktory:

- Konstruktor se třemi argumenty je obvykle volána.

- Konstruktor se dvěma argumenty používá `TBase::GetWndClassName`název třídy z .

- Konstruktor bez argumentů se používá, pokud chcete zadat argumenty později. Při pozdějším volání `Create`je nutné zadat název třídy okna, objekt mapy zpráv a ID mapy zpráv .

Pokud podřadíte existující okno prostřednictvím [Okna podtřídy](#subclasswindow), hodnota *lpszClassName* nebude použita. proto můžete předat hodnotu NULL pro tento parametr.

## <a name="ccontainedwindowtcreate"></a><a name="create"></a>CContainedWindowT::Vytvořit

Volá [RegisterWndSuperclass](#registerwndsuperclass) zaregistrovat třídu okna, která je založena na existující třídy, ale používá [CContainedWindowT::WindowProc](#windowproc).

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

*název lpszClassName*<br/>
[v] Název existující třídy okna, na které bude založeno obsažené okno.

*pObjekt*<br/>
[v] Ukazatel na obsahující objekt, který deklaruje mapu zprávy. Třída tohoto objektu musí být odvozena z [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[v] Identifikuje mapu zpráv, která bude zpracovávat zprávy obsaženého okna. Výchozí hodnota 0 určuje výchozí mapu zpráv deklarovanou [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Chcete-li použít alternativní mapu zpráv deklarovanou s `msgMapID` [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)předaj .

*hWndParent*<br/>
[v] Popisovač do okna nadřazeného nebo vlastníka.

*Rect*<br/>
[v] A [RECT](/windows/win32/api/windef/ns-windef-rect) struktura určující umístění okna. Může `RECT` být předán ukazatelem nebo odkazem.

*szNázev_okna*<br/>
[v] Určuje název okna. Výchozí hodnota je NULL.

*dwStyl*<br/>
[v] Styl okna. Výchozí hodnota je WS_CHILD &#124; WS_VISIBLE. Seznam možných hodnot naleznete v tématu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v sadě Windows SDK.

*dwExStyl*<br/>
[v] Rozšířený styl okna. Výchozí hodnota je 0, což znamená žádný rozšířený styl. Seznam možných hodnot naleznete v tématu [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*ID nabídky*<br/>
[v] Pro podřízené okno identifikátor okna. Pro okno nejvyšší úrovně popisovač nabídky pro okno. Výchozí hodnota je **0U**.

*lpCreateParam*<br/>
[v] Ukazatel na data vytváření oken. Úplný popis naleznete v popisu konečného parametru [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač nově vytvořené okno; jinak NULL.

### <a name="remarks"></a>Poznámky

Existující název třídy okna je uložen v [m_lpszClassName](#m_lpszclassname). `Create`pak vytvoří okno založené na této nové třídy. Nově vytvořené okno je automaticky `CContainedWindowT` připojeno k objektu.

> [!NOTE]
> Nevolejte, `Create` pokud jste již [volali PodtřídyOkno](#subclasswindow).

> [!NOTE]
> Pokud 0 se používá jako hodnota pro *MenuOrID* parametr, musí být zadán jako 0U (výchozí hodnota), aby se zabránilo chybě kompilátoru.

## <a name="ccontainedwindowtdefwindowproc"></a><a name="defwindowproc"></a>CContainedWindowT::DefWindowProc

Volána [WindowProc](#windowproc) ke zpracování zpráv, které nejsou zpracovány mapy zpráv.

```
LRESULT DefWindowProc()
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
[v] Zpráva odeslaná do okna.

*wParam*<br/>
[v] Další informace specifické pro zprávu.

*Lparam*<br/>
[v] Další informace specifické pro zprávu.

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy.

### <a name="remarks"></a>Poznámky

Ve výchozím `DefWindowProc` nastavení volá [callWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 funkce odeslat informace o zprávě do okna postup zadaný v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

## <a name="ccontainedwindowtgetcurrentmessage"></a><a name="getcurrentmessage"></a>CContainedWindowT::GetCurrentMessage

Vrátí aktuální zprávu`m_pCurrentMsg`( ).

```
const _ATL_MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zpráva, zabalené ve `MSG` struktuře.

## <a name="ccontainedwindowtm_dwmsgmapid"></a><a name="m_dwmsgmapid"></a>CContainedWindowT::m_dwMsgMapID

Obsahuje identifikátor mapy zpráv, která se právě používá pro uzavřené okno.

```
DWORD m_dwMsgMapID;
```

### <a name="remarks"></a>Poznámky

Tato mapa zpráv musí být deklarována v obsahujícím objektu.

Výchozí mapa zpráv deklarovaná [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)je vždy označena nulou. Alternativní mapa zpráv deklarovaná [pomocí ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)je identifikována . `msgMapID`

`m_dwMsgMapID`je nejprve inicializován konstruktorem a lze jej změnit voláním [SwitchMessageMap](#switchmessagemap). Příklad naleznete v tématu [CContainedWindowT Overview](../../atl/reference/ccontainedwindowt-class.md).

## <a name="ccontainedwindowtm_lpszclassname"></a><a name="m_lpszclassname"></a>CContainedWindowT::m_lpszClassName

Určuje název existující třídy okna.

```
LPTSTR m_lpszClassName;
```

### <a name="remarks"></a>Poznámky

Při vytváření okna [Create registruje](#create) novou třídu okna, která je založena na této existující třídě, ale používá [CContainedWindowT::WindowProc](#windowproc).

`m_lpszClassName`je inicializován konstruktorem. Příklad naleznete v přehledu [CContainedWindowT.](../../atl/reference/ccontainedwindowt-class.md)

## <a name="ccontainedwindowtm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CContainedWindowT::m_pfnSuperWindowProc

Pokud je obsažené okno podtřídou, `m_pfnSuperWindowProc` odkazuje na původní proceduru okna třídy okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Poznámky

Pokud je uzavřené okno superclassed, což znamená, že je založena na třídě `m_pfnSuperWindowProc` okna, která upravuje existující třídu, odkazuje na proceduru okna existující třídy okna.

[Metoda DefWindowProc](#defwindowproc) odešle informace o zprávě `m_pfnSuperWindowProc`do procedury okna uložené v .

## <a name="ccontainedwindowtm_pobject"></a><a name="m_pobject"></a>CContainedWindowT::m_pObject

Odkazuje na objekt obsahující `CContainedWindowT` objekt.

```
CMessageMap* m_pObject;
```

### <a name="remarks"></a>Poznámky

Tento kontejner, jehož třída musí být odvozena z [CMessageMap](../../atl/reference/cmessagemap-class.md), deklaruje mapu zpráv používanou obsaženým oknem.

`m_pObject`je inicializován konstruktorem. Příklad naleznete v přehledu [CContainedWindowT.](../../atl/reference/ccontainedwindowt-class.md)

## <a name="ccontainedwindowtregisterwndsuperclass"></a><a name="registerwndsuperclass"></a>CContainedWindowT::RegisterWndSuperclass

Volána [Create](#create) zaregistrovat třídu okna obsažené ho okna.

```
ATOM RegisterWndSuperClass();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, atom, který jednoznačně identifikuje třídu okna, která je registrována; jinak nula.

### <a name="remarks"></a>Poznámky

Tato třída okna je založena na existující třídě, ale používá [CContainedWindowT::WindowProc](#windowproc). Název existující třídy okna a procedura okna jsou uloženy v [m_lpszClassName](#m_lpszclassname) a [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

## <a name="ccontainedwindowtsubclasswindow"></a><a name="subclasswindow"></a>CContainedWindowT::Okno podtřídy

Podtřídy okno označené *hWnd* a připojí `CContainedWindowT` jej k objektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Popisovač okna, které je podtřídy.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je okno úspěšně podtřídy; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Okno s podtřídou nyní používá [CContainedWindowT::WindowProc](#windowproc). Původní procedura okna je uložena v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> Nevolejte, `SubclassWindow` pokud jste již [volali Vytvořit](#create).

## <a name="ccontainedwindowtswitchmessagemap"></a><a name="switchmessagemap"></a>CContainedWindowT::SwitchMessageMap

Změny, které mapy zpráv budou použity ke zpracování zpráv obsaženého okna.

```cpp
void SwitchMessageMap(DWORD dwMsgMapID);
```

### <a name="parameters"></a>Parametry

*dwMsgMapID*<br/>
[v] Identifikátor mapy zprávy. Chcete-li použít výchozí mapu zpráv deklarovanou [s BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), předavažte nulu. Chcete-li použít alternativní mapu zpráv deklarovanou s `msgMapID` [ALT_MSG_MAP(msgMapID),](message-map-macros-atl.md#alt_msg_map)předaj .

### <a name="remarks"></a>Poznámky

Mapa zpráv musí být definována v obsahujícím objektu.

Nejprve zadáte identifikátor mapy zprávy v konstruktoru.

## <a name="ccontainedwindowtunsubclasswindow"></a><a name="unsubclasswindow"></a>CContainedWindowT::UnsubclassWindow CContainedWindowT::UnsubclassWindow CContainedWindowT::UnsubclassWindow CContain

Odpojí okno podtřídy od `CContainedWindowT` objektu a obnoví původní proceduru okna uloženou v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow(BOOL bForce = FALSE);
```

### <a name="parameters"></a>Parametry

*bSíla*<br/>
[v] Nastavte hodnotu TRUE, chcete-li vynutit obnovení procedury `CContainedWindowT` původního okna i v případě, že procedura okna pro tento objekt není aktuálně aktivní. Pokud *je bForce* nastavena na hodnotu FALSE a procedura okna pro tento `CContainedWindowT` objekt není aktuálně aktivní, původní procedura okna nebude obnovena.

### <a name="return-value"></a>Návratová hodnota

Popisovač okna dříve podtřídy. Pokud *je hodnota bForce* nastavena na `CContainedWindowT` hodnotu FALSE a procedura okna pro tento objekt není aktuálně aktivní, vrátí hodnotu NULL.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze v případě, že chcete obnovit původní proceduru okna před zničením okna. V opačném případě [WindowProc](#windowproc) automaticky provede, když je okno zničeno.

## <a name="ccontainedwindowtwindowproc"></a><a name="windowproc"></a>CContainedWindowT::WindowProc

Tato statická metoda implementuje proceduru okna.

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Rukojeť k oknu.

*uMsg*<br/>
[v] Zpráva odeslaná do okna.

*wParam*<br/>
[v] Další informace specifické pro zprávu.

*Lparam*<br/>
[v] Další informace specifické pro zprávu.

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy.

### <a name="remarks"></a>Poznámky

`WindowProc`přesměruje zprávy na mapu zpráv označenou [m_dwMsgMapID](#m_dwmsgmapid). V případě `WindowProc` potřeby volá [DefWindowProc](#defwindowproc) pro další zpracování zpráv.

## <a name="see-also"></a>Viz také

[Třída CWindow](../../atl/reference/cwindow-class.md)<br/>
[Třída CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Třída CMessageMap](../../atl/reference/cmessagemap-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
