---
title: Cprogressctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f20a5f2767da015bb92a8e64491c2e5226f58aa5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705910"
---
# <a name="cprogressctrl-class"></a>Cprogressctrl – třída
Poskytuje funkce pro ovládací prvek panelu průběhu běžné Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Vytvoří `CProgressCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CProgressCtrl::Create](#create)|Vytvoří ovládací prvek indikátoru průběhu a připojí ho k `CProgressCtrl` objektu.|  
|[CProgressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek průběh se zadaným rozšířené styly Windows a připojí ho k `CProgressCtrl` objektu.|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|Získá barvu indikátoru průběhu pro aktuální ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|Získá barvu pozadí aktuální indikátor průběhu.|  
|[CProgressCtrl::GetPos](#getpos)|Získá aktuální pozici indikátor průběhu.|  
|[CProgressCtrl::GetRange](#getrange)|Získá horní a dolní mez rozsahu ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::GetState](#getstate)|Získá stav aktuální ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::GetStep](#getstep)|Načte přírůstek krok pro indikátor průběhu aktuální ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::OffsetPos](#offsetpos)|Posune aktuální pozici ovládací prvek indikátoru průběhu ve zadaným přírůstkem nebo ho překreslí panelu tak, aby odrážely novou pozici.|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|Nastavuje barvu indikátoru průběhu v aktuální ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí pro indikátor průběhu.|  
|[CProgressCtrl::SetMarquee](#setmarquee)|Vypne režim marquee zapnutí nebo vypnutí pro aktuální ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::SetPos](#setpos)|Nastaví aktuální pozici pro ovládací prvek indikátoru průběhu a překreslí panelu tak, aby odrážely novou pozici.|  
|[CProgressCtrl::SetRange](#setrange)|Nastaví minimální a maximální rozsahy pro ovládací prvek indikátoru průběhu a překreslí panelu tak, aby odrážela nové rozsahy.|  
|[CProgressCtrl::SetState](#setstate)|Nastaví stav aktuální ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::SetStep](#setstep)|Určuje přírůstek krok pro ovládací prvek indikátoru průběhu.|  
|[CProgressCtrl::StepIt](#stepit)|Posune aktuální pozici pro ovládací prvek indikátoru průběhu v přírůstcích kroku (naleznete v tématu [SetStep](#setstep)) a překreslí panelu tak, aby odrážely novou pozici.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek indikátoru průběhu je okno, které aplikace můžete použít k indikaci průběhu dlouhodobé operace. Zahrnuje obdélníku, který se postupně vyplněné, zleva doprava, systémem barva zvýraznění v průběhu operace.  
  
 Ovládací prvek indikátoru průběhu má rozsah a aktuální pozici. Rozsah představuje celkovou dobu trvání operace a aktuální pozici představuje průběhu, který aplikace odeslala směrem k dokončení operace. Proceduru okna využívá k určení procentuální podíl indikátor průběhu vyplnit barvou zvýraznění rozsahu a aktuální pozici. Protože rozsahu a aktuální pozici hodnoty jsou vyjádřené jako celá čísla se znaménkem, je možné rozsahu hodnot aktuální pozici od-2,147,483,648 do 2 147 483 647 (včetně).  
  
 Další informace o používání `CProgressCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl  
 Vytvoří `CProgressCtrl` objektu.  
  
```  
CProgressCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření `CProgressCtrl` objektu, volejte `CProgressCtrl::Create` vytvořit ovládací prvek indikátoru průběhu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CProgressCtrl::Create  
 Vytvoří ovládací prvek indikátoru průběhu a připojí ho k `CProgressCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje ovládací prvek indikátoru průběhu stylu. Použít libovolnou kombinaci stylesdescribed okno v [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) v sadě Windows SDK, kromě následujících průběhu – styly ovládacího prvku do ovládacího prvku:  
  
- Pbs_vertical – zobrazí informace o průběhu svisle, shora dolů. Bez tento příznak ovládací prvek indikátoru průběhu zobrazí ve vodorovném směru, zleva doprava.  
  
