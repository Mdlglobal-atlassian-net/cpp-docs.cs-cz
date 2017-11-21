---
title: "CDateTimeCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
dev_langs: C++
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ced7bfbb2cedd8cad4353cdbb2d5627864de5ad7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl – třída
Zapouzdřuje funkce ovládacího prvku pro výběr data a času.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Vytvoří `CDateTimeCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Zavře aktuální datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::Create](#create)|Vytvoří prvku pro výběr data a času a připojí jej k `CDateTimeCtrl` objektu.|  
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Načte informace o aktuální datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Vrátí jeho ideální velikost ovládacího prvku pro výběr data a času, který je vyžadována k zobrazení aktuální datum nebo čas.|  
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Načte barvu pro danou část měsíční kalendář v rámci prvku pro výběr data a času.|  
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Načte `CMonthCalCtrl` objektu přidruženého k ovládacímu prvku pro výběr data a času.|  
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Načte písma, které využívají data a ovládací prvek měsíční kalendář podřízené čas výběru ovládacího prvku.|  
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Získá styl aktuální datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální povolená systémové časy pro ovládací prvek pro výběr data a času.|  
|[CDateTimeCtrl::GetTime](#gettime)|Načte aktuálně vybraný čas z ovládacího prvku pro výběr data a času a vloží ho v zadané `SYSTEMTIME` struktura.|  
|[CDateTimeCtrl::SetFormat](#setformat)|Nastaví zobrazení ovládací prvek pro výběr data a času v souladu s danou formátovací řetězec.|  
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Nastaví barvu pro danou část měsíční kalendář v ovládacím prvku pro výběr data a času.|  
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Nastaví písmo, který bude používat ovládací prvek měsíční kalendář podřízené datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Nastavuje styl aktuální datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::SetRange](#setrange)|Nastaví minimální a maximální povolený systémové časy pro ovládací prvek pro výběr data a času.|  
|[CDateTimeCtrl::SetTime](#settime)|Nastaví dobu v ovládacím prvku pro výběr data a času.|  
  
## <a name="remarks"></a>Poznámky  
 Datum a čas pro výběr ovládacího prvku (DTP řízení) poskytuje jednoduché rozhraní k výměně informací o datu a času s uživatelem. Toto rozhraní obsahuje pole, z nichž každá obsahuje součást datum a čas informace, které jsou uložené v ovládacím prvku. Uživatel může změnit informace uložené v ovládacím prvku tak, že změníte obsah řetězec v dané pole. Může uživatel přesunout z jednoho pole pomocí myši nebo klávesnice.  
  
 Použití různých stylů na objekt při jeho vytvoření můžete přizpůsobit prvku pro výběr data a času. V tématu [datum a čas styly ovládacího prvku pro výběr](http://msdn.microsoft.com/library/windows/desktop/bb761728) ve Windows SDK pro další informace o styly konkrétní do ovládacího prvku pro výběr data a času. Můžete nastavit formát zobrazení ovládacího prvku DTP pomocí formátu stylů. Tyto styly formátu jsou popsané v části "Formát styly" v tématu Windows SDK [datum a čas styly ovládacího prvku pro výběr](http://msdn.microsoft.com/library/windows/desktop/bb761728).  
  
 Datum a čas ovládací prvek výběru také používá oznámení a zpětná volání, které jsou popsány v [pomocí CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdtctl.h  
  
##  <a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl  
 Vytvoří `CDateTimeCtrl` objektu.  
  
```  
CDateTimeCtrl();
```  
  
##  <a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal  
 Zavře aktuální datum a čas pro výběr ovládacího prvku.  
  
```  
void CloseMonthCal() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_CLOSEMONTHCAL](http://msdn.microsoft.com/library/windows/desktop/bb761753) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_dateTimeCtrl`, který používá k programovému přístupu prvku pro výběr data a času. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu zavře kalendář rozevíracího seznamu pro aktuální datum a čas pro výběr ovládacího prvku.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]  
  
##  <a name="create"></a>CDateTimeCtrl::Create  
 Vytvoří prvku pro výběr data a času a připojí jej k `CDateTimeCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje kombinaci styly ovládacího prvku datum čas. V tématu [datum a čas styly ovládacího prvku pro výběr](http://msdn.microsoft.com/library/windows/desktop/bb761728) ve Windows SDK pro další informace o styly pro výběr data a času.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, což je pozice a velikosti prvku pro výběr data a času.  
  
 `pParentWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je okno nadřazeného prvku pro výběr data a času. Nesmí být **NULL**.  
  
 `nID`  
 Určuje datum a čas pro výběr ovládacího prvku ID ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vytvoření byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##### <a name="to-create-a-date-and-time-picker-control"></a>Chcete-li vytvořit ovládací prvek pro výběr data a času  
  
1.  Volání [CDateTimeCtrl](#cdatetimectrl) k vytvoření `CDateTimeCtrl` objektu.  
  
2.  Volání této funkce člen, který vytvoří ovládacím prvku pro výběr data a času Windows a připojí jej k `CDateTimeCtrl` objektu.  
  
 Při volání **vytvořit**, běžné ovládací prvky jsou inicializovány.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]  
  
##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo  
 Načte informace o aktuální datum a čas pro výběr ovládacího prvku.  
  
```   
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out]`pDateTimePickerInfo`|Ukazatel [DATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761729) struktura, která přijímá popis aktuální datum a čas pro výběr ovládacího prvku.<br /><br /> Volající zodpovídá za přidělování tuto strukturu. Však tato metoda inicializuje `cbSize` členů struktury.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_GETDATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761755) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_dateTimeCtrl`, který používá k programovému přístupu prvku pro výběr data a času. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu určuje, zda úspěšně načte informace o aktuální datum a čas pro výběr ovládacího prvku.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]  
  
