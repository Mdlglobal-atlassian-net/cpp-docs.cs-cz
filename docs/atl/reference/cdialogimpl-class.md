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
ms.openlocfilehash: 04acfb9c653df85be8958d7248bafd93f3e0a30b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693656"
---
# <a name="cdialogimpl-class"></a>CDialogImpl – třída

Tato třída poskytuje metody pro vytváření modální a nemodální dialogové okno.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `CDialogImpl`.

*Tčíslice*<br/>
Základní třídy novou třídu. Výchozí základní třída je [cwindow –](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Vytvoření](#create)|Vytvoří nemodální dialogové okno.|
|[Destroywindow –](#destroywindow)|Zničí nemodální dialogové okno.|
|[DoModal](#domodal)|Vytvoří modální dialogové okno.|
|[EndDialog](#enddialog)|Zničí modální dialogové okno.|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT metody

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Vrátí aktuální proceduru dialogového okna pole.|
|[MapDialogRect](#mapdialogrect)|Mapy jednotky dialogového okna obdélníku zadaného na obrazovce jednotek (v pixelech).|
|[OnFinalMessage](#onfinalmessage)|Volá se po přijetí poslední zprávy, obvykle WM_NCDESTROY.|

### <a name="static-functions"></a>Statické funkce

|||
|-|-|
|[DialogProc](#dialogproc)|Zpracovává zprávy odeslané do dialogového okna.|
|[StartDialogProc](#startdialogproc)|Volá se při přijetí první zprávu zpracovat zprávy odeslané do dialogového okna.|

## <a name="remarks"></a>Poznámky

S `CDialogImpl` vytvoříte modální a nemodální dialogové okno. `CDialogImpl` poskytuje pole proceduru dialogového okna, který používá výchozí mapování zpráv ke směrování zpráv do příslušné obslužné rutiny.

Destruktor základní třídy `~CWindowImplRoot` zajistí, že v okně zmizel před zničení objektu.

`CDialogImpl` je odvozen od `CDialogImplBaseT`, která je dále odvozeno z `CWindowImplRoot`.

> [!NOTE]
>  Musíte definovat třídu `IDD` člena, který určuje ID prostředku šablony dialogového okna. Například Průvodce projektem ATL automaticky přidá následující řádek do vaší třídy:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

kde `MyDlg` je **krátký název** zadali v průvodci **názvy** stránky.

|Další informace o|Další informace naleznete v tématu|
|--------------------------------|---------|
|Vytváření ovládacích prvků|[ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md)|
|Pomocí dialogových oken v ATL|[ATL – třídy oken](../../atl/atl-window-classes.md)|
|Průvodce projektem ATL|[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Dialogová okna|[Dialogová okna](/windows/desktop/dlgbox/dialog-boxes) a dalších tématech v sadě Windows SDK|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="create"></a>  CDialogImpl::Create

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
[in] Popisovač nadřazenému oknu.

**Rect – &** *rect* [in] A [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura určující velikost a umístění dialogového okna.

*dwInitParam*<br/>
[in] Určuje hodnotu pro předání do dialogového okna aplikace *lParam* parametr nezavěsíte zprávu.

### <a name="return-value"></a>Návratová hodnota

Popisovač do nově vytvořeného dialogových oken.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojen k `CDialogImpl` objektu. Chcete-li vytvořit modální dialogové okno, zavolejte [DoModal](#domodal). Druhý výše uvedené přepsání se používá jenom s [ccomcontrol –](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow

Zničí nemodální dialogové okno.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl úspěšně zničení dialogových oken; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Vrátí hodnotu TRUE, pokud byl úspěšně zničení dialogových oken; v opačném případě FALSE.

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

Tato statická funkce implementuje pole proceduru dialogového okna.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Popisovač do dialogového okna.

*uMsg*<br/>
[in] Zpráva odeslaná do dialogového okna.

*wParam*<br/>
[in] Další informace specifické pro zprávy.

*lParam*<br/>
[in] Další informace specifické pro zprávy.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud zpráva se zpracuje; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

`DialogProc` Výchozí mapování zpráv používá ke směrování zpráv do příslušné obslužné rutiny.

Můžete přepsat `DialogProc` jiný mechanismus pro zpracování zpráv.

##  <a name="domodal"></a>  CDialogImpl::DoModal

Vytvoří modální dialogové okno.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[in] Popisovač nadřazenému oknu. Výchozí hodnota je vrácená hodnota [GetActiveWindow](/windows/desktop/api/winuser/nf-winuser-getactivewindow) funkci Win32.

*dwInitParam*<br/>
[in] Určuje hodnotu pro předání do dialogového okna aplikace *lParam* parametr nezavěsíte zprávu.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu se hodnota *nRetCode* parametr zadaný ve volání [EndDialog](#enddialog). Jinak -1.

### <a name="remarks"></a>Poznámky

Toto dialogové okno je automaticky připojen k `CDialogImpl` objektu.

Vytvoří nemodální dialogové okno, voláním [vytvořit](#create).

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

Zničí modální dialogové okno.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
[in] Hodnota, která má být vrácen [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud jeho zničení dialogových oken; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

`EndDialog` musí být volána prostřednictvím proceduru dialogového okna. Po zničení dialogových oken Windows používá hodnotu *nRetCode* jako návratovou hodnotu pro `DoModal`, který vytvoří dialogové okno.

> [!NOTE]
>  Nevolejte `EndDialog` ke zničení nemodální dialogové okno. Volání [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) místo.

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

Vrátí `DialogProc`, aktuální proceduru dialogového okna pole.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální proceduru dialogového okna pole.

### <a name="remarks"></a>Poznámky

Potlačí tuto metodu za účelem proceduru dialogového okna nahradit svojí vlastní.

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

Převede (map) – dialogové okno jednotek zadané obdélník na obrazovku jednotek (v pixelech).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lprect –*<br/>
Odkazuje na `CRect` objektu nebo [RECT](../../mfc/reference/rect-structure.md) struktura, která má obdržet souřadnice klienta, který obklopuje oblast aktualizace aktualizace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aktualizace úspěšně. 0, pokud se aktualizace nezdaří. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.

### <a name="remarks"></a>Poznámky

Funkce nahrazuje souřadnice v zadaném `RECT` struktury pomocí převedený souřadnice, což umožňuje struktura se použije k vytvoření dialogového nebo umístit ovládací prvek v rámci dialogového okna.

##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage

Volá se po přijetí poslední zprávy (obvykle `WM_NCDESTROY`).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Popisovač okna zničen.

### <a name="remarks"></a>Poznámky

Všimněte si, že pokud chcete automaticky odstranit objekt při odstraňování oken, můžete volat **odstranit tento;** tady.

##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc

Volána pouze jednou, při přijetí první zprávu zpracovat zprávy odeslané do dialogového okna.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Popisovač do dialogového okna.

*uMsg*<br/>
[in] Zpráva odeslaná do dialogového okna.

*wParam*<br/>
[in] Další informace specifické pro zprávy.

*lParam*<br/>
[in] Další informace specifické pro zprávy.

### <a name="return-value"></a>Návratová hodnota

Proceduru okna.

### <a name="remarks"></a>Poznámky

Po počáteční volání `StartDialogProc`, `DialogProc` není nastaven jako proceduru dialogového okna a další volání tam.

## <a name="see-also"></a>Viz také

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)