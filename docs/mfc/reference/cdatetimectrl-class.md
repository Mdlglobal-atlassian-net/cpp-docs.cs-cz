---
title: Cdatetimectrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9eb3b70851cb5e51ef2ddc0e99347c81fe632b6d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726658"
---
# <a name="cdatetimectrl-class"></a>Cdatetimectrl – třída
Zapouzdřuje funkce ovládací prvek pro výběr data a času.  
  
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
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Zavře aktuální prvek Výběr data a času.|  
|[CDateTimeCtrl::Create](#create)|Vytvoří prvek Výběr data a času a připojí ho k `CDateTimeCtrl` objektu.|  
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Načte informace o aktuální prvek Výběr data a času.|  
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Vrátí ideální velikost ovládacího prvku Výběr data a času, který je vyžadována k zobrazení aktuálního data a času.|  
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Zjišťuje barvu pro danou část měsíční kalendář ovládacího prvku pro výběr data a času.|  
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Načte `CMonthCalCtrl` objekt přidružený k prvku Výběr data a času.|  
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Načte písma, které využívají data a ovládací prvek měsíční kalendář podřízený prvek pro výběr času.|  
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Získá styl aktuální prvek Výběr data a času.|  
|[CDateTimeCtrl::GetRange](#getrange)|Načte aktuální minimální a maximální povolený systémové časy pro ovládací prvek pro výběr data a času.|  
|[CDateTimeCtrl::GetTime](#gettime)|Načte aktuálně vybraný časový z ovládacího prvku pro výběr data a času a vloží jej do zadaného `SYSTEMTIME` struktury.|  
|[CDateTimeCtrl::SetFormat](#setformat)|Nastaví zobrazení ovládací prvek pro výběr data a času v souladu s danou formátovací řetězec.|  
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Nastaví barvu pro danou část kalendářní měsíc v rámci ovládací prvek pro výběr data a času.|  
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Nastaví písmo, které budou používat ovládací prvek měsíční kalendář podřízené datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Nastaví styl aktuální datum a čas pro výběr ovládacího prvku.|  
|[CDateTimeCtrl::SetRange](#setrange)|Nastaví minimální a maximální povolený systémové časy pro ovládací prvek pro výběr data a času.|  
|[CDateTimeCtrl::SetTime](#settime)|Nastaví dobu v ovládacím prvku Výběr data a času.|  
  
## <a name="remarks"></a>Poznámky  
 Datum a čas pro výběr ovládacího prvku (ovládacího prvku DTP) poskytuje jednoduché rozhraní k výměně informací data a času s uživatelem. Toto rozhraní obsahuje pole, z nichž každý se zobrazí část data a času informací uložených v ovládacím prvku. Uživatel může změnit informace uložené v ovládacím prvku tak, že změníte obsah řetězce v daném poli. Uživatel může přesouvat z jednoho pole pomocí myši nebo klávesnice.  
  
 Použitím různých stylů na objektu při vytváření můžete přizpůsobit prvku Výběr data a času. Zobrazit [datum a čas – styly ovládacího prvku pro výběr](/windows/desktop/Controls/date-and-time-picker-control-styles) v sadě Windows SDK pro další informace o stylech konkrétní do ovládacího prvku pro výběr data a času. Můžete nastavit formát zobrazení pomocí formátu styly ovládacího prvku DTP. Tyto styly formátu jsou popsány v části "Formát styly" v tématu Windows SDK [datum a čas – styly ovládacího prvku pro výběr](/windows/desktop/Controls/date-and-time-picker-control-styles).  
  
 Ovládací prvek Výběr data a času také používá oznámení a zpětná volání, které jsou popsány v [používání atributu CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdtctl.h  
  
##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl  
 Vytvoří `CDateTimeCtrl` objektu.  
  
```  
CDateTimeCtrl();
```  
  
##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal  
 Zavře aktuální prvek Výběr data a času.  
  
```  
void CloseMonthCal() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, který umožňuje programový přístup k prvku Výběr data a času. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu se zavře rozevírací kalendář pro aktuální prvek Výběr data a času.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]  
  
##  <a name="create"></a>  CDateTimeCtrl::Create  
 Vytvoří prvek Výběr data a času a připojí ho k `CDateTimeCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje kombinaci – styly ovládacího prvku datum čas. Zobrazit [datum a čas – styly ovládacího prvku pro výběr](/windows/desktop/Controls/date-and-time-picker-control-styles) v sadě Windows SDK pro další informace o stylech výběr data a času.  
  
 *Rect*  
 Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, což je umístění a velikost prvku Výběr data a času.  
  
 *pParentWnd*  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku datum a čas výběr. Nesmí být NULL.  
  
 *nID*  
 Určuje, datum a čas pro výběr ID ovládacího prvku  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo vytváření úspěšné; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
##### <a name="to-create-a-date-and-time-picker-control"></a>Chcete-li vytvořit ovládací prvek pro výběr data a času  
  
1.  Volání [atributu CDateTimeCtrl](#cdatetimectrl) k vytvoření `CDateTimeCtrl` objektu.  
  
2.  Voláním této členské funkce, která vytvoří ovládacím prvku Výběr data a času Windows a připojí ho k `CDateTimeCtrl` objektu.  
  
 Při volání `Create`, běžné ovládací prvky jsou inicializovány.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]  
  
##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo  
 Načte informace o aktuální prvek Výběr data a času.  
  
```   
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*pDateTimePickerInfo*|[out] Ukazatel [DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo) struktura, která přijímá popis aktuální datum a čas pro výběr ovládacího prvku.<br /><br /> Volající zodpovídá za přidělování této struktury. Nicméně tato metoda inicializuje *cbSize* členu struktury.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, který umožňuje programový přístup k prvku Výběr data a času. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu určuje, zda úspěšně načte informace o aktuální prvek Výběr data a času.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]  
  
##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor  
 Zjišťuje barvu pro danou část měsíční kalendář ovládacího prvku pro výběr data a času.  
  
```  
COLORREF GetMonthCalColor(int iColor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *iColor*  
 **Int** hodnotu určující, které oblasti barvu kalendáře měsíce pro načtení. Seznam hodnot, najdete v článku *iColor* parametr pro [SetMonthCalColor](#setmonthcalcolor).  
  
### <a name="return-value"></a>Návratová hodnota  
 COLORREF hodnotu, která představuje nastavení barev pro specifikovanou část prvku měsíční kalendář, pokud je úspěšná. Pokud není úspěšné, vrátí funkce hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]  
  
##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl::GetMonthCalCtrl  
 Načte `CMonthCalCtrl` objekt přidružený k prvku Výběr data a času.  
  
```  
CMonthCalCtrl* GetMonthCalCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) objektu, nebo hodnota NULL, pokud není úspěšné nebo pokud není okno viditelné.  
  
### <a name="remarks"></a>Poznámky  
 Prvků pro výběr data a času vytvořit ovládací prvek měsíční kalendář podřízený, když uživatel klepne na šipku rozevíracího seznamu. Když `CMonthCalCtrl` objektu je už je nepotřebujete, zničen, takže vaše aplikace nesmí založená na ukládání objekt představující datum čas výběr ovládacího prvku podřízené měsíční kalendář.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]  
  
##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont  
 Získá písmo aktuálně použité datum a čas výběr ovládacího prvku měsíční kalendář.  
  
```  
CFont* GetMonthCalFont() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [cfont –](../../mfc/reference/cfont-class.md) objektu, nebo hodnota NULL, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 `CFont` Objekt odkazovaný návratovou hodnotou je dočasný objekt a je zničen při nečinnosti příště zpracování.  
  
##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle  
 Získá styl ovládacím prvku měsíční rozevírací kalendář, který je přidružený aktuální prvek Výběr data a času.  
  
```  
DWORD GetMonthCalStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Styl rozevíracím seznamu ovládací prvek měsíční kalendář, který je bitová kombinace (nebo) styly ovládacího prvku pro výběr data a času. Další informace najdete v tématu [– styly ovládacích prvků kalendáře měsíce](/windows/desktop/Controls/month-calendar-control-styles).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="getrange"></a>  CDateTimeCtrl::GetRange  
 Načte aktuální minimální a maximální povolený systémové časy pro ovládací prvek pro výběr data a času.  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pMinRange*  
 Ukazatel na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje Nejdřívější čas v povolené `CDateTimeCtrl` objektu.  
  
 *pMaxRange*  
 Ukazatel na `COleDateTime` objektu nebo `CTime` objekt, který obsahuje nejpozdější čas v povolena `CDateTimeCtrl` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota DWORD obsahující příznaky, které označují, které rozsahy jsou nastavené. If  
  
 `return value & GDTR_MAX` == 0  
  
 druhý parametr je platný. Podobně pokud  
  
 `return value & GDTR_MIN` == 0  
  
 první parametr je platný.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange), jak je popsáno v sadě Windows SDK. V implementaci MFC, můžete zadat buď `COleDateTime` nebo `CTime` použití.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]  
  
##  <a name="gettime"></a>  CDateTimeCtrl::GetTime  
 Načte aktuálně vybraný časový z ovládacího prvku pro výběr data a času a vloží jej do zadaného `SYSTEMTIME` struktury.  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;  
DWORD GetTime(CTime& timeDest) const;  
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *timeDest*  
 V první verzi odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který se zobrazí informace o času systému. V druhém verzi odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který se zobrazí informace o času systému.  
  
 *pTimeDest*  
 Ukazatel [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktura přijímat informace o času systému. Nesmí mít hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první verzi nenulové, pokud čas je úspěšně zapsána do `COleDateTime` objektu; jinak 0. Ve verzích druhý a třetí hodnota rovna hodnotě typu DWORD *dwFlag* člen nastaven [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) struktury. Zobrazit **poznámky** níže v části Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime), jak je popsáno v sadě Windows SDK. V implementaci MFC `GetTime`, můžete použít `COleDateTime` nebo `CTime` třídy, nebo můžete použít `SYSTEMTIME` struktura ukládat informace o čase.  
  
 Návratová hodnota DWORD ve verzích druhý a třetí výše, označuje, zda prvku Výběr data a času je nastavena do stavu "žádné datum", jak je uvedeno v [NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange) člen struktury *dwFlags* . Pokud vrácená hodnota se rovná GDT_NONE, ovládacího prvku nastavená na "žádné datum" stav a používá DTS_SHOWNONE styl. Pokud je vrácená hodnota GDT_VALID, systémového času úspěšně uloženy v cílovém umístění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]  
  
##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize  
 Vrátí ideální velikost ovládacího prvku Výběr data a času, který je vyžadována k zobrazení aktuálního data a času.  
  
```  
BOOL GetIdealSize(LPSIZE psize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*psize*|[out] Ukazatel [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) strukturu, která obsahuje ideální velikost ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je vždy hodnotu TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, který umožňuje programový přístup k prvku Výběr data a času. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte ideální velikost zobrazíte prvku Výběr data a času.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]  
  
##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat  
 Nastaví zobrazení ovládací prvek pro výběr data a času v souladu s danou formátovací řetězec.  
  
```  
BOOL SetFormat(LPCTSTR pstrFormat);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrFormat*  
 Ukazatel na řetězec formátu ukončit nulou, který definuje požadovaný zobrazený. Nastavení tohoto parametru na hodnotu NULL se resetuje na výchozí řetězec formátu pro aktuální styl ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
> [!NOTE]
>  Uživatelský vstup není stanovení úspěšného či neúspěšného pro toto volání.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]  
  
##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor  
 Nastaví barvu pro danou část kalendářní měsíc v rámci ovládací prvek pro výběr data a času.  
  
```  
COLORREF SetMonthCalColor(
    int iColor,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 *iColor*  
 **int** hodnotu určující, které oblasti ovládací prvek měsíční kalendář nastavit. Tato hodnota může být jedna z následujících akcí.  
  
|Hodnota|Význam|  
|-----------|-------------|  
|MCSC_BACKGROUND|Nastavte barvu pozadí zobrazují mezi měsíců.|  
|MCSC_MONTHBK|Nastavte barvu pozadí zobrazí během jednoho měsíce.|  
|MCSC_TEXT|Nastavení barvy použité k zobrazení textu během jednoho měsíce.|  
|MCSC_TITLEBK|Nastavte barva pozadí zobrazená v nadpisu kalendáře.|  
|MCSC_TITLETEXT|Nastavte barvu použitou k zobrazení textu v nadpisu kalendáře.|  
|MCSC_TRAILINGTEXT|Nastavení barvy použité k zobrazení záhlaví a text na konci dne. Úvodní a koncové dny jsou dny z předchozího a následujícího měsíce, které se zobrazují na aktuální kalendář.|  
  
 *ref*  
 COLORREF hodnotu představující barvu, která se nastaví pro zadanou oblast měsíční kalendář.  
  
### <a name="return-value"></a>Návratová hodnota  
 COLORREF hodnotu, která představuje předchozí nastavení barev pro specifikovanou část prvku měsíční kalendář, pokud je úspěšná. Zpráva v opačném případě vrátí hodnotu -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).  
  
##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont  
 Nastaví písmo, které budou používat ovládací prvek měsíční kalendář podřízené datum a čas pro výběr ovládacího prvku.  
  
```  
void SetMonthCalFont(
    HFONT hFont,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *hFont*  
 Zpracování písma, nastaví se.  
  
 *bRedraw*  
 Určuje, zda ovládací prvek by se měl překreslit okamžitě po nastavení písma. Nastavení tohoto parametru na hodnotu TRUE způsobí, že svoje vlastní překreslení ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]  
  
> [!NOTE]
>  Tento kód použít, budete chtít jako člena vaší `CDialog`-odvozenou třídu s názvem *m_MonthFont* typu `CFont`.  
  
##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle  
 Nastaví styl ovládacím prvku měsíční rozevírací kalendář, který je přidružený aktuální prvek Výběr data a času.  
  
```  
DWORD SetMonthCalStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|*dwStyle*|[in] Na nový měsíc kalendář stylu ovládacího prvku, který je bitová kombinace (nebo) – styly ovládacích prvků kalendáře měsíce. Další informace najdete v tématu [– styly ovládacích prvků kalendáře měsíce](/windows/desktop/Controls/month-calendar-control-styles).|  
  
### <a name="return-value"></a>Návratová hodnota  
 V předchozím stylu ovládací prvek rozevírací seznam měsíční kalendář.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, *m_dateTimeCtrl*, který umožňuje programový přístup k prvku Výběr data a času. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví zobrazovat čísla týdnů, zkrácené názvy dnů v týdnu a bez informací o dnešku indikátor prvku pro výběr data a času.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CDateTimeCtrl::SetRange  
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
 *pMinRange*  
 Ukazatel na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objektu nebo [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje Nejdřívější čas v povolené `CDateTimeCtrl` objektu.  
  
 *pMaxRange*  
 Ukazatel na `COleDateTime` objektu nebo `CTime` objekt, který obsahuje nejpozdější čas v povolena `CDateTimeCtrl` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange), jak je popsáno v sadě Windows SDK. V implementaci MFC, můžete zadat buď `COleDateTime` nebo `CTime` použití. Pokud `COleDateTime` objekt je ve stavu hodnotu NULL, rozsahu se odeberou. Pokud `CTime` ukazatel nebo `COleDateTime` ukazatel hodnotu NULL, rozsahu se odeberou.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CDateTimeCtrl::GetRange](#getrange).  
  
##  <a name="settime"></a>  CDateTimeCtrl::SetTime  
 Nastaví dobu v ovládacím prvku Výběr data a času.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);  
BOOL SetTime(const CTime* pTimeNew);  
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *timeNew*  
 Odkaz na [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt obsahující které ovládací prvek nastavit.  
  
 *pTimeNew*  
 V druhé verzi výše, ukazatel [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, ke kterému bude ovládací prvek nastavit. Ve třetí verzi výše, ukazatel [SYSTEMTIME –](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury obsahující čas, ke kterému bude ovládací prvek nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime), jak je popsáno v sadě Windows SDK. V implementaci MFC `SetTime`, můžete použít `COleDateTime` nebo `CTime` třídy, nebo můžete použít `SYSTEMTIME` strukturu, chcete-li nastavit informace o čase.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 knihovny MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl – třída](../../mfc/reference/cmonthcalctrl-class.md)
