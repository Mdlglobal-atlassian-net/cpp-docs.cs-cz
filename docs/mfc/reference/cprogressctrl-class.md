---
title: CProgressCtrl – třída | Microsoft Docs
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
ms.openlocfilehash: 38ccc4acfdfd618bf0fa11f4a49c1e0b78f009ca
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079387"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl – třída
Poskytuje funkce ovládacího panelu Windows běžné průběh.  
  
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
|[CProgressCtrl::Create](#create)|Ovládací prvek panelu průběhu vytvoří a připojí jej k `CProgressCtrl` objektu.|  
|[CProgressCtrl::CreateEx](#createex)|Vytvoří ovládací prvek průběhu s zadaný Windows rozšířené styly a připojí jej k `CProgressCtrl` objektu.|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|Získá aktuální ovládací panel prvek průběh barva indikátoru indikátor průběhu.|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|Získá barvu pozadí aktuální indikátor průběhu.|  
|[CProgressCtrl::GetPos](#getpos)|Získá aktuální umístění indikátoru průběhu.|  
|[CProgressCtrl::GetRange](#getrange)|Získá horní a dolní mez rozsahu ovládací panel prvek průběh.|  
|[CProgressCtrl::GetState](#getstate)|Získá stav aktuální ovládací panel prvek průběh.|  
|[CProgressCtrl::GetStep](#getstep)|Načte krok krok pro indikátor průběhu aktuální ovládacího panelu průběhu.|  
|[CProgressCtrl::OffsetPos](#offsetpos)|Přejde aktuální pozici ovládací prvek panelu průběhu o určený přírůstek nebo ho překreslí panelu tak, aby odrážely novou pozici.|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|Nastaví barvu indikátoru průběhu indikátoru v ovládacím panelu aktuální průběh.|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí pro indikátor průběhu.|  
|[CProgressCtrl::SetMarquee](#setmarquee)|Změní režim výběr zapnout nebo vypnout pro aktuální ovládací panel prvek průběh.|  
|[CProgressCtrl::SetPos](#setpos)|Nastaví aktuální pozici pro ovládací prvek panelu průběhu nebo ho překreslí panelu tak, aby odrážely novou pozici.|  
|[CProgressCtrl::SetRange](#setrange)|Nastaví minimální a maximální rozsahy pro ovládací prvek panelu průběhu nebo ho překreslí panelu tak, aby odrážely novou rozsahy.|  
|[CProgressCtrl::SetState](#setstate)|Nastaví stav aktuální ovládací panel prvek průběh.|  
|[CProgressCtrl::SetStep](#setstep)|Určuje krok krok pro ovládací prvek panelu průběhu.|  
|[CProgressCtrl::StepIt](#stepit)|Přejde na aktuální pozici pro ovládací prvek panelu průběhu krok krok (viz [SetStep](#setstep)) nebo ho překreslí panelu tak, aby odrážely novou pozici.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek panelu průběhu je okno, které aplikace můžete použít informace o průběhu časově náročná operace. Skládá se z obdélníku, která se postupně zaplní, zleva doprava, systémem barva zvýraznění v průběhu operace.  
  
 Ovládací prvek panelu průběhu má rozsah a aktuální pozici. Rozsah reprezentuje celkovou dobu trvání operace a aktuální pozici reprezentuje průběh provedena aplikace k dokončení operace. Okno postup používá k určení procento indikátor průběhu vyplníte barva zvýraznění rozsahu a aktuální pozici. Protože rozsah a aktuální pozici hodnoty jsou vyjádřené jako podepsaná celá čísla, je možné rozsahu hodnot aktuální pozici z-2,147,483,648 na 2 147 483 647 (včetně).  
  
 Další informace o používání `CProgressCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
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
 Poté, co vytvořen `CProgressCtrl` objektu, volání `CProgressCtrl::Create` vytvoření ovládacího prvku panel průběhu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CProgressCtrl::Create  
 Ovládací prvek panelu průběhu vytvoří a připojí jej k `CProgressCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje styl ovládacího panelu průběhu. Použít libovolnou kombinaci okno stylesdescribed v [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK kromě následující průběh panelu Styly ovládacího prvku do ovládacího prvku:  
  
- `PBS_VERTICAL` Zobrazí informace o průběhu svisle, shora dolů. Bez tento příznak zobrazí ovládací panel prvek průběh vodorovně, vlevo vpravo.  
  
- `PBS_SMOOTH` Zobrazí postupné, technologie smooth naplnění v ovládacím prvku panel průběhu. Bez tento příznak bude bloky vyplníte ovládací prvek.  
  
 *Rect –*  
 Určuje velikost a umístění ovládacích prvků panelu průběhu. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura. Protože ovládací prvek musí být podřízeného okna, zadaný souřadnice jsou relativní vzhledem k klientské oblasti *pParentWnd*.  
  
 *pParentWnd*  
 Určuje průběh panelu ovládacího prvku nadřazeného okna, obvykle `CDialog`. Nesmí být **hodnotu NULL.**  
  
 *nID*  
 Určuje ID ovládacího prvku panel průběhu.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud `CProgressCtrl` objekt je úspěšně vytvořená; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CProgressCtrl` objektu ve dvou krocích. Nejprve volání konstruktoru, který vytvoří `CProgressCtrl` objektu a pak zavolají `Create`, která vytvoří ovládací panel prvek průběh.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CProgressCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CProgressCtrl` objektu.  
  
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
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 *dwStyle*  
 Určuje styl ovládacího panelu průběhu. Použít libovolnou kombinaci styly oken popsané v [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) ve Windows SDK.  
  
 *Rect –*  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta *pParentWnd*.  
  
 *pParentWnd*  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 *nID*  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 Získá aktuální ovládací panel prvek průběh barva indikátoru indikátor průběhu.  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva aktuální indikátor průběhu, vyjádřené [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, nebo `CLR_DEFAULT` Pokud výchozí barvu barvu panelu indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 Získá barvu pozadí aktuální indikátor průběhu.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva pozadí aktuální indikátor průběhu, vyjádřené [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 Načte aktuální pozici indikátor průběhu.  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Umístění ovládacího panelu průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Pozice ovládací panel prvek průběh není na fyzické umístění na obrazovce, ale spíše je mezi horní a dolní rozsah uvedené v [SetRange](#setrange).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 Získá aktuální horní a dolní mez, nebo rozsah, ovládacího panelu průběhu.  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>Parametry  
 *nLower*  
 Odkaz na typ integer přijetí dolní limit ovládací panel prvek průběh.  
  
 *nUpper*  
 Odkaz na typ integer přijetí horní limit počtu ovládací panel prvek průběh.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce zkopíruje hodnoty horní a dolní mez na celá čísla odkazuje *nLower* a *nUpper*, v uvedeném pořadí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  CProgressCtrl::GetState  
 Získá stav aktuální ovládací panel prvek průběh.  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav aktuální panelu Ovládací prvek průběh, což je jedna z následujících hodnot:  
  
|Hodnota|Stav|  
|-----------|-----------|  
|`PBST_NORMAL`|V průběhu|  
|`PBST_ERROR`|Chyba|  
|`PBST_PAUSED`|Pozastaveno|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, který používá k programovému přístupu ovládací panel prvek průběh. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte stav aktuální ovládací panel prvek průběh.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 Načte krok krok pro indikátor průběhu aktuální ovládacího panelu průběhu.  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Přírůstek krok indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Krok přírůstek je hodnota, o kterou volání [CProgressCtrl::StepIt](#stepit) zvyšuje aktuální pozici indikátor průběhu.  
  
 Tato metoda odesílá [PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, který používá k programovému přístupu ovládací panel prvek průběh. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte krok přírůstek aktuální ovládací panel prvek průběh.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 Posune průběh panelu aktuální pozici ovládacího prvku pomocí určeného přírůstek *nPos –* nebo ho překreslí panelu tak, aby odrážely novou pozici.  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos –*  
 Velikost posunut pozici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozici panelu Ovládací prvek průběh.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 Nastaví barvu indikátoru průběhu indikátoru v ovládacím panelu aktuální průběh.  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *clrBar*|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která určuje nové barva indikátoru indikátor průběhu. Zadejte `CLR_DEFAULT` způsobí indikátor průběhu používat jeho výchozí barvu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí barva indikátoru průběhu, vyjádřené [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, nebo `CLR_DEFAULT` Pokud výchozí barvu barva indikátoru indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 `SetBarColor` Metoda nastaví průběh panelu Barva pouze v případě [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] [motiv](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx) není funkční.  
  
 Tato metoda odesílá [PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, který používá k programovému přístupu ovládací panel prvek průběh. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu změny barva indikátoru průběhu červená, zelená, modrá nebo výchozí.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 Nastaví barvu pozadí pro indikátor průběhu.  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parametry  
 *clrNew*  
 A **COLORREF** hodnotu, která určuje barvu pozadí nové. Zadejte `CLR_DEFAULT` hodnotu výchozí barvu pozadí pro indikátor průběhu.  
  
### <a name="return-value"></a>Návratová hodnota  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která určuje barvu pozadí předchozí nebo **CLR_DEFAULT** je-li barvu pozadí výchozí barvy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 Změní režim výběr zapnout nebo vypnout pro aktuální ovládací panel prvek průběh.  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *fMarqueeMode*|`true` Zapnutí režimu výběr, nebo `false` Chcete-li režim výběru vypnout.|  
|[v] *nInterval*|Čas v milisekundách mezi aktualizace animace běžícího textu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vždy vrátí hodnotu `true`.  
  
### <a name="remarks"></a>Poznámky  
 Když je zapnutý režim výběr, je animovaný indikátoru průběhu a viditelné jako přihlašování hranice výběru celé obrazovky.  
  
 Tato metoda odesílá [PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, který používá k programovému přístupu ovládací panel prvek průběh. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu se spustí a ukončí běžící animace.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 Nastaví průběh panelu Ovládací prvek na aktuální pozici podle specifikace *nPos –* nebo ho překreslí panelu tak, aby odrážely novou pozici.  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 *nPos –*  
 Nové umístění ovládacího panelu průběhu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozici panelu Ovládací prvek průběh.  
  
### <a name="remarks"></a>Poznámky  
 Pozice ovládací panel prvek průběh není na fyzické umístění na obrazovce, ale spíše je mezi horní a dolní rozsah uvedené v [SetRange](#setrange).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 Nastaví horní a dolní limity průběh panelu ovládacího prvku rozsah nebo ho překreslí panelu tak, aby odrážely novou rozsahy.  
  
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
 Nastaví stav aktuální ovládací panel prvek průběh.  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *iState*|Stav, který se má nastavit indikátor průběhu. Použijte jednu z následujících hodnot:<br /><br /> - `PBST_NORMAL` – V průběhu<br />- `PBST_ERROR` – Chyba<br />- `PBST_PAUSED` -Pozastavena|  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí stav aktuální ovládací panel prvek průběh.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_progressCtrl`, který používá k programovému přístupu ovládací panel prvek průběh. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví stav aktuální ovládací panel prvek průběh pozastaveno nebo probíhá.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>  CProgressCtrl::SetStep  
 Určuje krok krok pro ovládací prvek panelu průběhu.  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>Parametry  
 *nStep*  
 Nový krok přírůstku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí krok přírůstku.  
  
### <a name="remarks"></a>Poznámky  
 Krok přírůstek je hodnota, o kterou volání `CProgressCtrl::StepIt` zvyšuje průběh panelu je aktuální pozici.  
  
 Výchozí krok krok je 10.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 Přejde na aktuální pozici pro ovládací prvek panelu průběhu krok krok nebo ho překreslí panelu tak, aby odrážely novou pozici.  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí pozici panelu Ovládací prvek průběh.  
  
### <a name="remarks"></a>Poznámky  
 Přírůstek krok se nastavuje pomocí `CProgressCtrl::SetStep` – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL2 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)


