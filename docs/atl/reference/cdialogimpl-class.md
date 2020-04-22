---
title: CDialogImpl – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: d5ab7293f73429a93c3fcab243c2e34d3c78f28a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747716"
---
# <a name="cdialogimpl-class"></a>CDialogImpl – třída

Tato třída poskytuje metody pro vytvoření modálního nebo nemodálního dialogového okna.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `CDialogImpl`.

*TBase*<br/>
Základní třída vaší nové třídy. Výchozí základní třída je [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Vytvořit](#create)|Vytvoří nemodální dialogové okno.|
|[Zničit okno](#destroywindow)|Zničí nemodální dialogové okno.|
|[DoModal](#domodal)|Vytvoří modální dialogové okno.|
|[Ukončit dialog](#enddialog)|Zničí modální dialogové okno.|

### <a name="cdialogimplbaset-methods"></a>Metody CDialogimplbaset

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Vrátí aktuální proceduru dialogového okna.|
|[MapDialogRect](#mapdialogrect)|Mapuje jednotky dialogového okna určeného obdélníku na jednotky obrazovky (pixely).|
|[Zpráva OnFinalMessage](#onfinalmessage)|Volána po obdržení poslední zprávy, obvykle WM_NCDESTROY.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[DialogProc](#dialogproc)|Zpracuje zprávy odeslané do dialogového okna.|
|[StartDialogProc](#startdialogproc)|Volána při přijetí první zprávy ke zpracování zpráv odeslaných do dialogového okna.|

## <a name="remarks"></a>Poznámky

Pomocí `CDialogImpl` aplikace můžete vytvořit modální nebo nemodální dialogové okno. `CDialogImpl`Poskytuje proceduru dialogového okna, která používá výchozí mapování zpráv k přesměrování zpráv na příslušné obslužné rutiny.

Destruktor `~CWindowImplRoot` základní třídy zajišťuje, že okno je pryč před zničením objektu.

`CDialogImpl`pochází z `CDialogImplBaseT`, což zase `CWindowImplRoot`pochází z .

> [!NOTE]
> Vaše třída musí `IDD` definovat člena, který určuje ID prostředku šablony dialogu. Například Průvodce projektem ATL automaticky přidá do vaší třídy následující řádek:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

kde `MyDlg` je **krátký název** zadaný na stránce **Jména** průvodce.

|Další informace o|Seznamte se s |
|--------------------------------|---------|
|Vytváření ovládacích prvků|[Kurz ATL](../../atl/active-template-library-atl-tutorial.md)|
|Použití dialogových oken v atl|[Třídy oken ATL](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Dialogová okna|[Dialogová okna](/windows/win32/dlgbox/dialog-boxes) a následující témata v sadě Windows SDK|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Vytvořit

Vytvoří nemodální dialogové okno.

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

*hWndParent*<br/>
[v] Popisovač do okna vlastníka.

**RECT&** *rect* [in] Struktura [RECT](/windows/win32/api/windef/ns-windef-rect) určující velikost a umístění dialogu.

*dwInitParam*<br/>
[v] Určuje hodnotu, která má být předávána dialogovému oknu v parametru *lParam* WM_INITDIALOG zprávy.

### <a name="return-value"></a>Návratová hodnota

Úchyt k nově vytvořenému dialogovému oknu.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je `CDialogImpl` automaticky připojeno k objektu. Chcete-li vytvořit modální dialogové okno, volejte [DoModal](#domodal). Druhé výše uvedené přepsání se používá pouze u [ccomcontrolu](../../atl/reference/ccomcontrol-class.md).

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyOkno

Zničí nemodální dialogové okno.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo dialogové okno úspěšně zničeno; jinak FALSE.

### <a name="remarks"></a>Poznámky

Vrátí hodnotu PRAVDA, pokud bylo dialogové okno úspěšně zničeno. jinak FALSE.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc

Tato statická funkce implementuje postup dialogového okna.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Úchyt do dialogového okna.

*uMsg*<br/>
[v] Zpráva odeslaná do dialogového okna.

*wParam*<br/>
[v] Další informace specifické pro zprávu.

*Lparam*<br/>
[v] Další informace specifické pro zprávu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zpráva zpracována; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

`DialogProc`používá výchozí mapování zpráv k přesměrování zpráv na příslušné obslužné rutiny.

Můžete přepsat `DialogProc` poskytnout jiný mechanismus pro zpracování zpráv.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModální

Vytvoří modální dialogové okno.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[v] Popisovač do okna vlastníka. Výchozí hodnota je vrácená hodnota funkce [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
[v] Určuje hodnotu, která má být předávána dialogovému oknu v parametru *lParam* WM_INITDIALOG zprávy.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu, hodnota *parametru nRetCode* zadaná ve volání [EndDialog](#enddialog). Jinak -1.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je `CDialogImpl` automaticky připojeno k objektu.

Chcete-li vytvořit nemodální dialogové okno, volejte [vytvořit](#create).

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogimpl::EndDialog

Zničí modální dialogové okno.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
[v] Hodnota, která má být vrácena [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je dialogové okno zničeno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

`EndDialog`musí být volána dialogovou procedurou. Po zničení dialogového okna použije systém Windows hodnotu *nRetCode* jako vrácenou hodnotu pro `DoModal`aplikaci , která dialogové okno vytvořila.

> [!NOTE]
> Nevolejte, `EndDialog` abyste zničili nemodální dialogové okno. Volání [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) místo.

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc

Vrátí `DialogProc`, aktuální proceduru dialogového okna.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální postup dialogového okna.

### <a name="remarks"></a>Poznámky

Přepište tuto metodu a nahraďte dialogový postup vlastním.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect

Převede (mapuje) jednotky dialogového okna určeného obdélníku na jednotky obrazovky (pixely).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `CRect` objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) strukturu, která má přijímat souřadnice klienta aktualizace, která obklopuje oblast aktualizace.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je aktualizace úspěšná; 0, pokud se aktualizace nezdaří. Chcete-li získat rozšířené `GetLastError`informace o chybě, volejte .

### <a name="remarks"></a>Poznámky

Funkce nahradí souřadnice v `RECT` zadané struktuře převedenými souřadnicemi, což umožňuje použít strukturu k vytvoření dialogového okna nebo umístění ovládacího prvku v dialogovém okně.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>cDialogimpl::OnFinalMessage

Volána po obdržení poslední `WM_NCDESTROY`zprávy (obvykle).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Popisovač k zničenému oknu.

### <a name="remarks"></a>Poznámky

Všimněte si, že pokud chcete automaticky odstranit objekt při zničení okna, můžete volat **odstranit;** zde.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc

Volána pouze jednou, když je přijata první zpráva, ke zpracování zpráv odeslaných do dialogového okna.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Úchyt do dialogového okna.

*uMsg*<br/>
[v] Zpráva odeslaná do dialogového okna.

*wParam*<br/>
[v] Další informace specifické pro zprávu.

*Lparam*<br/>
[v] Další informace specifické pro zprávu.

### <a name="return-value"></a>Návratová hodnota

Procedura okna.

### <a name="remarks"></a>Poznámky

Po počáteční volání `StartDialogProc` `DialogProc` na , je nastaven jako dialog postup a další volání jít tam.

## <a name="see-also"></a>Viz také

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
