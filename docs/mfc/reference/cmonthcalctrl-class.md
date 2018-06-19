---
title: CMonthCalCtrl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f8dd962a06d6c7edadcdd029bd83d44b251aec8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377736"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl – třída
Zapouzdřuje funkce ovládací prvek měsíční kalendář.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Vytvoří `CMonthCalCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMonthCalCtrl::Create](#create)|Vytvoří ovládací prvek měsíční kalendář a připojí jej k `CMonthCalCtrl` objektu.|  
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Načte šířka ohraničení ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Načte počet kalendářů zobrazí v ovládacím prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Načte informace o ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::GetCalID](#getcalid)|Načte identifikátor kalendáře ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::GetColor](#getcolor)|Získá barvu zadané oblasti ovládací prvek měsíční kalendář.|  
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Načte zobrazení, které je aktuálně zobrazený v ovládacím prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::GetCurSel](#getcursel)|Načte systémového času uvedeného data aktuálně vybrané.|  
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Získá první den v týdnu, který se má zobrazit v levém sloupci kalendáře.|  
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Načte aktuální maximální počet dní, které je možné vybrat v ovládacím prvku měsíční kalendář.|  
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Načte maximální šířku řetězec "Dnes" ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Získá minimální velikost pro indikaci úplný měsíc v ovládacím prvku měsíční kalendář.|  
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Načte scroll rychlost pro ovládací prvek měsíční kalendář.|  
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Načte aktuální informace představující vysoké a nízké omezení prvku měsíční kalendář zobrazení.|  
|[CMonthCalCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální datum nastaveno v ovládacím prvku měsíční kalendář.|  
|[CMonthCalCtrl::GetSelRange](#getselrange)|Načte informace o datu představující horní a dolní meze rozsahu kalendářních dat, který je aktuálně vybraný uživatelem.|  
|[CMonthCalCtrl::GetToday](#gettoday)|Načte informace o datu zadané jako "dnes" pro ovládací prvek měsíční kalendář datum.|  
|[CMonthCalCtrl::HitTest](#hittest)|Určuje, které části ovládací prvek měsíční kalendář je k danému bodu na obrazovce.|  
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce století zobrazení.|  
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce desetiletí zobrazení.|  
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce zobrazení měsíce.|  
|[CMonthCalCtrl::IsYearView](#isyearview)|Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce roku zobrazení.|  
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Nastaví šířku ohraničení ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Nastaví výchozí šířku ohraničení ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::SetCalID](#setcalid)|Nastaví identifikátor kalendáře ovládacího prvku kalendář aktuálního měsíce.|  
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Nastaví ovládací prvek aktuální měsíční kalendář zobrazit století.|  
|[CMonthCalCtrl::SetColor](#setcolor)|Nastaví barvu zadané oblasti ovládací prvek měsíční kalendář.|  
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Nastaví ovládací prvek aktuální měsíční kalendář zobrazíte zadané zobrazení.|  
|[CMonthCalCtrl::SetCurSel](#setcursel)|Nastaví aktuálně vybrané datum pro ovládací prvek měsíční kalendář.|  
|[CMonthCalCtrl::SetDayState](#setdaystate)|Nastaví zobrazení dní v ovládacím prvku měsíční kalendář.|  
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Nastaví aktuální měsíční kalendář řídit desetiletí zobrazení.|  
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Nastaví den v týdnu, který se má zobrazit v levém sloupci kalendáře.|  
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Nastaví maximální počet dní, které je možné vybrat v ovládacím prvku měsíční kalendář.|  
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Nastaví četnost posuv pro ovládací prvek měsíční kalendář.|  
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Nastaví ovládací prvek aktuální měsíční kalendář zobrazit měsíc.|  
|[CMonthCalCtrl::SetRange](#setrange)|Nastaví minimální a maximální počet povolených data pro ovládací prvek měsíční kalendář.|  
|[CMonthCalCtrl::SetSelRange](#setselrange)|Nastaví výběr měsíční kalendář řízení na daném časovém období.|  
|[CMonthCalCtrl::SetToday](#settoday)|Nastaví ovládacího prvku kalendář aktuálního dne.|  
|[CMonthCalCtrl::SetYearView](#setyearview)|Nastaví aktuální měsíční kalendář řídit k zobrazení roku.|  
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Ovládací prvek měsíční kalendář repaints jeho velikost minimální, jeden měsíc.|  
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Aktuální ovládací prvek měsíční kalendář vypočítá nejmenší obdélníku, která může obsahovat všech kalendářů splňující v obdélníku zadaný.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek měsíční kalendář poskytuje uživatele s kalendáři jednoduché rozhraní, ze kterého může uživatel vybrat datum. Uživatel může změnit zobrazení podle:  
  
-   Zpětný posun a jejich předávání z měsíc měsíc.  
  
-   Kliknutím na text dnes zobrazíte aktuální den (Pokud **MCS_NOTODAY** styl nepoužívá).  
  
-   Výběr měsíc nebo rok z místní nabídky.  
  
 Můžete přizpůsobit v měsíci v ovládacím prvku kalendář s použitím různých styly k objektu při jeho vytvoření. Tyto styly jsou popsané v [styly ovládacího prvku měsíční kalendář](http://msdn.microsoft.com/library/windows/desktop/bb760919) ve Windows SDK.  
  
 Ovládací prvek měsíční kalendář můžete zobrazit více než jeden měsíc a speciální dnů (například svátků) může svědčit o tom podle tučné datum.  
  
 Další informace o použití ovládací prvek měsíční kalendář, najdete v části [pomocí CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdtctl.h  
  
##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl  
 Vytvoří `CMonthCalCtrl` objektu.  
  
```  
CMonthCalCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat **vytvořit** po vytvoření objektu.  
  
