---
title: Cpagerctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a582d5de7087e433aed839dc2f55db01dd926f22
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447567"
---
# <a name="cpagerctrl-class"></a>Cpagerctrl – třída

`CPagerCtrl` Třídy obaluje ovládací prvek stránkování Windows, který můžete přejít do zobrazení obsaženého okna obsahujícího okna nevejde.

## <a name="syntax"></a>Syntaxe

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Vytvoří `CPagerCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|Vytvoří ovládací prvek stránkování se zadaným styly a připojí ho k aktuální `CPagerCtrl` objektu.|
|[CPagerCtrl::CreateEx](#createex)|Vytvoří ovládací prvek stránkování se zadaným rozšířené styly a připojí ho k aktuální `CPagerCtrl` objektu.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Povolí nebo zakáže předávání [wm_mousemove a](/windows/desktop/inputdev/wm-mousemove) zprávu do okna, která je součástí aktuální ovládacího prvku stránkování.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Zjišťuje barvu pozadí ovládacího prvku aktuální stránkování.|
|[CPagerCtrl::GetBorder](#getborder)|Získá velikost ohraničení ovládacího prvku aktuální stránkování.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Získá velikost tlačítka aktuálního ovládacího prvku stránkování.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Načte stav určeného tlačítka v ovládacím prvku aktuální stránkování.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Načte [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) rozhraní pro aktuální ovládací prvek stránkování.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Načte pozici posunutí aktuální ovládacího prvku stránkování.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Určuje, zda je zadaný tlačítko aktuální ovládací prvek stránkování v `pressed` stavu.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Určuje, zda je zadaný tlačítko aktuální ovládací prvek stránkování v `grayed` stavu.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Určuje, zda je zadaný tlačítko aktuální ovládací prvek stránkování v `hot` stavu.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Určuje, zda je zadaný tlačítko aktuální ovládací prvek stránkování v `invisible` stavu.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Určuje, zda je zadaný tlačítko aktuální ovládací prvek stránkování v `normal` stavu.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Způsobí, že aktuální ovládacího prvku stránkování přepočítat velikost obsaženého okna.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ovládacího prvku aktuální stránkování.|
|[CPagerCtrl::SetBorder](#setborder)|Nastaví velikost ohraničení ovládacího prvku aktuální stránkování.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Nastaví velikost tlačítka aktuálního ovládacího prvku stránkování.|
|[CPagerCtrl::SetChild](#setchild)|Nastaví obsaženého okna pro ovládací prvek aktuální stránkování.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Nastaví pozici posunutí aktuální ovládacího prvku stránkování.|

## <a name="remarks"></a>Poznámky

Ovládací prvek stránkování je okno, které obsahuje další okno, které je větší než obsahujícího okna a lineární a umožňuje přejděte do zobrazení obsaženého okna. Ovládacího prvku stránkování zobrazí dvě tlačítka pro posunutí, které automaticky zmizí při posunu obsaženého okna jeho nejvíce rozsahu a v opačném případě se zase objeví. Můžete vytvořit ovládací prvek stránkování, který posouvána vodorovně nebo svisle.

Pokud má vaše aplikace, která není dost široký, chcete-li zobrazit všechny jeho položky panelu nástrojů, panelu nástrojů můžete přiřadit do ovládacího prvku stránkování a uživatelé budou moci posunout doleva nebo doprava přístup ke všem položek panelu nástrojů. Microsoft Internet Explorer verze 4.0 (verze commctrl.dll 4.71) představuje ovládacího prvku stránkování.

`CPagerCtrl` Je třída odvozena z [CWnd](../../mfc/reference/cwnd-class.md) třídy. Další informace a ilustraci ovládacího prvku stránkování najdete v tématu [ovládacími prvky stránkování](/windows/desktop/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl

Vytvoří `CPagerCtrl` objektu.

```
CPagerCtrl();
```

### <a name="remarks"></a>Poznámky

Použití [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) metodu pro vytvoření ovládacího prvku stránkování a připojte ji k `CPagerCtrl` objektu.

##  <a name="create"></a>  CPagerCtrl::Create

Vytvoří ovládací prvek stránkování se zadaným styly a připojí ho k aktuální `CPagerCtrl` objektu.

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
|*dwStyle*|[in] Bitová kombinace (nebo) [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles) u ovládacího prvku.|
|*Rect*|[in] Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která obsahuje umístění a velikost ovládacího prvku, v souřadnicích klienta.|
|*pParentWnd*|[in] Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku. Tento parametr nemůže mít hodnotu NULL.|
|*nID*|[in] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit ovládací prvek stránkování, deklarujte `CPagerCtrl` proměnnou, zavolejte [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) metoda u této proměnné.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a pak pomocí [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit ovládací prvek velmi dlouhý tlačítko s ovládacím prvkem pager. Příklad poté použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metody nastavte výšku ovládacího prvku stránkování na 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metody nastavte tloušťku ohraničení 1 pixelu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>  CPagerCtrl::CreateEx

Vytvoří ovládací prvek stránkování se zadaným rozšířené styly a připojí ho k aktuální `CPagerCtrl` objektu.

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
|*dwExStyle*|[in] Bitová kombinace hodnot rozšířené styly pro ovládací prvek. Další informace najdete v tématu *dwExStyle* parametr [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) funkce.|
|*dwStyle*|[in] Bitová kombinace (nebo) [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles) u ovládacího prvku.|
|*Rect*|[in] Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která obsahuje umístění a velikost ovládacího prvku, v souřadnicích klienta.|
|*pParentWnd*|[in] Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku. Tento parametr nemůže mít hodnotu NULL.|
|*nID*|[in] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit ovládací prvek stránkování, deklarujte `CPagerCtrl` proměnnou, zavolejte [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) metoda u této proměnné.

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

Povolí nebo zakáže předávání [wm_mousemove a](/windows/desktop/inputdev/wm-mousemove) zprávu do okna, která je součástí aktuální ovládacího prvku stránkování.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bForward*|[in] True pro zprávy týkající se myši dopředu, nebo hodnotu NEPRAVDA nelze předávat zprávy týkající se myši.|

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_FORWARDMOUSE](/windows/desktop/Controls/pgm-forwardmouse) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

Získá velikost ohraničení ovládacího prvku aktuální stránkování.

```
int GetBorder() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost ohraničení měřená v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBORDER](/windows/desktop/Controls/pgm-getborder) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