- Pbs_smooth – zobrazí postupné, technologie smooth vyplníte ovládací prvek indikátoru průběhu. Bez tohoto příznaku ovládací prvek vyplní bloky.  
  
 *Rect*  
 Určuje ovládací prvek indikátoru průběhu velikost a umístění. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury. Vzhledem k tomu, ovládací prvek musí být podřízené okno, zadaných souřadnic jsou vzhledem ke klientské oblasti *pParentWnd*.  
  
 *pParentWnd*  
 Určuje průběhu nadřazené okno ovládacího prvku, obvykle `CDialog`. Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládací prvek indikátoru průběhu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud `CProgressCtrl` je objekt byl úspěšně vytvořen; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CProgressCtrl` objektu ve dvou krocích. Nejprve volat konstruktor, který vytvoří `CProgressCtrl` objekt a následně zavolat `Create`, což vytvoří ovládací prvek indikátoru průběhu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CProgressCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CProgressCtrl` objektu.  
  
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
 Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.  
  
 *dwStyle*  
 Určuje ovládací prvek indikátoru průběhu stylu. Použít libovolnou kombinaci styly oken, které jsou popsané v [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) v sadě Windows SDK.  
  
 *Rect*  
 Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.  
  
 *pParentWnd*  
 Ukazatel na okno, který je nadřazeného ovládacího prvku.  
  
 *nID*  
 ID ovládacího prvku podřízené okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 Získá barvu indikátoru průběhu pro aktuální ovládací prvek indikátoru průběhu.  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva aktuální indikátor průběhu, vyjádřené [COLORREF](/windows/desktop/gdi/colorref) hodnotu nebo CLR_DEFAULT, pokud je barva řádku indikátoru průběhu výchozí barvy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_GETBARCOLOR](/windows/desktop/Controls/pbm-getbarcolor) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 Získá barvu pozadí aktuální indikátor průběhu.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva pozadí aktuální indikátor průběhu, vyjádřené [COLORREF](/windows/desktop/gdi/colorref) hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_GETBKCOLOR](/windows/desktop/Controls/pbm-getbkcolor) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 Načte aktuální pozici indikátor průběhu.  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice ovládací prvek indikátoru průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Pozice ovládací prvek indikátoru průběhu není fyzické umístění na obrazovce, ale spíš mezi horní a dolní rozsahu uvedené v [SetRange](#setrange).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 Získá aktuální horní a dolní mez nebo rozsahu, ovládací prvek indikátoru průběhu.  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 *nLower*  
 Odkaz na celé číslo, které přijímají dolní mez ovládací prvek indikátoru průběhu.  
  
 *nUpper*  
 Odkaz na celé číslo, které přijímají horní limit počtu ovládací prvek indikátoru průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce zkopíruje hodnot dolní a horní omezení na celá čísla odkazuje *nLower* a *nUpper*v uvedeném pořadí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  CProgressCtrl::GetState  
 Získá stav aktuální ovládací prvek indikátoru průběhu.  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav aktuální ovládací prvek indikátoru průběhu, který je jedním z následujících hodnot:  
  
|Hodnota|Stav|  
|-----------|-----------|  
|PBST_NORMAL|V průběhu|  
|PBST_ERROR|Chyba|  
|PBST_PAUSED|Pozastaveno|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_GETSTATE](/windows/desktop/Controls/pbm-getstate) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která je použita k programovému přístupu ke ovládací prvek indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte stav aktuální ovládací prvek indikátoru průběhu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 Načte přírůstek krok pro indikátor průběhu aktuální ovládací prvek indikátoru průběhu.  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Krok přírůstek indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Krok přírůstek je rozsah, pomocí kterého volání [CProgressCtrl::StepIt](#stepit) zvyšuje aktuální pozici indikátor průběhu.  
  
 Tato metoda odesílá [PBM_GETSTEP](/windows/desktop/Controls/pbm-getstep) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která je použita k programovému přístupu ke ovládací prvek indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte krok přírůstek aktuální ovládací prvek indikátoru průběhu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 Posune průběhu aktuální pozice ovládacího prvku v přírůstcích určené *nPos* a překreslí panelu tak, aby odrážely novou pozici.  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos –*  
 Velikost přejdete pozice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozice ovládací prvek indikátoru průběhu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 Nastavuje barvu indikátoru průběhu v aktuální ovládací prvek indikátoru průběhu.  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*clrBar*|[in] A [COLORREF](/windows/desktop/gdi/colorref) hodnota, která určuje novou barvu indikátoru průběhu. Zadejte CLR_DEFAULT způsobit indikátor průběhu používat výchozí barvy.|  
  
### <a name="return-value"></a>Návratová hodnota  

Na předchozí barvu indikátoru průběhu, vyjádřené [COLORREF](/windows/desktop/gdi/colorref) hodnotu nebo CLR_DEFAULT, pokud je Barva Indikátor průběhu výchozí barvy.  
  
### <a name="remarks"></a>Poznámky  

`SetBarColor` Metoda nastaví průběhu barva pouze tehdy, pokud Windows Vista [motiv](/windows/desktop/Controls/visual-styles-overview) není platná.  
  
 Tato metoda odesílá [PBM_SETBARCOLOR](/windows/desktop/Controls/pbm-setbarcolor) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která je použita k programovému přístupu ke ovládací prvek indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu změní barvu indikátoru průběhu pro červená, zelená, modrá nebo výchozí.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 Nastaví barvu pozadí pro indikátor průběhu.  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parametry  
 *clrNew*  
 COLORREF hodnotu, která určuje novou barvou pozadí. Zadejte hodnotu CLR_DEFAULT používat výchozí barva pozadí pro indikátor průběhu.  
  
### <a name="return-value"></a>Návratová hodnota  
 [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která předchozí barvu pozadí nebo CLR_DEFAULT, pokud je barva pozadí výchozí barvy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 Vypne režim marquee zapnutí nebo vypnutí pro aktuální ovládací prvek indikátoru průběhu.  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*fMarqueeMode*|[in] True pro zapnutí marquee režim on, nebo FALSE, pokud chcete vypnout režim výběr.|  
|*nInterval*|[in] Doba v milisekundách mezi aktualizacemi animace běžícího textu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vždy vrátí hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Když je zapnutý režim marquee, je animovaný indikátor průběhu a posouvání, jako je přihlašování marquee celé obrazovky.  
  
 Tato metoda odesílá [PBM_SETMARQUEE](/windows/desktop/Controls/pbm-setmarquee) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která je použita k programovému přístupu ke ovládací prvek indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu spouští a zastavuje běžící animace.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 Nastaví průběh panelu aktuální pozice ovládacího prvku podle specifikace *nPos* a překreslí panelu tak, aby odrážely novou pozici.  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos –*  
 Nové pozice ovládací prvek indikátoru průběhu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozice ovládací prvek indikátoru průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Pozice ovládací prvek indikátoru průběhu není fyzické umístění na obrazovce, ale spíš mezi horní a dolní rozsahu uvedené v [SetRange](#setrange).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 Nastaví horní a dolní limity průběhu rozsah ovládacího prvku a překreslí panelu tak, aby odrážela nové rozsahy.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 *nLower*  
 Určuje dolní mez rozsahu (výchozí hodnota je nula).  
  
 *nUpper*  
 Určuje horní mez rozsahu (výchozí hodnota je 100).  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce `SetRange32` Nastaví rozsah 32bitové pro ovládací prvek průběh.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>  CProgressCtrl::SetState  
 Nastaví stav aktuální ovládací prvek indikátoru průběhu.  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*iState*|[in] Stav nastavení indikátor průběhu. Použijte jednu z následujících hodnot:<br /><br /> -PBST_NORMAL – probíhá<br />-PBST_ERROR – chyba<br />-PBST_PAUSED – pozastaveno|  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí stav aktuální ovládací prvek indikátoru průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_SETSTATE](/windows/desktop/Controls/pbm-setstate) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, která je použita k programovému přístupu ke ovládací prvek indikátoru průběhu. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví stav aktuální ovládací prvek indikátoru průběhu pozastaveno nebo probíhá.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>  CProgressCtrl::SetStep  
 Určuje přírůstek krok pro ovládací prvek indikátoru průběhu.  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>Parametry  
 *nStep*  
 Nový krok přírůstku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí krok přírůstku.  
  
### <a name="remarks"></a>Poznámky  
 Krok přírůstek je rozsah, pomocí kterého volání `CProgressCtrl::StepIt` zvyšuje průběh panelu na aktuální pozici.  
  
 Přírůstek krok výchozí je 10.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 Posune aktuální pozici pro ovládací prvek indikátoru průběhu v přírůstcích kroku nebo ho překreslí panelu tak, aby odrážely novou pozici.  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozice ovládací prvek indikátoru průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Přírůstek krok nastavuje `CProgressCtrl::SetStep` členskou funkci.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL2 knihovny MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)


