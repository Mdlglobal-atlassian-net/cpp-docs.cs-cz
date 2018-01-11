---
title: "Třída CScrollBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
dev_langs: C++
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d458fe5f7bcaf25fc5bb0685bb382a72d44d183
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cscrollbar-class"></a>CScrollBar – třída
Poskytuje funkce ovládacího prvku Windows posuvníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CScrollBar : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](#cscrollbar)|Vytvoří `CScrollBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CScrollBar::Create](#create)|Posuvník Windows vytvoří a připojí jej k `CScrollBar` objektu.|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Povolí nebo zakáže jeden nebo oba šipek na posuvníku.|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Načte informace o posuvník pomocí `SCROLLBARINFO` struktury.|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Načte informace o posuvníku.|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Načte limit posuvníku|  
|[CScrollBar::GetScrollPos](#getscrollpos)|Načte aktuální pozici jezdce.|  
|[CScrollBar::GetScrollRange](#getscrollrange)|Načte aktuální minimální a maximální posuvníku pozice pro danou posuvníku.|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Nastaví informace o posuvníku.|  
|[CScrollBar::SetScrollPos](#setscrollpos)|Nastaví aktuální pozici jezdce.|  
|[CScrollBar::SetScrollRange](#setscrollrange)|Nastaví pozici minimální a maximální hodnoty pro danou posuvníku.|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|Zobrazí nebo skryje posuvníku.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek typu posuvník vytvoříte ve dvou krocích. Nejprve volat konstruktor `CScrollBar` vytvořit `CScrollBar` objekt a potom volání [vytvořit](#create) členské funkce ovládacího prvku Windows posuvníku a vytvořte jej do `CScrollBar` objektu.  
  
 Pokud vytvoříte `CScrollBar` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CScrollBar` automaticky zničen při zavření dialogu.  
  
 Pokud vytvoříte `CScrollBar` objektu v okně a také můžete potřebovat jeho odstranění.  
  
 Pokud vytvoříte `CScrollBar` objektu v zásobníku, byla automaticky. Pokud vytvoříte `CScrollBar` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte, jakmile uživatel ukončí posuvníku systému Windows.  
  
 Pokud přidělíte libovolná paměť v `CScrollBar` objektu, přepsat `CScrollBar` destruktor k odstranění přidělení.  
  
 Související informace o používání `CScrollBar`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="create"></a>CScrollBar::Create  
 Posuvník Windows vytvoří a připojí jej k `CScrollBar` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje, o posun styl panelu. Použít libovolnou kombinaci [styly posuvníku](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) na posuvníku.  
  
 `rect`  
 Určuje typu posuvník velikost a umístění. Může být buď `RECT` struktura nebo `CRect` objektu.  
  
 `pParentWnd`  
 Určuje posuvníku panelu nadřazené okno, obvykle `CDialog` objektu. Nesmí být **NULL**.  
  
 `nID`  
 Ovládací prvek typu posuvník ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CScrollBar` objektu ve dvou krocích. Nejprve volání konstruktoru, který vytvoří `CScrollBar` objektu; potom volat **vytvořit**, která vytvoří a inicializuje přidružené posuvníku Windows a připojí jej k `CScrollBar` objektu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na posuvníku:  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
- **Ws_group –** k seskupování ovládacích prvků  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>CScrollBar::CScrollBar  
 Vytvoří `CScrollBar` objektu.  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření objektu, volání **vytvořit** členskou funkci pro vytvoření a inicializace posuvníku systému Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>CScrollBar::EnableScrollBar  
 Povolí nebo zakáže jeden nebo oba šipek na posuvníku.  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>Parametry  
 `nArrowFlags`  
 Určuje, jestli jsou na šipky posuvníku povolená nebo zakázaná a které dvojice šipek, které jsou zapnutá nebo vypnutá. Tento parametr může být jedna z následujících hodnot:  
  
- **ESB_ENABLE_BOTH** umožňuje obou šipek na posuvníku.  
  
- **ESB_DISABLE_LTUP** zakáže na šipku vlevo vodorovného posuvníku nebo šipku nahoru svislém posuvníku.  
  
- **ESB_DISABLE_RTDN** zakáže na šipku vpravo vodorovného posuvníku nebo na šipku dolů svislém posuvníku.  
  
- **ESB_DISABLE_BOTH** zakáže oba šipek na posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou zapnutá nebo vypnutá uvedeného; šipky v opačném případě 0, což naznačuje, šipky se již v požadovaný stav nebo že došlo k chybě.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo  
 Načte informace, **SCROLLBARINFO** struktura udržuje o posuvníku.  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pScrollInfo*  
 Ukazatel [SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getscrollinfo"></a>CScrollBar::GetScrollInfo  
 Načte informace o který `SCROLLINFO` struktura udržuje o posuvníku.  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpScrollInfo`  
 Ukazatel [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury. Najdete v části sada Windows SDK pro další informace o tuto strukturu.  
  
 `nMask`  
 Určuje parametry panelu přejděte k načtení. Typická využití, SIF_ALL, určuje kombinaci SIF_PAGE, SIF_POS, SIF_TRACKPOS a SIF_RANGE. V tématu `SCROLLINFO` Další informace o nMask hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud zpráva načíst všechny hodnoty, je návratový **TRUE**. Jinak je **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 `GetScrollInfo`umožňuje aplikacím používat 32-bit posuňte pozic.  
  
 [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktura obsahuje informace o posuvníku panelu, včetně minimální a maximální posouvání pozic, velikost stránky a pozice posuvníku (Flash). Najdete v článku `SCROLLINFO` tématu Struktura ve Windows SDK pro další informace o změně výchozí hodnoty strukturu.  
  
 Zprávy MFC Windows obslužné rutiny, které indikují pozici posunutí panelu, [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), zadejte umístění dat pouze 16 bitů. `GetScrollInfo`a `SetScrollInfo` poskytují 32 bity posuvník pozice data. Proto aplikace může volat `GetScrollInfo` při zpracování buď `CWnd::OnHScroll` nebo `CWnd::OnVScroll` můžete získat data pozici panelu přejděte 32-bit.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrolllimit"></a>CScrollBar::GetScrollLimit  
 Načte maximální posouvání pozice posuvníku.  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje maximální umístění posuvníku v případě úspěšného; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollpos"></a>CScrollBar::GetScrollPos  
 Načte aktuální pozici jezdce.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje aktuální umístění posouvací políčko, v případě úspěšného; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aktuální pozice je relativní hodnota, která závisí na aktuálním posouvání rozsahu. Například pokud posouvání rozsahu 100 až 200 a posouvací políčko zrovna panelu, aktuální pozici je 150.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollrange"></a>CScrollBar::GetScrollRange  
 Zkopíruje aktuální minimální a maximální posuvníku pozice pro danou posuvník do umístění určeného `lpMinPos` a `lpMaxPos`.  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpMinPos`  
 Body proměnnou celé číslo, které se zobrazí minimální pozici.  
  
 `lpMaxPos`  
 Body proměnnou celé číslo, které se zobrazí maximální pozici.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí rozsah pro ovládací prvek typu posuvník je prázdná (obě hodnoty jsou 0).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="setscrollinfo"></a>CScrollBar::SetScrollInfo  
 Nastaví informace, které `SCROLLINFO` struktura udržuje o posuvníku.  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpScrollInfo`  
 Ukazatel [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury.  
  
 `bRedraw`  
 Určuje, zda by měl být aby reflektoval nové informace o překreslen posuvníku. Pokud `bRedraw` je **TRUE**, bude překreslen posuvníku. Pokud je **FALSE**, není překreslen. Ve výchozím nastavení bude překreslen posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, návratový je **TRUE**. Jinak je **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné zadat hodnoty požadované pomocí `SCROLLINFO` struktury parametry, včetně hodnot příznaku.  
  
 `SCROLLINFO` Struktura obsahuje informace o posuvníku panelu, včetně minimální a maximální posouvání pozic, velikost stránky a pozice posuvníku (Flash). Najdete v článku [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) tématu Struktura ve Windows SDK pro další informace o změně výchozí hodnoty strukturu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>CScrollBar::SetScrollPos  
 Nastaví aktuální pozici jezdce, určeného `nPos` a -li zadána, je vykreslován posuvník tak, aby odrážely novou pozici.  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Určuje nové umístění pro posouvací políčko. Musí být v rozsahu posouvání.  
  
 `bRedraw`  
 Určuje, zda by měl být posuvníku překreslen tak, aby odrážely novou pozici. Pokud `bRedraw` je **TRUE**, bude překreslen posuvníku. Pokud je **FALSE**, není překreslen. Ve výchozím nastavení bude překreslen posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje předchozí pozici posouvací políčko, v případě úspěšného; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nastavit `bRedraw` k **FALSE** vždy, když následné volat jinou funkci nemuseli posuvníku překreslen dvakrát v krátkém časovém bude posuvník překreslit.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="setscrollrange"></a>CScrollBar::SetScrollRange  
 Nastaví pozici minimální a maximální hodnoty pro danou posuvníku.  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMinPos`  
 Určuje minimální posouvání pozici.  
  
 `nMaxPos`  
 Určuje maximální počet posouvání pozici.  
  
 `bRedraw`  
 Určuje, zda by měl být typu posuvník překreslen, aby odrážely změny. Pokud `bRedraw` je **TRUE**, bude překreslen posuvníku; Pokud **FALSE**, není překreslen. Ve výchozím nastavení se překreslí ho.  
  
### <a name="remarks"></a>Poznámky  
 Nastavit `nMinPos` a `nMaxPos` na hodnotu 0, chcete-li skrýt standardní posuvníky.  
  
 Nevolejte tuto funkci chcete skrýt posuvníku při zpracování zprávy oznámení posuvníku.  
  
 Pokud volání `SetScrollRange` následuje volání `SetScrollPos` – členská funkce, nastavení `bRedraw` v `SetScrollPos` 0 zabráníte posuvníku z se překreslen dvakrát.  
  
 Rozdíl mezi hodnotami určeného `nMinPos` a `nMaxPos` nesmí být větší než 32 767. Výchozí rozsah pro ovládací prvek typu posuvník je prázdná (obě `nMinPos` a `nMaxPos` jsou 0).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>CScrollBar::ShowScrollBar  
 Zobrazí nebo skryje posuvníku.  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bShow`  
 Určuje, zda se posuvník ukazuje nebo skrytý. Pokud tento parametr je **TRUE**, se zobrazí posuvníku; v opačném případě je skrytá.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace by neměl volání této funkce můžete skrýt posuvníku při zpracování zprávy oznámení posuvníku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CScrollBar::Create](#create).  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [CStatic – třída](../../mfc/reference/cstatic-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