##  <a name="create"></a>  CMonthCalCtrl::Create  
 Vytvoří ovládací prvek měsíční kalendář a připojí jej k `CMonthCalCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);

 
virtual BOOL Create(
    DWORD dwStyle,  
    const POINT& pt,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje kombinaci styly Windows použité pro ovládací prvek měsíční kalendář. V tématu [styly ovládacího prvku měsíční kalendář](http://msdn.microsoft.com/library/windows/desktop/bb760919) ve Windows SDK pro další informace o stylů.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura. Obsahuje umístění a velikost ovládací prvek měsíční kalendář.  
  
 `pt`  
 Odkaz na [bodu](http://msdn.microsoft.com/library/windows/desktop/dd162805) struktura, která identifikuje umístění ovládací prvek měsíční kalendář.  
  
 `pParentWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je okno nadřazeného prvku měsíční kalendář. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku měsíční kalendář  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření měsíce v ovládacím prvku ve dvou krocích kalendář:  
  
1.  Volání [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) k vytvoření `CMonthCalCtrl` objektu.  
  
2.  Volání této funkce člen, který vytvoří ovládací prvek měsíční kalendář a připojí jej k `CMonthCalCtrl` objektu.  
  
 Při volání **vytvořit**, běžné ovládací prvky jsou inicializovány. Verze **vytvořit** jste volání Určuje, jak je velikost:  
  
-   Pokud chcete, aby MFC automaticky velikost ovládacího prvku na jeden měsíc, volání přepsání, které používá `pt` parametr.  
  
-   Chcete-li velikost ovládacího prvku, volejte přepsání této funkce, která používá `rect` parametr.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]  
  
##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder  
 Načte šířka ohraničení ovládacího prvku kalendář aktuálního měsíce.  
  
```  
int GetCalendarBorder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka ohraničení ovládacího prvku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760945) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount  
 Načte počet kalendářů zobrazí v ovládacím prvku kalendář aktuálního měsíce.  
  
```  
int GetCalendarCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet aktuálně zobrazený v ovládacím prvku měsíční kalendář kalendáře. Maximální povolený počet kalendáře je 12.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCALENDARCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760947) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo  
 Načte informace o ovládacího prvku kalendář aktuálního měsíce.  
  
