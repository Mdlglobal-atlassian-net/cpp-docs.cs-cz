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
ms.openlocfilehash: cd27a3acf26abe39831089546df317679f2ecab6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753700"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl – třída

Třída `CPagerCtrl` obtéká ovládací prvek stránkovače systému Windows, který lze posunout do zobrazení obsažené okno, které se nevejde obsahující okno.

## <a name="syntax"></a>Syntaxe

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Vytvoří `CPagerCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPagerCtrl::Vytvořit](#create)|Vytvoří ovládací prvek pageru se zadanými `CPagerCtrl` styly a připojí jej k aktuálnímu objektu.|
|[CPagerCtrl::CreateEx](#createex)|Vytvoří ovládací prvek pageru se zadanými rozšířenými styly a připojí jej k aktuálnímu `CPagerCtrl` objektu.|
|[CPagerCtrl::Přesměrovávač myši](#forwardmouse)|Povolí nebo zakáže předávání [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) zpráv do okna, které je obsaženo v aktuálním ovládacím prvku pageru.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Načte barvu pozadí aktuálního ovládacího prvku pageru.|
|[CPagerCtrl::GetBorder](#getborder)|Načte velikost ohraničení aktuálního ovládacího prvku pageru.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Načte velikost tlačítka aktuálního ovládacího prvku pager.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Načte stav zadaného tlačítka v aktuálním ovládacím prvku pageru.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Načte rozhraní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pro aktuální ovládací prvek operátoru.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Načte pozici posouvání aktuálního ovládacího prvku pageru.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Označuje, zda je zadané tlačítko aktuálního `pressed` ovládacího prvku pageru ve stavu.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Označuje, zda je zadané tlačítko aktuálního `grayed` ovládacího prvku pageru ve stavu.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Označuje, zda je zadané tlačítko aktuálního `hot` ovládacího prvku pageru ve stavu.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Označuje, zda je zadané tlačítko aktuálního `invisible` ovládacího prvku pageru ve stavu.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Označuje, zda je zadané tlačítko aktuálního `normal` ovládacího prvku pageru ve stavu.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Způsobí, že aktuální ovládací prvek pageru přepočítat velikost obsaženého okna.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí aktuálního ovládacího prvku pageru.|
|[CPagerCtrl::SetBorder](#setborder)|Nastaví velikost ohraničení aktuálního ovládacího prvku pageru.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Nastaví velikost tlačítka aktuálního ovládacího prvku pageru.|
|[CPagerCtrl::SetChild](#setchild)|Nastaví uzavřené okno pro aktuální ovládací prvek pageru.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Nastaví pozici posouvání aktuálního ovládacího prvku pageru.|

## <a name="remarks"></a>Poznámky

Pager ovládací prvek je okno, které obsahuje jiné okno, které je lineární a větší než obsahující okno a umožňuje posunout obsažené okno do zobrazení. Ovládací prvek pager zobrazí dvě tlačítka posouvání, která automaticky zmizí, když je obsažené okno posunuto do nejvzdálenějšího rozsahu, a znovu se zobrazí jinak. Můžete vytvořit ovládací prvek operátoru, který se posouvá vodorovně nebo svisle.

Pokud má například aplikace panel nástrojů, který není dostatečně široký, aby zobrazoval všechny jeho položky, můžete panel nástrojů přiřadit ovládacímu prvku operátora a uživatelé budou moci posunout panel nástrojů doleva nebo doprava, aby získali přístup ke všem položkám. Aplikace Microsoft Internet Explorer verze 4.0 (commctrl.dll verze 4.71) zavádí ovládací prvek pager.

Třída `CPagerCtrl` je odvozena z [CWnd](../../mfc/reference/cwnd-class.md) třídy. Další informace a ilustraci ovládacího prvku pageru naleznete v tématu [Pager Controls](/windows/win32/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl

Vytvoří `CPagerCtrl` objekt.

```
CPagerCtrl();
```

### <a name="remarks"></a>Poznámky

Pomocí metody [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) vytvořte ovládací prvek `CPagerCtrl` pageru a připojte jej k objektu.

## <a name="cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::Vytvořit

Vytvoří ovládací prvek pageru se zadanými `CPagerCtrl` styly a připojí jej k aktuálnímu objektu.

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
|*dwStyl*|[v] Bitová kombinace (OR) [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a stylů [ovládacího prvku pageru,](/windows/win32/Controls/pager-control-styles) která má být použita na ovládací prvek.|
|*Rect*|[v] Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která obsahuje umístění a velikost ovládacího prvku v souřadnicích klienta.|
|*pParentWnd*|[v] Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku. Tento parametr nemůže mít hodnotu NULL.|
|*Nid*|[v] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit ovládací prvek `CPagerCtrl` pager, deklarujte proměnnou a pak zavolejte metodu [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) u této proměnné.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek pageru a potom použije metodu [CPagerCtrl::SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku operátoru. V příkladu pak používá metodu [CPagerCtrl::SetButtonSize](#setbuttonsize) k nastavení výšky ovládacího prvku pageru na 20 pixelů a metoda [CPagerCtrl::SetBorder](#setborder) pro nastavení tloušťky ohraničení na 1 obrazový bod.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::CreateEx

Vytvoří ovládací prvek pageru se zadanými rozšířenými styly a připojí jej k aktuálnímu `CPagerCtrl` objektu.

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
|*dwExStyl*|[v] Bitová kombinace rozšířených stylů, které mají být použity na ovládací prvek. Další informace naleznete v parametru *dwExStyle* funkce [CreateWindowEx.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*dwStyl*|[v] Bitová kombinace (OR) [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a stylů [ovládacího prvku pageru,](/windows/win32/Controls/pager-control-styles) která má být použita na ovládací prvek.|
|*Rect*|[v] Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která obsahuje umístění a velikost ovládacího prvku v souřadnicích klienta.|
|*pParentWnd*|[v] Ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku. Tento parametr nemůže mít hodnotu NULL.|
|*Nid*|[v] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit ovládací prvek `CPagerCtrl` pager, deklarujte proměnnou a pak zavolejte metodu [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) u této proměnné.

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::Přesměrovávač myši

Povolí nebo zakáže předávání [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) zpráv do okna, které je obsaženo v aktuálním ovládacím prvku pageru.

```cpp
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bVpřed*|[v] TRUE předávat zprávy myši nebo FALSE nepředávat zprávy myši.|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_FORWARDMOUSE,](/windows/win32/Controls/pgm-forwardmouse) která je popsána v sadě Windows SDK.

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::GetBorder