##  <a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor  
 Načte barvu pro danou část měsíční kalendář v rámci prvku pro výběr data a času.  
  
```  
COLORREF GetMonthCalColor(int iColor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `iColor`  
 `int` Hodnotu udávající, které oblasti barva měsíční kalendář pro načtení. Seznam hodnot, najdete v článku `iColor` parametr pro [SetMonthCalColor](#setmonthcalcolor).  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje barvu nastavení pro zadanou část ovládací prvek měsíční kalendář, pokud bylo úspěšné. Funkce vrátí hodnotu -1, pokud je neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_GETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761759), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]  
  
##  <a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl  
 Načte `CMonthCalCtrl` objektu přidruženého k ovládacímu prvku pro výběr data a času.  
  
```  
CMonthCalCtrl* GetMonthCalCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) objekt, nebo **NULL** Pokud neúspěšně nebo pokud není viditelná okna.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvky pro výběr data a času vytvoření ovládací prvek měsíční kalendář podřízené, když uživatel klikne na šipku rozevíracího seznamu. Když `CMonthCalCtrl` objekt je již nejsou potřebné, byla, takže aplikace nesmí spoléhat na ukládání objekt představující datum čas výběru ovládacího prvku podřízené měsíční kalendář.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]  
  
##  <a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont  
 Získá datum a čas pro výběr ovládacího prvku prvku měsíční kalendář aktuálně použité písmo.  
  