V následujícím příkladu [CPagerCtrl::GetBorder](#getborder) metodu pro načtení Tloušťka ohraničení ovládacího prvku stránkování.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

Zjišťuje barvu pozadí ovládacího prvku aktuální stránkování.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Návratová hodnota

A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která obsahuje aktuální barva pozadí ovládacího prvku stránkování.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBKCOLOR](/windows/desktop/Controls/pgm-getbkcolor) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá [CPagerCtrl::SetBkColor](#setbkcolor) metodu a nastavit barvu pozadí ovládacího prvku stránkování na červený, tak i [CPagerCtrl::GetBkColor](#getbkcolor) metody pro potvrzení, že byla změněna.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize

Získá velikost tlačítka aktuálního ovládacího prvku stránkování.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální velikost tlačítka měřená v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBUTTONSIZE](/windows/desktop/Controls/pgm-getbuttonsize) zprávu, která je popsána v sadě Windows SDK.

Pokud je ovládací prvek stránkování PGS_HORZ styl, velikost tlačítka Určuje šířku tlačítka stránkování a pokud PGS_VERT stylu ovládacího prvku stránkování, velikost tlačítka Určuje výšku tlačítka stránkování. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

Načte stav tlačítko zadané posouvání v ovládacím prvku aktuální stránkování.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|[in] Určuje tlačítko, pro který je načten do stavu. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte pro tlačítko vlevo a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro pravým tlačítkem. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte pro tlačítko nahoře a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro tlačítko dole. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Stav tlačítka určené *iButton* parametru. Stav je buď PGF_INVISIBLE PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED či PGF_HOT. Další informace najdete v části vrátit hodnotu z [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávy.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

Načte [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) rozhraní pro aktuální ovládací prvek stránkování.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `IDropTarget` rozhraní pro aktuální ovládací prvek stránkování.

### <a name="remarks"></a>Poznámky

`IDropTarget` je jedním z rozhraní implementaci pro podporu operací přetažení myší ve vaší aplikaci.

Tato metoda odesílá [PGM_GETDROPTARGET](/windows/desktop/Controls/pgm-getdroptarget) zprávu, která je popsána v sadě Windows SDK. Volající této metody je zodpovědná za volání `Release` člena [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) rozhraní, pokud rozhraní je už nepotřebujete.

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

Načte pozici posunutí aktuální ovládacího prvku stránkování.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální pozice posuvníku, měřeno v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETPOS](/windows/desktop/Controls/pgm-getpos) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