```  
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] `pmcGridInfo`|Ukazatel na [MCGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760925) struktura, která přijímá informace o ovládacího prvku kalendář aktuálního měsíce. Volající zodpovídá za přidělování a inicializace tuto strukturu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCALENDARGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760949) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, který používá k programovému přístupu ovládací prvek měsíční kalendář. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu používá `GetCalendarGridInfo` metoda pro načtení ovládací prvek aktuální měsíční kalendář zobrazí datum kalendáře.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]  
  
##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID  
 Načte identifikátor kalendáře ovládacího prvku kalendář aktuálního měsíce.  
  
```  
CALID GetCalID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jeden z [kalendáře identifikátor](http://msdn.microsoft.com/library/windows/desktop/dd317732) konstanty.  
  
### <a name="remarks"></a>Poznámky  
 Identifikátor kalendáře označuje oblast kalendář, jako je například Gregoriánský (lokalizovaný), japonština nebo hidžra kalendáře. Aplikace můžete použít identifikátor kalendář, který obsahuje různé jazykové podpory funkce.  
  
 Tato metoda odesílá [MCM_GETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760951) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor  
 Načte barva oblast v měsíci v ovládacím prvku určeného kalendář `nRegion`.  
  
```  
COLORREF GetColor(int nRegion) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nRegion`  
 Oblast prvku měsíční kalendář, ze kterého je načíst barvu. Seznam hodnot, najdete v článku `nRegion` parametr [setcolor –](#setcolor).  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnota, která určuje barvu přidružené část ovládací prvek měsíční kalendář, pokud bylo úspěšné. Tato funkce člena, jinak vrátí hodnotu -1.  
  
##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView  
 Načte zobrazení, které je aktuálně zobrazený v ovládacím prvku kalendář aktuálního měsíce.  
  
```  
DWORD GetCurrentView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální zobrazení, které je indikován jednu z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`MCMV_MONTH`|Měsíční zobrazení|  
|`MCMV_YEAR`|Zobrazení pro roční|  
|`MCMV_DECADE`|Desetiletí zobrazení|  
|`MCMV_CENTURY`|Století zobrazení|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, který používá k programovému přístupu ovládací prvek měsíční kalendář. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad sestavy kódu, které zobrazení měsíční kalendář řídit aktuálně zobrazuje.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]  
  
##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel  
 Načte systémového času uvedeného data aktuálně vybrané.  
  
```  
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;  
   
BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `refDateTime`  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu. Přijme aktuální čas.  
  
 `pDateTime`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která bude přijímat informace o aktuálně vybraném datu. Tento parametr musí být platná adresa a nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; otherwize 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb760957), jak je popsáno v sadě Windows SDK.  
  
> [!NOTE]
>  Tato funkce člen selže, pokud styl **MCS_MULTISELECT** nastavena.  
  
 Implementace MFC na `GetCurSel`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek  
 Získá první den v týdnu, který se má zobrazit v levém sloupci kalendáře.  
  
```  
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pbLocal*  
 Ukazatel **BOOL** hodnotu. Pokud je hodnota nulová, nastavení ovládacího prvku neodpovídá nastavení v Ovládacích panelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselná hodnota představující první den v týdnu. V tématu **poznámky** Další informace o co představují tyto celých čísel.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb760958), jak je popsáno v sadě Windows SDK. Dny v týdnu je vyjádřena jako celá čísla, následujícím způsobem.  
  
|Hodnota|Den v týdnu|  
|-----------|---------------------|  
|0|Pondělí|  
|1|Úterý|  
|2|Středa|  
|3|Čtvrtek|  
|4|Pátek|  
|5|Sobota|  
|6|Neděle|  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).  
  
##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount  
 Načte aktuální maximální počet dní, které je možné vybrat v ovládacím prvku měsíční kalendář.  
  
```  
int GetMaxSelCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselná hodnota, která představuje celkový počet dní, které lze vybrat pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760960), jak je popsáno v sadě Windows SDK. Tuto funkci člen použít pro ovládací prvky s **MCS_MULTISELECT** styl sady.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).  
  
