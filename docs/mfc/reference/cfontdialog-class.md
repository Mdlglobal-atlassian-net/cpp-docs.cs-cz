---
title: Třída CFontDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
dev_langs:
- C++
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d64ec306f77174b72c130c3afc14a732464c43be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cfontdialog-class"></a>CFontDialog – třída
Umožňuje začlenit dialogové okno Výběr písma do vaší aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFontDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFontDialog::CFontDialog](#cfontdialog)|Vytvoří `CFontDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFontDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživateli proveďte výběr.|  
|[CFontDialog::GetCharFormat](#getcharformat)|Načte formátování vybraného písma.|  
|[CFontDialog::GetColor](#getcolor)|Vrátí barvy vybraných písma.|  
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Přiřadí charakteristiky pro aktuálně vybrané písma `LOGFONT` struktury.|  
|[CFontDialog::GetFaceName](#getfacename)|Vrací název vzhled vybrané písma.|  
|[CFontDialog::GetSize](#getsize)|Vrátí velikost vybraného písma.|  
|[CFontDialog::GetStyleName](#getstylename)|Vrátí název stylu vybraného písma.|  
|[CFontDialog::GetWeight](#getweight)|Vrací váhu vybrané písmo.|  
|[CFontDialog::IsBold](#isbold)|Určuje, zda je tučné písmo.|  
|[CFontDialog::IsItalic](#isitalic)|Určuje, zda je písmo kurzíva.|  
|[CFontDialog::IsStrikeOut](#isstrikeout)|Určuje, zda se má zobrazit písma s přeškrtnutí.|  
|[CFontDialog::IsUnderline](#isunderline)|Určuje, zda je podtržený písmo.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFontDialog::m_cf](#m_cf)|Struktura sloužící k přizpůsobení `CFontDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 A `CFontDialog` objektu je dialogové okno se seznamem písem, které jsou aktuálně nainstalovány v systému. Uživatele můžete vybrat konkrétní písmo ze seznamu a tento výběr je pak hlášené zpět do aplikace.  
  
 K vytvoření `CFontDialog` objektu, použijte zadaný konstruktor nebo odvození nové podtřídy a používat vlastní vlastní konstruktor.  
  
 Jednou `CFontDialog` objekt byl vytvořen, můžete použít `m_cf` struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. [M_cf](#m_cf) struktura je typu [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832). Další informace o tuto strukturu najdete v části Windows SDK.  
  
 Po inicializaci objektu dialogového okna Ovládací prvky, volání `DoModal` – členská funkce a zobrazit dialogové okno Povolit uživatelům výběr písma. `DoModal` Vrátí, zda uživatel vybral OK ( **IDOK**) nebo zrušit ( **IDCANCEL**) tlačítko.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete použít jednu z `CFontDialog`na členské funkce načíst informace o zadaný uživatelem.  
  
 Můžete použít Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě během inicializace dialogových oken a další informace o této chybě. Další informace o této funkci najdete v části Windows SDK.  
  
 `CFontDialog` spoléhá na COMMDLG. Soubor knihovny DLL, která se dodává s verzí systému Windows verze 3.1 nebo novější.  
  
 Chcete-li přizpůsobit dialogové okno, odvození třídy z `CFontDialog`zadejte dialogové okno vlastní šablony a přidat mapy zpráv pro zpracování zprávy s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měla být předána základní třídy.  
  
 Přizpůsobení funkce háku se nevyžaduje.  
  
 Další informace o používání `CFontDialog`, najdete v části [třídy společných dialogů](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFontDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog  
 Vytvoří `CFontDialog` objektu.  
  
```  
CFontDialog(
    LPLOGFONT lplfInitial = NULL,  
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,  
    CDC* pdcPrinter = NULL,  
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,  
    DWORD dwFlags = CF_SCREENFONTS,  
    CDC* pdcPrinter = NULL,  
    CWnd* pParentWnd = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 l `plfInitial`  
 Ukazatel [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) datová struktura, která vám umožní nastavit některé z vlastností písma.  
  
 `charFormat`  
 Ukazatel [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) ovládacích prvků pro úpravy datová struktura, která vám umožní nastavit některé z vlastností písma v s formátováním.  
  
 `dwFlags`  
 Určuje jeden nebo více příznaků zvolit písmo. Jeden nebo více přednastavené hodnoty lze spojovat pomocí bitový operátor OR. Pokud změníte `m_cf.Flag`s struktura člena, je nutné používat bitový operátor OR v změny zachovat výchozí chování beze změn. Podrobnosti o každé z těchto příznaků, najdete v části Popis [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832) struktura ve Windows SDK.  
  
 pdcPrinter  
 Ukazatel na kontextu zařízení tiskárny. Pokud je zadaný, tento parametr odkazuje na kontextu tiskárny zařízení tiskárny, na které mají být vybrán písma.  
  
 `pParentWnd`  
 Ukazatel na písma dialogové okno nadřazené nebo vlastníka.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že konstruktoru automaticky vyplní členů `CHOOSEFONT` struktura. Měli byste pouze změnit tyto Pokud chcete dialogové okno písmo jiné než výchozí.  
  
> [!NOTE]
>  První verze součásti tuto funkci existuje pouze v případě, že podpora ovládací prvek pro úpravy s formátováním žádné.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>  CFontDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno Písmo Windows běžné a umožnit uživatelům zvolit písmo.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **IDOK** nebo **IDCANCEL**. Pokud **IDCANCEL** je vrácen, volání Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě.  
  
 **IDOK** a **IDCANCEL** jsou konstanty, které označuje, zda uživatel vybrané na tlačítko OK nebo Storno.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různé ovládací prvky dialogového okna písma a to nastavením členy [m_cf](#m_cf) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete volat jiné členské funkce načíst nastavení nebo uživatelský vstup informace do dialogových oken.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklady pro [CFontDialog::CFontDialog](#cfontdialog) a [CFontDialog::GetColor](#getcolor).  
  
##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat  
 Načte formátování vybraného písma.  
  
```  
void GetCharFormat(CHARFORMAT& cf) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 A [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) struktura obsahující informace o formátování vybraného písma.  
  
##  <a name="getcolor"></a>  CFontDialog::GetColor  
 Volání této funkce načíst barvy vybraných písma.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Barva písma vybrané.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]  
  
##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont  
 Volání této funkce můžete přiřadit charakteristiky písma aktuálně vybrané členy [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
```  
void GetCurrentFont(LPLOGFONT lplf);
```  
  
### <a name="parameters"></a>Parametry  
 *lplf*  
 Ukazatel na `LOGFONT` struktury.  
  
### <a name="remarks"></a>Poznámky  
 Další `CFontDialog` členské funkce jsou k dispozici pro přístup k jednotlivých vlastnostech aktuálním písmem.  
  
 Pokud je tato funkce je volána při volání [DoModal](#domodal), vrátí aktuální výběr v době (co uživatel uvidí, nebo má změnit v dialogovém okně). Pokud je tato funkce je volána po volání `DoModal` (pouze v případě `DoModal` vrátí **IDOK**), vrátí co ve skutečnosti vybraného uživatele.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]  
  
##  <a name="getfacename"></a>  CFontDialog::GetFaceName  
 Volání této funkce načíst název vzhled vybrané písma.  
  
```  
CString GetFaceName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název řez písma vybraného v `CFontDialog` dialogové okno.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]  
  
##  <a name="getsize"></a>  CFontDialog::GetSize  
 Volání této funkce načíst velikost vybraných písma.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost písma v desetin bodu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]  
  
##  <a name="getstylename"></a>  CFontDialog::GetStyleName  
 Volání této funkce načíst název stylu vybraného písma.  
  
```  
CString GetStyleName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název stylu písma.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]  
  
##  <a name="getweight"></a>  CFontDialog::GetWeight  
 Volání této funkce načíst váhu vybrané písmo.  
  
```  
int GetWeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Váha vybrané písmo.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o váhu písmo, najdete v části [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]  
  
##  <a name="isbold"></a>  CFontDialog::IsBold  
 Volání této funkce můžete zjistit, jestli je vybrané písmo tučně.  
  
```  
BOOL IsBold() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vybrané písmo tučné vlastnosti povoleno; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]  
  
##  <a name="isitalic"></a>  CFontDialog::IsItalic  
 Volání této funkce můžete zjistit, jestli je vybrané písmo kurzíva.  
  
```  
BOOL IsItalic() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vybrané písmo kurzíva vlastnosti povoleno; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]  
  
##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut  
 Volání této funkce můžete určit, pokud je s přeškrtnutí zobrazeny vybrané písmo.  
  
```  
BOOL IsStrikeOut() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vybrané písmo má vlastnosti přeškrtnutí povoleno; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]  
  
##  <a name="isunderline"></a>  CFontDialog::IsUnderline  
 Volání této funkce k určení, pokud je vybrané písmo podtržené.  
  
```  
BOOL IsUnderline() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud vybrané písmo má vlastnosti podtržení, které bylo povoleno; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]  
  
##  <a name="m_cf"></a>  CFontDialog::m_cf  
 Struktura, jejíž členové uložení charakteristiky objektu dialogového okna.  
  
```  
CHOOSEFONT m_cf;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `CFontDialog` objekt, můžete použít `m_cf` změnit různé aspekty dialogu před voláním `DoModal` – členská funkce. Další informace o této struktuře naleznete v tématu [CHOOSEFONT](http://msdn.microsoft.com/library/windows/desktop/ms646832) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



