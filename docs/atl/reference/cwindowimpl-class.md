---
title: CWindowImpl – třída
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862961"
---
# <a name="cwindowimpl-class"></a>CWindowImpl – třída

Poskytuje metody pro vytváření nebo roztřídění okna.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše nová třída odvozená z `CWindowImpl`.

*TBase*<br/>
Základní třída vaší třídy. Ve výchozím nastavení je základní třída [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
[Třída vlastností](../../atl/understanding-window-traits.md) , která definuje styly pro vaše okno. Výchozí formát je `CControlWinTraits`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWindowImpl:: Create](#create)|Vytvoří okno.|

### <a name="cwindowimplbaset-methods"></a>Metody CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zpráv.|
|[GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|
|[GetWindowProc](#getwindowproc)|Vrátí aktuální proceduru okna.|
|[OnFinalMessage](#onfinalmessage)|Volá se po přijetí poslední zprávy (obvykle WM_NCDESTROY).|
|[SubclassWindow](#subclasswindow)|Podtřídí okno.|
|[UnsubclassWindow](#unsubclasswindow)|Obnoví dříve podtřídované okno.|

### <a name="static-methods"></a>Statické metody

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Vrátí statickou instanci třídy [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), která spravuje informace o třídě okna.|
|[WindowProc](#windowproc)|Zpracuje zprávy odesílané do okna.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Odkazuje na původní proceduru okna třídy okna.|

## <a name="remarks"></a>Poznámky

Pomocí `CWindowImpl` můžete vytvořit okno nebo podtřídu existující okno. procedura okna `CWindowImpl` používá mapu zpráv k přímému směrování zpráv do příslušných obslužných rutin.

`CWindowImpl::Create` vytvoří okno na základě informací o třídě okna spravovaném pomocí [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl` obsahuje makro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , což znamená, že `CWndClassInfo` zaregistruje novou třídu okna. Chcete-li použít supertřídy existující třídy okna, odvodit třídu z `CWindowImpl` a zahrnout makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . V tomto případě `CWndClassInfo` zaregistruje třídu okna, která je založena na stávající třídě, ale používá `CWindowImpl::WindowProc`. Příklad:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  Protože `CWndClassInfo` spravuje informace pouze pro jednu třídu okna, každé okno vytvořené prostřednictvím instance `CWindowImpl` je založeno na stejné třídě okna.

`CWindowImpl` také podporuje podtříd oken. Metoda `SubclassWindow` připojí existující okno k objektu `CWindowImpl` a změní proceduru okna na `CWindowImpl::WindowProc`. Každá instance `CWindowImpl` může podtřídit jiné okno.

> [!NOTE]
>  Pro libovolný daný objekt `CWindowImpl` volejte buď `Create` nebo `SubclassWindow`. U stejného objektu Nevolejte obě metody.

Kromě `CWindowImpl`ATL poskytuje [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) k vytvoření okna, které je obsaženo v jiném objektu.

Destruktor základní třídy (~ `CWindowImplRoot`) zajistí, že okno zmizí před zničením objektu.

`CWindowImpl` je odvozena z `CWindowImplBaseT`, která je odvozena z `CWindowImplRoot`, která je odvozena od `TBase` a [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Další informace o|Seznamte se s|
|--------------------------------|---------|
|Vytváření ovládacích prvků|[Kurz ATL](../../atl/active-template-library-atl-tutorial.md)|
|Použití Windows v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="create"></a>CWindowImpl:: Create

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

*hWndParent*<br/>
pro Popisovač nadřazeného nebo vlastníka okna.

*OBD*<br/>
pro Struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) určující pozici okna. `RECT` lze předat pomocí ukazatele nebo odkazu.

*szWindowName*<br/>
pro Určuje název okna. Výchozí hodnota je NULL.

*dwStyle*<br/>
pro Styl okna Tato hodnota je kombinována se stylem poskytnutým třídou vlastností okna. Výchozí hodnota dává vlastnostem třídy plnou kontrolu nad stylem. Seznam možných hodnot naleznete v tématu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v Windows SDK.

*dwExStyle*<br/>
pro Rozšířený styl okna Tato hodnota je kombinována se stylem poskytnutým třídou vlastností okna. Výchozí hodnota dává vlastnostem třídy plnou kontrolu nad stylem. Seznam možných hodnot naleznete v tématu [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*MenuOrID*<br/>
pro V případě podřízeného okna identifikátor okna. Pro okno nejvyšší úrovně se pro okno zobrazí popisovač nabídky. Výchozí hodnota je **0U**.

*lpCreateParam*<br/>
pro Ukazatel na data vytváření oken. Úplný popis naleznete v popisu pro výsledný parametr [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu se popisovač nově vytvořeného okna. V opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

`Create` nejprve zaregistrovat třídu okna, pokud ještě nebyla zaregistrována. Nově vytvořené okno je automaticky připojeno k objektu `CWindowImpl`.

> [!NOTE]
>  Nevolejte `Create`, pokud jste již volali [SubclassWindow](#subclasswindow).

Chcete-li použít třídu okna, která je založena na existující třídě okna, odvodit třídu z `CWindowImpl` a zahrnout makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . Procedura okna existující třídy okna je uložena v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Další informace najdete v tématu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Overview.

> [!NOTE]
>  Pokud se hodnota 0 používá jako hodnota parametru *MenuOrID* , musí být zadána jako 0U (výchozí hodnota), aby se předešlo chybě kompilátoru.

##  <a name="defwindowproc"></a>CWindowImpl::D efWindowProc

Volá se [WindowProc](#windowproc) ke zpracování zpráv, které nezpracovává mapa zpráv.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>Parametry

*uMsg*<br/>
pro Zpráva byla odeslána do okna.

*wParam*<br/>
pro Další informace specifické pro zprávy

*lParam*<br/>
pro Další informace specifické pro zprávy

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `DefWindowProc` volá funkci [CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 pro odeslání informací o zprávě do procedury okna zadané v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

Funkce bez parametrů automaticky načte potřebné parametry z aktuální zprávy.

##  <a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage

Vrátí aktuální zprávu zabalenou ve struktuře `MSG`.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zpráva

##  <a name="getwindowproc"></a>CWindowImpl::GetWindowProc

Vrátí `WindowProc`aktuální procedura okna.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální procedura okna

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete proceduru okna nahradit vlastními.

##  <a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo

Volá se [vytvořením](#create) pro přístup k informacím o třídě okna.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Návratová hodnota

Statická instance třídy [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CWindowImpl` získá tuto metodu prostřednictvím makra [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) , které určuje novou třídu okna.

Chcete-li použít supertřídy existující třídy okna, odvodit třídu z `CWindowImpl` a zahrnout makro [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) pro přepsání `GetWndClassInfo`. Další informace najdete v tématu [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Overview.

Kromě použití makra DECLARE_WND_CLASS a DECLARE_WND_SUPERCLASS můžete přepsat `GetWndClassInfo` s vlastní implementací.

##  <a name="m_pfnsuperwindowproc"></a>CWindowImpl:: m_pfnSuperWindowProc

V závislosti na okně odkazuje na jeden z následujících postupů okna.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Poznámky

|Typ okna|Procedura okna|
|--------------------|----------------------|
|Okno založené na nové třídě okna zadané pomocí makra [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) .|Funkce [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32.|
|Okno na základě třídy okna, která upravuje existující třídu určenou pomocí makra [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) .|Procedura okna existující třídy okna.|
|Okno podtřídy.|Původní procedura okna podtřídy okna|

[CWindowImpl::D efwindowproc](#defwindowproc) odesílá informace o zprávě do procedury okna uložené v `m_pfnSuperWindowProc`.

##  <a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage

Volá se po přijetí poslední zprávy (obvykle WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Popisovač pro zničené okno.

### <a name="remarks"></a>Poznámky

Výchozí implementace `OnFinalMessage` nedělá nic, ale tuto funkci můžete před zničením okna přepsat, aby se vyčistila. Pokud chcete automaticky odstranit objekt po zničení okna, můžete zavolat **Odstranit this;** v této funkci.

##  <a name="subclasswindow"></a>CWindowImpl::SubclassWindow

Roztřídí okno identifikované pomocí *HWND* a připojí ho k objektu `CWindowImpl`.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Popisovač roztříděné okna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je okno úspěšně podtříd; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Okno podtříd teď používá [CWindowImpl:: WindowProc](#windowproc). Původní procedura okna je uložena v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
>  Nevolejte `SubclassWindow`, pokud jste již volali [Create](#create).

##  <a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow

Odpojí okno podtřídy od objektu `CWindowImpl` a obnoví původní proceduru okna uloženou v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro dříve vytříděné okno.

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

*hWnd*<br/>
pro Popisovač okna.

*uMsg*<br/>
pro Zpráva byla odeslána do okna.

*wParam*<br/>
pro Další informace specifické pro zprávy

*lParam*<br/>
pro Další informace specifické pro zprávy

### <a name="return-value"></a>Návratová hodnota

Výsledek zpracování zprávy

### <a name="remarks"></a>Poznámky

`WindowProc` používá výchozí mapu zpráv (deklarovaná s [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)) k přímému směrování zpráv na příslušné obslužné rutiny. V případě potřeby `WindowProc` voláním [DefWindowProc](#defwindowproc) pro další zpracování zpráv. Pokud se Závěrečná zpráva nezpracovává, `WindowProc` provede následující akce:

- Provede unsubclassing, pokud bylo okno unsubclassed.

- Zruší `m_hWnd`.

- Volá [OnFinalMessage](#onfinalmessage) před zničením okna.

Můžete přepsat `WindowProc` k poskytnutí jiného mechanismu pro zpracování zpráv.

## <a name="see-also"></a>Viz také

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
