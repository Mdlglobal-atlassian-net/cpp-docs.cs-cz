---
title: CComboBox – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4fc2eb252c81e903174d99d4a55b2f3c1eed321
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205284"
---
# <a name="ccombobox-class"></a>CComboBox – třída
Poskytuje funkce pro pole se seznamem Windows.  
  
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
|[CComboBox::AddString](#addstring)|Přidá řetězec do konce seznamu v poli seznamu pole se seznamem, nebo na seřazený pozici pro pole se seznamem se stylem CBS_SORT.|  
|[CComboBox::Clear](#clear)|Odstraní (vymaže) aktuální výběr, pokud existuje, v textovém poli.|  
|[CComboBox::CompareItem](#compareitem)|Volá se rozhraním k určení relativní pozice novou položku seznamu do pole se seznamem seřazený vykreslovaných vlastníkem.|  
|[CComboBox::Copy](#copy)|Zkopíruje aktuální výběr, pokud existuje, do schránky ve formátu CF_TEXT.|  
|[CComboBox::Create](#create)|Vytvoří pole se seznamem a připojí ho k `CComboBox` objektu.|  
|[CComboBox::Cut](#cut)|Odstraní (kusů) aktuální výběr, pokud existuje, v úpravách řízení a zkopíruje ve formátu CF_TEXT odstraněný text do schránky.|  
|[CComboBox::DeleteItem](#deleteitem)|Volá se rozhraním při odstranění položky seznamu z – pole se seznamem vykreslovaných vlastníkem.|  
|[CComboBox::DeleteString](#deletestring)|Řetězec se odstraní ze seznamu pole se seznamem.|  
|[CComboBox::Dir](#dir)|Seznam názvů souborů se přidá do seznamu pole se seznamem.|  
|[CComboBox::DrawItem](#drawitem)|Volá se rozhraním při úpravě vizuálního aspektu změní vykreslovaných vlastníkem – pole se seznamem.|  
|[CComboBox::FindString](#findstring)|Najde první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.|  
|[CComboBox::FindStringExact](#findstringexact)|Najde první řetězec pole se seznamem (v poli se seznamem), který odpovídá zadaného řetězce.|  
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Načte informace o `CComboBox` objektu.|  
|[CComboBox::GetCount](#getcount)|Získá počet položek v seznamu pole se seznamem.|  
|[CComboBox::GetCueBanner](#getcuebanner)|Získá startovací text, který se zobrazí pro ovládací prvek pole se seznamem.|  
|[CComboBox::GetCurSel](#getcursel)|Načte index aktuálně vybrané položky, pokud existuje, v seznamu pole se seznamem.|  
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Načte souřadnice obrazovky viditelné (vynechaných dolů) seznamu rozevíracím seznamem.|  
|[CComboBox::GetDroppedState](#getdroppedstate)|Určuje, zda pole se seznamem rozevíracím seznamem je viditelné (rozbalil).|  
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Získá minimální povolenou Šířka rozevíracích seznamů část pole se seznamem.|  
|[CComboBox::GetEditSel](#geteditsel)|Získá počáteční a koncová pozice znaku aktuálního výběru v textovém poli se seznamem.|  
|[CComboBox::GetExtendedUI](#getextendedui)|Určuje, zda pole se seznamem obsahuje výchozí uživatelské rozhraní nebo rozšířené uživatelského rozhraní.|  
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v pixelech, že je vodorovně posuvný seznam – část pole se seznamem.|  
|[CComboBox::GetItemData](#getitemdata)|Načte 32bitovou hodnotu poskytované aplikací přidružených k položce zadané pole se seznamem.|  
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Načte 32bitového ukazatele poskytované aplikací, která je přidružená k položce zadané pole se seznamem.|  
|[CComboBox::GetItemHeight](#getitemheight)|Získá výšku položky seznamu v poli se seznamem.|  
|[CComboBox::GetLBText](#getlbtext)|Získá řetězec ze seznamu pole se seznamem.|  
|[CComboBox::GetLBTextLen](#getlbtextlen)|Získá délku řetězce v seznamu pole se seznamem.|  
|[CComboBox::GetLocale](#getlocale)|Načte identifikátor národního prostředí pro pole se seznamem.|  
|[CComboBox::GetMinVisible](#getminvisible)|Získá minimální počet viditelných položek v rozevíracím seznamu aktuálního pole se seznamem.|  
|[CComboBox::GetTopIndex](#gettopindex)|Vrátí index první viditelné položky v seznamu. část pole se seznamem.|  
|[CComboBox::InitStorage](#initstorage)|Preallocates bloky paměti pro položky a řetězce v seznamu. část pole se seznamem.|  
|[CComboBox::InsertString](#insertstring)|Řetězec se vloží do seznamu pole se seznamem.|  
|[CComboBox::LimitText](#limittext)|Omezení délky textu, který může uživatel zadat do ovládacího prvku pro úpravy pole se seznamem.|  
|[CComboBox::MeasureItem](#measureitem)|Volá se rozhraním pro určení rozměry pole se seznamem, kdy je vytvořen vlastníkem vykreslované seznamem.|  
|[CComboBox::Paste](#paste)|Vloží data ze schránky do textového pole na aktuální pozici kurzoru. Data budou vložena pouze v případě, že obsahuje data ve formátu CF_TEXT do schránky.|  
|[CComboBox::ResetContent](#resetcontent)|Odebere všechny položky v seznamu pole a upravit ovládací prvek pole se seznamem.|  
|[CComboBox::SelectString](#selectstring)|Vyhledá řetězec v seznamu pole se seznamem a pokud se řetězec najde, vybere řetězec v seznamu a zkopíruje řetězec do ovládacího prvku pro úpravy.|  
|[CComboBox::SetCueBanner](#setcuebanner)|Nastaví startovací text, který se zobrazí u ovládacího prvku pole se seznamem.|  
|[CComboBox::SetCurSel](#setcursel)|Vybere řetězec v seznamu pole se seznamem.|  
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Nastaví minimální povolenou Šířka rozevíracích seznamů část pole se seznamem.|  
|[CComboBox::SetEditSel](#seteditsel)|Vybere znaků v textovém poli se seznamem.|  
|[CComboBox::SetExtendedUI](#setextendedui)|Vybere výchozí uživatelské rozhraní nebo rozšířené uživatelského rozhraní pro pole se seznamem, který má CBS_DROPDOWN nebo CBS_DROPDOWNLIST style.|  
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Nastavuje šířku v pixelech, že je vodorovně posuvný seznam – část pole se seznamem.|  
|[CComboBox::SetItemData](#setitemdata)|Nastaví hodnotu 32-bit přidruženou k zadané položky pole se seznamem.|  
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Nastaví 32bitového ukazatele přidružené zadaná položka v poli se seznamem.|  
|[CComboBox::SetItemHeight](#setitemheight)|Nastaví výšku položky seznamu v poli se seznamem nebo výška textové pole (nebo statický text) část pole se seznamem.|  
|[CComboBox::SetLocale](#setlocale)|Nastaví identifikátor národního prostředí pro pole se seznamem.|  
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Nastaví minimální počet viditelných položek v rozevíracím seznamu aktuálního pole se seznamem.|  
|[CComboBox::SetTopIndex](#settopindex)|Určuje pole se seznamem část pole se seznamem, aby se zobrazila položka se zadaným indexem v horní části.|  
|[CComboBox::ShowDropDown](#showdropdown)|Zobrazí nebo skryje seznam pole se seznamem, který má CBS_DROPDOWN nebo CBS_DROPDOWNLIST style.|  
  
## <a name="remarks"></a>Poznámky  
 Pole se seznamem se skládá z pole se seznamem v kombinaci se statický ovládací prvek nebo ovládací prvek pro úpravy. Pole se seznamem části ovládacího prvku nemusí být zobrazeny po celou dobu nebo může pouze rozevírací seznam, když uživatel vybere na šipku rozevíracího seznamu vedle ovládacího prvku.  
  
 Aktuálně vybrané položky (pokud existuje) v rozevíracím seznamu se zobrazí ve statické nebo ovládacích prvků pro úpravy. Kromě toho pokud pole se seznamem obsahuje rozevírací seznam styl, může uživatel zadat počáteční znak z jedné z položek v seznamu a seznam, pokud je viditelná, vyzdvihne na další položku, že počáteční znak.  
  
 Následující tabulka porovnává tři pole se seznamem [styly](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles).  
  
|Styl|Pokud je pole se seznamem viditelné|Statické nebo upravit ovládací prvek|  
|-----------|-------------------------------|-----------------------------|  
|Jednoduché|Vždy|Upravit|  
|Rozevírací seznam|Když se rozbalil|Upravit|  
|Rozevírací seznam|Když se rozbalil|Static|  
  
 Můžete vytvořit `CComboBox` objekt z šablony dialogového okna nebo přímo v kódu. V obou případech se nejprve volat konstruktor `CComboBox` k sestavení kompletních `CComboBox` objektu; poté zavolejte [vytvořit](#create) členská funkce vytvoření ovládacího prvku a připojit ho k `CComboBox` objektu.  
  
 Pokud chcete zpracovávat Windows oznamující zprávy odeslal pole se seznamem a jeho nadřazeným (obvykle třída odvozená z `CDialog`), přidat mapu zpráv položku a obslužná rutina zprávy členskou funkci na nadřazené třídu pro každou zprávu.  
  
 Každá položka mapování zpráv má následující podobu:  
  
 **ON_** oznámení **(**`id`**,**`memberFxn`**)**  
  
 kde `id` Určuje ID podřízeného okna ovládacího prvku pole se seznamem zasílání oznámení a `memberFxn` je název nadřazené členské funkce mají napsané tak, aby oznámení.  
  
 Prototyp funkce nadřazeného objektu je následujícím způsobem:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Pořadí, ve kterém se budou odesílat určité oznámení nemůže být předpovězen. Zejména CBN_SELCHANGE oznámení může dojít před nebo po CBN_CLOSEUP oznámení.  
  
 Potenciální položky mapování zpráv jsou následující:  
  
- ON_CBN_CLOSEUP (Windows 3.1 nebo novější.) Seznam pole se seznamem byl uzavřen. Tato oznámení neodešle pole se seznamem, který má [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
- ON_CBN_DBLCLK uživatel dvakrát klikne řetězec v seznamu pole se seznamem. Tato oznámení se odesílají pouze pro pole se seznamem se stylem CBS_SIMPLE. Pro pole se seznamem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, poklepání nelze provést, protože jedním kliknutím skryjete pole se seznamem.  
  
- Seznam pole se seznamem je rozevírací seznam ON_CBN_DROPDOWN (nastavena jako viditelná). Tato oznámení může dojít pouze pro pole se seznamem se stylem CBS_DROPDOWN nebo CBS_DROPDOWNLIST.  
  
- ON_CBN_EDITCHANGE uživatel má provést akce, která mohou být ovlivněny text v textové pole část pole se seznamem. Tato zpráva se pošle na rozdíl od CBN_EDITUPDATE zprávu po dokončení aktualizace Windows na obrazovce. Pokud má pole se seznamem styl CBS_DROPDOWNLIST neodesílají.  
  
- ON_CBN_EDITUPDATE textové pole část pole se seznamem připravuje se text zobrazení změnit. Tato zpráva oznámení se pošle po ovládací prvek má formátovaný text, ale před zobrazí text. Pokud má pole se seznamem styl CBS_DROPDOWNLIST neodesílají.  
  
- ON_CBN_ERRSPACE pole se seznamem nemůže přidělit dostatek paměti k uspokojení konkrétní žádost.  
  
- ON_CBN_SELENDCANCEL (Windows 3.1 nebo novější.) Označuje, že by měl být zrušen uživatelem. Uživatel klikne na položku a poté klikne na tlačítko jiného okna nebo ovládací prvek skrýt seznam pole se seznamem. Tato zpráva oznámení se pošle před zprávy oznámení CBN_CLOSEUP označující, zda mají být ignorovány výběru uživatele. CBN_SELENDCANCEL nebo CBN_SELENDOK zprávy oznámení, přijde i v případě, že nejsou odesílány zprávy oznámení CBN_CLOSEUP (třeba v případě pole se seznamem se stylem CBS_SIMPLE).  
  
- ON_CBN_SELENDOK uživatel vybere položku a stiskne klávesu ENTER nebo kliknutím klávesu šipka dolů, chcete-li skrýt seznam pole se seznamem. Tato zpráva oznámení se pošle před CBN_CLOSEUP zpráva označující, že výběr uživatele by měly být považovány za platné. CBN_SELENDCANCEL nebo CBN_SELENDOK zprávy oznámení, přijde i v případě, že nejsou odesílány zprávy oznámení CBN_CLOSEUP (třeba v případě pole se seznamem se stylem CBS_SIMPLE).  
  
- ON_CBN_KILLFOCUS pole se seznamem je ztráta vstupního fokusu.  
  
- ON_CBN_SELCHANGE výběr v seznamu pole se seznamem je změnit v důsledku uživatel kliknutím na položku v seznamu nebo změní volbu pomocí kláves se šipkami. Při zpracování této zprávy, text v textovém poli pole se seznamem je možné načíst pouze prostřednictvím `GetLBText` nebo jiné podobné funkce. `GetWindowText` nelze použít.  
  
- Pole se seznamem ON_CBN_SETFOCUS nastaven vstupní fokus.  
  
 Pokud vytvoříte `CComboBox` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CComboBox` objekt je zničen automaticky, když uživatel zavře dialogové okno.  
  
 Vložíte-li `CComboBox` objekt v rámci jiného okna objektu, není potřeba ji odstranit. Pokud jste vytvořili `CComboBox` objekt v zásobníku, je automaticky zničen. Pokud jste vytvořili `CComboBox` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** na objekt, který chcete zničit ho při zničení pole se seznamem Windows.  
  
 **Poznámka:** Pokud chcete zpracovávat zprávy WM_KEYDOWN a z WM_CHAR, budete muset podtřídy pole se seznamem pro úpravy a seznamu ovládací prvky, odvozovat z `CEdit` a `CListBox`, a přidejte obslužné rutiny pro zprávy do odvozené třídy. Další informace najdete v tématu [ http://support.microsoft.com/default.aspxscid=kb; en-us; Q174667](http://support.microsoft.com/default.aspxscid=kb;en-us;q174667) a [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CComboBox`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="addstring"></a>  CComboBox::AddString  
 Přidá řetězec do seznamu pole se seznamem.  
  
```  
int AddString(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszString*  
 Odkazuje na řetězec zakončený hodnotou null, který se má přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud vrácená hodnota je větší než nebo rovno 0, je z nuly vycházející index na řetězec v poli seznamu. Vrácená hodnota je CB_ERR, pokud dojde k chybě; Vrácená hodnota je CB_ERRSPACE, pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole se seznamem nebylo vytvořeno pomocí [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, řetězec je přidán na konec seznamu. V opačném případě řetězec je vložen do seznamu a seznam je seřazen.  
  
> [!NOTE]
>  Tato funkce není podporována Windows `ComboBoxEx` ovládacího prvku. Další informace o tohoto ovládacího prvku, naleznete v tématu [ovládací prvky ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) v sadě Windows SDK.  
  
 Chcete-li vložit řetězec do určitého umístění v seznamu, použijte [InsertString](#insertstring) členskou funkci.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]  
  
##  <a name="ccombobox"></a>  CComboBox::CComboBox  
 Vytvoří `CComboBox` objektu.  
  
```  
CComboBox();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]  
  
##  <a name="clear"></a>  CComboBox::Clear  
 Odstraní (vymaže) aktuální výběr, pokud existuje, v textovém poli seznamem.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li odstranit aktuální výběr a umístí odstranil obsah do schránky, použijte [Vyjmout](#cut) členskou funkci.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]  
  
##  <a name="compareitem"></a>  CComboBox::CompareItem  
 Volá se rozhraním pro určení relativní pozice nové položky pole se seznamem část pole se seznamem seřazený vykreslené vlastníkem.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpCompareItemStruct*  
 Dlouhým ukazatelem na [compareitemstruct –](../../mfc/reference/compareitemstruct-structure.md) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Označuje relativní polohu dvě položky podle `COMPAREITEMSTRUCT` struktury. Může být některý z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|- 1|Položka 1 se řadí před položkou 2.|  
|0|Položka 1 a položka 2 seřadí hodnoty stejné.|  
|1|Položka 1 se řadí po položce 2.|  
  
 Zobrazit [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) popis `COMPAREITEMSTRUCT`.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce ve výchozím nastavení nemá žádný účinek. Pokud jste do pole se seznamem vykreslené vlastníkem stylem LBS_SORT, je nutné přepsat tato členská funkce, které pomáhají rozhraní framework při řazení nové položky přidané do seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]  
  
##  <a name="copy"></a>  CComboBox::Copy  
 Zkopíruje aktuální výběr, pokud existuje, v textovém poli do schránky ve formátu CF_TEXT pole se seznamem.  
  
```  
void Copy();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]  
  
##  <a name="create"></a>  CComboBox::Create  
 Vytvoří pole se seznamem a připojí ho k `CComboBox` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Určuje styl pole se seznamem. Použít libovolnou kombinaci [pole se seznamem stylů](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) do pole.  
  
 *Rect*  
 Odkazuje na umístění a velikost pole se seznamem. Může být [Rect – struktura](../../mfc/reference/rect-structure1.md) nebo `CRect` objektu.  
  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku pole se seznamem (obvykle `CDialog`). Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládacího prvku pole se seznamem  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CComboBox` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, který vytvoří pole se seznamem Windows a připojí ho k `CComboBox` objektu.  
  
 Když `Create` spustí, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy do pole se seznamem.  
  
 Tyto zprávy jsou zpracovány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Pokud chcete rozšířit výchozí zpracování zpráv, odvoďte třídu z `CComboBox`, přidání mapy zpráv do nové třídy a přepsat předchozí členské funkce obslužná rutina zprávy. Přepsat `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku pole se seznamem. :  
  
- WS_CHILD vždy  
  
- WS_VISIBLE obvykle  
  
- WS_DISABLED jen zřídka  
  
- WS_VSCROLL k přidání svislé posouvání pro pole se seznamem v poli se seznamem  
  
- WS_HSCROLL chcete přidat, vodorovné posouvání pro pole se seznamem v poli se seznamem  
  
- WS_GROUP k seskupování ovládacích prvků  
  
- WS_TABSTOP pole se seznamem v obsahovat pořadí procházení  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]  
  
##  <a name="cut"></a>  CComboBox::Cut  
 Odstraní (kusů) aktuální výběr, pokud existuje, v poli se seznamem upravit ovládací prvek a zkopíruje ve formátu CF_TEXT odstraněný text do schránky.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li odstranit aktuální výběr bez uvedení odstraněný text do schránky, zavolejte [vymazat](#clear) členskou funkci.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]  
  
##  <a name="deleteitem"></a>  CComboBox::DeleteItem  
 Volá se rozhraním, když uživatel odstraní položku ze vykreslené vlastníkem `CComboBox` objektu nebo odstraní pole se seznamem.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDeleteItemStruct*  
 Dlouhým ukazatelem na Windows [deleteitemstruct –](../../mfc/reference/deleteitemstruct-structure.md) strukturu, která obsahuje informace o odstraněné položky. Zobrazit [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) popis této struktury.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce nemá žádný účinek. Přepsání této funkce můžete podle potřeby ho překreslit pole se seznamem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]  
  
##  <a name="deletestring"></a>  CComboBox::DeleteString  
 Odstraní položku na pozici *nIndex* v poli se seznamem.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Určuje index na řetězec, který má být odstraněn.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud vrácená hodnota je větší než nebo rovno 0, je počet zbývajících v seznamu řetězců. Vrácená hodnota je CB_ERR Pokud *nIndex* Určuje index větší než počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny položky následující *nIndex* teď přejít o jednu pozici dolů. Například pokud pole se seznamem obsahuje dvě položky, odstranění první položky způsobí zbývající položky, která má být nyní na první pozici. *nIndex*= 0 pro položku na první pozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]  
  
##  <a name="dir"></a>  CComboBox::Dir  
 Seznam názvů souborů nebo jednotky přidá do seznamu pole se seznamem.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parametry  
 *attr*  
 Může být libovolná kombinace **výčtu** podle hodnoty [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) nebo libovolnou kombinaci následujícího:  
  
- Soubor DDL_READWRITE může číst nebo zapisovat do.  
  
- Soubor DDL_READONLY můžete číst z ale nezapíše se do.  
  
- Soubor DDL_HIDDEN je skrytá a se nezobrazí v seznamu adresářů.  
  
- Soubor DDL_SYSTEM je systémový soubor.  
  
- DDL_DIRECTORY určeného parametrem *lpszWildCard* Určuje adresář.  
  
- Soubor DDL_ARCHIVE byl archivován.  
  
- DDL_DRIVES zahrnout všechny jednotky, které odpovídají názvu určeného *lpszWildCard*.  
  
- Příznak DDL_EXCLUSIVE Exclusive. Pokud je nastavený příznak exclusive, jsou uvedeny pouze soubory zadaného typu. Jinak jsou kromě "normální" soubory uvedené soubory zadaného typu.  
  
 *lpszWildCard*  
 Odkazuje na řetězec specifikace souboru. Řetězec může obsahovat zástupné znaky (například *.\*).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud vrácená hodnota je větší než nebo rovno 0, je index založený na nule poslední název souboru přidán do seznamu. Vrácená hodnota je CB_ERR, pokud dojde k chybě; Vrácená hodnota je CB_ERRSPACE, pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce není podporována Windows `ComboBoxEx` ovládacího prvku. Další informace o tohoto ovládacího prvku, naleznete v tématu [ovládací prvky ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]  
  
##  <a name="drawitem"></a>  CComboBox::DrawItem  
 Volá se rozhraním při úpravě vizuálního aspektu změny pole – pole se seznamem vykreslené vlastníkem.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpDrawItemStruct*  
 Ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) strukturu, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 `itemAction` Člena `DRAWITEMSTRUCT` struktury definuje výkresu akci, která se má provést. Zobrazit [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis této struktury.  
  
 Tato členská funkce ve výchozím nastavení nemá žádný účinek. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CComboBox` objektu. Předtím, než skončí tato členská funkce, aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct*.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]  
  
##  <a name="findstring"></a>  CComboBox::FindString  
 Najde, ale není vybrán první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nStartAfter*  
 Obsahuje položku před první položky, které chcete prohledat index založený na nule. Dolní části seznamu dosáhne hledání pokračuje od horního okraje pole se seznamem zpět položku určenou na základě *nStartAfter*. Pokud hodnotu-1, je prohledána celý seznam od začátku.  
  
 *lpszString*  
 Odkazuje na řetězec zakončený hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Vyhledávání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud vrácená hodnota je větší než nebo rovno 0, je index založený na nule odpovídající položka. Je CB_ERR vyhledávání nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce není podporována Windows `ComboBoxEx` ovládacího prvku. Další informace o tohoto ovládacího prvku, naleznete v tématu [ovládací prvky ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]  
  
##  <a name="findstringexact"></a>  CComboBox::FindStringExact  
 Volání `FindStringExact` členskou funkci Najít první řetězec pole se seznamem (v poli se seznamem), který odpovídá řetězci zadanému v *lpszFind*.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndexStart*  
 Určuje index založený na nule položku před první položky, které chcete prohledat. Dolní části seznamu dosáhne hledání pokračuje od horního okraje pole se seznamem zpět položku určenou na základě *nIndexStart*. Pokud *nIndexStart* se -1, je prohledána celý seznam od začátku.  
  
 *lpszFind*  
 Odkazuje na hledaný řetězec zakončený hodnotou null. Tento řetězec může obsahovat úplný název souboru, včetně přípony. Hledání není velká a malá písmena, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule odpovídající položka nebo CB_ERR Pokud vyhledávání nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se pole se seznamem vytvořil stylem vykreslené vlastníkem. ale bez [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, `FindStringExact` porovnává hodnotu doubleword proti hodnotě *lpszFind*.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]  
  
##  <a name="getcomboboxinfo"></a>  CComboBox::GetComboBoxInfo  
 Načte informace o `CComboBox` objektu.  
  
```  
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pcbi*  
 Ukazatel [COMBOBOXINFO](/windows/desktop/api/winuser/ns-winuser-tagcomboboxinfo) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce emuluje funkčnost [CB_GETCOMBOBOXINFO](/windows/desktop/Controls/cb-getcomboboxinfo) zprávu, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getcount"></a>  CComboBox::GetCount  
 Voláním této členské funkce se načíst počet položek v seznamu. část pole se seznamem.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek. Vrácený počet je větší než hodnota indexu na poslední položku (index je založený na nule). Jedná se CB_ERR, pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]  
  
##  <a name="getcuebanner"></a>  CComboBox::GetCueBanner  
 Získá startovací text, který se zobrazí pro ovládací prvek pole se seznamem.  
  
```  
CString GetCueBanner() const;  
  
BOOL GetCueBanner(
    LPTSTR lpszText,   
    int cchText) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] *lpszText*|Ukazatel do vyrovnávací paměti, která bude přijímat upozornění text nápisu.|  
|[in] *cchText*|Velikost vyrovnávací paměti, *lpszText* parametr odkazuje na.|  
  
### <a name="return-value"></a>Návratová hodnota  
 V první přetížení [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obsahuje text nápisu upozornění, pokud existuje; v opačném případě `CString` objekt, který má nulovou délku.  
  
 -nebo-  
  
 V druhé přetížení je hodnota TRUE, pokud metoda úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Text upozornění je řádku, který se zobrazí v oblasti vstupního ovládacího prvku pole se seznamem. Text upozornění se nezobrazí, dokud uživatel poskytne vstup.  
  
 Tato metoda odesílá [CB_GETCUEBANNER](/windows/desktop/Controls/cb-getcuebanner) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="getcursel"></a>  CComboBox::GetCurSel  
 Voláním této členské funkce k určení, která položka v seznamu je vybrána.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule aktuálně vybrané položky v seznamu pole se seznamem nebo CB_ERR, pokud není vybrána žádná položka.  
  
### <a name="remarks"></a>Poznámky  
 `GetCurSel` Vrátí index do seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]  
  
##  <a name="getdroppedcontrolrect"></a>  CComboBox::GetDroppedControlRect  
 Volání `GetDroppedControlRect` členské funkce lze získat souřadnice obrazovky viditelné (vyřadit dolů) seznamu rozevíracím seznamem.  
  
```  
void GetDroppedControlRect(LPRECT lprect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprect –*  
 Odkazuje [Rect – struktura](../../mfc/reference/rect-structure1.md) , která má obdržet souřadnice.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]  
  
##  <a name="getdroppedstate"></a>  CComboBox::GetDroppedState  
 Volání `GetDroppedState` členskou funkci k určení, zda pole se seznamem rozevíracím seznamem je viditelné (rozbalil).  
  
```  
BOOL GetDroppedState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je viditelný; pole se seznamem jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]  
  
##  <a name="getdroppedwidth"></a>  CComboBox::GetDroppedWidth  
 Voláním této funkce načtete šířku v pixelech, seznamu pole se seznamem minimální povolená.  
  
```  
int GetDroppedWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu, minimální povolená šířka v pixelech; v opačném případě CB_ERR.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce platí jenom pro pole se seznamem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
 Ve výchozím nastavení je povolený minimální šířku pole rozevíracího seznamu 0. Minimální šířka povolená lze nastavit pomocí volání [SetDroppedWidth](#setdroppedwidth). Když je zobrazena část pole se seznamem pole se seznamem, jeho šířka byla větší minimální šířka povolená nebo šířka pole se seznamem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [SetDroppedWidth](#setdroppedwidth).  
  
##  <a name="geteditsel"></a>  CComboBox::GetEditSel  
 Získá počáteční a koncová pozice znaku aktuálního výběru v textovém poli se seznamem.  
  
```  
DWORD GetEditSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 32bitová hodnota, která obsahuje počáteční pozice v nižší řád slova a pozice prvního znaku nevybrané za koncem výběr v vyšší řád slova. Pokud tato funkce je použit na pole se seznamem bez ovládacího prvku pro úpravy, je vrácena CB_ERR.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]  
  
##  <a name="getextendedui"></a>  CComboBox::GetExtendedUI  
 Volání `GetExtendedUI` členská funkce slouží k určení, zda má pole se seznamem výchozí uživatelské rozhraní nebo rozšířené uživatelského rozhraní.  
  
```  
BOOL GetExtendedUI() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud má rozšířené uživatelského rozhraní; pole se seznamem jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozšířené uživatelského rozhraní lze identifikovat následujícími způsoby:  
  
-   Kliknutím na statický ovládací prvek zobrazí pole se seznamem pouze pro pole se seznamem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
-   Klávesy Šipka dolů zobrazí pole se seznamem (F4 je zakázáno).  
  
 Posouvání v statický ovládací prvek je zakázáno, pokud seznam položek není viditelné (šipka klíče jsou zakázané).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]  
  
##  <a name="gethorizontalextent"></a>  CComboBox::GetHorizontalExtent  
 Načte z pole se seznamem šířku v pixelech, podle kterých pole se seznamem část pole se seznamem lze seznam vodorovně posunout.  
  
```  
UINT GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posuvný šířka pole se seznamem část pole se seznamem v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 To platí jenom v případě, že pole se seznamem část pole se seznamem má vodorovný posuvník.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]  
  
##  <a name="getitemdata"></a>  CComboBox::GetItemData  
 Načte 32bitovou hodnotu poskytované aplikací přidružených k položce zadané pole se seznamem.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Z nuly vycházející index položky v seznamu pole se seznamem obsahuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 32bitová hodnota přidružené položky nebo CB_ERR, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Lze nastavit hodnotu 32-bit *dwItemData* parametr [setitemdata –](#setitemdata) volání členské funkce. Použití `GetItemDataPtr` členskou funkci, pokud je 32bitová hodnota, která se má načíst ukazatel (**void** <strong>\*</strong>).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]  
  
##  <a name="getitemdataptr"></a>  CComboBox::GetItemDataPtr  
 Načte 32bitovou hodnotu poskytované aplikací přidružených k položce zadané pole se seznamem jako ukazatel (**void** <strong>\*</strong>).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Z nuly vycházející index položky v seznamu pole se seznamem obsahuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte ukazatel nebo -1, pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]  
  
##  <a name="getitemheight"></a>  CComboBox::GetItemHeight  
 Volání `GetItemHeight` členské funkce lze získat výšku položky seznamu v poli se seznamem.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Určuje komponentu pole se seznamem, jejichž výška má být načtena. Pokud *nIndex* -1 je parametr, Výška textové pole (nebo statický text) část pole se seznamem se načítají. Pokud má pole se seznamem [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, *nIndex* určuje z nuly vycházející index položky seznamu, jehož výška má být načtena. V opačném případě *nIndex* by měla být nastavena na hodnotu 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech, že zadaná položka v poli se seznamem. Vrácená hodnota je CB_ERR, pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]  
  
##  <a name="getlbtext"></a>  CComboBox::GetLBText  
 Získá řetězec ze seznamu pole se seznamem.  
  
```  
int GetLBText(
    int nIndex,  
    LPTSTR lpszText) const;  
  
void GetLBText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Obsahuje index založený na nule pole se seznamem řetězec, který má být zkopírován.  
  
 *lpszText*  
 Body do vyrovnávací paměti, která se zobrazí řetězec. Vyrovnávací paměť musí mít dostatek místa pro řetězce a ukončujícího znaku null.  
  
 *rString*  
 Odkaz na `CString`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce, s výjimkou ukončujícího znaku null (v bajtech). Pokud *nIndex* neurčuje platný index, vrácená hodnota je CB_ERR.  
  
### <a name="remarks"></a>Poznámky  
 Tedy o druhou podobu této členské funkce výplně `CString` objekt s text položky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]  
  
##  <a name="getlbtextlen"></a>  CComboBox::GetLBTextLen  
 Získá délku řetězce v seznamu pole se seznamem.  
  
```  
int GetLBTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Obsahuje index založený na nule řetězcového pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce v bajtech, bez ukončujícího znaku null. Pokud *nIndex* neurčuje platný index, vrácená hodnota je CB_ERR.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetLBText](#getlbtext).  
  
##  <a name="getlocale"></a>  CComboBox::GetLocale  
 Načte národního prostředí používaného pole se seznamem.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota identifikátoru LCID národního prostředí pro řetězce v poli se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Národní prostředí, které se používá, například k určení pořadí řazení řetězců v seřazeném pole se seznamem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::SetLocale](#setlocale).  
  
##  <a name="getminvisible"></a>  CComboBox::GetMinVisible  
 Získá minimální počet viditelných položek v rozevíracím seznamu aktuální prvek pole se seznamem.  
  
```  
int GetMinVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minimální počet viditelných položek v seznamu aktuální rozevíracího seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [CB_GETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="gettopindex"></a>  CComboBox::GetTopIndex  
 Načte z nuly vycházející index první viditelné položky v seznamu. část pole se seznamem.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Z nuly vycházející index první viditelné položky v seznamu. část pole se seznamem, pokud je úspěšná, jinak CB_ERR.  
  
### <a name="remarks"></a>Poznámky  
 Na začátku položka 0 je v horní části seznamu, ale pokud je pole se seznamem posunul, jiná položka může být v horní části.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]  
  
##  <a name="initstorage"></a>  CComboBox::InitStorage  
 Přiděluje paměť pro ukládání seznam položek pole v seznamu. část pole se seznamem.  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *nItems*  
 Určuje počet položek, které chcete přidat.  
  
 *nBytes*  
 Určuje velikost paměti, v bajtech pro přidělení pro položku řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, maximální počet položek, které pole se seznamem část pole se seznamem můžete uložit před realokace paměti je zapotřebí, jinak CB_ERRSPACE, není to znamená, je k dispozici dostatek paměti.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této funkce před přidáním velký počet položek na část pole se seznamem `CComboBox`.  
  
 Windows 95/98 pouze: *wParam* je omezená na 16bitové hodnoty parametru. To znamená, že pole se seznamem nemůže obsahovat více než 32 767 položky. I když je počet položek, které s omezeným přístupem, celková velikost položky v seznamu je omezen pouze dostupnou paměť.  
  
 Tato funkce pomáhá zrychlit inicializace pole se seznamem, které mají velký počet položek (více než 100). Preallocates zadaného množství paměti, takže to následné [addstring –](#addstring), [InsertString](#insertstring), a [Dir](#dir) funkce přijímají nejkratší možné době. Odhad můžete použít pro parametry. Pokud jste overestimate, je přidělen některé další paměť. Pokud jste příliš nízko, normální rozdělení se používá pro položky, které překračují předběžně přidělená velikost.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]  
  
##  <a name="insertstring"></a>  CComboBox::InsertString  
 Řetězec se vloží do seznamu pole se seznamem.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Index o základu 0 na pozici v seznamu, který bude příjemcem řetězec obsahuje. Pokud tento parametr hodnotu -1, řetězec je přidána na konec seznamu.  
  
 *lpszString*  
 Odkazuje na řetězec zakončený hodnotou null, který má být vložen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Z nuly vycházející index pozice vložený řetězec. Vrácená hodnota je CB_ERR, pokud dojde k chybě. Vrácená hodnota je CB_ERRSPACE, pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [addstring –](#addstring) členskou funkci `InsertString` členskou funkci nezpůsobí seznam [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, který se má seřadit.  
  
> [!NOTE]
>  Tato funkce není podporována Windows `ComboBoxEx` ovládacího prvku. Další informace o tohoto ovládacího prvku, naleznete v tématu [ovládací prvky ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]  
  
##  <a name="limittext"></a>  CComboBox::LimitText  
 Omezí délku v bajtech text, který může uživatel zadat do ovládacího prvku pro úpravy pole se seznamem.  
  
```  
BOOL LimitText(int nMaxChars);
```  
  
### <a name="parameters"></a>Parametry  
 *nMaxChars*  
 Určuje délku (v bajtech), který může uživatel zadat text. Pokud má parametr hodnotu 0, délka textu je nastavena na 65 535 bajtů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. Pokud je volána pro pole se seznamem se stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo pro pole se seznamem bez ovládacího prvku pro úpravy, vrácená hodnota je CB_ERR.  
  
### <a name="remarks"></a>Poznámky  
 Pokud styl neobsahuje žádná pole se seznamem [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), limit textu větší než velikost ovládacích prvků pro úpravy nastavení nebude mít žádný efekt.  
  
 `LimitText` omezuje pouze text, který může uživatel zadat. Nemá žádný vliv na žádný text již v textovém poli při je zpráva odeslána ani nemá vliv délka textu zkopírován do ovládacího prvku pro úpravy, pokud řetězec v seznamu je vybrána.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]  
  
##  <a name="measureitem"></a>  CComboBox::MeasureItem  
 Volá se rozhraním, když se vytvoří pole se seznamem stylem vykreslené vlastníkem.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMeasureItemStruct*  
 Dlouhým ukazatelem na [measureitemstruct –](../../mfc/reference/measureitemstruct-structure.md) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce ve výchozím nastavení nemá žádný účinek. Tato členská funkce přepsání a vyplňte `MEASUREITEMSTRUCT` struktura informovat Windows dimenzí v seznamu pole se seznamem. Pokud pole se seznamem se vytvoří s [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, rozhraní volá tuto funkci člena pro každou položku v seznamu. V opačném případě tento člen je volána pouze jednou.  
  
 Použije styl CBS_OWNERDRAWFIXED do pole se seznamem vykreslené vlastníkem. vytvoří se [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) členskou funkci `CWnd` zahrnuje další programovací aspekty. Viz diskuze v [Technická poznámka 14](../../mfc/tn014-custom-controls.md).  
  
 Zobrazit [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) popis `MEASUREITEMSTRUCT` struktury.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]  
  
##  <a name="paste"></a>  CComboBox::Paste  
 Vloží data ze schránky do ovládacího prvku pro úpravy pole se seznamem na aktuální pozici kurzoru.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Poznámky  
 Data budou vložena pouze v případě, že obsahuje data ve formátu CF_TEXT do schránky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]  
  
##  <a name="resetcontent"></a>  CComboBox::ResetContent  
 Odebere všechny položky v seznamu pole a upravit ovládací prvek pole se seznamem.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]  
  
##  <a name="selectstring"></a>  CComboBox::SelectString  
 Vyhledá řetězec v seznamu pole se seznamem a pokud se řetězec najde, vybere řetězec v seznamu a zkopíruje se do ovládacího prvku pro úpravy.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 *nStartAfter*  
 Obsahuje položku před první položky, které chcete prohledat index založený na nule. Dolní části seznamu dosáhne hledání pokračuje od horního okraje pole se seznamem zpět položku určenou na základě *nStartAfter*. Pokud hodnotu-1, je prohledána celý seznam od začátku.  
  
 *lpszString*  
 Odkazuje na řetězec zakončený hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Vyhledávání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule vybranou položku, pokud byl nalezen řetězec. Pokud se vyhledávání nebylo úspěšné, vrácená hodnota je CB_ERR a se změní aktuální výběr.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec je vybrána pouze v případě, že jeho počáteční znaky (od počátečního bodu) odpovídat znakům v řetězci předpony.  
  
 Všimněte si, že `SelectString` a `FindString` členské funkce najít řetězce, ale `SelectString` členské funkce také vybere řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]  
  
##  <a name="setcuebanner"></a>  CComboBox::SetCueBanner  
 Nastaví startovací text, který se zobrazí u ovládacího prvku pole se seznamem.  
  
```  
BOOL SetCueBanner(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] *lpszText*|Ukazatel na vyrovnávací paměť zakončená hodnotou null, obsahující text upozornění.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je metoda úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Text upozornění je řádku, který se zobrazí v oblasti vstupního ovládacího prvku pole se seznamem. Text upozornění se nezobrazí, dokud uživatel poskytne vstup.  
  
 Tato metoda odesílá [CB_SETCUEBANNER](/windows/desktop/Controls/cb-setcuebanner) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, *m_combobox*, která je použita k programovému přístupu ke prvek pole se seznamem. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví startovací banner pro ovládací prvek pole se seznamem.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="setcursel"></a>  CComboBox::SetCurSel  
 Vybere řetězec v seznamu pole se seznamem.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parametry  
 *nVyberte*  
 Určuje řetězec, který má vyberte index založený na nule. -1, pokud se odebere všechny aktuální výběr v seznamu a vymaže ovládací prvek pro úpravy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule položka vybrána, pokud zpráva je úspěšné. Vrácená hodnota je CB_ERR Pokud *nVyberte* je větší než počet položek v seznamu nebo, pokud *nVyberte* je nastavena na hodnotu -1, který vymaže výběr.  
  
### <a name="remarks"></a>Poznámky  
 V případě potřeby pole se seznamem (Pokud je pole se seznamem viditelné) posouvá řetězec do zobrazení. Text v textovém poli pole se seznamem se změní tak, aby odrážely nový výběr. Odeberou se všechny předchozí výběr v seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]  
  
##  <a name="setdroppedwidth"></a>  CComboBox::SetDroppedWidth  
 Voláním této funkce nastavit minimální povolená šířka v pixelech, seznamu pole se seznamem.  
  
```  
int SetDroppedWidth(UINT nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *nWidth*  
 Minimální povolená šířka pole se seznamem část pole se seznamem v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ověření novou šířku pole seznamu, jinak CB_ERR.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce platí jenom pro pole se seznamem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
 Ve výchozím nastavení je povolený minimální šířku pole rozevíracího seznamu 0. Když je zobrazena část pole se seznamem pole se seznamem, jeho šířka byla větší minimální šířka povolená nebo šířka pole se seznamem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]  
  
##  <a name="seteditsel"></a>  CComboBox::SetEditSel  
 Vybere znaků v textovém poli se seznamem.  
  
```  
BOOL SetEditSel(
    int nStartChar,  
    int nEndChar);
```  
  
### <a name="parameters"></a>Parametry  
 *nStartChar*  
 Určuje počáteční pozici. Pokud počáteční pozice je nastavena na hodnotu -1, se odebere všechny existující výběru.  
  
 *nEndChar*  
 Určuje koncovou pozici. Pokud koncovou pozici je nastavena na hodnotu -1, pak veškerého textu od počáteční pozice na poslední znak v textovém poli se vybere.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je členská funkce úspěšná. jinak 0. Pokud je CB_ERR `CComboBox` má [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu nebo nemá žádné pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Pozice jsou počítány od nuly. Pokud chcete vybrat první znak ovládacího prvku pro úpravy, zadáte počáteční pozici 0. Koncová pozice je pro znak bezprostředně po poslední znak k výběru. Například pokud chcete vybrat první čtyři znaky ovládacích prvků pro úpravy, můžete využít počáteční pozice 0 a koncovou pozici 4.  
  
> [!NOTE]
>  Tato funkce není podporována Windows `ComboBoxEx` ovládacího prvku. Další informace o tohoto ovládacího prvku, naleznete v tématu [ovládací prvky ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetEditSel](#geteditsel).  
  
##  <a name="setextendedui"></a>  CComboBox::SetExtendedUI  
 Volání `SetExtendedUI` členské funkce a vyberte výchozí uživatelské rozhraní nebo rozšířené uživatelského rozhraní pro pole se seznamem, který má [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
```  
int SetExtendedUI(BOOL bExtended = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bExtended*  
 Určuje, zda by měl pole se seznamem používat rozšířené uživatelského rozhraní nebo výchozí uživatelské rozhraní. Hodnota TRUE vybere rozšířené uživatelského rozhraní; hodnota FALSE, vybere se standardní uživatelské rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 CB_OKAY, pokud je operace úspěšná, nebo CB_ERR, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Rozšířené uživatelského rozhraní lze identifikovat následujícími způsoby:  
  
-   Kliknutím na statický ovládací prvek zobrazuje pouze pro pole se seznamem se stylem CBS_DROPDOWNLIST pole se seznamem.  
  
-   Klávesy Šipka dolů zobrazí pole se seznamem (F4 je zakázáno).  
  
 Posouvání v statický ovládací prvek je zakázáno, pokud není zobrazen seznam položek (klávesy se šipkami jsou zakázány).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetExtendedUI](#getextendedui).  
  
##  <a name="sethorizontalextent"></a>  CComboBox::SetHorizontalExtent  
 Nastaví šířku v pixelech, podle kterých pole se seznamem část pole se seznamem lze seznam vodorovně posunout.  
  
```  
void SetHorizontalExtent(UINT nExtent);
```  
  
### <a name="parameters"></a>Parametry  
 *nExtent*  
 Určuje počet pixelů, podle kterých pole se seznamem část pole se seznamem lze seznam vodorovně posunout.  
  
### <a name="remarks"></a>Poznámky  
 Pokud šířka pole se seznamem je menší než tato hodnota, bude vodorovný posuvník vodorovně posouvat položky v seznamu. Pokud šířka pole se seznamem je roven nebo větší než tato hodnota, je skrytá vodorovný posuvník nebo, pokud má pole se seznamem [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, zakázané.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]  
  
##  <a name="setitemdata"></a>  CComboBox::SetItemData  
 Nastaví hodnotu 32-bit přidruženou k zadané položky pole se seznamem.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Z nuly vycházející index položky k nastavení obsahuje.  
  
 *dwItemData*  
 Obsahuje novou hodnotu pro přidružení k položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 CB_ERR, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Použití `SetItemDataPtr` členskou funkci, pokud je položka 32-bit jako ukazatel.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]  
  
##  <a name="setitemdataptr"></a>  CComboBox::SetItemDataPtr  
 Nastaví hodnotu 32-bit přidruženou k zadané položky pole se seznamem být zadaný ukazatel (**void** <strong>\*</strong>).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Obsahuje index počítaný od nuly k položce.  
  
 *pData*  
 Obsahuje ukazatel na přidružit k položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 CB_ERR, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 This – ukazatel zůstane platný po celou dobu životnosti pole se seznamem i v případě, že položky relativní pozici v rámci pole se seznamem může změnit, protože položky jsou přidány nebo odebrány. Proto můžete změnit index položky v poli, ale ukazatel zůstane spolehlivé.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]  
  
##  <a name="setitemheight"></a>  CComboBox::SetItemHeight  
 Volání `SetItemHeight` členskou funkci nastavit výšku položky seznamu v poli se seznamem nebo výška textové pole (nebo statický text) část pole se seznamem.  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Určuje, zda je nastaven výšku položky seznamu nebo výšku ovládacího prvku úpravy (nebo statický text) část pole se seznamem.  
  
 Pokud má pole se seznamem [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, *nIndex* z nuly vycházející index položky seznamu, jehož výška bude potřeba nastavit; v opačném případě určuje *nIndex* musí být 0. a nastaví se výška všech položek seznamu.  
  
 Pokud *nIndex* se -1, výška ovládacího prvku pro úpravy nebo má být nastavena statická textovou část pole se seznamem.  
  
 *cyItemHeight*  
 Určuje výšku v pixelech, pole se seznamem komponenty identifikovaný *nIndex*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je index nebo výška je neplatný; CB_ERR jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výška ovládacího prvku úpravy (nebo statický text) část pole se seznamem nastavená nezávisle na výšku položky seznamu. Aplikace musíte zajistit, výška část textové pole (nebo statický text) není menší než výška položky konkrétního seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]  
  
##  <a name="setlocale"></a>  CComboBox::SetLocale  
 Nastaví identifikátor národního prostředí pro toto pole se seznamem.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parametry  
 *nNewLocale*  
 Nová hodnota národního prostředí identifikátor (LCID) pro pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnota identifikátoru LCID národního prostředí pro toto pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `SetLocale` nevolá výchozí národní prostředí je získané ze systému. Tento výchozí národní prostředí systému lze upravit pomocí ovládacích panelů aplikace místní (nebo mezinárodní).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]  
  
##  <a name="setminvisibleitems"></a>  CComboBox::SetMinVisibleItems  
 Nastaví minimální počet viditelných položek v rozevíracím seznamu aktuální – pole se seznamem ovládací prvek pole.  
  
```  
BOOL SetMinVisibleItems(int iMinVisible);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[in] *iMinVisible*|Určuje minimální počet viditelných položek.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [CB_SETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, *m_combobox*, která je použita k programovému přístupu ke prvek pole se seznamem. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu vloží 20 položek do rozevíracího seznamu ovládacího prvku pole se seznamem. Pak určuje, že minimálně 10 položek zobrazí, když uživatel stiskne klávesu na šipku rozevíracího seznamu.  
  
 [!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]  
  
##  <a name="settopindex"></a>  CComboBox::SetTopIndex  
 Zajišťuje, že je zobrazená v seznamu. část pole se seznamem určité položky.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Určuje index založený na nule položky pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, nebo CB_ERR, pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Systém posune pole se seznamem do položku určenou na základě *nIndex* se zobrazí v horní části seznamu bylo dosaženo maximální posuvníku rozsahu nebo pole.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]  
  
##  <a name="showdropdown"></a>  CComboBox::ShowDropDown  
 Zobrazí nebo skryje seznam pole se seznamem, který má [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
```  
void ShowDropDown(BOOL bShowIt = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShowIt*  
 Určuje, zda pole rozevíracího seznamu zobrazen nebo skryt. Hodnota TRUE zobrazí pole se seznamem. Hodnota FALSE skryje pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude pole se seznamem tohoto stylu zobrazit pole se seznamem.  
  
 Tato členská funkce nemá žádný vliv na vytvořené pomocí pole se seznamem [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) style.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CComboBox::GetDroppedState](#getdroppedstate).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [Cedit – třída](../../mfc/reference/cedit-class.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [Cscrollbar – třída](../../mfc/reference/cscrollbar-class.md)   
 [Cstatic – třída](../../mfc/reference/cstatic-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
