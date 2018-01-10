---
title: "CSliderCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
dev_langs: C++
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2788777b9a5014790e094cf39871b3e4d40750fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csliderctrl-class"></a>CSliderCtrl – třída
Poskytuje funkci Windows posuvník běžné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Vytvoří `CSliderCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|Vymaže aktuální výběr v ovládacím prvku posuvníku.|  
|[CSliderCtrl::ClearTics](#cleartics)|Odebere z ovládacího prvku posuvník aktuální osové značky.|  
|[CSliderCtrl::Create](#create)|Ovládací prvek typu jezdec vytvoří a připojí jej k `CSliderCtrl` objektu.|  
|[CSliderCtrl::CreateEx](#createex)|Vytvoří ovládací prvek typu jezdec s zadaný Windows rozšířené styly a připojí jej k `CSliderCtrl` objektu.|  
|[CSliderCtrl::GetBuddy](#getbuddy)|Načte popisovač okno kamarád ovládacího prvku posuvník v daném umístění.|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Načte velikosti v ovládacím prvku posuvník kanálu.|  
|[CSliderCtrl::GetLineSize](#getlinesize)|Získá velikost řádku ovládací prvek typu jezdec.|  
|[CSliderCtrl::GetNumTics](#getnumtics)|Načte počet značek v ovládacím prvku posuvníku.|  
|[CSliderCtrl::GetPageSize](#getpagesize)|Získá velikost stránky ovládací prvek typu jezdec.|  
|[CSliderCtrl::GetPos](#getpos)|Načte aktuální pozice posuvníku.|  
|[CSliderCtrl::GetRange](#getrange)|Načte minimální a maximální pozice pro jezdce.|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|Načte maximální pozici pro jezdce.|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|Načte minimální pozici pro jezdce.|  
|[CSliderCtrl::GetSelection](#getselection)|Načte rozsah aktuální výběr.|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|Načte délka jezdec v aktuální TrackBar – ovládací prvek.|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Načte velikosti v ovládacím prvku posuvník jezdce.|  
|[CSliderCtrl::GetTic](#gettic)|Načte pozici zadaný značky.|  
|[CSliderCtrl::GetTicArray](#getticarray)|Načte pole osové značky pozice pro ovládací prvek typu jezdec.|  
|[CSliderCtrl::GetTicPos](#getticpos)|Načte pozici zadané značky, v souřadnicích klienta.|  
|[CSliderCtrl::GetToolTips](#gettooltips)|Načte popisovač do ovládacího prvku tooltip přiřazenou ovládacímu prvku posuvník, pokud existuje.|  
|[CSliderCtrl::SetBuddy](#setbuddy)|Přiřadí okno jako kamarád okna pro ovládací prvek typu jezdec.|  
|[CSliderCtrl::SetLineSize](#setlinesize)|Nastaví velikost čáry ovládacího prvku posuvník.|  
|[CSliderCtrl::SetPageSize](#setpagesize)|Nastaví velikost stránky ovládacího prvku posuvník.|  
|[CSliderCtrl::SetPos](#setpos)|Nastaví aktuální umístění posuvníku.|  
|[CSliderCtrl::SetRange](#setrange)|Nastaví minimální a maximální pozice pro jezdce.|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|Nastaví maximální pozici pro jezdce.|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|Nastaví minimální pozici pro jezdce.|  
|[CSliderCtrl::SetSelection](#setselection)|Nastaví rozsah aktuální výběr.|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|Nastaví délku posuvníku v aktuální TrackBar – ovládací prvek.|  
|[CSliderCtrl::SetTic](#settic)|Nastavuje pozici zadaný značky.|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|Nastaví frekvenci osové značky za přírůstek ovládacího prvku posuvník.|  
|[CSliderCtrl::SetTipSide](#settipside)|Pozice ovládacího prvku tooltip používá TrackBar – ovládací prvek.|  
|[CSliderCtrl::SetToolTips](#settooltips)|Ovládací prvek typu jezdec přiřadí ovládacího prvku popisek.|  
  
## <a name="remarks"></a>Poznámky  
 "Ovládací prvek typu jezdec" (také označované jako TrackBar –) je okno obsahující jezdce a volitelné osové značky. Když se uživatel přesune posuvníku pomocí myši nebo klíče směr, odešle řízení zpráv s oznámením označíte změnu.  
  
 Ovládací prvky posuvníku jsou užitečné, když chcete uživateli vybrat hodnotu diskrétní nebo sadu po sobě jdoucích hodnot v rozsahu. Například můžete použít ovládací prvek typu jezdec Pokud chcete umožnit uživatelům nastavit rychlost opakování klávesnice přesunutím posuvníku do dané osových značek.  
  
 Tento ovládací prvek (a proto `CSliderCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Posuvník přesune v krocích, které určíte při jeho vytvoření. Například pokud určíte, že posuvník by měl mít řadu pět, posuvník pouze zabírat šest bodů: na pozici na levou stranu ovládacího prvku posuvník a jednu pozici pro každý přírůstek v rozsahu. Obvykle každý z těchto umístění je identifikována osových značek.  
  
 Vytvoření jezdce pomocí konstruktoru a **vytvořit** členské funkce `CSliderCtrl`. Jakmile vytvoříte ovládací prvek typu jezdec, můžete použít členské funkce ve `CSliderCtrl` ke změně mnoha jeho vlastnosti. Změny, které můžete provést zahrnují nastavení minimální a maximální pozice pro posuvník, kreslení osové značky, nastavení výběru rozsahu a přemístění posuvníku.  
  
 Další informace o používání `CSliderCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="clearsel"></a>CSliderCtrl::ClearSel  
 Vymaže aktuální výběr v ovládacím prvku posuvníku.  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRedraw`  
 Ho překreslit příznak. Pokud tento parametr je **TRUE**, posuvník bude překreslen po výběru se vymaže; jinak není překreslen posuvníku.  
  