##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth  
 Načte maximální šířku řetězec "Dnes" ovládacího prvku kalendář aktuálního měsíce.  
  
```  
DWORD GetMaxTodayWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka řetězec "Dnes", v pixelech.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, který používá k programovému přístupu ovládací prvek měsíční kalendář. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `GetMaxTodayWidth` metoda.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]  
  
### <a name="remarks"></a>Poznámky  
 Uživatel může vrátit na aktuální datum kliknutím řetězec "Dnes", který se zobrazí v dolní části ovládací prvek měsíční kalendář. Řetězec "Dnes" obsahuje text popisku a datum text.  
  
 Tato metoda odesílá [MCM_GETMAXTODAYWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760962) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect  
 Získá minimální velikost pro indikaci úplný měsíc v ovládacím prvku měsíční kalendář.  
  
```  
BOOL GetMinReqRect(RECT* pRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pRect`  
 Ukazatel [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která bude přijímat ohraničující obdélník informace. Tento parametr musí být platná adresa a nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšné, tato funkce člen vrací nenulové hodnoty a `lpRect` obdrží ohraničující příslušné informace. Pokud je úspěšné, – členská funkce vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETMINREQRECT](http://msdn.microsoft.com/library/windows/desktop/bb760978), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta  
 Načte scroll rychlost pro ovládací prvek měsíční kalendář.  
  
```  
int GetMonthDelta() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Míra posuv pro ovládací prvek měsíční kalendář. Rychlost, jakou scroll je počet měsíců, že ovládací prvek přesune jeho zobrazení, když uživatel klikne tlačítko posuvníku jednou.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb760980), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange  
 Načte aktuální informace představující vysoké a nízké omezení prvku měsíční kalendář zobrazení.  
  
