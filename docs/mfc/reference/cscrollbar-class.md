---
title: Cscrollbar – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c37e8cb4d69e93fd0842aa7cb2149331f502eae
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850040"
---
# <a name="cscrollbar-class"></a>Cscrollbar – třída
Poskytuje funkce pro ovládací prvek posuvníku Windows.  
  
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
|[CScrollBar::Create](#create)|Vytvoří posuvník Windows a připojí ho k `CScrollBar` objektu.|  
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Povolí nebo zakáže jednoho nebo obou šipek u posuvníku.|  
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Načte informace o posuvník pomocí `SCROLLBARINFO` struktury.|  
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Načte informace o posuvníku.|  
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Načte limit na posuvník.|  
|[CScrollBar::GetScrollPos](#getscrollpos)|Načte aktuální pozice posuvníku.|  
|[CScrollBar::GetScrollRange](#getscrollrange)|Načte aktuální pozice minimální a maximální posuvník pro danou posuvníku.|  
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Nastaví informace o posuvníku.|  
|[CScrollBar::SetScrollPos](#setscrollpos)|Nastaví aktuální pozice posuvníku.|  
|[CScrollBar::SetScrollRange](#setscrollrange)|Nastaví pozici minimální a maximální hodnoty pro daný posuvník.|  
|[CScrollBar::ShowScrollBar](#showscrollbar)|Zobrazí nebo skryje posuvníku.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření ovládacího prvku posuvníku ve dvou krocích. Nejprve volat konstruktor `CScrollBar` k sestavení kompletních `CScrollBar` objekt a potom voláním [vytvořit](#create) členská funkce, které chcete vytvořit ovládací prvek posuvníku Windows a připojit ho k `CScrollBar` objektu.  
  
 Pokud jste vytvořili `CScrollBar` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CScrollBar` se automaticky odstraní, když uživatel zavře dialogové okno.  
  
 Pokud jste vytvořili `CScrollBar` objektů v okně a také je nutné ji odstranit.  
  
 Pokud jste vytvořili `CScrollBar` objekt v zásobníku, je automaticky zničen. Pokud jste vytvořili `CScrollBar` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** na objekt, který chcete zničit ho, když uživatel ukončí posuvník Windows.  
  
 Pokud přidělení paměti v `CScrollBar` objektu, přepsat `CScrollBar` destruktor k uvolnění přidělení.  
  
 Související informace o používání `CScrollBar`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="create"></a>  CScrollBar::Create  
 Vytvoří posuvník Windows a připojí ho k `CScrollBar` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje posuvníku styl pruhu. Použít libovolnou kombinaci [styly posuvníku](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) na posuvníku.  
  
 *Rect*  
 Určuje velikost na posuvník a umístění. Může být buď `RECT` struktury nebo `CRect` objektu.  
  
 *pParentWnd*  
 Určuje posuvníku panelu nadřazené okno, obvykle `CDialog` objektu. Nesmí být NULL.  
  
 *nID*  
 ID ovládací prvek typu posuvník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CScrollBar` objektu ve dvou krocích. Nejprve volat konstruktor, který vytvoří `CScrollBar` objektu; poté zavolejte `Create`, který vytvoří a inicializuje přidružené posuvník Windows a připojí ho k `CScrollBar` objektu.  
  
 Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na posuvníku:  
  
- WS_CHILD vždy  
  
- WS_VISIBLE obvykle  
  
- WS_DISABLED jen zřídka  
  
- WS_GROUP k seskupování ovládacích prvků  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]  
  
##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar  
 Vytvoří `CScrollBar` objektu.  
  
```  
CScrollBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření objektu, zavolejte `Create` členskou funkci pro vytváření a inicializace posuvník Windows.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]  
  
##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar  
 Povolí nebo zakáže jednoho nebo obou šipek u posuvníku.  
  
```  
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```  
  
### <a name="parameters"></a>Parametry  
 *nArrowFlags*  
 Určuje, jestli jsou na šipky zapnutá nebo vypnutá a šipky, které jsou povolené nebo zakázané. Tento parametr může být jeden z následujících hodnot:  
  
- ESB_ENABLE_BOTH povolí obě šipek u posuvníku.  
  
- ESB_DISABLE_LTUP zakáže šipku vlevo vodorovný posuvník nebo na šipku nahoru svislý posuvník.  
  
- ESB_DISABLE_RTDN zakáže šipku vpravo vodorovný posuvník nebo na šipku dolů svislý posuvník.  
  
- ESB_DISABLE_BOTH zakáže obou šipek u posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud jsou povolené nebo zakázané uvedená; šipky v opačném případě 0, což znamená, že šipky jsou již v požadované stavu nebo že došlo k chybě.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo  
 Načte informace, které `SCROLLBARINFO` struktura udržuje o posuvníku.  
  
```  
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pScrollInfo*  
 Ukazatel [SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787535) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce emuluje funkčnost [SBM_SCROLLBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb787545) zprávu, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo  
 Načte informace, které `SCROLLINFO` struktura udržuje o posuvníku.  
  
```  
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    UINT nMask = SIF_ALL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpScrollInfo*  
 Ukazatel [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury. Zobrazit sady Windows SDK pro další informace o této struktury.  
  
 *nMask*  
 Určuje parametry panelu přejděte k načtení. Typické použití SIF_ALL, určí kombinaci možností SIF_PAGE, SIF_POS, SIF_TRACKPOS a SIF_RANGE. Zobrazit `SCROLLINFO` pro další informace o hodnotách nMask.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud zpráva načíst všechny hodnoty, je vrácená hodnota TRUE. V opačném případě je FALSE.  
  
### <a name="remarks"></a>Poznámky  
 `GetScrollInfo` umožňuje aplikacím používat pozice posuvníku 32-bit.  
  
 [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktura obsahuje informace o posuvník, včetně minimální a maximální posouvání pozic, velikost stránky a pozice posuvníku (Flash). Zobrazit `SCROLLINFO` struktura téma v sadě Windows SDK pro další informace o změně výchozího nastavení struktury.  
  
 Zprávy Windows MFC obslužné rutiny, které označuje pozici posunutí řádku, [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), zadejte umístění dat pouze 16 bitů. `GetScrollInfo` a `SetScrollInfo` poskytují 32 bitů posuvník se data umístění. Díky tomu se může volat aplikaci `GetScrollInfo` při zpracování buď `CWnd::OnHScroll` nebo `CWnd::OnVScroll` získávat data pozici panelu 32-bit posuvníku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit  
 Získá maximální posouvání pozice posuvníku.  
  
```  
int GetScrollLimit();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje maximální pozice posuvníku v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos  
 Načte aktuální pozice posuvníku.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje aktuální pozice posuvníku v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Je aktuální pozice relativní hodnotu, která závisí na aktuální rozsah umožňující posouvání. Například pokud posouvání rozsahu 100 až 200 a posouvacího políčka je uprostřed panelu, je aktuální pozice 150.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange  
 Zkopíruje aktuální pozice minimální a maximální posuvník pro danou posuvník do umístění určeného *lpMinPos* a *lpMaxPos*.  
  
```  
void GetScrollRange(
    LPINT lpMinPos,  
    LPINT lpMaxPos) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpMinPos*  
 Odkazuje na celočíselnou proměnnou, která se zobrazí minimální pozici.  
  
 *lpMaxPos*  
 Odkazuje na celočíselnou proměnnou, která se zobrazí na nejvyšší pozici.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí rozsah pro ovládací prvek posuvníku je prázdná (jsou obě hodnoty 0).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).  
  
##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo  
 Nastaví informace o `SCROLLINFO` struktura udržuje o posuvníku.  
  
```  
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lpScrollInfo*  
 Ukazatel [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktury.  
  
 *bRedraw*  
 Určuje, zda by se měl překreslit posuvníku, tak, aby odrážela nové informace. Pokud *bRedraw* má hodnotu TRUE, překreslení posuvníku. Pokud je FALSE, není překreslení. Ve výchozím nastavení se překreslí posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu je vrácená hodnota TRUE. V opačném případě je FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné zadat potřebné hodnoty `SCROLLINFO` struktury parametry, včetně hodnoty příznaku.  
  
 `SCROLLINFO` Struktura obsahuje informace o posuvník, včetně minimální a maximální posouvání pozic, velikost stránky a pozice posuvníku (Flash). Zobrazit [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) struktura téma v sadě Windows SDK pro další informace o změně výchozího nastavení struktury.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]  
  
##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos  
 Nastaví aktuální pozici jezdce na klíči určenému *nPos* nebo ho překreslí, je-li zadána, posuvník tak, aby odrážely novou pozici.  
  
```  
int SetScrollPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos –*  
 Určuje novou pozici pro posuvníku. Musí být v rozsahu posouvání.  
  
 *bRedraw*  
 Určuje, zda by se měl překreslit posuvníku, tak, aby odrážely novou pozici. Pokud *bRedraw* má hodnotu TRUE, překreslení posuvníku. Pokud je FALSE, není překreslení. Ve výchozím nastavení se překreslí posuvníku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje předchozí pozice posuvníku v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nastavte *bRedraw* na hodnotu FALSE vždy, když posuvníku se vyžadovaly překreslení následných volání do jiné funkce vyhnout se tak nutnosti posuvník překreslení dvakrát během krátkého intervalu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CScrollBar::SetScrollRange](#setscrollrange).  
  
##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange  
 Nastaví pozici minimální a maximální hodnoty pro daný posuvník.  
  
```  
void SetScrollRange(
    int nMinPos,  
    int nMaxPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nMinPos*  
 Určuje minimum pro posouvání pozici.  
  
 *nMaxPos*  
 Určuje maximální posouvání pozici.  
  
 *bRedraw*  
 Určuje, zda by se měl překreslit posuvníku, tak, aby odrážely změny. Pokud *bRedraw* má hodnotu TRUE, překreslení posuvníku; Pokud je hodnota FALSE, není překreslení. Ve výchozím nastavení se překreslí ho.  
  
### <a name="remarks"></a>Poznámky  
 Nastavte *nMinPos* a *nMaxPos* na hodnotu 0, chcete-li skrýt standardní posuvníky.  
  
 Nevolejte tuto funkci chcete skrýt posuvníku při zpracování zprávy oznámení posuvníku.  
  
 Pokud je volání `SetScrollRange` bezprostředně následuje po volání `SetScrollPos` členskou funkci, nastavte *bRedraw* v `SetScrollPos` 0 zabráníte posuvníku z se měl překreslit dvakrát.  
  
 Rozdíl mezi hodnotami určené *nMinPos* a *nMaxPos* nesmí být větší než 32 767. Výchozí rozsah pro ovládací prvek posuvníku je prázdná (obojí *nMinPos* a *nMaxPos* mají hodnotu 0).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]  
  
##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar  
 Zobrazí nebo skryje posuvníku.  
  
```  
void ShowScrollBar(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShow*  
 Určuje, zda posuvník je zobrazený nebo skrytý. Pokud tento parametr má hodnotu TRUE, je zobrazen posuvník; v opačném případě je skrytá.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace by neměl voláním této funkce skrýt posuvníku při zpracování zprávy oznámení posuvníku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CScrollBar::Create](#create).  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [Cedit – třída](../../mfc/reference/cedit-class.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [Cstatic – třída](../../mfc/reference/cstatic-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