Načte velikost ohraničení aktuálního ovládacího prvku pageru.

```
int GetBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost ohraničení měřená v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBORDER,](/windows/win32/Controls/pgm-getborder) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá [metodu CPagerCtrl::GetBorder](#getborder) k načtení tloušťky ohraničení ovládacího prvku pageru.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl::GetBkColor

Načte barvu pozadí aktuálního ovládacího prvku pageru.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

[Colorref](/windows/win32/gdi/colorref) hodnota, která obsahuje aktuální barvu pozadí ovládacího prvku operátoru.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBKCOLOR,](/windows/win32/Controls/pgm-getbkcolor) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl::SetBkColor](#setbkcolor) k nastavení barvy pozadí ovládacího prvku pageru na červenou a metodu [CPagerCtrl::GetBkColor](#getbkcolor) k potvrzení, že změna byla provedena.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize

Načte velikost tlačítka aktuálního ovládacího prvku pager.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost tlačítka měřená v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBUTTONSIZE,](/windows/win32/Controls/pgm-getbuttonsize) která je popsána v sadě Windows SDK.

Pokud má ovládací prvek pager styl PGS_HORZ, velikost tlačítka určuje šířku tlačítek operátoru a pokud má ovládací prvek pager PGS_VERT styl, velikost tlačítka určuje výšku tlačítek operátoru. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::GetButtonState

Načte stav zadaného tlačítka posouvání v aktuálním ovládacím prvku pageru.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*tlačítko iButton*|[v] Označuje tlačítko, pro které je načten stav. Pokud je styl ovládacího prvku pageru PGS_HORZ, zadejte PGB_TOPORLEFT pro levé tlačítko a PGB_BOTTOMORRIGHT pro pravé tlačítko. Pokud je styl ovládacího prvku operátoru PGS_VERT, zadejte PGB_TOPORLEFT pro horní tlačítko a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Stav tlačítka určeného parametrem *iButton.* Stát je buď PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED nebo PGF_HOT. Další informace naleznete v části Vrácená hodnota [zprávy PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) která je popsána v sadě Windows SDK.

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::GetDropTarget

Načte rozhraní [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) pro aktuální ovládací prvek operátoru.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `IDropTarget` rozhraní pro aktuální ovládací prvek pageru.

### <a name="remarks"></a>Poznámky

`IDropTarget`je jedním z rozhraní, které implementujete pro podporu operací přetažení myší ve vaší aplikaci.

Tato metoda odešle [zprávu PGM_GETDROPTARGET,](/windows/win32/Controls/pgm-getdroptarget) která je popsána v sadě Windows SDK. Volající této metody je zodpovědný `Release` za volání člena rozhraní [IDropTarget,](/windows/win32/api/oleidl/nn-oleidl-idroptarget) když rozhraní již není potřeba.

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::GetScrollPos

Načte pozici posouvání aktuálního ovládacího prvku pageru.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice posouvání měřená v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETPOS,](/windows/win32/Controls/pgm-getpos) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl::GetScrollPos](#getscrollpos) k načtení aktuální pozice posouvání ovládacího prvku pageru. Pokud ovládací prvek pager ještě není posunut na nulu, pozice nejvíce vlevo, příklad používá [Metodu CPagerCtrl::SetScrollPos](#setscrollpos) k nastavení polohy posouvání na nulu.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed

Označuje, zda je zadané tlačítko posouvání aktuálního ovládacího prvku pageru stisknuto.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*tlačítko iButton*|[v] Označuje tlačítko, pro které je načten stav. Pokud je styl ovládacího prvku pageru PGS_HORZ, zadejte PGB_TOPORLEFT pro levé tlačítko a PGB_BOTTOMORRIGHT pro pravé tlačítko. Pokud je styl ovládacího prvku operátoru PGS_VERT, zadejte PGB_TOPORLEFT pro horní tlačítko a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zadané tlačítko stisknuto; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen, PGF_DEPRESSED. Další informace naleznete v části Vrácená hodnota [zprávy PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed

Označuje, zda je zadané tlačítko posouvání aktuálního ovládacího prvku pageru v šedě.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*tlačítko iButton*|[v] Označuje tlačítko, pro které je načten stav. Pokud je styl ovládacího prvku pageru PGS_HORZ, zadejte PGB_TOPORLEFT pro levé tlačítko a PGB_BOTTOMORRIGHT pro pravé tlačítko. Pokud je styl ovládacího prvku operátoru PGS_VERT, zadejte PGB_TOPORLEFT pro horní tlačítko a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je zadané tlačítko v šedém stavu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen, PGF_GRAYED. Další informace naleznete v části Vrácená hodnota [zprávy PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot

Označuje, zda je zadané tlačítko posouvání aktuálního ovládacího prvku pageru v horkém stavu.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*tlačítko iButton*|[v] Označuje tlačítko, pro které je načten stav. Pokud je styl ovládacího prvku pageru PGS_HORZ, zadejte PGB_TOPORLEFT pro levé tlačítko a PGB_BOTTOMORRIGHT pro pravé tlačítko. Pokud je styl ovládacího prvku operátoru PGS_VERT, zadejte PGB_TOPORLEFT pro horní tlačítko a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v horkém stavu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) která je popsána v sadě Windows SDK. Potom testuje, zda je PGF_HOT stav, který je vrácen. Další informace naleznete v části Vrácená hodnota [zprávy PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible

Označuje, zda je zadané tlačítko posouvání aktuálního ovládacího prvku pageru v neviditelném stavu.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*tlačítko iButton*|[v] Označuje tlačítko, pro které je načten stav. Pokud je styl ovládacího prvku pageru PGS_HORZ, zadejte PGB_TOPORLEFT pro levé tlačítko a PGB_BOTTOMORRIGHT pro pravé tlačítko. Pokud je styl ovládacího prvku operátoru PGS_VERT, zadejte PGB_TOPORLEFT pro horní tlačítko a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v neviditelném stavu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Systém Windows zneviditelní rolovací tlačítko v určitém směru, když je uzavřené okno posunuto do nejdále, protože dalším klepnutím na tlačítko nelze zobrazit více obsaženého okna.

Tato metoda odešle [zprávu PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) která je popsána v sadě Windows SDK. Potom testuje, zda je vrácený stav PGF_INVISIBLE. Další informace naleznete v části Vrácená hodnota [zprávy PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) k určení, zda jsou zobrazena tlačítka pro posouvání ovládacího prvku pageru.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal

Označuje, zda je zadané tlačítko posouvání aktuálního ovládacího prvku pageru v normálním stavu.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*tlačítko iButton*|[v] Označuje tlačítko, pro které je načten stav. Pokud je styl ovládacího prvku pageru PGS_HORZ, zadejte PGB_TOPORLEFT pro levé tlačítko a PGB_BOTTOMORRIGHT pro pravé tlačítko. Pokud je styl ovládacího prvku operátoru PGS_VERT, zadejte PGB_TOPORLEFT pro horní tlačítko a PGB_BOTTOMORRIGHT pro dolní tlačítko. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zadané tlačítko v normálním stavu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_GETBUTTONSTATE,](/windows/win32/Controls/pgm-getbuttonstate) která je popsána v sadě Windows SDK. Potom testuje, zda je PGF_NORMAL stav, který je vrácen. Další informace naleznete v části Vrácená hodnota [zprávy PGM_GETBUTTONSTATE.](/windows/win32/Controls/pgm-getbuttonstate)

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl::RecalcSize

Způsobí, že aktuální ovládací prvek pageru přepočítat velikost obsaženého okna.

```cpp
void RecalcSize();
```

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_RECALCSIZE,](/windows/win32/Controls/pgm-recalcsize) která je popsána v sadě Windows SDK. V důsledku toho ovládací prvek operátor odešle [oznámení PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) získat posuvné rozměry obsažené okno.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl::RecalcSize](#recalcsize) k vyžádání aktuálního ovládacího prvku pageru pro přepočítání jeho velikosti.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Příklad

Následující příklad používá [odraz zprávy](../../mfc/tn062-message-reflection-for-windows-controls.md) k tomu, aby ovládací prvek operátoru přepočítal vlastní velikost namísto toho, aby k provedení výpočtu vyžadoval nadřazený dialog ovládacího prvku. Příklad odvozuje `MyPagerCtrl` třídu z [třídy CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)a potom pomocí mapy `OnCalcsize` zpráv přidruží oznámení [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) k obslužné rutině oznámení. V tomto příkladu obslužná rutina oznámení nastaví šířku a výšku ovládacího prvku pageru na pevné hodnoty.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl::SetBkColor

Nastaví barvu pozadí aktuálního ovládacího prvku pageru.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*clrBk*|[v] [Colorref](/windows/win32/gdi/colorref) hodnota, která obsahuje novou barvu pozadí ovládacího prvku operátoru.|

### <a name="return-value"></a>Návratová hodnota

[Colorref](/windows/win32/gdi/colorref) hodnota, která obsahuje předchozí barvu pozadí ovládacího prvku operátoru.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_SETBKCOLOR,](/windows/win32/Controls/pgm-setbkcolor) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá metodu [CPagerCtrl::SetBkColor](#setbkcolor) k nastavení barvy pozadí ovládacího prvku pageru na červenou a metodu [CPagerCtrl::GetBkColor](#getbkcolor) k potvrzení, že změna byla provedena.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::SetBorder

Nastaví velikost ohraničení aktuálního ovládacího prvku pageru.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iHraniční*|[v] Nová velikost ohraničení měřená v pixelech. Pokud je parametr *iBorder* záporný, je velikost ohraničení nastavena na nulu.|

### <a name="return-value"></a>Návratová hodnota

Předchozí velikost ohraničení měřená v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_SETBORDER,](/windows/win32/Controls/pgm-setborder) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek pageru a potom použije metodu [CPagerCtrl::SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku operátoru. V příkladu pak používá metodu [CPagerCtrl::SetButtonSize](#setbuttonsize) k nastavení výšky ovládacího prvku pageru na 20 pixelů a metoda [CPagerCtrl::SetBorder](#setborder) pro nastavení tloušťky ohraničení na 1 obrazový bod.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize

Nastaví velikost tlačítka aktuálního ovládacího prvku pageru.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButtonSize*|[v] Nová velikost tlačítka měřená v pixelech.|

### <a name="return-value"></a>Návratová hodnota

Předchozí velikost tlačítka měřená v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_SETBUTTONSIZE,](/windows/win32/Controls/pgm-setpos) která je popsána v sadě Windows SDK.

Pokud má ovládací prvek pager styl PGS_HORZ, velikost tlačítka určuje šířku tlačítek operátoru a pokud má ovládací prvek pager PGS_VERT styl, velikost tlačítka určuje výšku tlačítek operátoru. Výchozí velikost tlačítka je tři čtvrtiny šířky posuvníku a minimální velikost tlačítka je 12 pixelů. Další informace naleznete v tématu [Pager Control Styles](/windows/win32/Controls/pager-control-styles).

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek pageru a potom použije metodu [CPagerCtrl::SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku operátoru. V příkladu pak používá metodu [CPagerCtrl::SetButtonSize](#setbuttonsize) k nastavení výšky ovládacího prvku pageru na 20 pixelů a metoda [CPagerCtrl::SetBorder](#setborder) pro nastavení tloušťky ohraničení na 1 obrazový bod.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild

Nastaví uzavřené okno pro aktuální ovládací prvek pageru.

```cpp
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*hwndChild řekl:*|[v] Popisovač do okna, které má být obsaženo.|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_SETCHILD,](/windows/win32/Controls/pgm-setchild) která je popsána v sadě Windows SDK.

Tato metoda nezmění nadřazené obsažené okno; přiřadí pouze popisovač okna ovládacímu prvku pageru pro posouvání. Ve většině případů bude obsažené okno podřízené okno ovládacího prvku operátoru.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek pageru a potom použije metodu [CPagerCtrl::SetChild](#setchild) k přidružení velmi dlouhého ovládacího prvku tlačítka k ovládacímu prvku operátoru. V příkladu pak používá metodu [CPagerCtrl::SetButtonSize](#setbuttonsize) k nastavení výšky ovládacího prvku pageru na 20 pixelů a metoda [CPagerCtrl::SetBorder](#setborder) pro nastavení tloušťky ohraničení na 1 obrazový bod.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::SetScrollPos

Nastaví pozici posouvání aktuálního ovládacího prvku pageru.

```cpp
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ipo*|[v] Nová pozice posouvání měřená v pixelech.|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu PGM_SETPOS,](/windows/win32/Controls/pgm-setpos) která je popsána v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[CPagerCtrl – třída](../../mfc/reference/cpagerctrl-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Ovládací prvky pageru](/windows/win32/Controls/pager-controls)
