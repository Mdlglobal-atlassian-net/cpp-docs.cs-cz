---
title: CDialogImpl – – třída
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
ms.openlocfilehash: bc39a5deeb270b0426a4b199fc9ba01917c292bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496815"
---
# <a name="cdialogimpl-class"></a>CDialogImpl – – třída

Tato třída poskytuje metody pro vytvoření modálního nebo nemodálního dialogového okna.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `CDialogImpl`odvozena z.

*TBase*<br/>
Základní třída vaší nové třídy. Výchozí základní třída je [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Vytvoření](#create)|Vytvoří nemodální dialogové okno.|
|[DestroyWindow](#destroywindow)|Odstraní nemodální dialogové okno.|
|[DoModal](#domodal)|Vytvoří modální dialogové okno.|
|[EndDialog](#enddialog)|Odstraní modální dialogové okno.|

### <a name="cdialogimplbaset-methods"></a>Metody CDialogImplBaseT

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Vrátí aktuální proceduru dialogového okna.|
|[MapDialogRect](#mapdialogrect)|Namapuje jednotky dialogového okna zadaného obdélníku na jednotky obrazovky (pixely).|
|[OnFinalMessage](#onfinalmessage)|Volá se po přijetí poslední zprávy, obvykle WM_NCDESTROY.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[DialogProc](#dialogproc)|Zpracuje zprávy odesílané do dialogového okna.|
|[StartDialogProc](#startdialogproc)|Volá se při přijetí první zprávy pro zpracování zpráv odeslaných do dialogového okna.|

## <a name="remarks"></a>Poznámky

Pomocí `CDialogImpl` můžete vytvořit modální nebo nemodální dialogové okno. `CDialogImpl`poskytuje proceduru dialogového okna, která používá výchozí mapu zpráv k přímému směrování zpráv na příslušné obslužné rutiny.

Destruktor `~CWindowImplRoot` základní třídy zajišťuje, že okno je pryč před zničením objektu.

`CDialogImpl`je odvozen z `CDialogImplBaseT`, který je zase odvozen z. `CWindowImplRoot`

> [!NOTE]
>  Vaše třída musí definovat `IDD` člena, který určuje ID prostředku šablony dialogového okna. Například Průvodce projektem ATL automaticky do vaší třídy přidá následující řádek:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

kde `MyDlg` je **krátký název** zadaný na stránce s **názvy** průvodce.

|Další informace o|Další informace naleznete v tématu|
|--------------------------------|---------|
|Vytváření ovládacích prvků|[Kurz ATL](../../atl/active-template-library-atl-tutorial.md)|
|Použití dialogových oken v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Dialogová okna|[Dialogová okna](/windows/win32/dlgbox/dialog-boxes) a další témata v Windows SDK|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="create"></a>CDialogImpl –:: Create

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
pro Popisovač okna vlastníka.

**& Rect** *Rect* pro Struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) určující velikost a polohu dialogového okna

*dwInitParam*<br/>
pro Určuje hodnotu, která má být předána do dialogového okna v parametru *lParam* zprávy WM_INITDIALOG.

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného dialogového okna.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojeno k `CDialogImpl` objektu. Chcete-li vytvořit modální dialogové okno, zavolejte [DoModal](#domodal). Druhé přepsání výše se používá pouze s [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>CDialogImpl –::D estroyWindow

Odstraní nemodální dialogové okno.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud bylo dialogové okno úspěšně zničeno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Vrátí hodnotu TRUE, pokud bylo dialogové okno úspěšně zničeno; v opačném případě FALSE.

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

Tato statická funkce implementuje proceduru dialogového okna.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Popisovač dialogového okna.

*uMsg*<br/>
pro Zpráva byla odeslána do dialogového okna.

*wParam*<br/>
pro Další informace specifické pro zprávy

*lParam*<br/>
pro Další informace specifické pro zprávy

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zpráva zpracována; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`DialogProc`používá výchozí mapu zpráv k přímému směrování zpráv do příslušných obslužných rutin.

Můžete přepsat `DialogProc` a poskytnout tak jiný mechanismus pro zpracování zpráv.

##  <a name="domodal"></a>  CDialogImpl::DoModal

Vytvoří modální dialogové okno.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
pro Popisovač okna vlastníka. Výchozí hodnota je návratová hodnota funkce [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
pro Určuje hodnotu, která má být předána do dialogového okna v parametru *lParam* zprávy WM_INITDIALOG.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu hodnota parametru *nRetCode* zadaného ve volání metody [EndDialog](#enddialog). V opačném případě-1.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojeno k `CDialogImpl` objektu.

Chcete-li vytvořit nemodální dialogové okno, zavolejte příkaz [Create](#create).

##  <a name="enddialog"></a>CDialogImpl –:: EndDialog

Odstraní modální dialogové okno.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
pro Hodnota, která má být vrácena funkcí [CDialogImpl –::D omodal](#domodal).

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je dialogové okno zničeno; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`EndDialog`musí být volána prostřednictvím postupu dialogu. Po zničení dialogového okna používá systém Windows hodnotu *nRetCode* jako návratovou hodnotu pro `DoModal`, což vytvořilo dialogové okno.

> [!NOTE]
>  Nevolejte `EndDialog` pro zničení nemodálního dialogového okna. Místo toho zavolejte [CWindow::D estroywindow](../../atl/reference/cwindow-class.md#destroywindow) .

##  <a name="getdialogproc"></a>CDialogImpl –:: GetDialogProc

Vrátí `DialogProc`aktuální proceduru dialogového okna.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální postup pro dialogové okno

### <a name="remarks"></a>Poznámky

Tuto metodu přepište, pokud chcete proceduru dialogu nahradit vlastními.

##  <a name="mapdialogrect"></a>CDialogImpl –:: MapDialogRect

Převede (mapuje) jednotky dialogového okna zadaného obdélníku na jednotky obrazovky (v pixelech).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `CRect` objekt nebo strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) , která má přijmout souřadnice klienta aktualizace, která obklopuje oblast aktualizace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je aktualizace úspěšná; 0, pokud aktualizace neproběhne úspěšně. Chcete-li získat rozšířené informace o `GetLastError`chybě, zavolejte.

### <a name="remarks"></a>Poznámky

Funkce nahradí souřadnice v zadané `RECT` struktuře pomocí převedených souřadnic, což umožňuje použít strukturu k vytvoření dialogového okna nebo umístit ovládací prvek v rámci dialogového okna.

##  <a name="onfinalmessage"></a>CDialogImpl –:: OnFinalMessage

Volá se po přijetí poslední zprávy (obvykle `WM_NCDESTROY`).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Popisovač pro zničené okno.

### <a name="remarks"></a>Poznámky

Všimněte si, že pokud chcete automaticky odstranit objekt po zničení okna, můžete zavolat **Odstranit this;** zde.

##  <a name="startdialogproc"></a>CDialogImpl –:: StartDialogProc

Volá se jenom jednou, když se přijme první zpráva, aby se zpracovala zpráva odeslaná do dialogového okna.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
pro Popisovač dialogového okna.

*uMsg*<br/>
pro Zpráva byla odeslána do dialogového okna.

*wParam*<br/>
pro Další informace specifické pro zprávy

*lParam*<br/>
pro Další informace specifické pro zprávy

### <a name="return-value"></a>Návratová hodnota

Procedura okna

### <a name="remarks"></a>Poznámky

Po počátečním volání `StartDialogProc`, `DialogProc` je nastaveno jako dialogový postup a další volání přejdou sem.

## <a name="see-also"></a>Viz také:

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