```  
int GetMonthRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    CTime& refMinRange,  
    CTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange,  
    DWORD dwFlags) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `refMinRange`  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující minimální povolené datum.  
  
 `refMaxRange`  
 Odkaz na `COleDateTime` nebo `CTime` objekt obsahující maximální povolené datum.  
  
 `pMinRange`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující data na nejnižší konec rozsahu.  
  
 `pMaxRange`  
 Ukazatel na `SYSTEMTIME` struktura obsahující datum na nejvyšší konec rozsahu.  
  
 `dwFlags`  
 Hodnota, která určuje obor omezení rozsahu mají být načteny. Tato hodnota musí mít jednu z následujících akcí.  
  
|Hodnota|Význam|  
|-----------|-------------|  
|GMR_DAYSTATE|Zahrnout předcházející a na konci měsíců viditelné rozsahu, které se zobrazují pouze částečně.|  
|GMR_VISIBLE|Zahrnout pouze měsíců, které jsou zcela zobrazeny.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo, které představuje rozsah, v měsících, předané dvě omezení indikován `refMinRange` a `refMaxRange` ve verzích první a druhý nebo `pMinRange` a `pMaxRange` ve třetí verzi.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETMONTHRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760981), jak je popsáno v sadě Windows SDK. Implementace MFC na `GetMonthRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMonthCalCtrl::SetDayState](#setdaystate).  
  
##  <a name="getrange"></a>  CMonthCalCtrl::GetRange  
 Načte aktuální minimální a maximální datum nastaveno v ovládacím prvku měsíční kalendář.  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
  
DWORD GetRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Ukazatel na `COleDateTime` objekt, `CTime` objekt, nebo [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující data na nejnižší konec rozsahu.  
  
 `pMaxRange`  
 Ukazatel na `COleDateTime` objekt, `CTime` objekt, nebo [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující datum na nejvyšší konec rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` , může být nula (žádná omezení jsou nastaveny) nebo jejich kombinaci následující hodnoty, které určují informace o limitu.  
  
|Hodnota|Význam|  
|-----------|-------------|  
|GDTR_MAX|Maximální limit je nastaven pro ovládací prvek; `pMaxRange` je platný a obsahuje informace o příslušných datu.|  
|GDTR_MIN|Minimální limit je nastaven pro ovládací prvek; `pMinRange` je platný a obsahuje informace o příslušných datu.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760983), jak je popsáno v sadě Windows SDK. Implementace MFC na `GetRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]  
  
##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange  
 Načte informace o datu představující horní a dolní meze rozsahu kalendářních dat, který je aktuálně vybraný uživatelem.  
  
```  
BOOL GetSelRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange) const;  
  
BOOL GetSelRange(
    CTime& refMinRange,  
    CTime& refMaxRange) const;  
  
BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `refMinRange`  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující minimální povolené datum.  
  
 `refMaxRange`  
 Odkaz na `COleDateTime` nebo `CTime` objekt obsahující maximální povolené datum.  
  
 `pMinRange`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující data na nejnižší konec rozsahu.  
  
 `pMaxRange`  
 Ukazatel na `SYSTEMTIME` struktura obsahující datum na nejvyšší konec rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760985), jak je popsáno v sadě Windows SDK. `GetSelRange` se nezdaří, pokud se použije k prvku měsíční kalendář, který nepoužívá **MCS_MULTISELECT** stylu.  
  
 Implementace MFC na `GetSelRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday  
 Načte informace o datu zadané jako "dnes" pro ovládací prvek měsíční kalendář datum.  
  
```  
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;  
   
BOOL GetToday(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `refDateTime`  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který označuje po aktuálním dni.  
  
 `pDateTime`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která bude přijímat informace o datu. Tento parametr musí být platná adresa a nemůže být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_GETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb760987), jak je popsáno v sadě Windows SDK. Implementace MFC na `GetToday`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]  
  
##  <a name="hittest"></a>  CMonthCalCtrl::HitTest  
 Určuje které ovládací prvek měsíční kalendář, pokud existuje, na zadané pozici.  
  
```  
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```  
  
### <a name="parameters"></a>Parametry  
 *pMCHitTest*  
 Ukazatel [MCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760927) struktura obsahující přístupů testování body pro ovládací prvek měsíční kalendář.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` hodnotu. Rovná **uHit** členem **MCHITTESTINFO** struktura.  
  
### <a name="remarks"></a>Poznámky  
 `HitTest` používá **MCHITTESTINFO** struktura, která obsahuje informace o počtu test.  
  
##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView  
 Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce století zobrazení.  
  
```  
BOOL IsCenturyView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální zobrazení století zobrazení; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) zprávy, která je popsána v sadě Windows SDK. Pokud který zprávy vrátí `MCMV_CENTURY`, vrátí tato metoda `true`.  
  
##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView  
 Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce desetiletí zobrazení.  
  
```  
BOOL IsDecadeView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální zobrazení desetiletí zobrazení; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) zprávy, která je popsána v sadě Windows SDK. Pokud který zprávy vrátí `MCMV_DECADE`, vrátí tato metoda `true`.  
  
##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView  
 Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce zobrazení měsíce.  
  
```  
BOOL IsMonthView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální zobrazení zobrazení měsíc; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) zprávy, která je popsána v sadě Windows SDK. Pokud který zprávy vrátí `MCMV_MONTH`, vrátí tato metoda `true`.  
  
##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView  
 Určuje, zda je aktuální zobrazení objektu ovládacího prvku kalendář aktuálního měsíce roku zobrazení.  
  
```  
BOOL IsYearView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální zobrazení roku zobrazení; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) zprávy, která je popsána v sadě Windows SDK. Pokud který zprávy vrátí `MCMV_YEAR`, vrátí tato metoda `true`.  
  
##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder  
 Nastaví šířku ohraničení ovládacího prvku kalendář aktuálního měsíce.  
  
