---
title: "CHotKeyCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 982d4dec9c00490248da0b0e0dec7fd44376c218
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl – třída
Poskytuje funkci běžné aktivní klíče ovládacího prvku Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Vytvoří `CHotKeyCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHotKeyCtrl::Create](#create)|Vytvoří ovládacího prvku klávesová zkratka a připojí jej k `CHotKeyCtrl` objektu.|  
|[CHotKeyCtrl::CreateEx](#createex)|Vytvoří zadaný Windows rozšířené styly ovládacího prvku klávesová zkratka a připojí jej k `CHotKeyCtrl` objektu.|  
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Načte virtuální klíče kód a modifikátor příznaky aktivní klíče z ovládacího prvku klávesová zkratka.|  
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Načte název klíče místní znakové sady, přiřazené klávesové zkratky.|  
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Načte název klíče místní znakové sady, přiřazena ke kódu zadaný virtuální klíče.|  
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Nastaví aktivní kombinace kláves pro ovládacího prvku klávesová zkratka.|  
|[CHotKeyCtrl::SetRules](#setrules)|Definuje neplatná kombinace a výchozí modifikátor kombinace pro ovládacího prvku klávesová zkratka.|  
  
## <a name="remarks"></a>Poznámky  
 "Ovládacího prvku klávesová zkratka" je okno, které umožňuje uživatelům vytvořit klávesové zkratky. "Klávesové zkratky" je kombinace klíče, který může uživatel stisknout k provedení akce rychle. (Například uživatel může vytvořit klávesové zkratky, která aktivuje okno daného a, zobrazí se na začátek pořadí vykreslování.) Aktivní klíče ovládací prvek zobrazí volby uživatele a zajistí, že uživatel vybere platnou kombinaci.  
  
 Tento ovládací prvek (a proto `CHotKeyCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Při výběru kombinaci kláves uživatelem aplikace můžete načíst zadaný kombinace kláves z ovládacího prvku a použít **WM_SETHOTKEY** zpráva nastavit klávesové zkratky v systému. Vždy, když uživatel stisknutím klávesové zkratky následně z jakékoliv části systému okno specifikované v **WM_SETHOTKEY** zprávu přijme `WM_SYSCOMMAND` zadání zprávy **SC_HOTKEY**. Tato zpráva aktivuje okně, které ji přijme. Klávesové zkratky zůstává platná do aplikace, která volá **WM_SETHOTKEY** ukončí.  
  
 Tento mechanismus se liší od aktivního klíče podpory, které závisí na **WM_HOTKEY** zprávu a Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) a [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) funkce.  
  
 Další informace o používání `CHotKeyCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl  
 Vytvoří `CHotKeyCtrl` objektu.  
  
```  
CHotKeyCtrl();
```  
  
##  <a name="create"></a>CHotKeyCtrl::Create  
 Vytvoří ovládacího prvku klávesová zkratka a připojí jej k `CHotKeyCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl aktivní klíče ovládacího prvku. Použijte libovolnou kombinaci styly ovládacího prvku. V tématu [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) ve Windows SDK pro další informace.  
  
 `rect`  
 Určuje velikost a umístění aktivního klíče ovládacího prvku. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect – struktura](../../mfc/reference/rect-structure1.md).  
  
 `pParentWnd`  
 Určuje aktivní klíče řízení nadřazené okno, obvykle [CDialog](../../mfc/reference/cdialog-class.md). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID aktivního klíče ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CHotKeyCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří prvku aktivního klíče a připojí jej k `CHotKeyCtrl` objektu.  
  
 Pokud chcete použít rozšířené windows styly s ovládacím prvkem, zavolejte [CreateEx](#createex) místo **vytvořit**.  
  
##  <a name="createex"></a>CHotKeyCtrl::CreateEx  
 Volání této funkce vytvoření ovládacího prvku (podřízeného okna) a její přidružení `CHotKeyCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje styl aktivní klíče ovládacího prvku. Použijte libovolnou kombinaci styly ovládacího prvku. Další informace najdete v tématu [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) ve Windows SDK.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="gethotkey"></a>CHotKeyCtrl::GetHotKey  
 Načte virtuální klíče kód a modifikátor příznaky systému klávesové zkratky z ovládacího prvku klávesová zkratka.  
  
```  
DWORD GetHotKey() const;  
  
void GetHotKey(
    WORD& wVirtualKeyCode,  
    WORD& wModifiers) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`wVirtualKeyCode`  
 Virtuální klíče kód klávesové zkratky. Seznam kódů standardní virtuální klíčů najdete v tématu winuser.  
  
 [out]`wModifiers`  
 Bitová kombinace (nebo) příznaky, které indikují modifikační klávesy v klávesové zkratky.  
  
 Modifikátor příznaky jsou následující:  
  
|Příznak|Odpovídající klíč|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|ALT klávesa|  
|`HOTKEYF_CONTROL`|Klávesu CTRL|  
|`HOTKEYF_EXT`|Rozšířené klíč|  
|`HOTKEYF_SHIFT`|Klávesy SHIFT|  
  
### <a name="return-value"></a>Návratová hodnota  
 V prvním metodu, přetížených `DWORD` obsahující virtuální klíče kód a modifikátor příznaky. Nejnižší bajt aplikace word nejnižší obsahuje kód virtuální, vysokou pořadí bajtů aplikace word nejnižší obsahuje modifikátor příznaky a horní slovo je nulová.  
  
### <a name="remarks"></a>Poznámky  
 Kód virtuální a společně modifikační klávesy definovat klávesové zkratky.  
  
##  <a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName  
 Volání této funkce člen získat lokalizovaný název klávesové zkratky.  
  
```  
CString GetHotKeyName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Lokalizovaný název aktuálně vybrané klávesové zkratky. Pokud neexistuje žádné vybrané klávesové zkratky `GetHotKeyName` vrátí prázdný řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Název, který vrátí tato funkce člen pochází z klávesnice ovladače. Lokalizované verze systému Windows, můžete nainstalovat ovladač Nelokalizováno klávesnice a naopak.  
  
##  <a name="getkeyname"></a>CHotKeyCtrl::GetKeyName  
 Volání této funkce člen získat lokalizovaný název klíč přiřazený k zadané virtuální klíče kódu.  
  
```  
static CString GetKeyName(
    UINT vk,  
    BOOL fExtended);
```  
  
### <a name="parameters"></a>Parametry  
 `vk`  
 Kód virtuální klíče.  
  
 *fExtended*  
 Pokud je virtuální klíče kód klíčem rozšířené **TRUE**jinak **FALSE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Lokalizovaný název je klíč zadaný pomocí `vk` parametr. Pokud klíč nemá žádné namapované název `GetKeyName` vrátí prázdný řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Název klíče, který vrátí tato funkce pochází z ovladač klávesnice, takže můžete nainstalovat ovladač Nelokalizováno klávesnice lokalizované verze systému Windows a naopak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]  
  
##  <a name="sethotkey"></a>CHotKeyCtrl::SetHotKey  
 Nastaví klávesové zkratky pro ovládacího prvku klávesová zkratka.  
  
```  
void SetHotKey(
    WORD wVirtualKeyCode,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`wVirtualKeyCode`  
 Virtuální klíče kód klávesové zkratky. Seznam kódů standardní virtuální klíčů najdete v tématu winuser.  
  
 [v]`wModifiers`  
 Bitová kombinace (nebo) příznaky, které indikují modifikační klávesy v klávesové zkratky.  
  
 Modifikátor příznaky jsou následující:  
  
|Příznak|Odpovídající klíč|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|ALT klávesa|  
|`HOTKEYF_CONTROL`|Klávesu CTRL|  
|`HOTKEYF_EXT`|Rozšířené klíč|  
|`HOTKEYF_SHIFT`|Klávesy SHIFT|  
  
### <a name="remarks"></a>Poznámky  
 Kód virtuální a společně modifikační klávesy definovat klávesové zkratky.  
  
##  <a name="setrules"></a>CHotKeyCtrl::SetRules  
 Volání této funkce můžete definovat neplatná kombinace a výchozí modifikátor kombinace pro ovládacího prvku klávesová zkratka.  
  
```  
void SetRules(
    WORD wInvalidComb,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parametry  
 `wInvalidComb`  
 Pole příznaky, které určuje neplatná kombinace kláves. Může být kombinací následujícího:  
  
- `HKCOMB_A`ALT  
  
- `HKCOMB_C`CTRL  
  
- `HKCOMB_CA`CTRL + ALT  
  
- `HKCOMB_NONE`Beze změny klíče  
  
- `HKCOMB_S`POSUNUTÍ  
  
- `HKCOMB_SA`SHIFT + ALT  
  
- `HKCOMB_SC`SHIFT + CTRL  
  
- `HKCOMB_SCA`SHIFT + CTRL + ALT  
  
 `wModifiers`  
 Pole příznaky, které určuje kombinaci kláves pro použijte, pokud uživatel zadá neplatnou kombinaci. Další informace o příznaky modifikátor najdete v tématu [GetHotKey](#gethotkey).  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel zadá neplatná kombinace kláves, podle definice příznaků zadaných ve `wInvalidComb`, používá systém operátor OR kombinovat klíče zadané uživatelem s příznaků zadaných ve `wModifiers`. Výsledná kombinace kláves je převést na řetězec a následně se zobrazují v ovládacím prvku aktivního klíče.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



