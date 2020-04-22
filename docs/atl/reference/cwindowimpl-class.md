---
title: Třída CWindowImpl
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
ms.openlocfilehash: ea150195f06d12cd6549b9026714d9e1bbf392df
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745994"
---
# <a name="cwindowimpl-class"></a>Třída CWindowImpl

Poskytuje metody pro vytváření nebo podtřídy okna.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše nová třída, `CWindowImpl`odvozená z .

*TBase*<br/>
Základní třída vaší třídy. Ve výchozím nastavení je základní třída [CWindow](../../atl/reference/cwindow-class.md).

*TWinTraits*<br/>
[Třída vlastností,](../../atl/understanding-window-traits.md) která definuje styly pro vaše okno. Výchozí formát je `CControlWinTraits`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWindowImpl::Vytvořit](#create)|Vytvoří okno.|

### <a name="cwindowimplbaset-methods"></a>Metody CWindowImplBaseT

|||
|-|-|
|[DefWindowProc](#defwindowproc)|Poskytuje výchozí zpracování zpráv.|
|[GetCurrentMessage](#getcurrentmessage)|Vrátí aktuální zprávu.|
|[GetWindowProc](#getwindowproc)|Vrátí aktuální proceduru okna.|
|[Zpráva OnFinalMessage](#onfinalmessage)|Volána po přijetí poslední zprávy (obvykle WM_NCDESTROY).|
|[Okno podtřídy](#subclasswindow)|Podtřídy okna.|
|[UnsubclassWindow](#unsubclasswindow)|Obnoví dříve podtřídy okna.|

### <a name="static-methods"></a>Statické metody

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|Vrátí statickou instanci [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), která spravuje informace o třídě okna.|
|[WindowProc](#windowproc)|Zpracuje zprávy odeslané do okna.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|Odkazuje na původní okno třídy okna postup.|

## <a name="remarks"></a>Poznámky

Můžete vytvořit `CWindowImpl` okno nebo podtřídu existující okno. Procedura `CWindowImpl` okna používá mapu zpráv k přesměrování zpráv příslušným obslužným rutinám.

`CWindowImpl::Create`vytvoří okno založené na informacích o třídě okna, které je spravováno [cWndClassInfo](../../atl/reference/cwndclassinfo-class.md). `CWindowImpl`obsahuje [makro DECLARE_WND_CLASS,](window-class-macros.md#declare_wnd_class) `CWndClassInfo` což znamená, že registruje novou třídu okna. Pokud chcete třídit existující třídu okna, `CWindowImpl` odvodit třídu z a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro. V tomto `CWndClassInfo` případě zaregistruje třídu okna, která je `CWindowImpl::WindowProc`založena na existující třídě, ale používá . Příklad:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
> Vzhledem k tomu, že `CWndClassInfo` spravuje informace pouze pro `CWindowImpl` jednu třídu okna, každé okno vytvořené prostřednictvím instance je založena na stejné třídě okna.

`CWindowImpl`podporuje také podtřídy oken. Metoda `SubclassWindow` připojí existující okno k `CWindowImpl` objektu a změní `CWindowImpl::WindowProc`proceduru okna na . Každá instance `CWindowImpl` může podtřídy jiné okno.

> [!NOTE]
> Pro daný `CWindowImpl` objekt volejte `Create` `SubclassWindow`buď nebo . Nevyvolávejte obě metody na stejném objektu.

Kromě , `CWindowImpl`KNIHOVNA ATL poskytuje [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) vytvořit okno, které je obsaženo v jiném objektu.

Destruktor základní třídy (~ `CWindowImplRoot`) zajišťuje, že okno je pryč před zničením objektu.

`CWindowImpl`pochází z `CWindowImplBaseT`, který `CWindowImplRoot`je odvozen z `TBase` , který je odvozen z a [CMessageMap](../../atl/reference/cmessagemap-class.md).

|Další informace o|Seznamte se s |
|--------------------------------|---------|
|Vytváření ovládacích prvků|[Kurz ATL](../../atl/active-template-library-atl-tutorial.md)|
|Použití oken v atl|[Třídy oken ATL](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cwindowimplcreate"></a><a name="create"></a>CWindowImpl::Vytvořit

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
[v] Popisovač do okna nadřazeného nebo vlastníka.

*Rect*<br/>
[v] A [RECT](/windows/win32/api/windef/ns-windef-rect) struktura určující umístění okna. Může `RECT` být předán ukazatelem nebo odkazem.

*szNázev_okna*<br/>
[v] Určuje název okna. Výchozí hodnota je NULL.

*dwStyl*<br/>
[v] Styl okna. Tato hodnota je kombinována se stylem poskytnutým třídou vlastností pro okno. Výchozí hodnota poskytuje vlastnosti třídy plnou kontrolu nad stylem. Seznam možných hodnot naleznete v tématu [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) v sadě Windows SDK.

*dwExStyl*<br/>
[v] Rozšířený styl okna. Tato hodnota je kombinována se stylem poskytnutým třídou vlastností pro okno. Výchozí hodnota poskytuje vlastnosti třídy plnou kontrolu nad stylem. Seznam možných hodnot naleznete v tématu [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*ID nabídky*<br/>
[v] Pro podřízené okno identifikátor okna. Pro okno nejvyšší úrovně popisovač nabídky pro okno. Výchozí hodnota je **0U**.

*lpCreateParam*<br/>
[v] Ukazatel na data vytváření oken. Úplný popis naleznete v popisu konečného parametru [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, popisovač nově vytvořené okno. V opačném případě null.

### <a name="remarks"></a>Poznámky

`Create`nejprve zaregistruje třídu okna, pokud ještě nebyla zaregistrována. Nově vytvořené okno je automaticky `CWindowImpl` připojeno k objektu.

> [!NOTE]
> Nevolejte, `Create` pokud jste již [volali PodtřídyOkno](#subclasswindow).

Chcete-li použít třídu okna, která je založena `CWindowImpl` na existující třídě okna, odvodit třídu z a zahrnout [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro. Procedura okna existující třídy okna je uložena v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc). Další informace naleznete v [přehledu CWindowImpl.](../../atl/reference/cwindowimpl-class.md)

> [!NOTE]
> Pokud 0 se používá jako hodnota pro *MenuOrID* parametr, musí být zadán jako 0U (výchozí hodnota), aby se zabránilo chybě kompilátoru.

## <a name="cwindowimpldefwindowproc"></a><a name="defwindowproc"></a>CWindowImpl::DefWindowProc

Volána [WindowProc](#windowproc) ke zpracování zpráv, které nejsou zpracovány mapy zpráv.

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
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

Funkce bez parametrů automaticky načte potřebné parametry z aktuální zprávy.

## <a name="cwindowimplgetcurrentmessage"></a><a name="getcurrentmessage"></a>CWindowImpl::GetCurrentMessage

Vrátí aktuální zprávu zabalenou `MSG` ve struktuře.

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální zpráva.

## <a name="cwindowimplgetwindowproc"></a><a name="getwindowproc"></a>CWindowImpl::GetWindowProc

Vrátí `WindowProc`, aktuální okno postup.

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální okno postup.

### <a name="remarks"></a>Poznámky

Přepsat tuto metodu nahradit postup okna s vlastní.

## <a name="cwindowimplgetwndclassinfo"></a><a name="getwndclassinfo"></a>CWindowImpl::GetWndClassInfo

Volána [Create](#create) pro přístup k informacím třídy okna.

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>Návratová hodnota

Statická instance [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md).

### <a name="remarks"></a>Poznámky

Ve výchozím `CWindowImpl` nastavení získá tuto metodu prostřednictvím [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makro, které určuje novou třídu okna.

Chcete-li nadtřídit existující třídu `CWindowImpl` okna, odvoděte `GetWndClassInfo`třídu a zahrňte [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro, které chcete přepsat . Další informace naleznete v [přehledu CWindowImpl.](../../atl/reference/cwindowimpl-class.md)

Kromě použití DECLARE_WND_CLASS a DECLARE_WND_SUPERCLASS makra, můžete přepsat `GetWndClassInfo` s vlastní implementací.

## <a name="cwindowimplm_pfnsuperwindowproc"></a><a name="m_pfnsuperwindowproc"></a>CWindowImpl::m_pfnSuperWindowProc

V závislosti na okně odkazuje na jeden z následujících okenních procedur.

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Poznámky

|Typ okna|Postup okna|
|--------------------|----------------------|
|Okno založené na nové třídě okna určené prostřednictvím [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) makra.|Funkce [DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32.|
|Okno založené na třídě okna, která upravuje existující třídu určenou prostřednictvím [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro.|Procedura okna existující třídy okna.|
|Okno podtřídy.|Původní okno podtřídy procedury.|

[CWindowImpl::DefWindowProc](#defwindowproc) odešle informace o zprávě `m_pfnSuperWindowProc`do procedury okna uložené v .

## <a name="cwindowimplonfinalmessage"></a><a name="onfinalmessage"></a>CWindowImpl::OnFinalMessage

Volána po obdržení poslední zprávy (obvykle WM_NCDESTROY).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Popisovač k zničenému oknu.

### <a name="remarks"></a>Poznámky

Výchozí implementace `OnFinalMessage` neprovede žádné, ale můžete přepsat tuto funkci ke zpracování vyčištění před zničením okna. Chcete-li automaticky odstranit objekt při zničení okna, můžete volat **delete this;** in this function.

## <a name="cwindowimplsubclasswindow"></a><a name="subclasswindow"></a>CWindowImpl::Okno podtřídy

Podtřídy okno označené *hWnd* a připojí `CWindowImpl` jej k objektu.

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Popisovač okna, které je podtřídy.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je okno úspěšně podtřídy; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Okno s podtřídou nyní používá [CWindowImpl::WindowProc](#windowproc). Původní procedura okna je uložena v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

> [!NOTE]
> Nevolejte, `SubclassWindow` pokud jste již [volali Vytvořit](#create).

## <a name="cwindowimplunsubclasswindow"></a><a name="unsubclasswindow"></a>CWindowImpl::UnsubclassWindow

Odpojí okno podtřídy od `CWindowImpl` objektu a obnoví původní proceduru okna uloženou v [m_pfnSuperWindowProc](#m_pfnsuperwindowproc).

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač okna dříve podtřídy.

## <a name="cwindowimplwindowproc"></a><a name="windowproc"></a>CWindowImpl::WindowProc

Tato statická funkce implementuje proceduru okna.

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

`WindowProc`používá výchozí mapu zpráv (deklarovanou [s BEGIN_MSG_MAP)](message-map-macros-atl.md#begin_msg_map)k přesměrování zpráv příslušným obslužným rutinám. V případě `WindowProc` potřeby volá [DefWindowProc](#defwindowproc) pro další zpracování zpráv. Pokud není zpracována konečná `WindowProc` zpráva, postupujte takto:

- Provádí nepodřazování, pokud bylo okno nepodřazené.

- Vymaže `m_hWnd`.

- Volá [OnFinalMessage](#onfinalmessage) před zničením okna.

Můžete přepsat `WindowProc` poskytnout jiný mechanismus pro zpracování zpráv.

## <a name="see-also"></a>Viz také

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