```  
void SetCalendarBorder(int cxyBorder);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `cxyBorder`|Šířka ohraničení v pixelech.|  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda bude úspěšná, šířka ohraničení nastavená na `cxyBorder` parametr. Jinak je šířka ohraničení resetovat na výchozí hodnotu, která je zadána aktuální [motiv](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), nebo nula, pokud se nepoužívají motivů.  
  
 Tato metoda odesílá [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, který používá k programovému přístupu ovládací prvek měsíční kalendář. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Příklad  
 Následující kód příklad nastavuje šířku ohraničení měsíční kalendář řídit k osm pixelů. Použití [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) metoda k určení, zda tato metoda byla úspěšná.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]  
  
##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault  
 Nastaví výchozí šířku ohraničení ovládacího prvku kalendář aktuálního měsíce.  
  
```  
void SetCalendarBorderDefault();
```  
  
### <a name="remarks"></a>Poznámky  
 Šířka ohraničení je nastaven na výchozí hodnotu určeného aktuálním [motiv](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), nebo nula, pokud se nepoužívají motivů.  
  
 Tato metoda odesílá [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID  
 Nastaví identifikátor kalendáře ovládacího prvku kalendář aktuálního měsíce.  
  
```  
BOOL SetCalID(CALID calid);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `calid`|Jeden z [kalendáře identifikátor](http://msdn.microsoft.com/library/windows/desktop/dd317732) konstanty.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Určuje identifikátor kalendáře kalendář oblast, například Gregoriánský (lokalizovaný), japonština nebo hidžra kalendáře. Použití `SetCalID` metodu pro zobrazení kalendáře, která je zadána `calid` parametru národního prostředí, který obsahuje kalendáře je nainstalován ve vašem počítači.  
  
 Tato metoda odesílá [MCM_SETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760995) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, který používá k programovému přístupu ovládací prvek měsíční kalendář. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví ovládací prvek měsíční kalendář zobrazíte japonský kalendář letopočtu kalendáři. `SetCalID` Metoda bude úspěšná pouze v případě, že se kalendář je nainstalován ve vašem počítači.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]  
  
##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView  
 Nastaví ovládací prvek aktuální měsíční kalendář zobrazit století.  
  
```  
BOOL SetCenturyView();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metodu a nastavit zobrazení `MCMV_CENTURY`, která představuje století zobrazení.  
  
##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor  
 Nastaví barvu zadané oblasti ovládací prvek měsíční kalendář.  
  
```  
COLORREF SetColor(
    int nRegion,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 `nRegion`  
 Celočíselná hodnota určující jakou barvu kalendáře měsíc nastavit. Tato hodnota může být jedna z následujících akcí.  
  
|Hodnota|Význam|  
|-----------|-------------|  
|MCSC_BACKGROUND|Barva pozadí zobrazí mezi měsíců.|  
|MCSC_MONTHBK|Barva pozadí zobrazí v rámci měsíce.|  
|MCSC_TEXT|Barva použitá k zobrazení textu během jednoho měsíce.|  
|MCSC_TITLEBK|Barva pozadí zobrazí v nadpisu kalendáře.|  
|MCSC_TITLETEXT|Barva použitá k zobrazení textu v nadpisu kalendáře.|  
|MCSC_TRAILINGTEXT|Barva použitá k zobrazení textu záhlaví a koncové den. Úvodní a koncové dny jsou dny z předešlých a následných měsíců, které se zobrazují na aktuálním kalendáři.|  
  
 `ref`  
 A **COLORREF** hodnotu pro nové nastavení barvu pro zadaný část ovládací prvek měsíční kalendář.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje předchozí nastavení barvu pro zadaný část ovládací prvek měsíční kalendář, pokud bylo úspěšné. Tato zpráva v opačném případě vrátí hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760997), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]  
  
##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView  
 Nastaví ovládací prvek aktuální měsíční kalendář zobrazíte zadané zobrazení.  
  
