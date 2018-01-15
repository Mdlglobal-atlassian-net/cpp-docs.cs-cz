---
title: "CComboBox – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
dev_langs: C++
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fffa5c09f1572200ca7850c8870b7daee9e3e75f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccombobox-class"></a>CComboBox – třída
Poskytuje funkci Windows pole se seznamem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CComboBox : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComboBox::CComboBox](#ccombobox)|Vytvoří `CComboBox` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComboBox::AddString](#addstring)|Přidá řetězec do konce seznamu v seznamu pole se seznamem, nebo na seřazenou pozici pro seznamy s **cbs_sort –** stylu.|  
|[CComboBox::Clear](#clear)|Odstraní (vymaže) aktuální výběr, pokud existuje, v textovém poli.|  
|[CComboBox::CompareItem](#compareitem)|Voláno rámcem určit relativní umístění nové položky seznamu v seřazené vykreslovaných vlastníkem pole se seznamem.|  
|[CComboBox::Copy](#copy)|Zkopíruje aktuální výběr, pokud existuje, do schránky v **CF_TEXT** formátu.|  
|[CComboBox::Create](#create)|Pole se seznamem vytvoří a připojí jej k `CComboBox` objektu.|  
|[CComboBox::Cut](#cut)|Odstraní (kusy) aktuální výběr, pokud existuje, v úpravy řízení a zkopíruje odstraněný text do schránky v **CF_TEXT** formátu.|  
|[CComboBox::DeleteItem](#deleteitem)|Voláno rámcem při odstranění položky seznamu z vykreslovaných vlastníkem pole se seznamem.|  
|[CComboBox::DeleteString](#deletestring)|Odstraní řetězec z pole se seznamem pole se seznamem.|  
|[CComboBox::Dir](#dir)|Přidá do pole se seznamem pole se seznamem seznam názvů souborů.|  
|[CComboBox::DrawItem](#drawitem)|Voláno rámcem při visual aspektů změny pole se seznamem vykreslované uživatelem.|  
|[CComboBox::FindString](#findstring)|Vyhledá první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.|  
|[CComboBox::FindStringExact](#findstringexact)|Najde první řetězec pole se seznamem (v pole se seznamem) odpovídající zadaný řetězec.|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Načte informace o `CComboBox` objektu.|  
|[CComboBox::GetCount](#getcount)|Načte počet položek v seznamu pole se seznamem.|  
|[CComboBox::GetCueBanner](#getcuebanner)|Získá cue text, který se zobrazí pro ovládací prvek pole se seznamem.|  
|[CComboBox::GetCurSel](#getcursel)|Načte index aktuálně vybrané položky, pokud existuje, v seznamu pole se seznamem.|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Načte souřadnice obrazovky pole se seznamem viditelné (vynechaných dolů) rozevíracím seznamem.|  
|[CComboBox::GetDroppedState](#getdroppedstate)|Určuje, zda pole se seznamem rozevíracím seznamem viditelné (vynechané).|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Načte minimální povolená šířka pro část rozevírací seznam pole se seznamem.|  
|[CComboBox::GetEditSel](#geteditsel)|Získá počáteční a koncové pozice znaku aktuální výběr v ovládacím prvku úpravy pole se seznamem.|  
|[CComboBox::GetExtendedUI](#getextendedui)|Určuje, zda pole se seznamem má výchozí uživatelské rozhraní nebo Rozšířené uživatelské rozhraní.|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v pixelech, vodorovně posunout pole se seznamem část pole se seznamem.|  
|[CComboBox::GetItemData](#getitemdata)|Načte přidružený k položce zadané pole se seznamem hodnotu 32-bit zadané aplikace.|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Načte ukazatel 32-bit zadané aplikace, která je přidružená k položce zadané pole se seznamem.|  
|[CComboBox::GetItemHeight](#getitemheight)|Načte výšku položky seznamu v poli se seznamem.|  
|[CComboBox::GetLBText](#getlbtext)|Získá řetězec z pole se seznamem pole se seznamem.|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|Získá délku řetězce v seznamu pole se seznamem.|  
|[CComboBox::GetLocale](#getlocale)|Načte identifikátor národního prostředí pro pole se seznamem.|  
|[CComboBox::GetMinVisible](#getminvisible)|Získá minimální počet viditelné položky v rozevíracím seznamu aktuální pole se seznamem.|  
|[CComboBox::GetTopIndex](#gettopindex)|Vrátí index první položky zobrazené v části pole se seznamem pole se seznamem.|  
|[CComboBox::InitStorage](#initstorage)|Preallocates bloky paměti pro položky a řetězce v části pole se seznamem pole se seznamem.|  
|[CComboBox::InsertString](#insertstring)|Řetězec se vloží do pole se seznamem pole se seznamem.|  
|[CComboBox::LimitText](#limittext)|Omezení délky textu, který může uživatel zadat do ovládacího prvku pole se seznamem pro úpravy.|  
|[CComboBox::MeasureItem](#measureitem)|Voláno rámcem pro určení rozměry pole se seznamem, kdy je vytvořena vykreslovaných vlastníkem pole se seznamem.|  
|[CComboBox::Paste](#paste)|Vloží data ze schránky do ovládacího prvku úprav na aktuální pozici kurzoru. Vloží se data jenom v případě, že schránky obsahuje data v **CF_TEXT** formátu.|  
|[CComboBox::ResetContent](#resetcontent)|Odebere všechny položky ze seznamu, pole a ovládacích prvků pole se seznamem pro úpravy.|  
|[CComboBox::SelectString](#selectstring)|Hledat řetězec v seznamu pole se seznamem a pokud se řetězec najde, vybere řetězec v seznamu a zkopíruje řetězec na ovládací prvek upravit.|  
|[CComboBox::SetCueBanner](#setcuebanner)|Nastaví cue text, který se zobrazí u ovládacího prvku pole se seznamem.|  
|[CComboBox::SetCurSel](#setcursel)|Vybere řetězec v seznamu pole se seznamem.|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Nastaví minimální povolená šířka pro část rozevírací seznam pole se seznamem.|  
|[CComboBox::SetEditSel](#seteditsel)|Vybere znaků v textovém poli pole se seznamem.|  
|[CComboBox::SetExtendedUI](#setextendedui)|Vybere výchozí uživatelské rozhraní nebo Rozšířené uživatelské rozhraní pro pole se seznamem, který má **cbs_dropdown –** nebo **cbs_dropdownlist –** stylu.|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Nastaví šířku v pixelech, vodorovně posunout pole se seznamem část pole se seznamem.|  
|[CComboBox::SetItemData](#setitemdata)|Nastaví hodnotu 32-bit přidružené k položce zadané v poli se seznamem.|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Nastaví ukazatel 32-bit přidružené k položce zadané v poli se seznamem.|  
|[CComboBox::SetItemHeight](#setitemheight)|Nastaví výšku položky seznamu v pole se seznamem nebo výška textové pole (nebo statický text) část pole se seznamem.|  
|[CComboBox::SetLocale](#setlocale)|Nastaví identifikátor národního prostředí pro pole se seznamem.|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Nastaví minimální počet viditelné položky v rozevíracím seznamu aktuální pole se seznamem.|  
|[CComboBox::SetTopIndex](#settopindex)|Určuje pole se seznamem část seznamu můžete zobrazit na začátku položka se zadaným indexem.|  
|[CComboBox::ShowDropDown](#showdropdown)|Zobrazí nebo skryje pole se seznamem pole se seznamem, který má **cbs_dropdown –** nebo **cbs_dropdownlist –** stylu.|  
  
## <a name="remarks"></a>Poznámky  
 Pole se seznamem se skládá z pole se seznamem kombinaci statického ovládacího prvku nebo ovládacích prvků pro úpravy. Pole se seznamem část ovládacího prvku se zobrazují za všech okolností, nebo může pouze rozevírací nabídku, když uživatel vybere na šipku rozevíracího seznamu vedle ovládacího prvku.  
  
 Aktuálně vybrané položky (pokud existuje) v rozevíracím seznamu se zobrazí v statické nebo ovládacích prvků pro úpravy. Kromě toho pokud má pole se seznamem styl rozevíracího seznamu, uživatel můžete zadat počáteční znak jedné z položek v seznamu a pole se seznamem, pokud viditelná, bude zvýrazní další položky se tento počáteční znak.  
  
 Následující tabulka porovnává tři pole se seznamem [styly](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
|Styl|Když je viditelná pole se seznamem|Statické nebo upravit ovládací prvek|  
|-----------|-------------------------------|-----------------------------|  
|Jednoduché|Vždy|Upravit|  
|Rozevírací seznam|Při umístění|Upravit|  
|Rozevírací seznam|Při umístění|Static|  
  
 Můžete vytvořit `CComboBox` objekt z šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve volat konstruktor `CComboBox` vytvořit `CComboBox` objektu; potom zavolejte [vytvořit](#create) členskou funkci pro vytvoření ovládacího prvku a připojte ji k `CComboBox` objektu.  
  
 Pokud chcete pro zpracování zpráv s oznámením Windows posílá nadřazené pole se seznamem (obvykle třída odvozená z `CDialog`), přidejte map zpráv položku a obslužné rutiny zpráv členské funkce do nadřazené třídy pro každou zprávu.  
  
 Každá položka mapování zpráv má následující podobu:  
  
 **ON_**oznámení **(**`id`**,**`memberFxn`**)**  
  
 kde `id` určuje podřízeného okna ID ovládacího prvku pole se seznamem odesílání oznámení a `memberFxn` je název nadřazeného člena funkce napsané pro zpracování oznámení.  
  
 Prototyp funkce nadřazeného objektu je následující:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Pořadí, ve které se budou odesílat určité oznámení nelze předpovědět. Konkrétně **CBN_SELCHANGE** oznámení může dojít před nebo po **CBN_CLOSEUP** oznámení.  
  
 Potenciální map zpráv položky jsou následující:  
  
- **ON_CBN_CLOSEUP** (Windows verze 3.1 nebo novější.) Pole se seznamem pole se seznamem je zavřená. Tato oznámení se neposílají pro pole se seznamem, který má [cbs_simple –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
- **ON_CBN_DBLCLK** poklepání řetězec v seznamu pole se seznamem. Tato oznámení se odesílají pouze pro pole se seznamem **cbs_simple –** stylu. Pro pole se seznamem [cbs_dropdown –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, dvakrát klikněte na soubor nemůže proběhnout, protože pole se seznamem skryje jedním kliknutím.  
  
- **ON_CBN_DROPDOWN** pole se seznamem pole se seznamem je rozevírací nabídku (se zobrazovat). Tato zpráva oznámení může dojít pouze pro pole se seznamem **cbs_dropdown –** nebo **cbs_dropdownlist –** stylu.  
  
- **ON_CBN_EDITCHANGE** uživatel má provést akce, která mohou být ovlivněny text v části textové pole se seznamem. Na rozdíl od **CBN_EDITUPDATE** , tato zpráva je odeslána zpráva po obrazovce aktualizace systému Windows. Nejsou odesílány, pokud má pole se seznamem **cbs_dropdownlist –** stylu.  
  
- **ON_CBN_EDITUPDATE** část textové pole se seznamem je zobrazit změnit text. Tato zpráva oznámení je odeslána po ovládacího prvku má formátovaný text, ale předtím, než se zobrazí text. Nejsou odesílány, pokud má pole se seznamem **cbs_dropdownlist –** stylu.  
  
- **ON_CBN_ERRSPACE** pole se seznamem nemůže přidělit dostatek paměti na splnění konkrétního požadavku.  
  
- **ON_CBN_SELENDCANCEL** (Windows verze 3.1 nebo novější.) Označuje, že mají zrušit výběr uživatele. Uživatel klikne na položku a pak na jiné okno nebo řízení ke skrytí pole se seznamem pole se seznamem. Tato zpráva oznámení je odeslána před **CBN_CLOSEUP** zprávy oznámení, která označuje, že výběr uživatele třeba ji ignorovat. **CBN_SELENDCANCEL** nebo **CBN_SELENDOK** odeslání zprávy oznámení i v případě **CBN_CLOSEUP** neposílají oznámení (jako v případě pole se seznamem **Cbs_simple –** styl).  
  
- **ON_CBN_SELENDOK** uživatel vybere položku a stiskne klávesu ENTER nebo kliknutím na šipka dolů skrýt pole se seznamem pole se seznamem. Tato zpráva oznámení je odeslána před **CBN_CLOSEUP** zprávy, která označuje, že výběr uživatele by měly být považovány za platné. **CBN_SELENDCANCEL** nebo **CBN_SELENDOK** odeslání zprávy oznámení i v případě **CBN_CLOSEUP** neposílají oznámení (jako v případě pole se seznamem **Cbs_simple –** styl).  
  
- **ON_CBN_KILLFOCUS** pole se seznamem je ztráty zaměření pro vstup.  
  
- **ON_CBN_SELCHANGE** výběr v seznamu pole se seznamem se chystáte se změnit v důsledku uživatel kliknutím na položku v seznamu nebo změna výběru pomocí klávesy se šipkami. Při zpracování této zprávy, text v textovém poli pole se seznamem se dají načítat jenom prostřednictvím `GetLBText` nebo jiné podobné funkce. `GetWindowText`nelze použít.  
  
- **ON_CBN_SETFOCUS** pole se seznamem obdrží zaměření pro vstup.  
  
 Pokud vytvoříte `CComboBox` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CComboBox` objekt zničen automaticky při zavření dialogu.  
  
 Pokud vložit `CComboBox` objekt v rámci jiného okna objektu, není potřeba ho zrušení. Pokud vytvoříte `CComboBox` objektu v zásobníku, byla automaticky. Pokud vytvoříte `CComboBox` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte, jakmile je zničen pole se seznamem systému Windows.  
  
 **Poznámka:** Pokud chcete zpracovávat `WM_KEYDOWN` a `WM_CHAR` zprávy, budete muset podtřídami pole se seznamem na Upravit a ovládací prvky seznamu, odvozovat z `CEdit` a `CListBox`, a přidejte obslužné rutiny pro tyto zprávy do odvozené třídy. Další informace najdete v tématu [http://support.microsoft.com/default.aspxscid=kb;en-us; Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667) a [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="addstring"></a>CComboBox::AddString  
 Přidá řetězec do seznam pole se seznamem.  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszString`  
 Body řetězce ukončené hodnotou null, který má být přidán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je vrácená hodnota je větší než nebo rovna 0, je index o základu 0 pro řetězec v seznamu. Vrácená hodnota je **CB_ERR** Pokud dojde k chybě; vrácená hodnota je **CB_ERRSPACE** Pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole se seznamem nebyla vytvořena pomocí [cbs_sort –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, řetězec se přidá na konec seznamu. Jinak řetězec vložíte do seznamu, a tento seznam je řazen.  
  
> [!NOTE]
>  Tato funkce není podporována ve Windows **ComboBoxEx** ovládacího prvku. Další informace o tomto ovládacím prvku najdete v tématu [ovládací prvky ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) ve Windows SDK.  
  
 Chcete-li vložit řetězec do určitého umístění v seznamu, použijte [InsertString](#insertstring) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>CComboBox::CComboBox  
 Vytvoří `CComboBox` objektu.  
  
```  
CComboBox();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>CComboBox::Clear  
 Odstraní (vymaže) aktuální výběr, pokud existuje, v ovládacím prvku úpravy pole se seznamem.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li odstranit aktuální výběr a umístit odstraněné obsah do schránky, použijte [Vyjmout](#cut) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CComboBox::CompareItem  
 Voláno rámcem určit relativní pozici nové položky v části pole se seznamem pole se seznamem seřazené vykreslování vlastníka.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpCompareItemStruct`  
 Dlouhé ukazatel [compareitemstruct –](../../mfc/reference/compareitemstruct-structure.md) struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje relativní pozici dvě položky, které jsou popsané v `COMPAREITEMSTRUCT` struktura. Může být libovolná z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|- 1|Položka 1 seřadí před položka 2.|  
|0|Položka 1 a 2 položky řadit stejné.|  
|1|Položka 1 seřadí po položka 2.|  
  
 V tématu [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) popis `COMPAREITEMSTRUCT`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Pokud vytvoříte vykreslování vlastníka pole se seznamem **lbs_sort –** styl, je nutné přepsat tuto členskou funkci rozhraní jako pomůcku při řazení nové položky, které jsou přidány do seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>CComboBox::Copy  
 Zkopíruje aktuální výběr, pokud existuje, v ovládacím prvku úpravy pole se seznamem do schránky v **CF_TEXT** formátu.  
  
```  
void Copy();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>CComboBox::Create  
 Pole se seznamem vytvoří a připojí jej k `CComboBox` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl pole se seznamem. Použít libovolnou kombinaci [pole se seznamem styly](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) do pole.  
  
 `rect`  
 Bodů na umístění a velikost pole se seznamem. Může být [Rect – struktura](../../mfc/reference/rect-structure1.md) nebo `CRect` objektu.  
  
 `pParentWnd`  
 Určuje pole se seznamem nadřazeného okna (obvykle `CDialog`). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku pole se seznamem  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CComboBox` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, která pole se seznamem Windows vytvoří a připojí jej k `CComboBox` objektu.  
  
 Když **vytvořit** provede, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy do pole se seznamem.  
  
 Tyto zprávy jsou zpracovávány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Rozšíření zpracování zpráv výchozí, odvození třídy z `CComboBox`, přidejte mapy zpráv do nové třídy a přepsat předchozí členské funkce obslužné rutiny zpráv. Přepsání `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku pole se seznamem. :  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
- **Ws_vscroll –** přidat svislé posouvání pro pole se seznamem do pole se seznamem  
  
- **Ws_hscroll –** přidat vodorovného posouvání pro pole se seznamem do pole se seznamem  
  
- **Ws_group –** k seskupování ovládacích prvků  
  
- **Ws_tabstop –** v pořadí, dají se procházet tabulátorem zahrnout pole se seznamem  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>CComboBox::Cut  
 Odstranění (kusy) aktuální výběr, pokud existuje, do pole se seznamem upravit řízení a zkopíruje odstraněný text do schránky v **CF_TEXT** formátu.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li odstranit aktuální výběr bez umístění odstraněný text do schránky, zavolejte [zrušte](#clear) – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>CComboBox::DeleteItem  
 Voláno rámcem, když uživatel odstraní položku z kreslení vlastníka `CComboBox` objektu nebo zničí pole se seznamem.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDeleteItemStruct`  
 Dlouhé ukazatel na Windows [deleteitemstruct –](../../mfc/reference/deleteitemstruct-structure.md) struktura, která obsahuje informace o odstraněné položky. V tématu [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) popis této struktury.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce neprovede žádnou akci. Přepsání této funkci můžete podle potřeby ho překreslit pole se seznamem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>CComboBox::DeleteString  
 Odstraní položky v pozici `nIndex` z pole se seznamem.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index pro řetězec, který má být odstraněn.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je vrácená hodnota je větší než nebo rovna 0, je počet řetězce zbývající v seznamu. Vrácená hodnota je **CB_ERR** Pokud `nIndex` Určuje indexu větší než počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny položky následující `nIndex` nyní přesunout o jednu pozici dolů. Například pokud pole se seznamem obsahuje dvě položky, odstranění první položka způsobí, že zbývající položka, která má být nyní v první pozici. `nIndex`= 0 pro položky v první pozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>CComboBox::Dir  
 Seznam názvů souborů nebo jednotky přidá do pole se seznamem pole se seznamem.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parametry  
 `attr`  
 Může být libovolnou kombinací `enum` hodnoty popsané v [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) nebo libovolnou kombinaci těchto hodnot:  
  
- **DDL_READWRITE** souboru může číst nebo zapisovat do.  
  
- **DDL_READONLY** lze číst z ale nezapíše se do souboru.  
  
- **DDL_HIDDEN** souboru je skrytá a nezobrazí se v seznamu adresářů.  
  
- **DDL_SYSTEM** soubor je soubor systému.  
  
- **DDL_DIRECTORY** název zadaný `lpszWildCard` Určuje adresář.  
  
- **DDL_ARCHIVE** soubor byl archivován.  
  
- **DDL_DRIVES** zahrnují všechny disky, které odpovídají názvu určeného `lpszWildCard`.  
  
- **DDL_EXCLUSIVE** výhradní příznak. Pokud je nastavený příznak výhradní, jsou uvedeny pouze soubory zadaného typu. Soubory zadaného typu, jinak, jsou uvedené kromě "normální" souborů.  
  
 `lpszWildCard`  
 Odkazuje na řetězec specifikaci souboru. Řetězec může obsahovat zástupné znaky (například *.\*).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je vrácená hodnota je větší než nebo rovna 0, je index založený na nule poslední názvu souboru do seznamu přidat. Vrácená hodnota je **CB_ERR** Pokud dojde k chybě; vrácená hodnota je **CB_ERRSPACE** Pokud je k dispozici pro uložení nových řetězců není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce není podporována ve Windows **ComboBoxEx** ovládacího prvku. Další informace o tomto ovládacím prvku najdete v tématu [ovládací prvky ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>CComboBox::DrawItem  
 Voláno rámcem při visual aspektů změny pole se seznamem vykreslování vlastníka.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktura, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** členem `DRAWITEMSTRUCT` struktura definuje kreslení akci, která má být provedena. V tématu [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis této struktury.  
  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CComboBox` objektu. Než tuto funkci člen ukončí, aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>CComboBox::FindString  
 Najde, ale není vybrán první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Obsahuje index položky před první má proběhnout založený na nule. Při hledání dosáhne spodní části pole se seznamem, pokračuje z horní části seznamu zpátky k položce určeného `nStartAfter`. Pokud-1, prohledají se celý seznam od začátku.  
  
 `lpszString`  
 Body řetězce ukončené hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Hledání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a velkých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je vrácená hodnota je větší než nebo rovna 0, je index založený na nule odpovídající položky. Je **CB_ERR** Pokud vyhledávání nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce není podporována ve Windows **ComboBoxEx** ovládacího prvku. Další informace o tomto ovládacím prvku najdete v tématu [ovládací prvky ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>CComboBox::FindStringExact  
 Volání `FindStringExact` – členská funkce Najít první řetězec pole se seznamem (v pole se seznamem) odpovídající řetězec zadaný v `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndexStart`  
 Určuje index položky před první má proběhnout založený na nule. Při hledání dosáhne spodní části pole se seznamem, pokračuje z horní části seznamu zpátky k položce určeného `nIndexStart`. Pokud `nIndexStart` je -1, prohledají se celý seznam od začátku.  
  
 `lpszFind`  
 Odkazuje na hledaný řetězec ukončené hodnotou null. Tento řetězec může obsahovat úplný název souboru, včetně přípony. Hledání není velká a malá písmena, takže tento řetězec může obsahovat libovolnou kombinaci velkých a velkých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule odpovídající položky nebo **CB_ERR** Pokud vyhledávání nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole se seznamem byl vytvořen s styl vykreslování vlastníka, ale bez [cbs_hasstrings –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, `FindStringExact` se pokusí o porovnání hodnota doubleword s hodnotou `lpszFind`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo  
 K načtení informací o `CComboBox` objektu.  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pcbi*  
 Ukazatel [COMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775798) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [CB_GETCOMBOBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775839) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getcount"></a>CComboBox::GetCount  
 Volání této funkce člen načíst počet položek v části pole se seznamem pole se seznamem.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek. Vrácený počet je větší než hodnota indexu poslední položky (index je počítáno od nuly). Je **CB_ERR** Pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>CComboBox::GetCueBanner  
 Získá cue text, který se zobrazí pro ovládací prvek pole se seznamem.  
  
```  
CString GetCueBanner() const;  
  
BOOL GetCueBanner(
    LPTSTR lpszText,   
    int cchText) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out]`lpszText`|Ukazatel na vyrovnávací paměť, která obdrží text hlavičky cue.|  
|[v]`cchText`|Velikost vyrovnávací paměti, která `lpszText` parametr odkazuje na.|  
  
### <a name="return-value"></a>Návratová hodnota  
 V první přetížení [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obsahuje text hlavičky cue, pokud existuje; jinak, `CString` objekt, který má nulové délky.  
  
 -nebo-  
  
 V druhé přetížení `true` Pokud tato metoda je úspěšné, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Cue text je řádku, který se zobrazí v oblasti vstupního ovládacího prvku pole se seznamem. Text upozornění se zobrazí, dokud uživatel nezadá vstup.  
  
 Tato metoda odesílá [CB_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775843) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getcursel"></a>CComboBox::GetCurSel  
 Volání této funkce člen k určení, která položka v seznamu je vybrána.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule aktuálně vybrané položky v seznamu pole se seznamem, nebo **CB_ERR** Pokud není vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 `GetCurSel`Vrátí index do seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect  
 Volání `GetDroppedControlRect` – členská funkce načíst souřadnice obrazovky pole se seznamem viditelné (vyřadit dolů) rozevíracím seznamem.  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje na [Rect – struktura](../../mfc/reference/rect-structure1.md) , který má přijímat souřadnice.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>CComboBox::GetDroppedState  
 Volání `GetDroppedState` – členská funkce k určení, zda pole se seznamem rozevíracím seznamem je viditelná (vynechané).  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je viditelná; pole se seznamem jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth  
 Volání této funkce načíst šířku v pixelech pole se seznamem seznamem minimální povolená.  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného minimální povolená šířku v pixelech; v opačném **CB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se vztahuje pouze na pole se seznamem s [cbs_dropdown –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
 Ve výchozím nastavení je minimální povolená šířka pole rozevíracího seznamu 0. Minimální povolená šířka můžete nastavit voláním [SetDroppedWidth](#setdroppedwidth). Když se zobrazí pole se seznamem část pole se seznamem, je jeho šířka větší šířku minimální povolená nebo šířka pole se seznamem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [SetDroppedWidth](#setdroppedwidth).  
  
##  <a name="geteditsel"></a>CComboBox::GetEditSel  
 Získá počáteční a koncové pozice znaku aktuální výběr v ovládacím prvku úpravy pole se seznamem.  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 32bitová hodnota, která obsahuje počáteční pozice v aplikaci word nejnižší a pozice prvního znaku nevybrané po skončení výběr v aplikaci word horní. Při použití této funkce na pole se seznamem bez ovládací prvek upravit **CB_ERR** je vrácen.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>CComboBox::GetExtendedUI  
 Volání `GetExtendedUI` – členská funkce k určení, zda má pole se seznamem výchozí uživatelské rozhraní nebo Rozšířené uživatelské rozhraní.  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud má pole se seznamem Rozšířené uživatelské rozhraní; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozšířené uživatelského rozhraní lze identifikovat následujícími způsoby:  
  
-   Kliknutím na statické ovládací prvek zobrazí pole se seznamem pouze pro pole se seznamem s [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
-   Stisknutím klávesy Šipka dolů zobrazí pole se seznamem (F4 je zakázáno).  
  
 Posouvání v ovládacím prvku statické je zakázáno, pokud seznamu položek není viditelné (šipka, které jsou zakázány klíčů).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent  
 Načte z pole se seznamem šířku v pixelech, které části pole se seznamem pole se seznamem vodorovně posunout.  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posuvný šířka pole se seznamem část pole se seznamem v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tuto možnost lze použít pouze v případě pole se seznamem část pole se seznamem vodorovného posuvníku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>CComboBox::GetItemData  
 Načte přidružený k položce zadané pole se seznamem hodnotu 32-bit zadané aplikace.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index položky v seznamu pole se seznamem založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 32-bit hodnotu přidruženou položku, nebo **CB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Můžete nastavit hodnotu 32-bit `dwItemData` parametr [setitemdata –](#setitemdata) volání funkce člen. Použití `GetItemDataPtr` – členská funkce, pokud je hodnota 32-bit mají být načteny ukazatel ( **void\***).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>CComboBox::GetItemDataPtr  
 Načte 32bitové hodnotu zadané aplikace přidružené k položce zadané pole se seznamem jako ukazatel ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index položky v seznamu pole se seznamem založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte ukazatel nebo -1, pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>CComboBox::GetItemHeight  
 Volání `GetItemHeight` – členská funkce načíst výšku položky seznamu v poli se seznamem.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje komponentu pole se seznamem, jehož výšku je mají být načteny. Pokud `nIndex` parametr -1, výška pole se seznamem část ovládacího prvku úpravy (nebo statický text) je načíst. Pokud má pole se seznamem [cbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl `nIndex` Určuje index založený na nule položky seznamu, jejíž výšku je mají být načteny. V opačném `nIndex` musí být nastavena na 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech zadané položky v poli se seznamem. Vrácená hodnota je **CB_ERR** Pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>CComboBox::GetLBText  
 Získá řetězec z pole se seznamem pole se seznamem.  
  
```  
int GetLBText(
    int nIndex,  
    LPTSTR lpszText) const;  
  
void GetLBText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index pole se seznamem řetězce, který se má zkopírovat založený na nule.  
  
 `lpszText`  
 Body do vyrovnávací paměti, která se zobrazí řetězec. Vyrovnávací paměti musí být dost místa pro řetězce a znak ukončující null.  
  
 `rString`  
 Odkaz na `CString`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce, s výjimkou ukončující znak hodnoty null (v bajtech). Pokud `nIndex` neurčuje platný index, je vrácenou hodnotou **CB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 Druhý formulář člen funkce výplněmi `CString` objekt s text položky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>CComboBox::GetLBTextLen  
 Získá délku řetězce v seznamu pole se seznamem.  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index pole se seznamem řetězce založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce v bajtech, s výjimkou ukončující znak hodnoty null. Pokud `nIndex` neurčuje platný index, je vrácenou hodnotou **CB_ERR**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetLBText](#getlbtext).  
  
##  <a name="getlocale"></a>CComboBox::GetLocale  
 Načte národní prostředí používané pole se seznamem.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota identifikátoru (LCID) národního prostředí pro řetězce v poli se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Národní prostředí se používá, například k určení pořadí řazení řetězců v seřazené pole se seznamem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::SetLocale](#setlocale).  
  
##  <a name="getminvisible"></a>CComboBox::GetMinVisible  
 Získá minimální počet viditelné položky v rozevíracím seznamu aktuální ovládacího prvku pole se seznamem.  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minimální počet viditelné položky v rozevíracím seznamu aktuální.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [CB_GETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="gettopindex"></a>CComboBox::GetTopIndex  
 Načte index založený na nule z první položky zobrazené v části pole se seznamem pole se seznamem.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule z první položky zobrazené v části pole se seznamem pole se seznamem v případě úspěšného **CB_ERR** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Na začátku položka 0 je v horní části seznamu, ale pokud přesunut pole se seznamem oblasti jiné položky může být v horní části.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>CComboBox::InitStorage  
 Přidělí paměť pro ukládání pole položky seznamu v části pole se seznamem pole se seznamem.  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `nItems`  
 Určuje počet položek, které chcete přidat.  
  
 `nBytes`  
 Určuje velikost paměti, v bajtech, přidělit pro položku řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, maximální počet položek, které části pole se seznamem pole se seznamem můžete uložit, než je potřeba opakované přidělení paměti, jinak hodnota **CB_ERRSPACE**, což znamená, není dost paměti je k dispozici.  
  
### <a name="remarks"></a>Poznámky  
 Před přidáním velké množství položek do pole se seznamem část volání této funkce `CComboBox`.  
  
 Systém Windows 95/98 pouze: `wParam` je omezený na 16bitové hodnoty parametru. To znamená, že seznamy nesmí obsahovat víc než 32 767 položky. I když počet položek, které je s omezeným přístupem, celková velikost položky v seznamu je omezena pouze dostupné paměti.  
  
 Tato funkce pomáhá zrychlit inicializace seznamy, které mají velký počet položek (více než 100). Ho preallocates zadaného množství paměti, že následné [addstring –](#addstring), [InsertString](#insertstring), a [Dir](#dir) funkce přebírat co nejdříve. Odhadne můžete použít pro parametry. Pokud jste overestimate, se přidělí některé další paměť; Pokud jste příliš nízko, použije se normální přidělení pro položky, které překračují předběžně přidělená velikost.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>CComboBox::InsertString  
 Řetězec se vloží do pole se seznamem pole se seznamem.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index na pozici v seznamu, která bude přijímat řetězec založený na nule. Pokud má parametr hodnotu -1, řetězec se přidá na konec seznamu.  
  
 `lpszString`  
 Body řetězce ukončené hodnotou null, který chcete vložit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule pozice, kdy byl vložen řetězec. Vrácená hodnota je **CB_ERR** Pokud dojde k chybě. Vrácená hodnota je **CB_ERRSPACE** Pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [addstring –](#addstring) – členská funkce `InsertString` – členská funkce nezpůsobí seznam s [cbs_sort –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, který se má seřadit.  
  
> [!NOTE]
>  Tato funkce není podporována ve Windows **ComboBoxEx** ovládacího prvku. Další informace o tomto ovládacím prvku najdete v tématu [ovládací prvky ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>CComboBox::LimitText  
 Omezí se délka v bajtech text, který může uživatel zadat do ovládacího prvku pole se seznamem pro úpravy.  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>Parametry  
 `nMaxChars`  
 Určuje text, který může uživatel zadat délku (v bajtech). Pokud má parametr hodnotu 0, délka textu je nastavena na 65 535 bajtů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu. Pokud je volána pro pole se seznamem se stylem [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo pro pole se seznamem bez ovládací prvek upravit, je vrácenou hodnotu **CB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole se seznamem nemá styl [cbs_autohscroll –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), text limit musí být větší než velikost ovládacích prvků pro úpravy nastavení nebude mít žádný vliv.  
  
 `LimitText`text, který lze zadat pouze omezení. Ho nemá žádný vliv na jakýkoli text již v ovládacím prvku upravit při odeslání zprávy jsou ani neovlivní délku textu zkopírován do ovládacího prvku úprav, pokud je řetězec v rozevíracím seznamu vybrána.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>CComboBox::MeasureItem  
 Voláno rámcem při vytvoření pole se seznamem s styl vykreslování vlastníka.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Dlouhé ukazatel [measureitemstruct –](../../mfc/reference/measureitemstruct-structure.md) struktura.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Funkci člena přepsat a vyplňte `MEASUREITEMSTRUCT` struktura k informování Windows dimenzí seznamu pole se seznamem. Pokud pole se seznamem je vytvořen s [cbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) volá framework styl, tato funkce člena pro každou položku v seznamu. Tento člen, jinak je volat pouze jednou.  
  
 Pomocí **cbs_ownerdrawfixed –** styl pole se seznamem vykreslování vlastníka vytvořené pomocí [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) členské funkce `CWnd` zahrnuje další programovací aspekty. Viz popis v [Technická poznámka 14](../../mfc/tn014-custom-controls.md).  
  
 V tématu [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) popis `MEASUREITEMSTRUCT` struktura.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>CComboBox::Paste  
 Vloží data ze schránky do ovládacího prvku úprav pole se seznamem na aktuální pozici kurzoru.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Poznámky  
 Vloží se data jenom v případě, že schránky obsahuje data v **CF_TEXT** formátu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>CComboBox::ResetContent  
 Odebere všechny položky ze seznamu, pole a ovládacích prvků pole se seznamem pro úpravy.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>CComboBox::SelectString  
 Hledat řetězec v seznamu pole se seznamem a pokud se řetězec najde, vybere řetězec v seznamu a zkopíruje je do ovládacího prvku úprav.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Obsahuje index položky před první má proběhnout založený na nule. Při hledání dosáhne spodní části pole se seznamem, pokračuje z horní části seznamu zpátky k položce určeného `nStartAfter`. Pokud-1, prohledají se celý seznam od začátku.  
  
 `lpszString`  
 Body řetězce ukončené hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Hledání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a velkých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule vybrané položky. Pokud byl nalezen řetězec. Pokud hledání nebylo úspěšné, je vrácenou hodnotu **CB_ERR** a aktuální výběr se nezmění.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec je vybrána pouze v případě, že jeho počáteční znaků (od počátečního bodu) shoduje s znaky v řetězci předpony.  
  
 Všimněte si, že `SelectString` a `FindString` členské funkce najít řetězec, ale `SelectString` – členská funkce také vybere řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>CComboBox::SetCueBanner  
 Nastaví cue text, který se zobrazí u ovládacího prvku pole se seznamem.  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] *lpszText*|Ukazatel na vyrovnávací paměť ukončené hodnotou null, která obsahuje cue text.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je metoda úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Cue text je řádku, který se zobrazí v oblasti vstupního ovládacího prvku pole se seznamem. Text upozornění se zobrazí, dokud uživatel nezadá vstup.  
  
 Tato metoda odesílá [CB_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb775897) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_combobox`, který používá k programovému přístupu ovládacího prvku pole se seznamem. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví hlavičku cue ovládacího prvku pole se seznamem.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>CComboBox::SetCurSel  
 Vybere řetězec v seznamu pole se seznamem.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parametry  
 `nSelect`  
 Určuje index založený na nule řetězce k výběru. Pokud -1, se odstraní všechny aktuální výběr v seznamu a textové pole není zaškrtnuto.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule položky vybrané Pokud zpráva je úspěšné. Vrácená hodnota je **CB_ERR** Pokud `nSelect` je větší než počet položek v seznamu nebo, pokud `nSelect` je nastaven na hodnotu -1, který vymaže výběr.  
  
### <a name="remarks"></a>Poznámky  
 V případě potřeby pole se seznamem posune řetězec do zobrazení (Pokud je pole se seznamem viditelné). Text v textovém poli pole se seznamem se změní na nový výběr projeví. Odeberou se všechny předchozí výběr v seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth  
 Volání této funkce se nastavit minimální povolená šířku v pixelech pole se seznamem pole se seznamem.  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Minimální povolená šířka pole se seznamem část pole se seznamem v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, nové šířku seznamu pole, v opačném případě **CB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se vztahuje pouze na pole se seznamem s [cbs_dropdown –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
 Ve výchozím nastavení je minimální povolená šířka pole rozevíracího seznamu 0. Když se zobrazí pole se seznamem část pole se seznamem, je jeho šířka větší šířku minimální povolená nebo šířka pole se seznamem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>CComboBox::SetEditSel  
 Vybere znaků v textovém poli pole se seznamem.  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartChar`  
 Určuje počáteční pozici. Pokud počáteční pozice nastavena na hodnotu -1, se odstraní všechny existující výběr.  
  
 `nEndChar`  
 Určuje koncovou pozici. Pokud koncovou pozici je nastavena na hodnotu -1, pak všechny text od počáteční pozice na poslední znak v textové pole je vybrán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného; – členská funkce jinak 0. Je **CB_ERR** Pokud `CComboBox` má [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl nebo nemá pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Polohy jsou od nuly. Vyberte první znak ovládacích prvků pro úpravy, zadejte počáteční pozici 0. Koncová pozice je znaku bezprostředně za jeho poslední znak vyberte. Vyberte první čtyři znaky ovládacích prvků pro úpravy, byste například použili počáteční pozice 0 a koncová pozice 4.  
  
> [!NOTE]
>  Tato funkce není podporována ve Windows **ComboBoxEx** ovládacího prvku. Další informace o tomto ovládacím prvku najdete v tématu [ovládací prvky ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775738) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetEditSel](#geteditsel).  
  
##  <a name="setextendedui"></a>CComboBox::SetExtendedUI  
 Volání `SetExtendedUI` – členská funkce a vyberte výchozí uživatelské rozhraní nebo Rozšířené uživatelské rozhraní pro pole se seznamem, který má [cbs_dropdown –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bExtended*  
 Určuje, zda pole se seznamem by měl používat rozšířené uživatelského rozhraní nebo výchozí uživatelské rozhraní. Hodnota **TRUE** vybere Rozšířené uživatelské rozhraní; hodnota **FALSE** vybere standardní uživatelské rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 **CB_OKAY** Pokud operace proběhne úspěšně, nebo **CB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Rozšířené uživatelského rozhraní lze identifikovat následujícími způsoby:  
  
-   Kliknutím na statické ovládací prvek zobrazí pole se seznamem pouze pro pole se seznamem s **cbs_dropdownlist –** stylu.  
  
-   Stisknutím klávesy Šipka dolů zobrazí pole se seznamem (F4 je zakázáno).  
  
 Posouvání v ovládacím prvku statické bude deaktivovaná, pokud není viditelná seznamu položek (klávesy se šipkami jsou zakázané).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetExtendedUI](#getextendedui).  
  
##  <a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent  
 Nastaví šířku v pixelech, které části pole se seznamem pole se seznamem vodorovně posunout.  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>Parametry  
 *nExtent*  
 Určuje počet pixelů, podle kterých části pole se seznamem pole se seznamem vodorovně posunout.  
  
### <a name="remarks"></a>Poznámky  
 Pokud šířka pole se seznamem je menší než tato hodnota, bude vodorovného posuvníku přejděte vodorovně položky v seznamu. Pokud je šířka pole se seznamem je rovna nebo větší než tato hodnota, je skrytá vodorovného posuvníku nebo, pokud má pole se seznamem [cbs_disablenoscroll –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, zakázána.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>CComboBox::SetItemData  
 Nastaví hodnotu 32-bit přidružené k položce zadané v poli se seznamem.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index počítaný od nuly s položkou. Chcete-li nastavit.  
  
 `dwItemData`  
 Obsahuje novou hodnotu pro přidružení k položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 **CB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Použití `SetItemDataPtr` – členská funkce, pokud je položka 32-bit jako ukazatel.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>CComboBox::SetItemDataPtr  
 Nastaví hodnotu 32-bit přidružené k položce zadané v poli se seznamem být zadaný ukazatele ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index počítaný od nuly k položce.  
  
 `pData`  
 Obsahuje má ukazatel na položce přidružena.  
  
### <a name="return-value"></a>Návratová hodnota  
 **CB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Tento ukazatel zůstane platný po celou dobu životnosti pole se seznamem, i když položky relativní pozici v rámci pole se seznamem může změnit, protože přidání nebo odebrání položky. Proto můžete změnit index položky v rámci pole, ale ukazatel zůstane spolehlivé.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>CComboBox::SetItemHeight  
 Volání `SetItemHeight` – členská funkce nastavit výšku položky seznamu v pole se seznamem nebo výška textové pole (nebo statický text) část pole se seznamem.  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje, zda je nastaven výšku položky seznamu nebo výšky části textové pole (nebo statický text) pole se seznamem.  
  
 Pokud má pole se seznamem [cbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, `nIndex` Určuje index založený na nule položky seznamu, jejíž výšku je potřeba, jinak hodnota `nIndex` musí být 0 a výšku všechny seznamu položek bude nastavena.  
  
 Pokud `nIndex` je -1, Výška ovládacích prvků pro úpravy nebo část statické textové pole se seznamem je možné nastavit.  
  
 `cyItemHeight`  
 Určuje výšku v pixelech komponentu pole se seznamem identifikovaný `nIndex`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **CB_ERR** Pokud je index nebo výška neplatný; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Výška pole se seznamem část ovládacího prvku úpravy (nebo statický text) je nastaven nezávisle na výšku položky seznamu. Aplikace musí zajistit, že výšku část ovládacího prvku úpravy (nebo statický text) není menší než výška konkrétní seznam položek.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>CComboBox::SetLocale  
 Nastaví identifikátor národního prostředí pro toto pole se seznamem.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLocale`  
 Nová hodnota národního prostředí identifikátor (LCID) pro pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnotu národního prostředí (LCID) identifikátor pro toto pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Pokud **SetLocale** není volán výchozí národní prostředí se získávají z systému. Tato výchozí národní prostředí systému můžete upravit pomocí ovládacích panelů místní (nebo mezinárodní) aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems  
 Nastaví minimální počet viditelné položky v rozevíracím seznamu aktuální pole se seznamem ovládacích prvků pole.  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`iMinVisible`|Určuje minimální počet viditelné položky.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [CB_SETMINVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb775915) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_combobox`, který používá k programovému přístupu ovládacího prvku pole se seznamem. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vloží 20 položky do rozevíracího seznamu ovládacího prvku pole se seznamem. Pak se určuje, že minimálně 10 položek zobrazí po stisknutí na šipku rozevíracího seznamu.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>CComboBox::SetTopIndex  
 Zajišťuje, že určité položky viditelné v části pole se seznamem pole se seznamem.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index položky pole se seznamem založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu nebo **CB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Systém se posouvá společně pole se seznamem dokud položka určeného `nIndex` se zobrazí v horní části seznamu bylo dosaženo pole nebo rozsah maximální scroll.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>CComboBox::ShowDropDown  
 Zobrazí nebo skryje pole se seznamem pole se seznamem, který má [cbs_dropdown –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [cbs_dropdownlist –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowIt*  
 Určuje, zda pole rozevíracího seznamu pro zobrazen nebo skryt. Hodnota **TRUE** zobrazí pole se seznamem. Hodnota **FALSE** skryje pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení zobrazí pole se seznamem tohoto stylu pole se seznamem.  
  
 Tato funkce člen nemá žádný vliv na pole se seznamem vytvořené pomocí [cbs_simple –](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetDroppedState](#getdroppedstate).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)   
 [CStatic – třída](../../mfc/reference/cstatic-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
