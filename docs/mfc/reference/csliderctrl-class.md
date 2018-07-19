---
title: Csliderctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd58faa0cda2162f1abe906da8e38d4d62402db8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850206"
---
# <a name="csliderctrl-class"></a>Csliderctrl – třída
Poskytuje funkce pro Windows běžný ovládací prvek posuvník.  
  
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
|[CSliderCtrl::ClearSel](#clearsel)|Zruší aktuální výběr v ovládacím prvku posuvník.|  
|[CSliderCtrl::ClearTics](#cleartics)|Zruší aktuální osové značky ovládacího prvku slider.|  
|[CSliderCtrl::Create](#create)|Vytvoří ovládací prvek posuvníku a připojí ho k `CSliderCtrl` objektu.|  
|[CSliderCtrl::CreateEx](#createex)|Vytvoří ovládací prvek posuvníku se zadaným rozšířené styly Windows a připojí ho k `CSliderCtrl` objektu.|  
|[CSliderCtrl::GetBuddy](#getbuddy)|Načte popisovač asociované okno ovládacího prvku jezdec do daného umístění.|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Načte velikosti v ovládacím prvku posuvník kanálu.|  
|[CSliderCtrl::GetLineSize](#getlinesize)|Načte velikosti řádku v ovládacím prvku posuvník.|  
|[CSliderCtrl::GetNumTics](#getnumtics)|Získá počet značek v ovládacím prvku posuvník.|  
|[CSliderCtrl::GetPageSize](#getpagesize)|Získá velikost stránky v ovládacím prvku posuvník.|  
|[CSliderCtrl::GetPos](#getpos)|Načte aktuální pozice posuvníku.|  
|[CSliderCtrl::GetRange](#getrange)|Získá minimální a maximální pozice posuvníku.|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|Získá maximální pozice posuvníku.|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|Získá minimální pozice posuvníku.|  
|[CSliderCtrl::GetSelection](#getselection)|Načte rozsah aktuálního výběru.|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|Načte délku jezdce v aktuální ovládací prvek posuvník.|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Získá velikost jezdce v ovládacím prvku posuvník.|  
|[CSliderCtrl::GetTic](#gettic)|Načte pozici zadané značky zaškrtnutí.|  
|[CSliderCtrl::GetTicArray](#getticarray)|Načte pole osové značky pozice pro ovládací prvek posuvník.|  
|[CSliderCtrl::GetTicPos](#getticpos)|Načte pozici zadané značky zaškrtnutí, v souřadnicích klienta.|  
|[CSliderCtrl::GetToolTips](#gettooltips)|Načte popisovač pro ovládací prvek tooltip přiřazenou ovládacímu prvku posuvník, pokud existuje.|  
|[CSliderCtrl::SetBuddy](#setbuddy)|Přiřadí časové období jako asociovaného okna pro ovládací prvek posuvník.|  
|[CSliderCtrl::SetLineSize](#setlinesize)|Nastaví velikost čáry posuvníku ovládacího prvku.|  
|[CSliderCtrl::SetPageSize](#setpagesize)|Nastaví velikost stránky v ovládacím prvku posuvník.|  
|[CSliderCtrl::SetPos](#setpos)|Nastaví aktuální pozice posuvníku.|  
|[CSliderCtrl::SetRange](#setrange)|Nastaví minimální a maximální pozice posuvníku.|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|Nastaví maximální pozice posuvníku.|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|Nastaví minimální pozice posuvníku.|  
|[CSliderCtrl::SetSelection](#setselection)|Nastaví rozsah aktuálního výběru.|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|Nastaví délku posuvník v aktuální ovládací prvek posuvník.|  
|[CSliderCtrl::SetTic](#settic)|Nastaví pozici zadané značky zaškrtnutí.|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|Nastaví frekvenci osové značky za přírůstek ovládací prvek posuvník.|  
|[CSliderCtrl::SetTipSide](#settipside)|Pozice ovládacího prvku tooltip používané TrackBar – ovládací prvek.|  
|[CSliderCtrl::SetToolTips](#settooltips)|ToolTip – ovládací prvek přiřadí ovládacím prvku posuvník.|  
  
## <a name="remarks"></a>Poznámky  
 "Ovládacího prvku posuvník" (také označované jako trackbar) je okno obsahující ovládací prvek posuvník a volitelné osové značky. Když uživatel přesune posuvník, pomocí myši nebo klávesy se šipkami, ovládací prvek odešle upozornění označíte změnu.  
  
 Posuvníky jsou užitečné, pokud chcete uživateli vybrat diskrétní hodnoty nebo sadu po sobě jdoucích hodnot v rozsahu. Například můžete použít ovládací prvek typu jezdec aby uživatel mohl nastavení opakování míry klávesnice přesunete posuvník na dané značky zaškrtnutí.  
  
 Tento ovládací prvek (a tedy `CSliderCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.  
  
 Posune posuvník po krocích, které určíte při jeho vytvoření. Například pokud chcete zadat, že posuvník by měl mít celou řadu pěti, posuvník pouze zabírat šest pozice: pozice na levé straně ovládacího prvku posuvníku a jednu pozici pro každý přírůstek v rozsahu. Obvykle každá z těchto umístění je identifikován značky zaškrtnutí.  
  
 Vytvořit ovládací prvek posuvník pomocí konstruktoru a `Create` členskou funkci `CSliderCtrl`. Po vytvoření ovládacího prvku slider. můžete členské funkce ve `CSliderCtrl` můžete změnit různá jeho vlastnosti. Změny, které můžete provést zahrnují nastavení minimální a maximální pozice pro posuvník, značky kreslení, nastavení oblast výběru a změnou pozice posuvníku.  
  
 Další informace o používání `CSliderCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="clearsel"></a>  CSliderCtrl::ClearSel  
 Zruší aktuální výběr v ovládacím prvku posuvník.  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *bRedraw*  
 Ho překreslit příznak. Pokud tento parametr má hodnotu TRUE, je po výběru se vymaže; překreslení posuvníku v opačném případě se měl překreslit posuvníku.  
  
##  <a name="cleartics"></a>  CSliderCtrl::ClearTics  
 Zruší aktuální osové značky ovládacího prvku slider.  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *bRedraw*  
 Ho překreslit příznak. Pokud tento parametr má hodnotu TRUE, je po osové značky jsou vymazány; překreslení posuvníku v opačném případě se měl překreslit posuvníku.  
  
##  <a name="create"></a>  CSliderCtrl::Create  
 Vytvoří ovládací prvek posuvníku a připojí ho k `CSliderCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje styl ovládacího prvku posuvník. Použít libovolnou kombinaci [– styly ovládacích prvků posuvník](http://msdn.microsoft.com/library/windows/desktop/bb760147), které jsou popsány v sadě Windows SDK do ovládacího prvku.  
  
 *Rect*  
 Určuje velikost a umístění v ovládacím prvku posuvník. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku posuvník, obvykle `CDialog`. Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládacího prvku posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CSliderCtrl` ve dvou krocích. Nejprve volat konstruktor a poté zavolejte `Create`, což vytvoří ovládací prvek posuvníku a připojí ho k `CSliderCtrl` objektu.  
  
 V závislosti na hodnoty nastavené pro *dwStyle*, ovládací prvek posuvník může mít svislé nebo vodorovné orientace. Může mít osové značky na obou stranách obě strany, nebo ani jeden. To lze také zadat rozsah po sobě jdoucích hodnot.  
  
 Chcete-li použít rozšířené styly oken pro ovládací prvek posuvník, zavolejte [CreateEx](#createex) místo `Create`.  
  
##  <a name="createex"></a>  CSliderCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CSliderCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) v sadě Windows SDK.  
  
 *dwStyle*  
 Určuje styl ovládacího prvku posuvník. Použít libovolnou kombinaci [– styly ovládacích prvků posuvník](http://msdn.microsoft.com/library/windows/desktop/bb760147), které jsou popsány v sadě Windows SDK do ovládacího prvku.  
  
 *Rect*  
 Odkaz na [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.  
  
 *pParentWnd*  
 Ukazatel na okno, který je nadřazeného ovládacího prvku.  
  
 *nID*  
 ID ovládacího prvku podřízené okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.  
  
##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl  
 Vytvoří `CSliderCtrl` objektu.  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy  
 Načte popisovač asociované okno ovládacího prvku jezdec do daného umístění.  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *fLocation*  
 Logická hodnota určující, které ze dvou obslužné rutiny buddy okna pro načtení. Může být jedna z následujících hodnot:  
  
- Hodnota TRUE načte popisovač buddy vlevo od jezdce. Pokud v ovládacím prvku posuvník používá styl TBS_VERT, načte zprávy buddy nad posuvník.  
  
- FALSE načte popisovač buddy vpravo od jezdce. Pokud v ovládacím prvku posuvník používá styl TBS_VERT, načte zprávy buddy pod posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je v místě určeném okna buddy *fLocation*, nebo hodnota NULL, pokud neexistuje žádný asociované okno na tomto místě.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178), jak je popsáno v sadě Windows SDK. Popis posuvník – styly ovládacího prvku, naleznete v tématu [– styly ovládacího prvku Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) v sadě Windows SDK.  
  
##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect  
 Načte velikost a umístění ohraničující rámeček pro ovládací prvek posuvník kanálu.  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Ukazatel [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje velikost a umístění kanálu je po návratu funkce ohraničující obdélník.  
  
### <a name="remarks"></a>Poznámky  
 Kanál je oblast, přes který se posuvník posune a který obsahuje zvýraznění, když je vybrána oblast.  
  
##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize  
 Získá velikost řádků pro ovládací prvek posuvník.  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost řádků pro ovládací prvek posuvník.  
  
### <a name="remarks"></a>Poznámky  
 Velikost řádku ovlivňuje, kolik se posuvník posune po TB_LINEUP a TB_LINEDOWN oznámení. Výchozí nastavení pro velikost řádku je 1.  
  
##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics  
 Získá počet značek v ovládacím prvku posuvník.  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet značek v ovládacím prvku posuvník.  
  
##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize  
 Získá velikost stránky pro ovládací prvek posuvník.  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost stránky pro ovládací prvek posuvník.  
  
### <a name="remarks"></a>Poznámky  
 Velikost stránky má vliv na tom, kolik se posuvník posune po TB_PAGEUP a TB_PAGEDOWN oznámení.  
  
##  <a name="getpos"></a>  CSliderCtrl::GetPos  
 Načte aktuální pozice posuvníku v ovládacím prvku posuvník.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální pozice.  
  
##  <a name="getrange"></a>  CSliderCtrl::GetRange  
 Získá maximální a minimální pozice pro posuvník v ovládacím prvku posuvník.  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Nminimum*  
 Odkaz na celé číslo, které přijímá minimální pozici.  
  
 *Nmaximum*  
 Odkaz na celé číslo, které přijímá maximální pozici.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce zkopíruje hodnoty do celých čísel odkazuje *Nminimum* a *Nmaximum*.  
  
##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax  
 Získá maximální pozici pro posuvník v ovládacím prvku posuvník.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální pozice ovládacího prvku.  
  
##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin  
 Získá minimální pozice pro posuvník v ovládacím prvku posuvník.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minimální pozice ovládacího prvku.  
  
##  <a name="getselection"></a>  CSliderCtrl::GetSelection  
 Získá počáteční a koncové pozice výběru v ovládacím prvku posuvník.  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Nminimum*  
 Odkaz na celé číslo, které přijímá počáteční pozici aktuálního výběru.  
  
 *Nmaximum*  
 Odkaz na celé číslo, které přijímá koncovou pozici aktuálního výběru.  
  
##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength  
 Načte délku jezdce v aktuální ovládací prvek posuvník.  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka posuvník v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect  
 Načte velikost a umístění ohraničující rámeček pro posuvník (palce) v ovládacím prvku posuvník.  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Ukazatel `CRect` objekt, který obsahuje ohraničující obdélník pro posuvník, pokud funkce vrátí.  
  
##  <a name="gettic"></a>  CSliderCtrl::GetTic  
 Načte pozici značky zaškrtnutí v ovládacím prvku posuvník.  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nTic*  
 Index založený na nule, identifikace značky zaškrtnutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění zadané značky zaškrtnutí nebo - 1, pokud *nTic* neurčuje platný index.  
  
##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray  
 Načte adresu pole obsahující podle polohy značek pro ovládací prvek posuvník.  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Adresa pole obsahující pozice označit značek pro ovládací prvek posuvník.  
  
##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos  
 Načte aktuální fyzické umístění značky zaškrtnutí v ovládacím prvku posuvník.  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nTic*  
 Index založený na nule, identifikace značky zaškrtnutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Fyzické umístění, v souřadnicích klienta zadané značky zaškrtnutí nebo - 1, pokud *nTic* neurčuje platný index.  
  
##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips  
 Načte popisovač pro ovládací prvek tooltip přiřazenou ovládacímu prvku posuvník, pokud existuje.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objektu, nebo hodnota NULL, pokud popisy nejsou používány. Pokud v ovládacím prvku posuvník nepoužívá TBS_TOOLTIPS styl, vrácená hodnota je NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209), jak je popsáno v sadě Windows SDK. Všimněte si, že tato členská funkce vrátí `CToolTipCtrl` objektu namísto popisovač do ovládacího prvku.  
  
 Popis posuvník – styly ovládacího prvku, naleznete v tématu [– styly ovládacího prvku Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) v sadě Windows SDK.  
  
##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy  
 Přiřadí časové období jako asociovaného okna pro ovládací prvek posuvník.  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndBuddy*  
 Ukazatel `CWnd` objekt, který bude nastaven jako přítel v ovládacím prvku posuvník.  
  
 *fLocation*  
 Hodnota, která určuje umístění, kam chcete-li zobrazit asociované okno. Tato hodnota může být jedna z následujících akcí:  
  
- TRUE buddy se zobrazí nalevo od objektu trackbar Pokud ovládací prvek posuvník používá TBS_HORZ style. Používá-li pozice TBS_VERT styl, se zobrazí buddy nad ovládací prvek posuvník.  
  
- FALSE buddy se zobrazí napravo od objektu trackbar Pokud ovládací prvek posuvník používá TBS_HORZ styl. Pokud objektu trackbar používá TBS_VERT styl, se zobrazí pod TrackBar – ovládací prvek kamaráda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objektu, který byl dříve přiřazen do ovládacího prvku jezdec na tomto místě.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213), jak je popsáno v sadě Windows SDK. Všimněte si, že tato členská funkce používá ukazatele na `CWnd` objekty, nikoli úchyty okna pro jeho návratovou hodnotu a parametr.  
  
 Popis posuvník – styly ovládacího prvku, naleznete v tématu [– styly ovládacího prvku Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) v sadě Windows SDK.  
  
##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize  
 Nastaví velikost čáry pro ovládací prvek posuvník.  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nSize*  
 Novou velikost řádku v ovládacím prvku posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Původní velikost řádku.  
  
### <a name="remarks"></a>Poznámky  
 Velikost řádku ovlivňuje, kolik se posuvník posune po TB_LINEUP a TB_LINEDOWN oznámení.  
  
##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize  
 Nastaví velikost stránky pro ovládací prvek posuvník.  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nSize*  
 Nové velikosti stránky v ovládacím prvku posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost předchozí stránky.  
  
### <a name="remarks"></a>Poznámky  
 Velikost stránky má vliv na tom, kolik se posuvník posune po TB_PAGEUP a TB_PAGEDOWN oznámení.  
  
##  <a name="setpos"></a>  CSliderCtrl::SetPos  
 Nastaví aktuální pozice posuvníku v ovládacím prvku posuvník.  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos –*  
 Určuje nové pozice posuvníku.  
  
##  <a name="setrange"></a>  CSliderCtrl::SetRange  
 Nastaví rozsah (minimální a maximální pozic) pro posuvník v ovládacím prvku posuvník.  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *Nminimum*  
 Minimální pozice pro posuvník.  
  
 *Nmaximum*  
 Maximální pozici pro posuvník.  
  
 *bRedraw*  
 Příznak redraw. Pokud tento parametr má hodnotu TRUE, je po je nastaven rozsah; překreslení posuvníku v opačném případě se měl překreslit posuvníku.  
  
##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax  
 Nastaví maximální rozsah pro posuvník v ovládacím prvku posuvník.  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *Nmaximum*  
 Maximální pozici pro posuvník.  
  
 *bRedraw*  
 Příznak redraw. Pokud tento parametr má hodnotu TRUE, je po je nastaven rozsah; překreslení posuvníku v opačném případě se měl překreslit posuvníku.  
  
##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin  
 Nastaví minimální rozsah pro posuvník v ovládacím prvku posuvník.  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *Nminimum*  
 Minimální pozice pro posuvník.  
  
 *bRedraw*  
 Příznak redraw. Pokud tento parametr má hodnotu TRUE, je po je nastaven rozsah; překreslení posuvníku v opačném případě se měl překreslit posuvníku.  
  
##  <a name="setselection"></a>  CSliderCtrl::SetSelection  
 Nastaví počáteční a koncová pozice pro aktuální výběr v ovládacím prvku posuvník.  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 *Nminimum*  
 Počáteční pozice pro posuvník.  
  
 *Nmaximum*  
 Koncová pozice posuvníku.  
  
##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength  
 Nastaví délku posuvník v aktuální ovládací prvek posuvník.  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] *nLength*|Délka posuvník v pixelech.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyžaduje, aby ovládací prvek posuvník nastavena na [TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147) style.  
  
 Tato metoda odesílá [TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_sliderCtrl`, která je pro přístup k aktuálnímu ovládacímu prvku trackbar. Příklad také definuje proměnnou, `thumbLength`, která je používá k ukládání délka výchozí TrackBar – ovládací prvek thumb součásti. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví TrackBar – ovládací prvek thumb komponenty dvakrát jeho výchozí hodnotu.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>  CSliderCtrl::SetTic  
 Nastaví pozici značky zaškrtnutí v ovládacím prvku posuvník.  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>Parametry  
 *nTic*  
 Pozice značky zaškrtnutí. Tento parametr zadejte kladnou hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je nastavení značky zaškrtnutí; jinak 0.  
  
##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq  
 Nastaví frekvenci, s kterou značek se zobrazují značky posuvníku.  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>Parametry  
 *nFreq*  
 Frekvence osové značky.  
  
### <a name="remarks"></a>Poznámky  
 Například pokud frekvence je nastavená na 2, zobrazí se pro každý další přírůstek v posuvníku rozsahu značky zaškrtnutí. Výchozí nastavení je frekvence 1 (to znamená, že každý přírůstek v rozsahu souvisí se značkou zaškrtnutí).  
  
 Je nutné vytvořit ovládací prvek se stylem TBS_AUTOTICKS použití této funkce. Další informace najdete v tématu [CSliderCtrl::Create](#create).  
  
##  <a name="settipside"></a>  CSliderCtrl::SetTipSide  
 Pozice ovládacího prvku tooltip používané TrackBar – ovládací prvek.  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>Parametry  
 *Numístění*  
 Hodnota představující umístění, kam chcete-li zobrazit ovládací prvek tooltip. Seznam možných hodnot, zobrazí zpráva Win32 [TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240), jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která představuje ovládací prvek tooltip předchozí umístění. Návratová hodnota se rovná jednu z možných hodnot pro *Numístění*.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 TBM_SETTIPSIDE, jak je popsáno v sadě Windows SDK. Ovládacích prvků posuvník, které používají styl TBS_TOOLTIPS zobrazit popisy tlačítek. Popis posuvník – styly ovládacího prvku, naleznete v tématu [– styly ovládacího prvku Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) v sadě Windows SDK.  
  
##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips  
 ToolTip – ovládací prvek přiřadí ovládacím prvku posuvník.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndTip*  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objekt, který obsahuje popisy tlačítek pro použití s ovládacím prvkem posuvníku.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242), jak je popsáno v sadě Windows SDK. Když se stylem TBS_TOOLTIPS ovládacím prvku posuvník, vytvoří ovládací prvek výchozí popisek, který se zobrazí vedle jezdce, zobrazení aktuální pozice posuvníku. Popis posuvník – styly ovládacího prvku, naleznete v tématu [– styly ovládacího prvku Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL2 knihovny MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl – třída](../../mfc/reference/cprogressctrl-class.md)