```  
BOOL SetCurrentView(DWORD dwNewView);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `dwNewView`|Jeden z následujících hodnot, která určuje měsíční, roční, desetiletí nebo století zobrazení.<br /><br /> MCMV_MONTH: Měsíční zobrazení<br /><br /> MCMV_YEAR: Zobrazení pro roční<br /><br /> MCMV_DECADE: Zobrazení desetiletí<br /><br /> MCMV_CENTURY: Zobrazení století|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [MCM_SETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760998) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel  
 Nastaví aktuálně vybrané datum pro ovládací prvek měsíční kalendář.  
  
```  
BOOL SetCurSel(const COleDateTime& refDateTime);  
BOOL SetCurSel(const CTime& refDateTime);  
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Parametry  
 `refDateTime`  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který označuje ovládacího prvku Kalendář aktuálně vybraném měsíci.  
  
 `pDateTime`  
 Ukazatel na [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která obsahuje data nastavit jako aktuální výběr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb761002), jak je popsáno v sadě Windows SDK. Implementace MFC na `SetCurSel`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]  
  
##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState  
 Nastaví zobrazení dní v ovládacím prvku měsíční kalendář.  
  
```  
BOOL SetDayState(
    int nMonths,  
    LPMONTHDAYSTATE pStates);
```  
  
### <a name="parameters"></a>Parametry  
 *nMonths*  
 Hodnotu, která určuje, kolik prvky jsou v poli, která `pStates` odkazuje na.  
  
 `pStates`  
 Ukazatel [MONTHDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760915) pole hodnot, které definují, jak bude ovládací prvek měsíční kalendář kreslení každý den v jeho zobrazení. **MONTHDAYSTATE** datový typ je bit pole, kde každý bit (1 až 31) představuje stav den v měsíci. Pokud je bit na, zobrazí se odpovídající den v bold; v opačném případě se bude zobrazovat s žádné zvýraznění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761004), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]  
  
##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView  
 Nastaví aktuální měsíční kalendář řídit desetiletí zobrazení.  
  
```  
BOOL SetDecadeView();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metodu a nastavit zobrazení `MCMV_DECADE`, která představuje desetiletí zobrazení.  
  
##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek  
 Nastaví den v týdnu, který se má zobrazit v levém sloupci kalendáře.  
  
```  
BOOL SetFirstDayOfWeek(
    int iDay,  
    int* lpnOld = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *iDay*  
 Celočíselná hodnota představující den, kdy má být nastavena jako první den v týdnu. Tato hodnota musí být jeden z čísla dne. V tématu [GetFirstDayOfWeek](#getfirstdayofweek) popis čísla dne.  
  
 *lpnOld*  
 Ukazatel na celočíselnou hodnotu označující první den v týdnu dříve nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud předchozí první den v týdnu je nastavený na jinou hodnotu než u nenulové hodnoty **LOCALE_IFIRSTDAYOFWEEK**, což je den uvedené v nastavení ovládacího panelu. Tuto funkci, jinak vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb761006), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]  
  
##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount  
 Nastaví maximální počet dní, které je možné vybrat v ovládacím prvku měsíční kalendář.  
  
```  
BOOL SetMaxSelCount(int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nMax`  
 Hodnota, která bude nastavena pro představují maximální počet dní volitelný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761008), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]  
  
##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta  
 Nastaví četnost posuv pro ovládací prvek měsíční kalendář.  
  
```  
int SetMonthDelta(int iDelta);
```  
  
### <a name="parameters"></a>Parametry  
 *položky iDelta*  
 Počet měsíců nastavit jako míra scroll ovládacího prvku. Pokud je tato hodnota nulová, je rozdílu měsíc obnovit výchozí, což je počet měsíců, zobrazují v ovládacím prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí scroll míra. Pokud rychlost scroll nebyla dříve nastavena, je vrácenou hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb761010), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView  
 Nastaví ovládací prvek aktuální měsíční kalendář zobrazit měsíc.  
  
```  
BOOL SetMonthView();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metodu a nastavit zobrazení `MCMV_MONTH`, která představuje zobrazení měsíce.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_monthCalCtrl`, který používá k programovému přístupu ovládací prvek měsíční kalendář. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví ovládací prvek měsíční kalendář zobrazíte měsíc, rok, desetiletí a století zobrazení.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]  
  