V následujícím příkladu [CPagerCtrl::GetScrollPos](#getscrollpos) metody k získání aktuální pozici posunutí ovládacího prvku stránkování. Pokud ovládacího prvku stránkování není již přešli na nulu, úplně vlevo pozice v příkladu se používá [CPagerCtrl::SetScrollPos](#setscrollpos) metody nastavte pozici posunutí na nulu.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

Označuje, zda tlačítko zadané posouvání aktuálního ovládacího prvku stránkování je ve stavu při stisknutí tlačítka.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|[in] Určuje tlačítko, pro který je načten do stavu. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte pro tlačítko vlevo a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro pravým tlačítkem. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte pro tlačítko nahoře a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro tlačítko dole. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud zadaný tlačítko je ve stavu při stisknutí; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávu, která je popsána v sadě Windows SDK. Pak ověřuje, jestli je stav, který je vrácen PGF_DEPRESSED. Další informace najdete v části vrátit hodnotu z [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávy.

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

Označuje, zda tlačítko zadané posouvání aktuálního ovládacího prvku stránkování v potlačených stavu.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|[in] Určuje tlačítko, pro který je načten do stavu. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte pro tlačítko vlevo a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro pravým tlačítkem. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte pro tlačítko nahoře a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro tlačítko dole. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je zadaný tlačítko v potlačených stavu; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávu, která je popsána v sadě Windows SDK. Pak ověřuje, jestli je stav, který je vrácen PGF_GRAYED. Další informace najdete v části vrátit hodnotu z [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávy.

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

Označuje, zda tlačítko zadané posouvání aktuálního ovládacího prvku stránkování v horkém stavu.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|[in] Určuje tlačítko, pro který je načten do stavu. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte pro tlačítko vlevo a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro pravým tlačítkem. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte pro tlačítko nahoře a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro tlačítko dole. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je zadaný tlačítko v horkém stavu; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávu, která je popsána v sadě Windows SDK. Pak ověřuje, jestli je stav, který je vrácen PGF_HOT. Další informace najdete v části vrátit hodnotu z [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávy.

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

Označuje, zda tlačítko zadané posouvání aktuálního ovládacího prvku stránkování je ve stavu neviditelné.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|[in] Určuje tlačítko, pro který je načten do stavu. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte pro tlačítko vlevo a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro pravým tlačítkem. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte pro tlačítko nahoře a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro tlačítko dole. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud zadaný tlačítko je ve stavu neviditelné; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Windows díky tlačítko posouvání v konkrétní směr neviditelné při obsaženého okna je přechod na jeho nejvíce rozsah, protože kliknutím na tlačítko Další nelze uvést do režimu více obsaženého okna do zobrazení.

Tato metoda odesílá [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávu, která je popsána v sadě Windows SDK. Pak ověřuje, jestli je stav, který je vrácen PGF_INVISIBLE. Další informace najdete v části vrátit hodnotu z [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávy.

### <a name="example"></a>Příklad

V následujícím příkladu [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) metodou ke zjištění, zda ovládací prvek stránkování levým a tlačítka pro posunutí doprava jsou viditelné.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

Označuje, zda tlačítko zadané posouvání aktuálního ovládacího prvku stránkování v normálním stavu.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButton*|[in] Určuje tlačítko, pro který je načten do stavu. Pokud je styl ovládacího prvku stránkování PGS_HORZ, zadejte pro tlačítko vlevo a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro pravým tlačítkem. Pokud je styl ovládacího prvku stránkování PGS_VERT, zadejte pro tlačítko nahoře a PGB_BOTTOMORRIGHT PGB_TOPORLEFT pro tlačítko dole. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je zadaný tlačítko v normálním stavu; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávu, která je popsána v sadě Windows SDK. Pak ověřuje, jestli je stav, který je vrácen PGF_NORMAL. Další informace najdete v části vrátit hodnotu z [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) zprávy.

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

Způsobí, že aktuální ovládacího prvku stránkování přepočítat velikost obsaženého okna.

```
void RecalcSize();
```

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_RECALCSIZE](/windows/desktop/Controls/pgm-recalcsize) zprávu, která je popsána v sadě Windows SDK. V důsledku toho odesílá ovládacího prvku stránkování [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) oznámení k získání posuvný dimenze obsaženého okna.

### <a name="example"></a>Příklad

V následujícím příkladu [CPagerCtrl::RecalcSize](#recalcsize) metodu pro žádost o aktuální ovládacího prvku stránkování přepočítat její velikost.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Příklad

Následující příklad používá [zprávy reflexe](../../mfc/tn062-message-reflection-for-windows-controls.md) k povolte stažení ovládacího prvku stránkování přepočítat vlastní velikost nemusíte mít nadřazeného ovládacího prvku dialogu k provedení výpočtu. V příkladu je odvozena `MyPagerCtrl` třídy z [cpagerctrl – třída](../../mfc/reference/cpagerctrl-class.md), pak používá mapy zpráv pro přiřazení [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) oznámení `OnCalcsize` obslužné rutina oznámení. V tomto příkladu nastaví obslužnou rutinu oznámení šířku a výšku ovládacího prvku stránkování na pevné hodnoty.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Nastaví barvu pozadí ovládacího prvku aktuální stránkování.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*clrBk*|[in] A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která obsahuje novou barvu pozadí ovládacího prvku stránkování.|

### <a name="return-value"></a>Návratová hodnota

A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která obsahuje na předchozí barvu pozadí ovládacího prvku stránkování.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_SETBKCOLOR](/windows/desktop/Controls/pgm-setbkcolor) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad používá [CPagerCtrl::SetBkColor](#setbkcolor) metodu a nastavit barvu pozadí ovládacího prvku stránkování na červený, tak i [CPagerCtrl::GetBkColor](#getbkcolor) metody pro potvrzení, že byla změněna.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Nastaví velikost ohraničení ovládacího prvku aktuální stránkování.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iBorder*|[in] Nová velikost ohraničení měřená v pixelech. Pokud *iBorder* nachází záporný parametr, velikost ohraničení je nastavena na hodnotu nula.|

### <a name="return-value"></a>Návratová hodnota

Předchozí velikost ohraničení měřená v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_SETBORDER](/windows/desktop/Controls/pgm-setborder) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a pak pomocí [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit ovládací prvek velmi dlouhý tlačítko s ovládacím prvkem pager. Příklad poté použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metody nastavte výšku ovládacího prvku stránkování na 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metody nastavte tloušťku ohraničení 1 pixelu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

Nastaví velikost tlačítka aktuálního ovládacího prvku stránkování.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iButtonSize*|[in] Nová velikost tlačítka měřená v pixelech.|

### <a name="return-value"></a>Návratová hodnota

Předchozí velikost tlačítka měřená v pixelech.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_SETBUTTONSIZE](/windows/desktop/Controls/pgm-setpos) zprávu, která je popsána v sadě Windows SDK.

Pokud je ovládací prvek stránkování PGS_HORZ styl, velikost tlačítka Určuje šířku tlačítka stránkování a pokud PGS_VERT stylu ovládacího prvku stránkování, velikost tlačítka Určuje výšku tlačítka stránkování. Tři čtvrtiny šířka posuvníku je výchozí velikost tlačítka a tlačítka minimální velikost je 12 pixelů. Další informace najdete v tématu [– styly ovládacího prvku stránkování](/windows/desktop/Controls/pager-control-styles).

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a pak pomocí [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit ovládací prvek velmi dlouhý tlačítko s ovládacím prvkem pager. Příklad poté použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metody nastavte výšku ovládacího prvku stránkování na 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metody nastavte tloušťku ohraničení 1 pixelu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

Nastaví obsaženého okna pro ovládací prvek aktuální stránkování.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*hwndChild*|[in] Popisovač okna, které mají být obsažena.|

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_SETCHILD](/windows/desktop/Controls/pgm-setchild) zprávu, která je popsána v sadě Windows SDK.

Tato metoda nezmění nadřazené okno omezením. pouze přiřadí popisovač okna ovládacího prvku stránkování pro posouvání. Ve většině případů bude obsaženého okna podřízeného okna ovládacího prvku stránkování.

### <a name="example"></a>Příklad

Následující příklad vytvoří ovládací prvek stránkování a pak pomocí [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit ovládací prvek velmi dlouhý tlačítko s ovládacím prvkem pager. Příklad poté použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metody nastavte výšku ovládacího prvku stránkování na 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metody nastavte tloušťku ohraničení 1 pixelu.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

Nastaví pozici posunutí aktuální ovládacího prvku stránkování.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iPos*|[in] Na nové pozici posunutí měřená v pixelech.|

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [PGM_SETPOS](/windows/desktop/Controls/pgm-setpos) zprávu, která je popsána v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[CPagerCtrl – třída](../../mfc/reference/cpagerctrl-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Ovládacími prvky stránkování](/windows/desktop/Controls/pager-controls)