##  <a name="cleartics"></a>CSliderCtrl::ClearTics  
 Odebere z ovládacího prvku posuvník aktuální osové značky.  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRedraw`  
 Ho překreslit příznak. Pokud tento parametr je **TRUE**, posuvník bude překreslen po značek jsou vymazány; jinak není překreslen posuvníku.  
  
##  <a name="create"></a>CSliderCtrl::Create  
 Ovládací prvek typu jezdec vytvoří a připojí jej k `CSliderCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládacího prvku posuvník. Použít libovolnou kombinaci [posuvník – styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb760147), které jsou popsány v sadě Windows SDK do ovládacího prvku.  
  
 `rect`  
 Určuje velikost a umístění v ovládacím prvku posuvník. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura.  
  
 `pParentWnd`  
 Určuje v ovládacím prvku posuvník nadřazeného okna, obvykle `CDialog`. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CSliderCtrl` ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří v ovládacím prvku posuvník a připojí jej k `CSliderCtrl` objektu.  
  
 V závislosti na hodnoty nastavené pro `dwStyle`, v ovládacím prvku posuvník může mít svislé nebo vodorovné orientaci. Může mít osové značky na obou stranách obě strany, nebo ani jeden z nich. Ho mohou sloužit také k určení rozsahu po sobě jdoucích hodnot.  
  
 Chcete-li použít rozšířené styly oken do ovládacího prvku posuvník, volejte [CreateEx](#createex) místo **vytvořit**.  
  
##  <a name="createex"></a>CSliderCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CSliderCtrl` objektu.  
  
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
 Určuje styl ovládacího prvku posuvník. Použít libovolnou kombinaci [posuvník – styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb760147), které jsou popsány v sadě Windows SDK do ovládacího prvku.  
  
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
  
##  <a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl  
 Vytvoří `CSliderCtrl` objektu.  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>CSliderCtrl::GetBuddy  
 Načte popisovač okno kamarád ovládacího prvku posuvník v daném umístění.  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `fLocation`  
 Logická hodnota, která určuje, které dvě obslužné rutiny kamarád okno načíst. Může být jedna z následujících hodnot:  
  
- **Hodnota TRUE,** načte popisovač kamarád vlevo od jezdce. Pokud se používá v ovládacím prvku posuvník `TBS_VERT` styl, zprávy budou načítat kamarád výše posuvníku.  
  
