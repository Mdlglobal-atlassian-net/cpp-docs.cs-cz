---
title: "Třída CCheckListBox | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
dev_langs: C++
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fe432aec3a68889ad70ab7c229df3c2f7529df3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cchecklistbox-class"></a>CCheckListBox – třída
Poskytuje funkci Windows kontrolní seznam pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Vytvoří `CCheckListBox` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|Políčko kontrolního seznamu Windows vytvoří a připojí jej k `CCheckListBox` objektu.|  
|[CCheckListBox::DrawItem](#drawitem)|Voláno rámcem při visual aspekt vykreslování vlastníka seznamu se změní.|  
|[CCheckListBox::Enable](#enable)|Povolí nebo zakáže položku kontrolní seznam pole.|  
|[CCheckListBox::GetCheck](#getcheck)|Získá stav položky zaškrtávacího políčka.|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Získá styl ovládacího prvku zaškrtávacích políček.|  
|[CCheckListBox::IsEnabled](#isenabled)|Určuje, zda je povoleno položku.|  
|[CCheckListBox::MeasureItem](#measureitem)|Voláno rámcem, když je vytvořen seznam s styl vykreslování vlastníka.|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Voláno rámcem získat pozici položky zaškrtávací políčko.|  
|[CCheckListBox::SetCheck](#setcheck)|Nastaví stav položky zaškrtávací políčko.|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Nastavuje styl ovládacího prvku zaškrtávacích políček.|  
  
## <a name="remarks"></a>Poznámky  
 "Políčko kontrolního seznamu" zobrazí seznam položek, jako jsou názvy souborů. Každá položka v seznamu má zaškrtávací políčko vedle sebe, který uživatel může zaškrtněte nebo zrušte zaškrtnutí.  
  
 `CCheckListBox`je pouze pro ovládací prvky vykreslované uživatelem, protože seznam obsahuje více než textové řetězce. V nejjednodušším pole kontrolní seznam obsahuje textové řetězce a zaškrtávací políčka, ale není potřeba mít textu vůbec. Například můžete mít seznam malé bitmap s zaškrtávací políčko vedle každé položky.  
  
 Pokud chcete vytvořit vlastní pole kontrolní seznam, musí být vaše vlastní třídy z `CCheckListBox`. Vlastní třída odvozena zápis konstruktoru odvozené třídy, pak zavolají **vytvořit**.  
  
 Pokud chcete pro zpracování zpráv s oznámením Windows posílá nadřazené pole se seznamem (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte map zpráv položku a obslužné rutiny zpráv členské funkce do nadřazené třídy pro každou zprávu.  
  
 Každá položka mapování zpráv má následující podobu:  
  
 **ON_**oznámení **(**`id`, `memberFxn` **)**  
  
 kde `id` Určuje ID okno podřízeného prvku odesílání oznámení a `memberFxn` je název nadřazeného člena funkce napsané pro zpracování oznámení.  
  
 Prototyp funkce nadřazeného objektu je následující:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Existuje pouze jedna položka mapování zpráv, která se týkají konkrétně pro **CCheckListBox** (viz také položky mapy zpráv pro, ale [clistbox –](../../mfc/reference/clistbox-class.md)):  
  
- **ON_CLBN_CHKCHANGE** uživatele došlo ke změně stavu zaškrtávací políčko položce.  
  
 Pokud vaše políčko kontrolního seznamu výchozí kontrolní seznam pole (seznam řetězců s výchozí velikosti zaškrtávací políčka nalevo od jednotlivých), můžete použít výchozí [CCheckListBox::DrawItem](#drawitem) k vykreslení políčko kontrolního seznamu. Jinak je nutné přepsat [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) funkce a [CCheckListBox::DrawItem](#drawitem) a [CCheckListBox::MeasureItem](#measureitem) funkce.  
  
 Políčko kontrolního seznamu můžete vytvořit buď z šablony dialogového okna, nebo přímo v kódu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Clistbox –](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox  
 Vytvoří `CCheckListBox` objektu.  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CCheckListBox` objektu ve dvou krocích. Nejdříve definovat třídy odvozené od `CCheckListBox`, pak zavolají **vytvořit**, která inicializuje políčko kontrolního seznamu Windows a připojí jej k `CCheckListBox` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>CCheckListBox::Create  
 Políčko kontrolního seznamu Windows vytvoří a připojí jej k `CCheckListBox` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl políčko kontrolního seznamu. Musí být styl **lbs_hasstrings –** a buď **lbs_ownerdrawfixed –** (všechny položky v seznamu jsou stejné výšce) nebo **lbs_ownerdrawvariable –** (položky v seznamu jsou různé výšky). Tento styl zkombinovat s jinými [styly seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) s výjimkou **lbs_usetabstops –**.  
  
 `rect`  
 Určuje políčko kontrolního seznamu velikost a umístění. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](../../mfc/reference/rect-structure1.md) struktura.  
  
 `pParentWnd`  
 Určuje pole kontrolní seznam nadřazeného okna (obvykle `CDialog` objekt). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID políčko kontrolního seznamu ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CCheckListBox` objektu ve dvou krocích. Nejprve definovat třídy odvozené od **CcheckListBox** a pak zavolají **vytvořit**, která inicializuje políčko kontrolního seznamu Windows a připojí jej k `CCheckListBox`. V tématu [CCheckListBox::CCheckListBox](#cchecklistbox) pro ukázku.  
  
 Když **vytvořit** provede, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy do ovládacího prvku políčko kontrolního seznamu.  
  
 Tyto zprávy jsou zpracovávány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Rozšířit zpracování zpráv výchozí, přidejte mapování zpráv do odvozené třídě a členské funkce přepsání předchozí popisovač zpráv. Přepsání `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku pole kontrolní seznam:  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
- **Ws_vscroll –** přidat svislý posuvník  
  
- **Ws_hscroll –** přidat vodorovného posuvníku  
  
- **Ws_group –** k seskupování ovládacích prvků  
  
- **Ws_tabstop –** umožňující pomocí klávesy tabulátor do tohoto ovládacího prvku  
  
##  <a name="drawitem"></a>CCheckListBox::DrawItem  
 Voláno rámcem při řídit se změní vykreslovaných vlastníkem kontrolní seznam.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Dlouhé ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktura, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** a **itemState** členy `DRAWITEMSTRUCT` struktura definovat kreslení akci, která má být provedena.  
  
 Ve výchozím nastavení tato funkce nevykresluje výchozím seznamu zaškrtávací políčko, obsahující seznam řetězců s výchozí velikosti zaškrtávací políčko nalevo. Velikost seznamu zaškrtávací políčko je uvedené v [vytvořit](#create).  
  
 Člen funkci implementovat kreslení vykreslování vlastníka kontrolní seznam polí, které nejsou výchozí, jako je například kontrolní seznam polí se seznamy, které nejsou řetězce, Proměnná výška položky nebo s zaškrtávací políčka, která nejsou na levé straně přepište. Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před ukončení této funkce člen.  
  
 Pokud políčko položky kontrolního seznamu nejsou stejné výška, v seznamu úkolů pole styl (zadaný v **vytvořit**) musí být **LBS_OWNERVARIABLE**, a je nutné přepsat [measureitem –](#measureitem) funkce.  
  
##  <a name="enable"></a>CCheckListBox::Enable  
 Volání této funkce, které chcete povolit nebo zakázat položku kontrolní seznam pole.  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index položky pole kontrolní seznam povolení.  
  
 `bEnabled`  
 Určuje, zda je povoleno položky.  
  
##  <a name="getcheck"></a>CCheckListBox::GetCheck  
 Načte stav zadané políčko.  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index počítaný od nuly zaškrtávací políčko, které se nachází v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav zadaného políčko. Následující tabulka uvádí možné hodnoty.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`BST_CHECKED`|Zaškrtávací políčko je zaškrtnuto.|  
|`BST_UNCHECKED`|Není zaškrtnuté políčko.|  
|`BST_INDETERMINATE`|Je v neurčitém stavu zaškrtávací políčko.|  
  
##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle  
 Volání této funkce můžete získat styl políčko kontrolního seznamu.  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Styl ovládacího prvku zaškrtávacích políček.  
  
### <a name="remarks"></a>Poznámky  
 Informace o možných styly najdete v tématu [SetCheckStyle](#setcheckstyle).  
  
##  <a name="isenabled"></a>CCheckListBox::IsEnabled  
 Volání této funkce určete, zda je povoleno položku.  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka povolena; jinak 0.  
  
##  <a name="measureitem"></a>CCheckListBox::MeasureItem  
 Voláno rámcem, když se vytvoří kontrolní seznam pole s jiný než výchozí styl.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Dlouhé ukazatel [measureitemstruct –](../../mfc/reference/measureitemstruct-structure.md) struktura.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Funkci člena přepsat a vyplňte `MEASUREITEMSTRUCT` struktura k informování Windows dimenzí políčko kontrolního seznamu položek. Pokud políčko kontrolního seznamu je vytvořen s [lbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) volá framework styl, tato funkce člena pro každou položku v seznamu. Tento člen, jinak je volat pouze jednou.  
  
##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition  
 Tato funkce se získat umístění a velikost zaškrtávacího políčka v položku volá framework.  
  
```  
virtual CRect OnGetCheckPosition(
    CRect rectItem,  
    CRect rectCheckBox);
```  
  
### <a name="parameters"></a>Parametry  
 *rectItem*  
 Pozice a velikosti položky seznamu.  
  
 `rectCheckBox`  
 Výchozí umístění a velikost položky zaškrtávacího políčka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice a velikosti položky zaškrtávacího políčka.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vrací pouze výchozí umístění a velikost zaškrtávacího políčka ( `rectCheckBox`). Ve výchozím nastavení zaškrtněte políčko zarovnán v levém horním rohu položky a je velikost standardní zaškrtávací políčko. Můžou nastat případy, kde mají zaškrtávací políčka na pravé straně, nebo chcete zaškrtávací políčko větší nebo menší. V těchto případech přepsat `OnGetCheckPosition` změnit políčko pozice a velikosti v rámci položky.  
  
##  <a name="setcheck"></a>CCheckListBox::SetCheck  
 Nastaví stav zadané políčko.  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index počítaný od nuly zaškrtávací políčko, které se nachází v seznamu.  
  
 `nCheck`  
 Tlačítko stavu pro zadané pole. Možné hodnoty v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí možné hodnoty pro `nCheck` parametr.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**BST_CHECKED**|Zaškrtněte políčko zadaný.|  
|**BST_UNCHECKED**|Zrušte zaškrtnutí políčka zadaný.|  
|**BST_INDETERMINATE**|Nastavte stav políčko zadaný na neurčitou.<br /><br /> Tento stav je k dispozici, pokud je styl políčko pouze `BS_AUTO3STATE` nebo `BS_3STATE`. Další informace najdete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
  
##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle  
 Volání této funkce lze nastavit v rozevíracím seznamu kontrolní seznam styl zaškrtávacích políček.  
  
```  
void SetCheckStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `nStyle`  
 Určuje styl zaškrtnutí políček v poli seznamu úkolů.  
  
### <a name="remarks"></a>Poznámky  
 Platný styly jsou:  
  
- **BS_CHECKBOX –**  
  
- **BS_AUTOCHECKBOX –**  
  
- **BS_AUTO3STATE –**  
  
- **BS_3STATE –**  
  
 Informace o těchto styly najdete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC TSTCON](../../visual-cpp-samples.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)
