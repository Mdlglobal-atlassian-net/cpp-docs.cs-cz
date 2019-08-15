---
title: CPagerCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: 519a376bdecc488a94eab65973e33d960ca50c8d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503018"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl – třída

`CPagerCtrl` Třída obaluje ovládací prvek stránkování v systému Windows, který se může posunout v zobrazení obsaženého okna, které se nevejde do obsahujícího okna.

## <a name="syntax"></a>Syntaxe

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|`CPagerCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|Vytvoří ovládací prvek stránkování se zadanými styly a připojí ho k aktuálnímu `CPagerCtrl` objektu.|
|[CPagerCtrl::CreateEx](#createex)|Vytvoří ovládací prvek stránkování se zadanými rozšířenými styly a připojí ho k aktuálnímu `CPagerCtrl` objektu.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Povolí nebo zakáže předávání zpráv [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) do okna, které je obsaženo v aktuálním ovládacím prvku stránkování.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Načte barvu pozadí aktuálního ovládacího prvku stránkování.|
|[CPagerCtrl::GetBorder](#getborder)|Načte velikost ohraničení aktuálního ovládacího prvku stránkování.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Načítá velikost tlačítka pro aktuální ovládací prvek stránkování.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Načte stav zadaného tlačítka v aktuálním ovládacím prvku stránkování.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Načte rozhraní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pro aktuální ovládací prvek stránkování.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Načte pozici posunutí aktuálního ovládacího prvku stránkování.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Označuje, zda je zadané tlačítko aktuálního ovládacího prvku stránkování ve `pressed` stavu.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Označuje, zda je zadané tlačítko aktuálního ovládacího prvku stránkování ve `grayed` stavu.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Označuje, zda je zadané tlačítko aktuálního ovládacího prvku stránkování ve `hot` stavu.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Označuje, zda je zadané tlačítko aktuálního ovládacího prvku stránkování ve `invisible` stavu.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Označuje, zda je zadané tlačítko aktuálního ovládacího prvku stránkování ve `normal` stavu.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Způsobí, že aktuální ovládací prvek pager přepočítá velikost obsaženého okna.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí pro aktuální ovládací prvek stránkování.|
|[CPagerCtrl::SetBorder](#setborder)|Nastaví velikost ohraničení aktuálního ovládacího prvku stránkování.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Nastaví velikost tlačítka pro aktuální ovládací prvek stránkování.|
|[CPagerCtrl::SetChild](#setchild)|Nastaví obsažené okno pro aktuální ovládací prvek stránkování.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Nastaví pozici posunutí aktuálního ovládacího prvku stránkování.|

## <a name="remarks"></a>Poznámky

Ovládací prvek pager je okno, které obsahuje jiné okno, které je lineární a větší než okno obsahující, a umožňuje posunovat obsažené okno do zobrazení. Ovládací prvek pager zobrazí dvě tlačítka posuvníku, která automaticky zmizí při posunutí obsaženého okna do nejnejvzdálenějšího rozsahu a znovu se zobrazí jinak. Můžete vytvořit ovládací prvek stránkování, který se posouvá buď vodorovně, nebo svisle.

Například pokud má vaše aplikace panel nástrojů, který není dostatečně velký pro zobrazení všech položek, můžete přiřadit panel nástrojů k ovládacímu prvku stránkování a uživatelé budou moci přejít na panel nástrojů doleva nebo doprava a získat přístup ke všem položkám. Aplikace Microsoft Internet Explorer verze 4,0 (commctrl. dll verze 4,71) zavádí ovládací prvek stránkování.

Třída je odvozena z třídy [CWnd.](../../mfc/reference/cwnd-class.md) `CPagerCtrl` Další informace a ilustrace ovládacího prvku stránkování naleznete v tématu [ovládací prvky stránkování](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl

`CPagerCtrl` Vytvoří objekt.

```
CPagerCtrl();
```

### <a name="remarks"></a>Poznámky

K vytvoření ovládacího prvku stránkování a `CPagerCtrl` jeho připojení k objektu použijte metodu [CPagerCtrl:: Create](#create) nebo [CPagerCtrl:: CreateEx](#createex) .

##  <a name="create"></a>  CPagerCtrl::Create

Vytvoří ovládací prvek stránkování se zadanými styly a připojí ho k aktuálnímu `CPagerCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwStyle*|pro Bitových kombinací (nebo) [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [ovládacích prvků stránkování](/windows/win32/Controls/pager-control-styles) , které mají být použity pro ovládací prvek.|
|*OBD*|pro Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obsahuje pozici a velikost ovládacího prvku v souřadnicích klienta.|
|*pParentWnd*|pro Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku. Tento parametr nemůže mít hodnotu NULL.|
|*nID*|pro ID ovládacího prvku|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit ovládací prvek stránkování, `CPagerCtrl` deklarujte proměnnou a potom zavolejte metodu [CPagerCtrl:: Create](#create) nebo [CPagerCtrl:: CreateEx](#createex) v této proměnné.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a poté používá metodu [CPagerCtrl:: SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku pager. Příklad pak pomocí metody [CPagerCtrl:: SetButtonSize](#setbuttonsize) nastaví výšku ovládacího prvku stránkování na 20 pixelů a metodu [CPagerCtrl:: SetBorder](#setborder) nastaví tloušťku ohraničení na 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>CPagerCtrl::CreateEx

Vytvoří ovládací prvek stránkování se zadanými rozšířenými styly a připojí ho k aktuálnímu `CPagerCtrl` objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwExStyle*|pro Bitová kombinace rozšířených stylů, která se má použít pro ovládací prvek Další informace najdete v parametru *dwExStyle* funkce [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .|
|*dwStyle*|pro Bitových kombinací (nebo) [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [ovládacích prvků stránkování](/windows/win32/Controls/pager-control-styles) , které mají být použity pro ovládací prvek.|
|*OBD*|pro Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obsahuje pozici a velikost ovládacího prvku v souřadnicích klienta.|
|*pParentWnd*|pro Ukazatel na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku. Tento parametr nemůže mít hodnotu NULL.|
|*nID*|pro ID ovládacího prvku|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit ovládací prvek stránkování, `CPagerCtrl` deklarujte proměnnou a potom zavolejte metodu [CPagerCtrl:: Create](#create) nebo [CPagerCtrl:: CreateEx](#createex) v této proměnné.

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

Povolí nebo zakáže předávání zpráv [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) do okna, které je obsaženo v aktuálním ovládacím prvku stránkování.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bForward*|pro TRUE pro přeposílání zpráv myší nebo false pro přeposílání zpráv myší|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) , která je popsána v Windows SDK.

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

Načte velikost ohraničení aktuálního ovládacího prvku stránkování.

```
int GetBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost ohraničení měřená v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl:: GetBorder](#getborder) k načtení tloušťky ohraničení ovládacího prvku stránkování.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

Načte barvu pozadí aktuálního ovládacího prvku stránkování.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která obsahuje aktuální barvu pozadí ovládacího prvku stránkování.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl:: SetBkColor](#setbkcolor) k nastavení barvy pozadí ovládacího prvku stránkování na červenou a k potvrzení, že změna [](#getbkcolor) byla provedena.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize

Načítá velikost tlačítka pro aktuální ovládací prvek stránkování.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost tlačítka měřená v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) , která je popsána v Windows SDK.

Pokud má ovládací prvek pager styl PGS_HORZ, velikost tlačítka Určuje šířku tlačítek stránkování a v případě, že ovládací prvek pager má styl PGS_VERT, velikost tlačítka Určuje výšku tlačítek stránkování. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

Načte stav zadaného tlačítka posuvníku v aktuálním ovládacím prvku stránkování.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|pro Určuje tlačítko, pro které je stav načten. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte PGB_TOPORLEFT pro tlačítko vlevo a PGB_BOTTOMORRIGHT pro tlačítko vpravo. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte PGB_TOPORLEFT pro tlačítko Top a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Stav tlačítka určeného parametrem *iButton* Stav je buď PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED nebo PGF_HOT. Další informace naleznete v části vrácená hodnota zprávy [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , která je popsána v Windows SDK.

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

Načte rozhraní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pro aktuální ovládací prvek stránkování.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IDropTarget` rozhraní pro aktuální ovládací prvek stránkování.

### <a name="remarks"></a>Poznámky

`IDropTarget`je jedno z rozhraní, které implementujete pro podporu operací přetažení ve vaší aplikaci.

Tato metoda pošle zprávu [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) , která je popsána v Windows SDK. Volající této metody je zodpovědný za volání `Release` členu rozhraní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) , když rozhraní již není potřeba.

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

Načte pozici posunutí aktuálního ovládacího prvku stránkování.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice posunutí měřená v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl:: GetScrollPos](#getscrollpos) k načtení aktuální pozice posunutí ovládacího prvku pager. Pokud ovládací prvek pager již není posunut na nulu, pozice zcela vlevo, v příkladu používá metodu [CPagerCtrl:: SetScrollPos](#setscrollpos) k nastavení pozice posunutí na nulu.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

Označuje, zda je zadané tlačítko posuvníku aktuálního ovládacího prvku pager ve stavu stisknuto.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|pro Určuje tlačítko, pro které je stav načten. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte PGB_TOPORLEFT pro tlačítko vlevo a PGB_BOTTOMORRIGHT pro tlačítko vpravo. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte PGB_TOPORLEFT pro tlačítko Top a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko ve stavu stisknuto; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , která je popsána v Windows SDK. Poté testuje, zda je vrácen stav PGF_DEPRESSED. Další informace naleznete v části vrácená hodnota zprávy [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

Označuje, zda je zadané tlačítko posuvníku aktuálního ovládacího prvku stránkování v šedém stavu.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|pro Určuje tlačítko, pro které je stav načten. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte PGB_TOPORLEFT pro tlačítko vlevo a PGB_BOTTOMORRIGHT pro tlačítko vpravo. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte PGB_TOPORLEFT pro tlačítko Top a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v šedém stavu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , která je popsána v Windows SDK. Poté testuje, zda je vrácen stav PGF_GRAYED. Další informace naleznete v části vrácená hodnota zprávy [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

Označuje, zda je zadané tlačítko posuvníku aktuálního ovládacího prvku stránkování v horkém stavu.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|pro Určuje tlačítko, pro které je stav načten. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte PGB_TOPORLEFT pro tlačítko vlevo a PGB_BOTTOMORRIGHT pro tlačítko vpravo. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte PGB_TOPORLEFT pro tlačítko Top a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v Hot State; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , která je popsána v Windows SDK. Poté testuje, zda je vrácen stav PGF_HOT. Další informace naleznete v části vrácená hodnota zprávy [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

Označuje, zda je zadané tlačítko posuvníku aktuálního ovládacího prvku stránkování v neviditelném stavu.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|pro Určuje tlačítko, pro které je stav načten. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte PGB_TOPORLEFT pro tlačítko vlevo a PGB_BOTTOMORRIGHT pro tlačítko vpravo. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte PGB_TOPORLEFT pro tlačítko Top a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v neviditelném stavu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Systém Windows změní tlačítko posuvníku v určitém směru jako neviditelné, když je obsažené okno posunuto do největšího rozsahu, protože po kliknutí na tlačítko Další nelze zobrazit další z obsažených oken v zobrazení.

Tato metoda pošle zprávu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , která je popsána v Windows SDK. Poté testuje, zda je vrácen stav PGF_INVISIBLE. Další informace naleznete v části vrácená hodnota zprávy [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl:: IsButtonInvisible](#isbuttoninvisible) k určení, zda jsou tlačítka ovládacího prvku stránkování viditelná vlevo a vpravo.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

Označuje, zda je zadané tlačítko posuvníku aktuálního ovládacího prvku stránkování v normálním stavu.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|pro Určuje tlačítko, pro které je stav načten. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte PGB_TOPORLEFT pro tlačítko vlevo a PGB_BOTTOMORRIGHT pro tlačítko vpravo. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte PGB_TOPORLEFT pro tlačítko Top a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v normálním stavu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , která je popsána v Windows SDK. Poté testuje, zda je vrácen stav PGF_NORMAL. Další informace naleznete v části vrácená hodnota zprávy [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="recalcsize"></a>CPagerCtrl::RecalcSize

Způsobí, že aktuální ovládací prvek pager přepočítá velikost obsaženého okna.

```
void RecalcSize();
```

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) , která je popsána v Windows SDK. V důsledku toho ovládací prvek pager pošle oznámení [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) k získání rolovacích rozměrů obsaženého okna.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl:: RecalcSize](#recalcsize) pro vyžádání aktuálního ovládacího prvku pager pro přepočítání jeho velikosti.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Příklad

Následující příklad používá reflexi [zprávy](../../mfc/tn062-message-reflection-for-windows-controls.md) , aby umožnil ovládacímu prvku pager znovu vypočítat svou vlastní velikost místo toho, aby byl výpočet proveden pomocí nadřazeného dialogového okna ovládacího prvku. V příkladu je `MyPagerCtrl` Třída odvozena od [třídy CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)a poté používá mapu zpráv k přidružení oznámení [](/windows/win32/Controls/pgn-calcsize) `OnCalcsize` PGN_CALCSIZE k obslužné rutině oznámení. V tomto příkladu obslužná rutina oznámení nastaví šířku a výšku ovládacího prvku stránkování na pevné hodnoty.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Nastaví barvu pozadí pro aktuální ovládací prvek stránkování.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*clrBk*|pro Hodnota [COLORREF](/windows/win32/gdi/colorref) , která obsahuje novou barvu pozadí ovládacího prvku stránkování.|

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která obsahuje předchozí barvu pozadí ovládacího prvku stránkování.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl:: SetBkColor](#setbkcolor) k nastavení barvy pozadí ovládacího prvku stránkování na červenou a k potvrzení, že změna [](#getbkcolor) byla provedena.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Nastaví velikost ohraničení aktuálního ovládacího prvku stránkování.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iBorder*|pro Nová velikost ohraničení měřená v pixelech Pokud je parametr *iBorder* záporný, velikost ohraničení je nastavena na hodnotu nula.|

### <a name="return-value"></a>Návratová hodnota

Velikost předchozí ohraničení měřená v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a poté používá metodu [CPagerCtrl:: SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku pager. Příklad pak pomocí metody [CPagerCtrl:: SetButtonSize](#setbuttonsize) nastaví výšku ovládacího prvku stránkování na 20 pixelů a metodu [CPagerCtrl:: SetBorder](#setborder) nastaví tloušťku ohraničení na 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize

Nastaví velikost tlačítka pro aktuální ovládací prvek stránkování.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButtonSize*|pro Nová velikost tlačítka měřená v pixelech|

### <a name="return-value"></a>Návratová hodnota

Velikost předchozího tlačítka měřená v pixelech

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) , která je popsána v Windows SDK.

Pokud má ovládací prvek pager styl PGS_HORZ, velikost tlačítka Určuje šířku tlačítek stránkování a v případě, že ovládací prvek pager má styl PGS_VERT, velikost tlačítka Určuje výšku tlačítek stránkování. Výchozí velikost tlačítka je tři čtvrtiny šířky posuvníku a minimální velikost tlačítka je 12 pixelů. Další informace naleznete v tématu [styly ovládacího prvku stránkování](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a poté používá metodu [CPagerCtrl:: SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku pager. Příklad pak pomocí metody [CPagerCtrl:: SetButtonSize](#setbuttonsize) nastaví výšku ovládacího prvku stránkování na 20 pixelů a metodu [CPagerCtrl:: SetBorder](#setborder) nastaví tloušťku ohraničení na 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

Nastaví obsažené okno pro aktuální ovládací prvek stránkování.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*hwndChild*|pro Popisovač okna, které se má zahrnout.|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) , která je popsána v Windows SDK.

Tato metoda nemění nadřazenou položku obsaženého okna. přiřadí pouze popisovač okna k ovládacímu prvku pager pro posouvání. Ve většině případů bude obsažené okno podřízeným oknem ovládacího prvku stránkování.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a poté používá metodu [CPagerCtrl:: SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku pager. Příklad pak pomocí metody [CPagerCtrl:: SetButtonSize](#setbuttonsize) nastaví výšku ovládacího prvku stránkování na 20 pixelů a metodu [CPagerCtrl:: SetBorder](#setborder) nastaví tloušťku ohraničení na 1 pixel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

Nastaví pozici posunutí aktuálního ovládacího prvku stránkování.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iPos*|pro Nová pozice posunutí měřená v pixelech|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) , která je popsána v Windows SDK.

## <a name="see-also"></a>Viz také:

[CPagerCtrl – třída](../../mfc/reference/cpagerctrl-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Ovládací prvky stránkování](/windows/win32/Controls/pager-controls)