##  <a name="setrange"></a>  CMonthCalCtrl::SetRange  
 Nastaví minimální a maximální povolená data pro ovládací prvek měsíční kalendář.  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);

 
BOOL SetRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Ukazatel na `COleDateTime` objekt, `CTime` objekt, nebo [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující data na nejnižší konec rozsahu.  
  
 `pMaxRange`  
 Ukazatel `COleDateTime` objekt, `CTime` objekt, nebo `SYSTEMTIME` struktura obsahující datum na nejvyšší konec rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761012), jak je popsáno v sadě Windows SDK. Implementace MFC na `SetRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMonthCalCtrl::GetRange](#getrange).  
  
##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange  
 Nastaví výběr měsíční kalendář řízení na daném časovém období.  
  
```  
BOOL SetSelRange(
    const COleDateTime& pMinRange,  
    const COleDateTime& pMaxRange);

 
BOOL SetSelRange(
    const CTime& pMinRange,  
    const CTime& pMaxRange);

 
BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Ukazatel na `COleDateTime` objekt, `CTime` objekt, nebo [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující data na nejnižší konec rozsahu.  
  
 `pMaxRange`  
 Ukazatel `COleDateTime` objekt, `CTime` objekt, nebo `SYSTEMTIME` struktura obsahující datum na nejvyšší konec rozsahu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761014), jak je popsáno v sadě Windows SDK. Implementace MFC na `SetSelRange`, můžete zadat `COleDateTime` využití, `CTime` využití, nebo `SYSTEMTIME` struktury využití.  
  
##  <a name="settoday"></a>  CMonthCalCtrl::SetToday  
 Nastaví ovládacího prvku kalendář aktuálního dne.  
  
```  
void SetToday(const COleDateTime& refDateTime);  
void SetToday(const CTime* pDateTime);  
  void SetToday(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Parametry  
 `refDateTime`  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje aktuální datum.  
  
 `pDateTime`  
 V druhé verzi ukazatel na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující informace o aktuálním datem. Ve třetí verzi ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která obsahuje informace o aktuálním datem.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [MCM_SETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb761016), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMonthCalCtrl::GetToday](#gettoday).  
  
##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView  
 Nastaví aktuální měsíční kalendář řídit k zobrazení roku.  
  
```  
BOOL SetYearView();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda používá [CMonthCalCtrl::SetCurrentView](#setcurrentview) metodu a nastavit zobrazení `MCMV_YEAR`, která představuje roční zobrazení.  
  
##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq  
 Zobrazí v měsíci prvek kalendáře pro minimální velikost, která zobrazuje jeden měsíc.  
  
```  
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRepaint`  
 Určuje, zda ovládacího prvku překreslen. Ve výchozím nastavení **TRUE**. Pokud **FALSE**, dojde k žádné překreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je velikost ovládací prvek měsíční kalendář, aby jeho minimální; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání metody `SizeMinReq` úspěšně zobrazí ovládací prvek celý měsíční kalendář pro kalendář jeden měsíc.  
  
##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin  
 Aktuální ovládací prvek měsíční kalendář vypočítá nejmenší obdélníku, která může obsahovat všech kalendářů splňující v obdélníku zadaný.  
  
```  
LPRECT SizeRectToMin(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `lpRect`|Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která definuje obdélníku, která obsahuje požadovanou hodnotu v kalendáři.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která definuje obdélníku, jejíž aktuální velikost je menší než nebo rovna rámeček definované `lpRect` parametr.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vypočítá, kolik kalendáře můžete začlenit v obdélníku určeného `lpRect` parametr a potom se vrátí nejmenší obdélníku, která může obsahovat tento počet kalendáře. V důsledku toho tato metoda zmenší zadaný rámeček přesně podle požadovaný počet kalendáře.  
  
 Tato metoda odesílá [MCM_SIZERECTTOMIN](http://msdn.microsoft.com/library/windows/desktop/bb761020) zprávy, která je popsána v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl – třída](../../mfc/reference/cdatetimectrl-class.md)
