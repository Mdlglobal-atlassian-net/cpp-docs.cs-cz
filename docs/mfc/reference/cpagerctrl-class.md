---
title: Třída CPagerCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c79fa877023c7a01c4814f61d75a54cb0dd64b51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cpagerctrl-class"></a>CPagerCtrl – třída
`CPagerCtrl` Třída zabalí řízení pager Windows, které můžete přejděte do zobrazení obsažené okno, které nebudou vyhovovat obsahující okno.  
  
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
|[CPagerCtrl::Create](#create)|Vytvoří se zadaný styly ovládacího prvku pager a připojí k aktuální `CPagerCtrl` objektu.|  
|[CPagerCtrl::CreateEx](#createex)|Vytvoří se zadaný rozšířené styly ovládacího prvku pager a připojí k aktuální `CPagerCtrl` objektu.|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Povolí nebo zakáže předávání [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) zprávy do okna je obsažen v ovládacím prvku aktuální pager.|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|Načte barvu pozadí ovládacího prvku aktuální pager.|  
|[CPagerCtrl::GetBorder](#getborder)|Získá velikost ohraničení ovládacího prvku aktuální pager.|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Načte tlačítko velikosti ovládacího prvku aktuální pager.|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Načte stav tlačítko zadaný v ovládacím prvku aktuální pager.|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Načte [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) rozhraní pro aktuální ovládací prvek pager.|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Načte pozici posunutí aktuální ovládacího prvku pager.|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Určuje, zda je dané tlačítko aktuální ovládacího prvku pager v `pressed` stavu.|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Určuje, zda je dané tlačítko aktuální ovládacího prvku pager v `grayed` stavu.|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Určuje, zda je dané tlačítko aktuální ovládacího prvku pager v `hot` stavu.|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Určuje, zda je dané tlačítko aktuální ovládacího prvku pager v `invisible` stavu.|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Určuje, zda je dané tlačítko aktuální ovládacího prvku pager v `normal` stavu.|  
|[CPagerCtrl::RecalcSize](#recalcsize)|Způsobí, že aktuální řízení pager přepočítat velikost okna obsažené.|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ovládacího prvku aktuální pager.|  
|[CPagerCtrl::SetBorder](#setborder)|Nastaví velikost ohraničení ovládacího prvku aktuální pager.|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Nastaví velikost tlačítko aktuální ovládacího prvku pager.|  
|[CPagerCtrl::SetChild](#setchild)|Nastaví obsažené okna pro ovládací prvek aktuální pager.|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Nastaví pozici posunutí aktuální ovládacího prvku pager.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek pager je okno, které obsahuje jiné okno, které je lineární a větší než okno obsahující a umožňuje přejděte do zobrazení okna obsažené. Stránkovací ovládací prvek zobrazí dvě Posunutí tlačítek, které automaticky při přesunut oblasti okno obsažené zmizí jeho nejvíce rozsahu a jinak objevit znova. Můžete vytvořit pager ovládací prvek, který se posouvá společně vodorovně nebo svisle.  
  
 Například pokud aplikace obsahuje panel nástrojů, který není dost široké, a zobrazit všechny jeho položky, můžete přiřadit panelu nástrojů do ovládacího prvku pager a uživatelé budou moci posuňte doleva nebo doprava přístup všechny položky panelu nástrojů. Microsoft Internet Explorer verze 4.0 (verze commctrl.dll 4.71) představuje ovládacího prvku pager.  
  
 `CPagerCtrl` Je třída odvozená z [CWnd](../../mfc/reference/cwnd-class.md) třídy. Obrázek ovládacího prvku pager a další informace najdete v tématu [ovládací prvky Pager](http://msdn.microsoft.com/library/windows/desktop/bb760855).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl  
 Vytvoří `CPagerCtrl` objektu.  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) metodu pro vytvoření ovládacího prvku pager a připojte ji k `CPagerCtrl` objektu.  
  
##  <a name="create"></a>CPagerCtrl::Create  
 Vytvoří se zadaný styly ovládacího prvku pager a připojí k aktuální `CPagerCtrl` objektu.  
  
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
|[v]`dwStyle`|Bitovou kombinaci (nebo) [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [styly ovládacího prvku pager](http://msdn.microsoft.com/library/windows/desktop/bb760859) má být použita pro ovládací prvek.|  
|[v]`rect`|Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje umístění a velikost ovládacího prvku souřadnice klienta.|  
|[v]`pParentWnd`|Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku. Tento parametr nemůže být `NULL`.|  
|[v]`nID`|ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření ovládacího prvku pager, deklarovat `CPagerCtrl` proměnnou, pak volání [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) metoda na tuto proměnnou.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří ovládacího prvku pager a pak používá [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit velmi dlouhé tlačítko – ovládací prvek s ovládacím prvkem pager. V příkladu se pak použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metodu a nastavit pager ovládacího prvku do 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metodu a nastavit tloušťku ohraničení na 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CPagerCtrl::CreateEx  
 Vytvoří se zadaný rozšířené styly ovládacího prvku pager a připojí k aktuální `CPagerCtrl` objektu.  
  
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
|[v]`dwExStyle`|Bitová kombinace rozšířené styly použité pro ovládací prvek. Další informace najdete v tématu `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) funkce.|  
|[v]`dwStyle`|Bitovou kombinaci (nebo) [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [styly ovládacího prvku pager](http://msdn.microsoft.com/library/windows/desktop/bb760859) má být použita pro ovládací prvek.|  
|[v]`rect`|Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje umístění a velikost ovládacího prvku souřadnice klienta.|  
|[v]`pParentWnd`|Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku. Tento parametr nemůže být `NULL`.|  
|[v]`nID`|ID ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření ovládacího prvku pager, deklarovat `CPagerCtrl` proměnnou, pak volání [CPagerCtrl::Create](#create) nebo [CPagerCtrl::CreateEx](#createex) metoda na tuto proměnnou.  
  
##  <a name="forwardmouse"></a>CPagerCtrl::ForwardMouse  
 Povolí nebo zakáže předávání [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) zprávy do okna je obsažen v ovládacím prvku aktuální pager.  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`bForward`|`true`k předávání zpráv myši nebo `false` není předávat zprávy myši.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getborder"></a>CPagerCtrl::GetBorder  
 Získá velikost ohraničení ovládacího prvku aktuální pager.  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální velikost ohraničení měřená v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [CPagerCtrl::GetBorder](#getborder) metoda pro načtení Tloušťka ohraničení ovládacího prvku pager.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="getbkcolor"></a>CPagerCtrl::GetBkColor  
 Načte barvu pozadí ovládacího prvku aktuální pager.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která obsahuje aktuální barva pozadí ovládacího prvku pager.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [CPagerCtrl::SetBkColor](#setbkcolor) metodu a nastavit barvu pozadí ovládacího prvku pager na červený a [CPagerCtrl::GetBkColor](#getbkcolor) metoda potvrďte, že změny.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize  
 Načte tlačítko velikosti ovládacího prvku aktuální pager.  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální velikost tlačítko měřená v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870) zprávy, která je popsána v sadě Windows SDK.  
  
 Pokud se má ovládací prvek pager `PGS_HORZ` styl, velikost tlačítko Určuje šířku tlačítka stránkování, a pokud se má ovládací prvek pager `PGS_VERT` styl, velikost tlačítko Určuje výšku tlačítka stránkování. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
##  <a name="getbuttonstate"></a>CPagerCtrl::GetButtonState  
 Načte stav tlačítko posuvníku zadaný v ovládacím prvku aktuální pager.  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButton`|Určuje, na tlačítko, pro kterou je načíst stav. Pokud je styl řízení pager `PGS_HORZ`, zadejte `PGB_TOPORLEFT` pro levé tlačítko a `PGB_BOTTOMORRIGHT` pro pravé tlačítko. Pokud je styl řízení pager `PGS_VERT`, zadejte `PGB_TOPORLEFT` pro tlačítko horní a `PGB_BOTTOMORRIGHT` pro tlačítko dole. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav tlačítko určeného `iButton` parametr. Stav je buď `PGF_INVISIBLE`, `PGF_NORMAL`, `PGF_GRAYED`, `PGF_DEPRESSED`, nebo `PGF_HOT`. Další informace najdete v tématu části vrátit hodnotu [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getdroptarget"></a>CPagerCtrl::GetDropTarget  
 Načte [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) rozhraní pro aktuální ovládací prvek pager.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `IDropTarget` rozhraní pro aktuální ovládací prvek pager.  
  
### <a name="remarks"></a>Poznámky  
 `IDropTarget`je jedním z rozhraní implementaci pro podporu operací přetažení myší v aplikaci.  
  
 Tato metoda odesílá [PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872) zprávy, která je popsána v sadě Windows SDK. Volající tuto metodu je zodpovědná za volání `Release` členem [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) rozhraní když rozhraní je už nepotřebují.  
  
##  <a name="getscrollpos"></a>CPagerCtrl::GetScrollPos  
 Načte pozici posunutí aktuální ovládacího prvku pager.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Na aktuální pozici posunutí měřená v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [CPagerCtrl::GetScrollPos](#getscrollpos) metoda pro načtení na aktuální pozici posunutí ovládacího prvku pager. Pokud ovládacího prvku pager není již přešli na nulu, levou krajní pozici v příkladu se používá [CPagerCtrl::SetScrollPos](#setscrollpos) metodu a nastavit na pozici posunutí na nulu.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed  
 Určuje, zda tlačítko posuvníku zadaného prvku aktuální pager je ve stavu při stisknutí tlačítka.  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButton`|Určuje, na tlačítko, pro kterou je načíst stav. Pokud je styl řízení pager `PGS_HORZ`, zadejte `PGB_TOPORLEFT` pro levé tlačítko a `PGB_BOTTOMORRIGHT` pro pravé tlačítko. Pokud je styl řízení pager `PGS_VERT`, zadejte `PGB_TOPORLEFT` pro tlačítko horní a `PGB_BOTTOMORRIGHT` pro tlačítko dole. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud zadaný tlačítko je ve stavu při stisknutí tlačítka; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy, která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen `PGF_DEPRESSED`. Další informace najdete v tématu části vrátit hodnotu [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy.  
  
##  <a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed  
 Určuje, zda tlačítko posuvníku zadaného prvku aktuální pager v šedým stavu.  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButton`|Určuje, na tlačítko, pro kterou je načíst stav. Pokud je styl řízení pager `PGS_HORZ`, zadejte `PGB_TOPORLEFT` pro levé tlačítko a `PGB_BOTTOMORRIGHT` pro pravé tlačítko. Pokud je styl řízení pager `PGS_VERT`, zadejte `PGB_TOPORLEFT` pro tlačítko horní a `PGB_BOTTOMORRIGHT` pro tlačítko dole. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je tlačítko zadaný v šedým stavu; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy, která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen `PGF_GRAYED`. Další informace najdete v tématu části vrátit hodnotu [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy.  
  
##  <a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot  
 Určuje, zda aktuální pager ovládacího prvku tlačítko zadaný posuvníku je ve stavu aktivní.  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButton`|Určuje, na tlačítko, pro kterou je načíst stav. Pokud je styl řízení pager `PGS_HORZ`, zadejte `PGB_TOPORLEFT` pro levé tlačítko a `PGB_BOTTOMORRIGHT` pro pravé tlačítko. Pokud je styl řízení pager `PGS_VERT`, zadejte `PGB_TOPORLEFT` pro tlačítko horní a `PGB_BOTTOMORRIGHT` pro tlačítko dole. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je tlačítko zadaný v aktivního stavu; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy, která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen `PGF_HOT`. Další informace najdete v tématu části vrátit hodnotu [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy.  
  
##  <a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible  
 Určuje, zda tlačítko posuvníku zadaného prvku aktuální pager v neviditelná stavu.  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButton`|Určuje, na tlačítko, pro kterou je načíst stav. Pokud je styl řízení pager `PGS_HORZ`, zadejte `PGB_TOPORLEFT` pro levé tlačítko a `PGB_BOTTOMORRIGHT` pro pravé tlačítko. Pokud je styl řízení pager `PGS_VERT`, zadejte `PGB_TOPORLEFT` pro tlačítko horní a `PGB_BOTTOMORRIGHT` pro tlačítko dole. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je tlačítko zadaný v neviditelná stavu; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Windows vytváří tlačítko posuvníku v konkrétní směr neviditelná při okno obsažené přesunut oblasti jeho nejvíce rozsahu vzhledem k tomu, že kliknete na tlačítko Další nelze uvést více okna obsažené do zobrazení.  
  
 Tato metoda odesílá [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy, která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen `PGF_INVISIBLE`. Další informace najdete v tématu části vrátit hodnotu [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) metodu za účelem zjištění, zda je ponecháno ovládacího prvku pager a správné Posunutí tlačítek jsou viditelné.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal  
 Určuje, zda tlačítko posuvníku zadaného prvku aktuální pager v normálním stavu.  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButton`|Určuje, na tlačítko, pro kterou je načíst stav. Pokud je styl řízení pager `PGS_HORZ`, zadejte `PGB_TOPORLEFT` pro levé tlačítko a `PGB_BOTTOMORRIGHT` pro pravé tlačítko. Pokud je styl řízení pager `PGS_VERT`, zadejte `PGB_TOPORLEFT` pro tlačítko horní a `PGB_BOTTOMORRIGHT` pro tlačítko dole. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je tlačítko zadaný v normálním stavu; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy, která je popsána v sadě Windows SDK. Potom testuje, zda je stav, který je vrácen `PGF_NORMAL`. Další informace najdete v tématu části vrátit hodnotu [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) zprávy.  
  
##  <a name="recalcsize"></a>CPagerCtrl::RecalcSize  
 Způsobí, že aktuální řízení pager přepočítat velikost okna obsažené.  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876) zprávy, která je popsána v sadě Windows SDK. V důsledku toho odesílá ovládacího prvku pager [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) oznámení k získání dimenze posuvného okna obsažené.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [CPagerCtrl::RecalcSize](#recalcsize) metoda požádat o prvku aktuální pager přepočítat jeho velikost.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [zprávy reflexe](../../mfc/tn062-message-reflection-for-windows-controls.md) povolit ovládacího prvku pager přepočítat vlastní velikost místo nutnosti dialog nadřazeného ovládacího prvku provést výpočet. V příkladu je odvozena `MyPagerCtrl` třídy z [CPagerCtrl třída](../../mfc/reference/cpagerctrl-class.md), pak použije mapy zpráv pro přidružení [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) oznámení s `OnCalcsize` obslužná rutina oznámení. V tomto příkladu obslužná rutina oznámení Nastaví šířku a výšku ovládacího prvku pager na pevné hodnoty.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="setbkcolor"></a>CPagerCtrl::SetBkColor  
 Nastaví barvu pozadí ovládacího prvku aktuální pager.  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`clrBk`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která obsahuje novou barvu pozadí ovládacího prvku pager.|  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která obsahuje předchozí barvu pozadí ovládacího prvku pager.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad používá [CPagerCtrl::SetBkColor](#setbkcolor) metodu a nastavit barvu pozadí ovládacího prvku pager na červený a [CPagerCtrl::GetBkColor](#getbkcolor) metoda potvrďte, že změny.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="setborder"></a>CPagerCtrl::SetBorder  
 Nastaví velikost ohraničení ovládacího prvku aktuální pager.  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iBorder`|Novou velikost ohraničení měřená v pixelech. Pokud `iBorder` nachází záporný parametr, bude velikost ohraničení nastavena na hodnotu nula.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost předchozí ohraničení měřená v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří ovládacího prvku pager a pak používá [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit velmi dlouhé tlačítko – ovládací prvek s ovládacím prvkem pager. V příkladu se pak použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metodu a nastavit pager ovládacího prvku do 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metodu a nastavit tloušťku ohraničení na 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize  
 Nastaví velikost tlačítko aktuální ovládacího prvku pager.  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iButtonSize`|Velikost nové tlačítko měřená v pixelech.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost předchozí tlačítko měřená v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886) zprávy, která je popsána v sadě Windows SDK.  
  
 Pokud se má ovládací prvek pager `PGS_HORZ` styl, velikost tlačítko Určuje šířku tlačítka stránkování, a pokud se má ovládací prvek pager `PGS_VERT` styl, velikost tlačítko Určuje výšku tlačítka stránkování. Výchozí tlačítko velikost je tříčtvrtinovou šířka posuvníku a tlačítko minimální velikost je 12 pixelů. Další informace najdete v tématu [styly ovládacího prvku Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří ovládacího prvku pager a pak používá [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit velmi dlouhé tlačítko – ovládací prvek s ovládacím prvkem pager. V příkladu se pak použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metodu a nastavit pager ovládacího prvku do 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metodu a nastavit tloušťku ohraničení na 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setchild"></a>CPagerCtrl::SetChild  
 Nastaví obsažené okna pro ovládací prvek aktuální pager.  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hwndChild`|Zpracování do okna být obsaženy.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884) zprávy, která je popsána v sadě Windows SDK.  
  
 Tato metoda se nemění nadřazeného okna obsažené; pouze pro posouvání ovládacího prvku pager přiřadí popisovač okna. Ve většině případů bude okno obsažené podřízeného okna ovládacího prvku pager.  
  
### <a name="example"></a>Příklad  
 Následující příklad vytvoří ovládacího prvku pager a pak používá [CPagerCtrl::SetChild](#setchild) metoda, jak přidružit velmi dlouhé tlačítko – ovládací prvek s ovládacím prvkem pager. V příkladu se pak použije [CPagerCtrl::SetButtonSize](#setbuttonsize) metodu a nastavit pager ovládacího prvku do 20 pixelů a [CPagerCtrl::SetBorder](#setborder) metodu a nastavit tloušťku ohraničení na 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setscrollpos"></a>CPagerCtrl::SetScrollPos  
 Nastaví pozici posunutí aktuální ovládacího prvku pager.  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iPos`|Nové pozici posunutí měřená v pixelech.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886) zprávy, která je popsána v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CPagerCtrl – třída](../../mfc/reference/cpagerctrl-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Ovládací prvky pager](http://msdn.microsoft.com/library/windows/desktop/bb760855)