```  
CFont* GetMonthCalFont() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CFont](../../mfc/reference/cfont-class.md) objekt, nebo **NULL** Pokud neúspěšně.  
  
### <a name="remarks"></a>Poznámky  
 `CFont` Objekt ukazuje návratová hodnota je dočasný objekt a zničen během další dobu nečinnosti, po zpracování.  
  
##  <a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle  
 Získá styl ovládací prvek rozevírací seznam měsíční kalendář, který je přidružen aktuální datum a čas pro výběr ovládacího prvku.  
  
```  
DWORD GetMonthCalStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Styl rozevírací seznam ovládací prvek měsíční kalendář, který je bitová kombinace (nebo) styly ovládacího prvku pro výběr data a času. Další informace najdete v tématu [styly ovládacího prvku měsíční kalendář](http://msdn.microsoft.com/library/windows/desktop/bb760919).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_GETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761763) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getrange"></a>CDateTimeCtrl::GetRange  
 Načte aktuální minimální a maximální povolená systémové časy pro ovládací prvek pro výběr data a času.  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Ukazatel [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt nebo [CTime –](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje nejdřívější časový limit v `CDateTimeCtrl` objektu.  
  
 `pMaxRange`  
 Ukazatel na `COleDateTime` objekt nebo `CTime` objekt, který obsahuje nejpozdější čas v povolena `CDateTimeCtrl` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` hodnotu obsahující příznaky, které označují, které rozsahy jsou nastavené. If  
  
 `return value & GDTR_MAX` == 0  
  
 druhý parametr je platný. Podobně pokud  
  
 `return value & GDTR_MIN` == 0  
  
 první parametr je platný.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761767), jak je popsáno v sadě Windows SDK. V implementaci společnosti MFC, můžete zadat buď `COleDateTime` nebo `CTime` použití.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]  
  
##  <a name="gettime"></a>CDateTimeCtrl::GetTime  
 Načte aktuálně vybraný čas z ovládacího prvku pro výběr data a času a vloží ho v zadané `SYSTEMTIME` struktura.  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;  
DWORD GetTime(CTime& timeDest) const;  
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *timeDest*  
 V první verzi, odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který se zobrazí informace o systémovém čase. V druhé verzi, odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který se zobrazí informace o systémovém čase.  
  
 *pTimeDest*  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura přijímat informace o systémovém čase. Nesmí být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první verzi nenulové hodnoty, pokud čas je úspěšně zapsána do `COleDateTime` objektu; jinak hodnota 0. Ve verzích druhý a třetí `DWORD` hodnota rovna **dwFlag** člen nastavit [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktury. Najdete v článku **poznámky** části níže Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_GETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761769), jak je popsáno v sadě Windows SDK. Implementace MFC **GetTime**, můžete použít `COleDateTime` nebo `CTime` třídy, nebo můžete použít `SYSTEMTIME` struktura uložit informace o času.  
  
 Návratová hodnota `DWORD` ve verzích druhý a třetí vyšší, označuje, zda prvku pro výběr data a času je nastaven stav "žádné datum", jak je uvedeno v [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktura člen `dwFlags`. Pokud hodnota vrácena rovná **GDT_NONE**, ovládací prvek je nastaven na stav "žádné datum" a používá **DTS_SHOWNONE** stylu. Pokud hodnota vrácena rovná **GDT_VALID**, systémového času je úspěšně uložen v cílovém umístění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize  
 Vrátí jeho ideální velikost ovládacího prvku pro výběr data a času, který je vyžadována k zobrazení aktuální datum nebo čas.  
  
```  
BOOL GetIdealSize(LPSIZE psize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out]`psize`|Ukazatel na [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která obsahuje jeho ideální velikost pro ovládací prvek.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je vždy `true`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb761757) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_dateTimeCtrl`, který používá k programovému přístupu prvku pro výběr data a času. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte jeho ideální velikost zobrazíte prvku pro výběr data a času.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]  
  
##  <a name="setformat"></a>CDateTimeCtrl::SetFormat  
 Nastaví zobrazení ovládací prvek pro výběr data a času v souladu s danou formátovací řetězec.  
  
```  
BOOL SetFormat(LPCTSTR pstrFormat);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrFormat*  
 Ukazatel na nula ukončena formátovací řetězec, který definuje požadované zobrazení. Nastavení tohoto parametru na **NULL** ovládacího prvku se obnoví na výchozí řetězec formátu pro aktuální styl.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
> [!NOTE]
>  Uživatelský vstup neurčuje úspěch nebo neúspěch pro toto volání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_SETFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb761771), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]  
  
##  <a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor  
 Nastaví barvu pro danou část měsíční kalendář v ovládacím prvku pro výběr data a času.  
  
```  
COLORREF SetMonthCalColor(
    int iColor,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 `iColor`  
 `int`hodnota, která určuje, které oblasti ovládací prvek měsíční kalendář nastavit. Tato hodnota může být jedna z následujících akcí.  
  
|Hodnota|Význam|  
|-----------|-------------|  
|MCSC_BACKGROUND|Nastavení barvy pozadí zobrazí mezi měsíců.|  
|MCSC_MONTHBK|Nastavení barvy pozadí zobrazí během jednoho měsíce.|  
|MCSC_TEXT|Nastavení barvy použité k zobrazení textu během jednoho měsíce.|  
|MCSC_TITLEBK|Nastavení barvy pozadí zobrazí v nadpisu kalendáře.|  
|MCSC_TITLETEXT|Nastavení barvy použité k zobrazení textu v nadpisu kalendáře.|  
|MCSC_TRAILINGTEXT|Nastavení barvy slouží k zobrazení záhlaví a text na konci dne. Úvodní a koncové dny jsou dny z předešlých a následných měsíců, které se zobrazují na aktuálním kalendáři.|  
  
 `ref`  
 A **COLORREF** hodnotu představující barvu, která bude nastavena pro určenou oblast měsíční kalendář.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje předchozí nastavení barvu pro zadaný část ovládací prvek měsíční kalendář, pokud bylo úspěšné. Zpráva, jinak vrátí hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_SETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761773), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).  
  
##  <a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont  
 Nastaví písmo, který bude používat ovládací prvek měsíční kalendář podřízené datum a čas pro výběr ovládacího prvku.  
  
```  
void SetMonthCalFont(
    HFONT hFont,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `hFont`  
 Popisovač písmo, které bude nastaveno.  
  
 `bRedraw`  
 Určuje, zda ovládací prvek je překreslit ihned po nastavení písma. Nastavení tohoto parametru na **TRUE** způsobí, že k překreslit ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_SETMCFONT](http://msdn.microsoft.com/library/windows/desktop/bb761775), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]  
  
> [!NOTE]
>  Pokud chcete použít tento kód, budete chtít mezi členy vaší `CDialog`-odvozené třídy s názvem `m_MonthFont` typu **CFont**.  
  
##  <a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle  
 Nastavuje styl ovládací prvek rozevírací seznam měsíční kalendář, který je přidružen aktuální datum a čas pro výběr ovládacího prvku.  
  
```  
DWORD SetMonthCalStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`dwStyle`|Na nový měsíc kalendář styl ovládací prvek, který je bitové kombinace styly ovládacího prvku měsíční kalendář (nebo). Další informace najdete v tématu [styly ovládacího prvku měsíční kalendář](http://msdn.microsoft.com/library/windows/desktop/bb760919).|  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí styl ovládací prvek rozevírací seznam měsíční kalendář.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_SETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761778) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_dateTimeCtrl`, který používá k programovému přístupu prvku pro výběr data a času. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví datum a čas pro výběr ovládacího prvku zobrazení čísla týdne, zkrácené názvy dnů v týdnu a bez informací o dnešku indikátoru.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]  
  
##  <a name="setrange"></a>CDateTimeCtrl::SetRange  
 Nastaví minimální a maximální povolený systémové časy pro ovládací prvek pro výběr data a času.  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Ukazatel [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt nebo [CTime –](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje nejdřívější časový limit v `CDateTimeCtrl` objektu.  
  
 `pMaxRange`  
 Ukazatel na `COleDateTime` objekt nebo `CTime` objekt, který obsahuje nejpozdější čas v povolena `CDateTimeCtrl` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761780), jak je popsáno v sadě Windows SDK. V implementaci společnosti MFC, můžete zadat buď `COleDateTime` nebo `CTime` použití. Pokud `COleDateTime` objekt má **NULL** stav, rozsah se odeberou. Pokud `CTime` ukazatel nebo `COleDateTime` ukazatel **NULL**, rozsah se odeberou.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CDateTimeCtrl::GetRange](#getrange).  
  
##  <a name="settime"></a>CDateTimeCtrl::SetTime  
 Nastaví dobu v ovládacím prvku pro výběr data a času.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);  
BOOL SetTime(const CTime* pTimeNew);  
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *timeNew*  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující které bude nastavení ovládacího prvku.  
  
 *pTimeNew*  
 V druhé verzi výše, odkazy [CTime –](../../atl-mfc-shared/reference/ctime-class.md) objekt obsahující čas, ke kterému bude nastavena ovládacího prvku. Ve třetí verzi výše, odkazy [SYSTEMTIME –](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura obsahující čas, ke kterému bude nastavena ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [DTM_SETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761782), jak je popsáno v sadě Windows SDK. Implementace MFC **SetTime**, můžete použít `COleDateTime` nebo `CTime` třídy, nebo můžete použít `SYSTEMTIME` struktura nastavení informací o času.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl – třída](../../mfc/reference/cmonthcalctrl-class.md)