- **FALSE** načte popisovač kamarád vpravo od jezdce. Pokud se používá v ovládacím prvku posuvník `TBS_VERT` styl, zprávy budou načítat kamarád níže posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je v umístění, které okno kamarád `fLocation`, nebo **NULL** Pokud žádný časový interval pro kamarád existuje v tomto umístění.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178), jak je popsáno v sadě Windows SDK. Popis styly ovládacího prvku posuvník najdete v tématu [styly ovládacího prvku TrackBar –](http://msdn.microsoft.com/library/windows/desktop/bb760147) ve Windows SDK.  
  
##  <a name="getchannelrect"></a>CSliderCtrl::GetChannelRect  
 Načte velikost a umístění ohraničující obdélník pro ovládací prvek typu jezdec na kanál.  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Ukazatel [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje velikost a umístění kanálu je ohraničujícího rámečku, když funkce vrátí hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Kanál je oblast, přes který přesune posuvník a obsahující zvýraznění, když je vybrána oblast.  
  
##  <a name="getlinesize"></a>CSliderCtrl::GetLineSize  
 Získá velikost řádku pro ovládací prvek typu jezdec.  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost řádku pro ovládací prvek posuvníku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost řádku ovlivňuje, kolik jezdec přesune pro **TB_LINEUP** a **TB_LINEDOWN** oznámení. Výchozí nastavení pro velikost řádku je 1.  
  
##  <a name="getnumtics"></a>CSliderCtrl::GetNumTics  
 Načte počet značek v ovládacím prvku posuvníku.  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet značek v ovládacím prvku posuvníku.  
  
##  <a name="getpagesize"></a>CSliderCtrl::GetPageSize  
 Získá velikost stránky pro ovládací prvek typu jezdec.  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost stránky pro ovládací prvek posuvníku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost stránky ovlivňuje, kolik jezdec přesune pro **TB_PAGEUP** a **TB_PAGEDOWN** oznámení.  
  
##  <a name="getpos"></a>CSliderCtrl::GetPos  
 Načte aktuální pozice posuvníku v ovládacím prvku posuvníku.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální pozici.  
  
##  <a name="getrange"></a>CSliderCtrl::GetRange  
 Načte maximální a minimální pozice pro posuvník v ovládací prvek typu jezdec.  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Odkaz na celé číslo, které obdrží minimální pozici.  
  
 `nMax`  
 Odkaz na celé číslo, které obdrží maximální pozici.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce zkopíruje hodnoty do celých čísel odkazuje `nMin` a `nMax`.  
  
##  <a name="getrangemax"></a>CSliderCtrl::GetRangeMax  
 Načte maximální pozici pro posuvník v ovládacím prvku posuvníku.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální pozice ovládacího prvku.  
  
##  <a name="getrangemin"></a>CSliderCtrl::GetRangeMin  
 Načte minimální pozici pro posuvník v ovládacím prvku posuvníku.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění ovládacího prvku minimální.  
  
##  <a name="getselection"></a>CSliderCtrl::GetSelection  
 Načte počáteční a koncové pozice aktuální výběr v ovládacím prvku posuvníku.  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Odkaz na celé číslo, které obdrží počáteční pozici aktuální výběr.  
  
 `nMax`  
 Odkaz na celé číslo, které přijímá koncovou pozici aktuální výběr.  
  
##  <a name="getthumblength"></a>CSliderCtrl::GetThumbLength  
 Načte délka jezdec v aktuální TrackBar – ovládací prvek.  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka posuvníku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getthumbrect"></a>CSliderCtrl::GetThumbRect  
 Načte velikost a umístění ohraničující obdélník pro posuvník (Flash) v ovládacím prvku posuvníku.  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Ukazatel na `CRect` objekt, který obsahuje ohraničující obdélník pro posuvník, když funkce vrátí hodnotu.  
  
##  <a name="gettic"></a>CSliderCtrl::GetTic  
 Načte pozici v ovládacím prvku posuvník osových značek.  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nTic`  
 Index počítaný od nuly identifikace osových značek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice zadané značky nebo - 1, pokud `nTic` neurčuje platný index.  
  
##  <a name="getticarray"></a>CSliderCtrl::GetTicArray  
 Načte adresu pole obsahující podle polohy značek pro ovládací prvek typu jezdec.  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa pole obsahující pozic osové značky ovládacího prvku posuvník.  
  
##  <a name="getticpos"></a>CSliderCtrl::GetTicPos  
 Načte aktuální fyzické umístění osových značek v ovládací prvek typu jezdec.  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nTic`  
 Index počítaný od nuly identifikace osových značek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Fyzické umístění, v souřadnicích klienta zadané značky nebo - 1, pokud `nTic` neurčuje platný index.  
  
##  <a name="gettooltips"></a>CSliderCtrl::GetToolTips  
 Načte popisovač do ovládacího prvku tooltip přiřazenou ovládacímu prvku posuvník, pokud existuje.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objekt, nebo **NULL** Pokud popisy tlačítek se nepoužívají. Pokud se nepoužívá prvku posuvník **TBS_TOOLTIPS** styl, vrácená hodnota je **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209), jak je popsáno v sadě Windows SDK. Všimněte si, že členské funkce vrátí hodnotu `CToolTipCtrl` objekt místo popisovač do ovládacího prvku.  
  
 Popis styly ovládacího prvku posuvník najdete v tématu [styly ovládacího prvku TrackBar –](http://msdn.microsoft.com/library/windows/desktop/bb760147) ve Windows SDK.  
  
##  <a name="setbuddy"></a>CSliderCtrl::SetBuddy  
 Přiřadí okno jako kamarád okna pro ovládací prvek typu jezdec.  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndBuddy`  
 Ukazatel na `CWnd` objekt, který bude nastaven jako přítel v ovládacím prvku posuvník.  
  
 `fLocation`  
 Hodnota, která určuje umístění, kam chcete-li zobrazení okna kamarád. Tato hodnota může být jeden z následujících akcí:  
  
- **Hodnota TRUE,** kamarád se zobrazí vlevo od pozice, pokud používá TrackBar – ovládací prvek `TBS_HORZ` stylu. Pokud používá pozice `TBS_VERT` styl, se zobrazí kamarád nad TrackBar – ovládací prvek.  
  
- **FALSE** kamarád se zobrazí vpravo od pozice, pokud používá TrackBar – ovládací prvek `TBS_HORZ` stylu. Pokud používá pozice `TBS_VERT` styl, kamarád se zobrazí pod TrackBar – ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který byl dříve přiřazen do ovládacího prvku posuvník v tomto umístění.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213), jak je popsáno v sadě Windows SDK. Všimněte si, že tento – členská funkce používá ukazatele na `CWnd` objekty, nikoli okno obslužné rutiny pro jeho návratovou hodnotu i parametr.  
  
 Popis styly ovládacího prvku posuvník najdete v tématu [styly ovládacího prvku TrackBar –](http://msdn.microsoft.com/library/windows/desktop/bb760147) ve Windows SDK.  
  
##  <a name="setlinesize"></a>CSliderCtrl::SetLineSize  
 Nastaví velikost čáry pro ovládací prvek typu jezdec.  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 `nSize`  
 Nové velikost řádku v ovládacím prvku posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí velikost řádku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost řádku ovlivňuje, kolik jezdec přesune pro **TB_LINEUP** a **TB_LINEDOWN** oznámení.  
  
##  <a name="setpagesize"></a>CSliderCtrl::SetPageSize  
 Nastaví velikost stránky pro ovládací prvek typu jezdec.  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 `nSize`  
 Nová velikost stránky ovládacího prvku posuvník  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí velikost stránky.  
  
### <a name="remarks"></a>Poznámky  
 Velikost stránky ovlivňuje, kolik jezdec přesune pro **TB_PAGEUP** a **TB_PAGEDOWN** oznámení.  
  
##  <a name="setpos"></a>CSliderCtrl::SetPos  
 Nastaví aktuální umístění posuvníku v ovládacím prvku posuvník.  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Určuje nové polohu jezdce.  
  
##  <a name="setrange"></a>CSliderCtrl::SetRange  
 Nastaví rozsah (minimální a maximální pozic) pro jezdec v ovládací prvek typu jezdec.  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Minimální pozice pro posuvníku.  
  
 `nMax`  
 Maximální pozice pro posuvníku.  
  
 `bRedraw`  
 Příznak započtení. Pokud tento parametr je **TRUE**, posuvník bude překreslen po je nastaven rozsah; jinak není překreslen posuvníku.  
  
##  <a name="setrangemax"></a>CSliderCtrl::SetRangeMax  
 Nastaví maximální rozsah pro jezdec v ovládací prvek typu jezdec.  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMax`  
 Maximální pozice pro posuvníku.  
  
 `bRedraw`  
 Příznak započtení. Pokud tento parametr je **TRUE**, posuvník bude překreslen po je nastaven rozsah; jinak není překreslen posuvníku.  
  
##  <a name="setrangemin"></a>CSliderCtrl::SetRangeMin  
 Určuje minimální rozsah jezdec v ovládací prvek typu jezdec.  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Minimální pozice pro posuvníku.  
  
 `bRedraw`  
 Příznak započtení. Pokud tento parametr je **TRUE**, posuvník bude překreslen po je nastaven rozsah; jinak není překreslen posuvníku.  
  
##  <a name="setselection"></a>CSliderCtrl::SetSelection  
 Nastaví počáteční a koncové pozice pro aktuální výběr v ovládacím prvku posuvníku.  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Počáteční pozice pro posuvníku.  
  
 `nMax`  
 Koncová pozice pro posuvníku.  
  
##  <a name="setthumblength"></a>CSliderCtrl::SetThumbLength  
 Nastaví délku posuvníku v aktuální TrackBar – ovládací prvek.  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`nLength`|Délka posuvníku v pixelech.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje, aby TrackBar – ovládací prvek nastavena na [TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147) stylu.  
  
 Tato metoda odesílá [TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_sliderCtrl`, který používá pro přístup k aktuální TrackBar – ovládací prvek. V příkladu definuje také proměnnou, `thumbLength`, který používá k ukládání výchozí délka component jezdcem TrackBar – ovládací prvek. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví TrackBar – ovládací prvek jezdec součást dvakrát jeho výchozí délka.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>CSliderCtrl::SetTic  
 Nastavuje pozici osových značek v ovládacím prvku posuvníku.  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>Parametry  
 `nTic`  
 Pozice značky. Tento parametr zadejte kladnou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je nastavený značky; jinak 0.  
  
##  <a name="setticfreq"></a>CSliderCtrl::SetTicFreq  
 Nastaví frekvenci, s kterou osové značky jsou zobrazeny v jezdce.  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>Parametry  
 *nFreq*  
 Četnost značek.  
  
### <a name="remarks"></a>Poznámky  
 Například pokud frekvence je nastavena na 2, zobrazí se pro každý další přírůstek v rozsahu posuvníku osových značek. Výchozí nastavení frekvence je 1 (každý přírůstek v rozsahu je přidružen osových značek).  
  
 Je nutné vytvořit pomocí ovládacího prvku `TBS_AUTOTICKS` styl použití této funkce. Další informace najdete v tématu [CSliderCtrl::Create](#create).  
  
##  <a name="settipside"></a>CSliderCtrl::SetTipSide  
 Pozice ovládacího prvku tooltip používá TrackBar – ovládací prvek.  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>Parametry  
 `nLocation`  
 Hodnota představující umístění, kam chcete-li zobrazit ovládací prvek popis tlačítka. Seznam možných hodnot najdete v tématu zpráva Win32 [TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240), jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která představuje ovládací prvek popisek předchozího umístění. Návratová hodnota se rovná jednu z možných hodnot pro `nLocation`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 **TBM_SETTIPSIDE**, jak je popsáno v sadě Windows SDK. Posuvník prvky, které používají **TBS_TOOLTIPS** styl zobrazení popisů tlačítek. Popis styly ovládacího prvku posuvník najdete v tématu [styly ovládacího prvku TrackBar –](http://msdn.microsoft.com/library/windows/desktop/bb760147) ve Windows SDK.  
  
##  <a name="settooltips"></a>CSliderCtrl::SetToolTips  
 Ovládací prvek typu jezdec přiřadí ovládacího prvku popisek.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndTip`  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objekt obsahující popisy tlačítek pro použití s posuvníku.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242), jak je popsáno v sadě Windows SDK. Vytvoření ovládacího prvku posuvník s **TBS_TOOLTIPS** styl, vytvoří ovládací prvek popisek výchozí, který se zobrazí vedle jezdce, zobrazení jezdec na aktuální pozici. Popis styly ovládacího prvku posuvník najdete v tématu [styly ovládacího prvku TrackBar –](http://msdn.microsoft.com/library/windows/desktop/bb760147) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL2 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl – třída](../../mfc/reference/cprogressctrl-class.md)
