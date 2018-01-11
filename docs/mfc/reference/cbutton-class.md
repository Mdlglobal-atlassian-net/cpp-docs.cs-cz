---
title: "Třída CButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
dev_langs: C++
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6e92efe5b5a99042426dd2e6a7594f2de46f2ce
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="cbutton-class"></a>CButton – třída
Poskytuje funkce Windows ovládacích prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CButton : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CButton::CButton](#cbutton)|Vytvoří `CButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CButton::Create](#create)|Vytvoří ovládacího prvku tlačítko Windows a připojí jej k `CButton` objektu.|  
|[CButton::DrawItem](#drawitem)|Přepsání pro kreslení vykreslovaných vlastníkem `CButton` objektu.|  
|[CButton::GetBitmap](#getbitmap)|Načte popisovač rastrového obrázku dříve nastavené s [SetBitmap](#setbitmap).|  
|[CButton::GetButtonStyle](#getbuttonstyle)|Načte informace o stylu ovládacího prvku tlačítko.|  
|[CButton::GetCheck](#getcheck)|Načte kontroly stavu ovládacího prvku tlačítko.|  
|[CButton::GetCursor](#getcursor)|Načte popisovač bitovou kopii kurzoru dříve nastavené s [SetCursor](#setcursor).|  
|[CButton::GetIcon](#geticon)|Načte popisovač ikonu dříve nastavené s [SetIcon](#seticon).|  
|[CButton::GetIdealSize](#getidealsize)|Načte ideální velikost ovládacího prvku tlačítko.|  
|[CButton::GetImageList](#getimagelist)|Načte seznam obrázků ovládacího prvku tlačítko.|  
|[CButton::GetNote](#getnote)|Načte Poznámka součást prvku odkaz aktuální příkaz.|  
|[CButton::GetNoteLength](#getnotelength)|Načte délka textu poznámky pro aktuální příkaz odkaz ovládacího prvku.|  
|[CButton::GetSplitGlyph](#getsplitglyph)|Načte glyfy přidružený k ovládacímu prvku aktuální rozdělení tlačítko.|  
|[CButton::GetSplitImageList](#getsplitimagelist)|Načte seznam obrázků pro aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::GetSplitInfo](#getsplitinfo)|Načte informace, které definují aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::GetSplitSize](#getsplitsize)|Načte ohraničující obdélník rozevíracího seznamu součástí aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::GetSplitStyle](#getsplitstyle)|Načte styly tlačítek rozdělení, které definují aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::GetState](#getstate)|Načte kontrolu stavu, zvýraznění stav a stav fokus ovládací prvek.|  
|[CButton::GetTextMargin](#gettextmargin)|Načte text okrajem tlačítko ovládacího prvku.|  
|[CButton::SetBitmap](#setbitmap)|Určuje rastrový obrázek, který se má zobrazit na tlačítko.|  
|[CButton::SetButtonStyle](#setbuttonstyle)|Změní styl tlačítko.|  
|[CButton::SetCheck](#setcheck)|Nastaví stav kontroly ovládacího prvku tlačítko.|  
|[CButton::SetCursor](#setcursor)|Určuje bitovou kopii kurzor, který se má zobrazit na tlačítko.|  
|[CButton::SetDropDownState](#setdropdownstate)|Nastaví stav rozevíracího seznamu aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::SetIcon](#seticon)|Určuje ikonu, která se zobrazí na tlačítko.|  
|[CButton::SetImageList](#setimagelist)|Nastaví seznamu obrázků ovládacího prvku tlačítko.|  
|[CButton::SetNote](#setnote)|Nastaví Poznámka pro aktuální příkaz odkaz ovládacího prvku.|  
|[CButton::SetSplitGlyph](#setsplitglyph)|Přidruží zadané glyf aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::SetSplitImageList](#setsplitimagelist)|Přidruží aktuální rozdělení tlačítko – ovládací prvek seznamu obrázků.|  
|[CButton::SetSplitInfo](#setsplitinfo)|Určuje informace, které definují aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::SetSplitSize](#setsplitsize)|Nastaví ohraničující obdélník rozevíracího seznamu součástí aktuální ovládací prvek tlačítko rozdělení.|  
|[CButton::SetSplitStyle](#setsplitstyle)|Nastavuje styl aktuální ovládacího prvku tlačítko rozdělení.|  
|[CButton::SetState](#setstate)|Nastaví stav zvýraznění ovládacího prvku tlačítko.|  
|[CButton::SetTextMargin](#settextmargin)|Nastaví okraj textu ovládacího prvku tlačítko.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek tlačítko je malý, obdélníková podřízené okno, které lze klepnout zapnout a vypnout. Tlačítka může být použito samostatně nebo ve skupinách a může být buď označené nebo zobrazit bez textu. Tlačítko obvykle mění vzhled, když uživatel klikne ho.  
  
 Zaškrtávací políčko, přepínače a pushbutton jsou typické tlačítka. A `CButton` objektu se může stát některý z těchto, podle požadavků [tlačítko Styl](../../mfc/reference/styles-used-by-mfc.md#button-styles) inicializace pomocí zadané [vytvořit](#create) – členská funkce.  
  
 Kromě toho [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) třída odvozená z `CButton` podporuje vytváření ovládacích prvků tlačítko označený verzí rastrové obrázky místo textu. A `CBitmapButton` může mít samostatné bitmap pro tlačítko je, dolů, zaměřuje a zakázané stavy.  
  
 Ovládací prvek tlačítko můžete vytvořit buď z šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve volat konstruktor `CButton` vytvořit `CButton` objektu; potom zavolejte **vytvořit** – členská funkce vytvoření okna pro ovládací prvek tlačítko a připojte ji k `CButton` objektu.  
  
 Konstrukce může být jednoduchý proces v třídy odvozené od `CButton`. Zápis konstruktoru odvozené třídy a volání **vytvořit** z v konstruktoru.  
  
 Pokud chcete pro zpracování zpráv s oznámením Windows posílá nadřazenému prvku tlačítko (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte map zpráv položku a obslužné rutiny zpráv členské funkce do nadřazené třídy pro každou zprávu.  
  
 Každá položka mapování zpráv má následující podobu:  
  
 **ON_**oznámení **(**`id`, `memberFxn` **)**  
  
 kde `id` Určuje ID okno podřízeného prvku odesílání oznámení a `memberFxn` je název nadřazeného člena funkce napsané pro zpracování oznámení.  
  
 Prototyp funkce nadřazeného objektu je následující:  
  
 **afx_msg** `void` `memberFxn` **();**  
  
 Potenciální map zpráv položky jsou následující:  
  
|Položku mapování|Posílá nadřazených při...|  
|---------------|----------------------------|  
|**ON_BN_CLICKED**|Uživatel klikne na tlačítko.|  
|**ON_BN_DOUBLECLICKED**|Poklepání tlačítko.|  
  
 Pokud vytvoříte `CButton` objekt z prostředku dialogového okna, `CButton` objekt zničen automaticky při zavření dialogu.  
  
 Pokud vytvoříte `CButton` objektů v rámci časového období, budete muset zničte jej. Pokud vytvoříte `CButton` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte, jakmile uživatel nezavře Windows tlačítko ovládacího prvku. Pokud vytvoříte `CButton` objekt v zásobníku, nebo je vložen do nadřazeného objektu dialogového okna, byla automaticky.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cbutton"></a>CButton::CButton  
 Vytvoří `CButton` objektu.  
  
```  
CButton();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>CButton::Create  
 Vytvoří ovládacího prvku tlačítko Windows a připojí jej k `CButton` objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszCaption`  
 Určuje text prvku tlačítka.  
  
 `dwStyle`  
 Určuje styl ovládacího prvku tlačítko. Použít libovolnou kombinaci [tlačítko styly](../../mfc/reference/styles-used-by-mfc.md#button-styles) pro tlačítko.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku tlačítko. Může být buď `CRect` objekt nebo `RECT` struktury.  
  
 `pParentWnd`  
 Určuje ovládacího prvku tlačítko nadřazené okno, obvykle `CDialog`. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CButton` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří ovládacího prvku tlačítko Windows a připojí jej k `CButton` objektu.  
  
 Pokud **ws_visible –** je zadána styl, systém Windows odešle ovládacího prvku tlačítko všechny zprávy, které jsou potřebné pro aktivaci a na tlačítko zobrazit.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku tlačítko:  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
- **Ws_group –** k seskupování ovládacích prvků  
  
- **Ws_tabstop –** zahrnout tlačítko v pořadí, dají se procházet tabulátorem  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>CButton::DrawItem  
 Voláno rámcem, pokud došlo ke změně visual aspekt tlačítka vykreslované uživatelem.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Dlouhé ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktura. Struktura obsahuje informace o položce, které se mají vykreslovat a typ kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 Vykreslovaných vlastníkem tlačítko má **bs_ownerdraw –** styl sady. Člen funkci implementovat kreslení pro vykreslovaných vlastníkem přepsat `CButton` objektu. Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před člen funkce ukončí.  
  
 Viz také [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) hodnoty stylu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>CButton::GetBitmap  
 Volání této funkce člen se získat popisovač rastrového obrázku, dříve nastavené s [SetBitmap](#setbitmap), která je spojená s tlačítkem na.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro rastrový obrázek. **NULL** dříve případného žádné rastrového obrázku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>CButton::GetButtonStyle  
 Načte informace o stylu ovládacího prvku tlačítko.  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí styly tlačítek pro tuto `CButton` objektu. Tato funkce vrátí pouze [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) hodnoty styl, nejsou žádné další styly oken.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>CButton::GetCheck  
 Načte stav zaškrtávací políčko nebo přepínač.  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota z ovládacího prvku tlačítko vytvořené pomocí **bs_autocheckbox –**, **bs_autoradiobutton –**, **bs_auto3state –**, **bs_checkbox –**, **Bs_radiobutton –**, nebo **bs_3state –** style je jedním z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|**BST_UNCHECKED**|Tlačítko stavu není zaškrtnuta.|  
|**BST_CHECKED**|Kontroly stavu tlačítko.|  
|**BST_INDETERMINATE**|Tlačítko Stav je neurčitou (platí jenom v případě, že má tlačítko **bs_3state –** nebo **bs_auto3state –** styl).|  
  
 Má-li na tlačítko Další styl, je vrácenou hodnotu **BST_UNCHECKED**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>CButton::GetCursor  
 Volání této funkce člen se získat popisovač kurzoru, dříve nastavené s [SetCursor](#setcursor), která je spojená s tlačítkem na.  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro bitovou kopii kurzoru. **NULL** dříve případného žádný ukazatel.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>CButton::GetIcon  
 Volání této funkce člen se získat popisovač ikonu, dříve nastavené s [SetIcon](#seticon), která je spojená s tlačítkem na.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro ikonu. **NULL** pokud dříve není určena žádná ikona.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CButton::GetIdealSize  
 Načte jeho ideální velikost pro ovládací prvek tlačítko.  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>Parametry  
 *psize*  
 Ukazatel na aktuální velikost tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce **BCM_GETIDEALSIZE** zprávy, jak je popsáno v [tlačítka](http://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.  
  
##  <a name="getimagelist"></a>CButton::GetImageList  
 Volejte tuto metodu za účelem získání seznamu obrázků z ovládacího prvku tlačítko.  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parametry  
 `pbuttonImagelist`  
 Ukazatel na seznamu bitové kopie `CButton` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce **BCM_GETIMAGELIST** zprávy, jak je popsáno v [tlačítka](http://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.  
  
##  <a name="getnote"></a>CButton::GetNote  
 Načte text poznámky, který je přidružený k ovládacímu prvku aktuální příkaz odkaz.  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out]`lpszNote`|Ukazatel na vyrovnávací paměť, která má volající zodpovídá za přidělování a rušení přidělení. Pokud je vrácenou hodnotou `true`, Poznámka: text, který je přidružen aktuální příkaz odkaz ovládacího prvku; jinak hodnota obsahuje vyrovnávací paměť, vyrovnávací paměť je beze změny.|  
|[ve out]`cchNote`|Ukazatel na proměnnou celé číslo bez znaménka.<br /><br /> Když tato metoda je volána, obsahuje proměnnou velikost vyrovnávací paměti určeného `lpszNote` parametr.<br /><br /> Když tato metoda vrátí hodnotu, pokud je vrácenou hodnotou `true` velikost Poznámka přidružený k ovládacímu prvku aktuální příkaz odkaz obsahuje proměnnou. Pokud je vrácenou hodnotou `false`, obsahuje proměnnou musí obsahovat Poznámka velikost vyrovnávací paměti.|  
  
### <a name="return-value"></a>Návratová hodnota  
 V první přetížení [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obsahuje text poznámky, který je přidružený k ovládacímu prvku aktuální příkaz odkaz.  
  
 -nebo-  
  
 V druhé přetížení `true` Pokud tato metoda je úspěšné, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_COMMANDLINK` nebo `BS_DEFCOMMANDLINK`.  
  
 Tato metoda odesílá [BCM_GETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775965) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getnotelength"></a>CButton::GetNoteLength  
 Načte délka textu poznámky pro aktuální příkaz odkaz ovládacího prvku.  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka textu poznámky, v 16bitové znaky znakové sady Unicode, pro aktuální příkaz odkaz ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_COMMANDLINK` nebo `BS_DEFCOMMANDLINK`.  
  
 Tato metoda odesílá [BCM_GETNOTELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb775967) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getsplitglyph"></a>CButton::GetSplitGlyph  
 Načte glyfy přidružený k ovládacímu prvku aktuální rozdělení tlačítko.  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Glyf znaku přidružený k ovládacímu prvku aktuální rozdělení tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Glyf je fyzický reprezentace znaku v určité písmo. Například ovládací prvek tlačítko rozdělení může být doplněny pomocí glyf znaku značky zaškrtnutí Unicode (U + 2713).  
  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_GLYPH` příznak a poté odešle, které struktury v [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v systému Windows SDK. Pokud zpráva funkce vrátí hodnotu, tato metoda načte glyfy z `himlGlyph` členů struktury.  
  
##  <a name="getsplitimagelist"></a>CButton::GetSplitImageList  
 Načte [seznamu obrázků](../../mfc/reference/cimagelist-class.md) pro aktuální ovládací prvek tlačítko rozdělení.  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_IMAGE` příznak a poté odešle, které struktury v [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v systému Windows SDK. Pokud zpráva funkce vrátí hodnotu, tato metoda načítá seznamu obrázků z `himlGlyph` členů struktury.  
  
##  <a name="getsplitinfo"></a>CButton::GetSplitInfo  
 Načte parametry, které určují, jak Windows nevykresluje aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out]`pInfo`|Ukazatel na [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktura, která přijímá informace o aktuální ovládací prvek tlačítko rozdělení. Volající zodpovídá za přidělování strukturu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Tato metoda odesílá [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getsplitsize"></a>CButton::GetSplitSize  
 Načte ohraničující obdélník rozevíracího seznamu součástí aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out]`pSize`|Ukazatel na [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která přijímá popis obdélníku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Když je rozšířena ovládacího prvku tlačítko rozdělení, zobrazí rozevírací seznam součástí například ovládací prvek seznamu nebo pager řízení. Tato metoda načte ohraničující obdélník, který obsahuje komponentu rozevíracího seznamu.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_SIZE` příznak a poté odešle, které struktury v [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v systému Windows SDK. Pokud zpráva funkce vrátí hodnotu, tato metoda načítá ohraničující obdélník z `size` členů struktury.  
  
##  <a name="getsplitstyle"></a>CButton::GetSplitStyle  
 Načte styly tlačítek rozdělení, které definují aktuální ovládací prvek tlačítko rozdělení.  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitová kombinace styly tlačítka rozdělení. Další informace najdete v tématu `uSplitStyle` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Styly tlačítek rozdělení zadejte zarovnání, poměr stran a grafické formátu, pomocí kterého Windows nevykresluje ikonu tlačítka rozdělení.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_STYLE` příznak a poté odešle, které struktury v [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v systému Windows SDK. Pokud zpráva funkce vrátí hodnotu, tato metoda načítá styly tlačítek rozdělení z `uSplitStyle` členů struktury.  
  
##  <a name="getstate"></a>CButton::GetState  
 Načte stav ovládacího prvku tlačítko.  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitová pole, které obsahuje kombinaci hodnot, které označují aktuální stav ovládacího prvku tlačítko. Následující tabulka uvádí možné hodnoty.  
  
|Tlačítko stavu|Hodnota|Popis|  
|------------------|-----------|-----------------|  
|`BST_UNCHECKED`|0x0000|Počáteční stav.|  
|`BST_CHECKED`|0x0001|Ovládací prvek tlačítko je zaškrtnuté.|  
|`BST_INDETERMINATE`|0x0002|Stav je neurčitou (možné pouze při ovládacího prvku tlačítko má tři stavy).|  
|`BST_PUSHED`|0x0004|Ovládací prvek tlačítko stisknutí.|  
|`BST_FOCUS`|0x0008|Ovládací prvek tlačítko fokus.|  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek tlačítko `BS_3STATE` nebo `BS_AUTO3STATE` stylů tlačítek vytvoří zaškrtávací políčko, které má třetí stav, který je s názvem neurčitém stavu. Neurčitého stavu označuje, že políčko není zaškrtnuté ani není zaškrtnuto.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>CButton::GetTextMargin  
 Volat tuto metodu za účelem získání rozpětí textu `CButton` objektu.  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parametry  
 `pmargin`  
 Ukazatel na rozpětí textu `CButton` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí okraj textu.  
  
### <a name="remarks"></a>Poznámky  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce **BCM_GETTEXTMARGIN** zprávy, jak je popsáno v [tlačítka](http://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.  
  
##  <a name="setbitmap"></a>CButton::SetBitmap  
 Volání této funkce člen přidružit nové rastrový obrázek na tlačítko.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametry  
 `hBitmap`  
 Popisovač rastrový obrázek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač rastrový obrázek dřív přidružené ke tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Bitmapy se automaticky umístí na tlačítku, standardně umístěn na střed. Pokud je příliš velký pro tlačítko bitovou mapu, tak bude oříznut na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících:  
  
- **BS_TOP –**  
  
- **BS_LEFT –**  
  
- **BS_RIGHT –**  
  
- **BS_CENTER –**  
  
- **BS_BOTTOM –**  
  
- **BS_VCENTER –**  
  
 Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři bitmap na tlačítko `SetBitmap` používá jenom jeden rastrový obrázek na tlačítko. Při stisknutí tlačítka bitmapy pravděpodobně Posunutí dolů a doprava.  
  
 Jste zodpovědní za uvolnění bitovou mapu, když jste hotovi s ním.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>CButton::SetButtonStyle  
 Změní styl tlačítko.  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nStyle`  
 Určuje, [tlačítko Styl](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 `bRedraw`  
 Určuje, zda je tlačítko překreslit. Nenulovou hodnotu překreslí tlačítko. Hodnota 0 zůstávají beze změny tlačítko. Ve výchozím nastavení bude překreslen tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Použití `GetButtonStyle` – členská funkce načíst stylů tlačítek. Word nejnižší stylu tlačítko Dokončit je styl specifické pro tlačítko.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>CButton::SetCheck  
 Nastaví nebo vynuluje stav zaškrtávací políčko nebo přepínač.  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nCheck`  
 Určuje stav kontroly. Tento parametr může být jedna z následujících akcí:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|**BST_UNCHECKED**|Nastavte stav tlačítko na nezaškrtnuté.|  
|**BST_CHECKED**|Nastavte stav tlačítko Zkontrolovat.|  
|**BST_INDETERMINATE**|Nastavte stav tlačítko na neurčitou. Tuto hodnotu lze použít pouze v případě na tlačítko **bs_3state –** nebo **bs_auto3state –** stylu.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen nemá žádný vliv na pushbutton.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>CButton::SetCursor  
 Volání této funkce člena na tlačítko přidružit nové kurzoru.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parametry  
 `hCursor`  
 Popisovač kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kurzoru dřív přidružené ke tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Kurzor se automaticky umístí na tlačítku, standardně umístěn na střed. Pokud je příliš velký pro tlačítko kurzor, tak bude oříznut na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících:  
  
- **BS_TOP –**  
  
- **BS_LEFT –**  
  
- **BS_RIGHT –**  
  
- **BS_CENTER –**  
  
- **BS_BOTTOM –**  
  
- **BS_VCENTER –**  
  
 Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři bitmap na tlačítko `SetCursor` používá jenom jeden kurzor na tlačítko. Při stisknutí tlačítka kurzor se zobrazí se posunou dolů a doprava.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>CButton::SetDropDownState  
 Nastaví stav rozevíracího seznamu aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`fDropDown`|`true`Chcete-li nastavit `BST_DROPDOWNPUSHED` stavu; jinak hodnota, `false`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek tlačítko rozdělení obsahuje styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON` a skládá se z tlačítka šipku rozevíracího seznamu záhlavím vpravo. Další informace najdete v tématu [styly tlačítek](http://msdn.microsoft.com/library/windows/desktop/bb775951). Stav rozevíracího seznamu je obvykle nastavena, když uživatel klikne na šipku rozevíracího seznamu. Tuto metodu použijte prostřednictvím kódu programu nastavit stav rozevíracího seznamu ovládacího prvku. Na šipku rozevíracího seznamu vykreslením možné zjistit stav šedou barvou.  
  
 Tato metoda odesílá [BCM_SETDROPDOWNSTATE](http://msdn.microsoft.com/library/windows/desktop/bb775973) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_splitButton`, který používá k programovému přístupu ovládacího prvku tlačítko rozdělení. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví stav ovládacího prvku tlačítko rozdělení indikující, že se instaluje na šipku rozevíracího seznamu.  
  
 [!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>CButton::SetElevationRequired  
 Nastaví stav aktuální ovládací prvek tlačítko pro `elevation required`, která je nezbytná pro ovládací prvek zobrazíte ikonu zvýšené zabezpečení.  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`fElevationRequired`|`true`Chcete-li nastavit `elevation required` stavu; jinak hodnota, `false`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládací prvek tlačítko nebo příkaz odkaz vyžaduje zvýšená oprávnění k provedení akce, nastavení ovládacího prvku `elevation required` stavu. Následně Windows zobrazuje ikona štítu řízení uživatelských účtů (UAC) na ovládací prvek. Další informace najdete v tématu "Řízení uživatelských účtů" v [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).  
  
 Tato metoda odesílá [BCM_SETSHIELD](http://msdn.microsoft.com/library/windows/desktop/bb775979) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="seticon"></a>CButton::SetIcon  
 Volání této funkce člena na tlačítko přidružit ikonu nový.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 `hIcon`  
 Popisovač ikonu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač ikonu dřív přidružené ke tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Ikona se automaticky umístí na tlačítku, standardně umístěn na střed. Pokud je příliš velký pro tlačítko ikonu, bude oříznut na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících:  
  
- **BS_TOP –**  
  
- **BS_LEFT –**  
  
- **BS_RIGHT –**  
  
- **BS_CENTER –**  
  
- **BS_BOTTOM –**  
  
- **BS_VCENTER –**  
  
 Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři bitmap na tlačítko `SetIcon` používá jenom jeden ikony pro tlačítko. Při stisknutí tlačítka, zobrazí se na ikonu se posunou dolů a doprava.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>CButton::SetImageList  
 Volat tuto metodu a nastavit seznam bitové kopie `CButton` objektu.  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parametry  
 `pbuttonImagelist`  
 Ukazatel na nový seznam obrázků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce **BCM_SETIMAGELIST** zprávy, jak je popsáno v [tlačítka](http://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.  
  
##  <a name="setnote"></a>CButton::SetNote  
 Nastaví text poznámky pro aktuální příkaz odkaz ovládacího prvku.  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`lpszNote`|Ukazatel na řetězec znaků Unicode, který je nastaven jako text poznámky pro ovládací prvek odkazu příkazu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_COMMANDLINK` nebo `BS_DEFCOMMANDLINK`.  
  
 Tato metoda odesílá [BCM_SETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775977) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_cmdLink`, který používá k programovému přístupu ovládací prvek odkazu příkazu. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví text poznámky pro ovládací prvek odkazu příkazu.  
  
 [!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>CButton::SetSplitGlyph  
 Přidruží zadané glyf aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`chGlyph`|Znak, který určuje glyf, který chcete použít jako na šipku rozevíracího seznamu tlačítka rozdělení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky, které mají stylů tlačítek `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Glyf je fyzický reprezentace znaku v určité písmo. `chGlyph` Parametr se nepoužívá jako glyf, ale místo toho slouží k výběru glyf ze sady glyfů definovaná systémem. Základního glyfu šipku rozevíracího seznamu je zadána znakem '6' a vypadá takto: znak Unicode ČERNÝM dolů TROJÚHELNÍK SMĚŘUJÍCÍ (U + 25BC).  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_GLYPH` příznak a `himlGlyph` člen s `chGlyph` parametr a poté odešle, které struktury v [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v sadě Windows SDK.  
  
##  <a name="setsplitimagelist"></a>CButton::SetSplitImageList  
 Přidruží [seznamu obrázků](../../mfc/reference/cimagelist-class.md) s aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`pSplitImageList`|Ukazatel na [CImageList](../../mfc/reference/cimagelist-class.md) objekt, který chcete přiřadit aktuální ovládací prvek tlačítko rozdělení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_IMAGE` příznak a `himlGlyph` člen s `pSplitImageList` parametr a poté odešle, které struktury v [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v sadě Windows SDK.  
  
##  <a name="setsplitinfo"></a>CButton::SetSplitInfo  
 Určuje parametry, které určují, jak Windows nevykresluje aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`pInfo`|Ukazatel na [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktura, která definuje aktuální ovládací prvek tlačítko rozdělení.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Tato metoda odesílá [BCM_SETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775981) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_splitButton`, který používá k programovému přístupu ovládacího prvku tlačítko rozdělení.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu změní glyf, který se používá pro na šipku rozevíracího seznamu tlačítka rozdělení. Příklad nahrazuje glyfy trojúhelník směřující nahoru pro základního glyfu trojúhelník směřující dolů. Glyf, který se zobrazí, závisí na znak, který určíte v `himlGlyph` členem `BUTTON_SPLITINFO` struktura. Glyfy směřující dolů trojúhelníček je zadán znakem ' 6 "a glyfy směřující nahoru trojúhelníček je zadán znakem ' 5". Porovnání najdete v tématu metodu pohodlí [CButton::SetSplitGlyph](#setsplitglyph).  
  
 [!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>CButton::SetSplitSize  
 Nastaví ohraničující obdélník rozevíracího seznamu součástí aktuální ovládací prvek tlačítko rozdělení.  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`pSize`|Ukazatel na [velikost](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která popisuje ohraničující obdélník.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Když je rozšířena ovládacího prvku tlačítko rozdělení, zobrazí rozevírací seznam součástí například ovládací prvek seznamu nebo pager řízení. Tato metoda určuje velikost ohraničující obdélník, který obsahuje komponentu rozevíracího seznamu.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_SIZE` příznak a `size` člen s `pSize` parametr a poté odešle, které struktury v [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_splitButton`, který používá k programovému přístupu ovládacího prvku tlačítko rozdělení. Tato proměnná se používá v následujícím příkladu.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu zdvojnásobuje velikost na šipku rozevíracího seznamu tlačítka rozdělení.  
  
 [!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>CButton::SetSplitStyle  
 Nastavuje styl aktuální ovládacího prvku tlačítko rozdělení.  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`uSplitStyle`|Bitová kombinace styly tlačítka rozdělení. Další informace najdete v tématu `uSplitStyle` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu lze použít pouze s ovládacími prvky mají tlačítko Styl `BS_SPLITBUTTON` nebo `BS_DEFSPLITBUTTON`.  
  
 Styly tlačítek rozdělení zadejte zarovnání, poměr stran a grafické formátu, pomocí kterého Windows nevykresluje ikonu tlačítka rozdělení. Další informace najdete v tématu `uSplitStyle` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury.  
  
 Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) struktury s `BCSIF_STYLE` příznak a `uSplitStyle` člen s `uSplitStyle` parametr a poté odešle, které struktury v [ BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) zpráva, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_splitButton`, který používá k programovému přístupu ovládacího prvku tlačítko rozdělení.  
  
 [!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví styl šipky rozevíracího seznamu tlačítka rozdělení. `BCSS_ALIGNLEFT` Styl zobrazí na šipku na levé straně na tlačítko a `BCSS_STRETCH` styl zachová poměr stran na šipku rozevíracího seznamu při změně velikosti tlačítko.  
  
 [!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>CButton::SetState  
 Nastaví, zda je ovládací prvek tlačítko zvýrazní nebo ne.  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 *bHighlight*  
 Určuje, jestli má mít zvýrazněná tlačítko. Nenulovou hodnotu klade důraz na tlačítko; Hodnota 0 odebere všechny zvýraznění.  
  
### <a name="remarks"></a>Poznámky  
 Zvýraznění ovlivňuje vnějšku ovládacího prvku tlačítko. Nemá žádný vliv na stav zaškrtávací políčko nebo přepínač.  
  
 Ovládací prvek tlačítko je označený automaticky, když uživatel klikne a obsahuje levým tlačítkem myši. Zvýraznění se odebere, když uživatel uvolní tlačítko myši.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>CButton::SetTextMargin  
 Volat tuto metodu a nastavit rozpětí textu `CButton` objektu.  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parametry  
 `pmargin`  
 Ukazatel na nové okraj textu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce **BCM_SETTEXTMARGIN** zprávy, jak je popsáno v [tlačítka](http://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)   
 [CStatic – třída](../../mfc/reference/cstatic-class.md)   
 [CBitmapButton – třída](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
