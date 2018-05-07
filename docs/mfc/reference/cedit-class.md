---
title: Třída CEdit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
dev_langs:
- C++
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72bf4ffb56ad34926b3a47d86d7609aae5dff4f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cedit-class"></a>CEdit – třída
Poskytuje funkce ovládacích prvků pro úpravy Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CEdit : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CEdit::CEdit](#cedit)|Vytvoří `CEdit` objekt ovládacího prvku.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CEdit::CanUndo](#canundo)|Určuje, zda může být operace textové pole vrátit zpět.|  
|[CEdit::CharFromPos](#charfrompos)|Načte řádku a znak indexy znaku, který je nejblíže k zadané pozici.|  
|[CEdit::Clear](#clear)|Odstranění (vymaže) aktuální výběr (pokud existuje) v úpravy řízení.|  
|[CEdit::Copy](#copy)|Zkopíruje aktuální výběr (pokud existuje) v ovládacím prvku upravit do schránky v **CF_TEXT** formátu.|  
|[CEdit::Create](#create)|Vytvoří ovládacího prvku úprav Windows a připojí jej k `CEdit` objektu.|  
|[CEdit::Cut](#cut)|Řízení aktuální výběr (pokud existuje) v úpravy odstranění (kusy) a zkopíruje odstraněný text do schránky v **CF_TEXT** formátu.|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Obnoví ovládací prvek (vymaže) příznak vrátit zpět úpravy.|  
|[CEdit::FmtLines](#fmtlines)|Nastaví zahrnutí znaků logicky koncem řádku zapnout nebo vypnout v rámci více řádků textové pole.|  
|[CEdit::GetCueBanner](#getcuebanner)|Načte text, který se zobrazí jako text cue nebo tip v ovládacím prvku upravit, pokud ovládací prvek je prázdná a nemá fokus.|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Určuje nejhornější viditelné řádku v ovládacím prvku upravit.|  
|[CEdit::GetHandle](#gethandle)|Načte popisovač pro paměti, které je právě přiděleno pro ovládací prvek upravit více řádků.|  
|[CEdit::GetHighlight](#gethighlight)|Získá indexy počáteční a koncové znaky v rozsahu textu, který je označený na aktuální ovládací prvek upravit.|  
|[CEdit::GetLimitText](#getlimittext)|Získá maximální objem textu, tento `CEdit` může obsahovat.|  
|[CEdit::GetLine](#getline)|Načte z ovládacího prvku úprav na řádku textu.|  
|[CEdit::GetLineCount](#getlinecount)|Získá počet řádků v ovládacím prvku upravit více řádků.|  
|[CEdit::GetMargins](#getmargins)|Získá levý a pravý okraj pro tento `CEdit`.|  
|[CEdit::GetModify](#getmodify)|Určuje, zda obsah ovládacích prvků pro úpravy byl změněn.|  
|[CEdit::GetPasswordChar](#getpasswordchar)|Načte heslo znak zobrazí v ovládacím prvku upravit, pokud uživatel zadá text.|  
|[CEdit::GetRect](#getrect)|Získá formátování rámeček ovládacích prvků pro úpravy.|  
|[CEdit::GetSel](#getsel)|Získá první a poslední znak pozice aktuální výběr v ovládacím prvku upravit.|  
|[CEdit::HideBalloonTip](#hideballoontip)|Skryje všechny tipu s přidružené k aktuální ovládací prvek upravit.|  
|[CEdit::LimitText](#limittext)|Omezení délky textu, který může uživatel zadat do ovládacího prvku úprav.|  
|[CEdit::LineFromChar](#linefromchar)|Načte číslo řádku řádek, který obsahuje index zadaný znak.|  
|[CEdit::LineIndex](#lineindex)|Načte znakový index řádku v rámci více řádků textové pole.|  
|[CEdit::LineLength](#linelength)|Načte délka řádku v ovládacím prvku upravit.|  
|[CEdit::LineScroll](#linescroll)|Posune text ovládacích prvků pro úpravy více řádků.|  
|[CEdit::Paste](#paste)|Vloží data ze schránky do ovládacího prvku úprav na aktuální pozici kurzoru. Vloží se data jenom v případě, že schránky obsahuje data v **CF_TEXT** formátu.|  
|[CEdit::PosFromChar](#posfromchar)|Načte souřadnice levého horního rohu indexu zadaný znak.|  
|[CEdit::ReplaceSel](#replacesel)|Aktuální výběr v ovládacím prvku upravit nahradí zadaný text.|  
|[CEdit::SetCueBanner](#setcuebanner)|Nastaví text, který se zobrazí jako text cue nebo tip v ovládacím prvku upravit, pokud ovládací prvek je prázdná a nemá fokus.|  
|[CEdit::SetHandle](#sethandle)|Nastaví popisovač pro místní paměti, která se použije v ovládacím prvku upravit více řádků.|  
|[CEdit::SetHighlight](#sethighlight)|Označuje a rozsah text, který se zobrazí v aktuální ovládacích prvků pro úpravy.|  
|[CEdit::SetLimitText](#setlimittext)|Nastaví maximální objem textu, to `CEdit` může obsahovat.|  
|[CEdit::SetMargins](#setmargins)|Nastaví levý a pravý okraj pro tento `CEdit`.|  
|[CEdit::SetModify](#setmodify)|Nastaví nebo vymaže příznak úprav pro ovládací prvek upravit.|  
|[CEdit::SetPasswordChar](#setpasswordchar)|Nastaví nebo odebere heslo znak zobrazí v ovládacím prvku upravit, pokud uživatel zadá text.|  
|[CEdit::SetReadOnly](#setreadonly)|Nastaví stav jen pro čtení ovládacích prvků pro úpravy.|  
|[CEdit::SetRect](#setrect)|Nastaví formátování rámeček ovládacích prvků pro úpravy více řádků a aktualizuje ovládacího prvku.|  
|[CEdit::SetRectNP](#setrectnp)|Nastaví formátování rámeček ovládacích prvků pro úpravy více řádků bez překreslování okně řízení.|  
|[CEdit::SetSel](#setsel)|Vybere rozsah znaků v ovládacím prvku upravit.|  
|[CEdit::SetTabStops](#settabstops)|Ovládacích prvků pro úpravy sady kartě zastaví v více řádků.|  
|[CEdit::ShowBalloonTip](#showballoontip)|Zobrazí bublinách tip, který je přidružen aktuální ovládací prvek upravit.|  
|[CEdit::Undo](#undo)|Vrátí zpět poslední akci textové pole.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek upravit je obdélníková podřízeného okna, ve kterém může uživatel zadat text.  
  
 Ovládací prvek upravit můžete vytvořit buď z šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve volat konstruktor `CEdit` vytvořit `CEdit` objekt a potom volání [vytvořit](#create) – členská funkce vytvořit Windows ovládacích prvků pro úpravy a připojte ji k `CEdit` objektu.  
  
 Konstrukce může být jednoduchý proces v třídy odvozené od `CEdit`. Zápis konstruktoru odvozené třídy a volání **vytvořit** z v konstruktoru.  
  
 `CEdit` dědí důležité funkce z `CWnd`. Nastavit a načíst text ze `CEdit` objektu, použijte `CWnd` členské funkce [SetWindowText](cwnd-class.md#setwindowtext) a [getwindowtext –](cwnd-class.md#getwindowtext), které sada nebo get celý obsah upravíte řídit, i když ho je Víceřádkový ovládacího prvku. Řádky textu v ovládacím prvku Víceřádkový jsou odděleny sekvence znaků '\r\n'. Navíc pokud ovládací prvek upravit je Víceřádkový, získání a nastavení součástí ovládacího prvku textu voláním `CEdit` členské funkce [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)a [ ReplaceSel](#replacesel).  
  
 Pokud chcete pro zpracování zpráv s oznámením Windows posílá nadřazený prvek úprav (obvykle třída odvozená z `CDialog`), přidejte map zpráv položku a obslužné rutiny zpráv členské funkce do nadřazené třídy pro každou zprávu.  
  
 Každá položka mapování zpráv má následující podobu:  
  
 **ON_** oznámení **(** *id, memberFxn ***)**  
  
 kde `id` Určuje ID okno podřízených ovládacích prvků pro úpravy odesílání oznámení, a `memberFxn` je název nadřazeného člena funkce napsané pro zpracování oznámení.  
  
 Prototyp funkce nadřazeného objektu je následující:  
  
 **afx_msg** void memberFxn **();**  
  
 Následuje seznam možných položkách map zpráv a popis v případech, ve kterých se mají být odeslány do nadřazené:  
  
- **On_en_change –** uživatel má provést akce, která může mít změnit text v ovládacím prvku upravit. Na rozdíl od **EN_UPDATE** oznámení, tato zpráva oznámení je odeslána po zobrazení aktualizace systému Windows.  
  
- **On_en_errspace –** textové pole nemůže přidělit dostatek paměti ke splnění konkrétního požadavku.  
  
- **On_en_hscroll –** uživatel klikne na ovládací prvek upravit vodorovného posuvníku. Nadřazené okno oznámení předtím, než se aktualizuje na obrazovce.  
  
- **On_en_killfocus –** textové pole ztratí zaměření pro vstup.  
  
- **On_en_maxtext –** aktuální vložení překročil zadaný počet znaků pro ovládací prvek upravit a byla zkrácena. Odesílá i když nemá ovládací prvek upravit **es_autohscroll –** styl a počet znaků, který má být vložen překročí šířku ovládacích prvků pro úpravy. Odesílá i když nemá ovládací prvek upravit **es_autovscroll –** style a celkový počet řádků, které jsou výsledkem vkládání textu překročí výšku ovládacích prvků pro úpravy.  
  
- **On_en_setfocus –** odeslané zaměření pro vstup přijetí ovládací prvek upravit.  
  
- **On_en_update –** textové pole je zobrazit změnit text. Odeslána po ovládacího prvku má formátovaný text, ale před jeho obrazovky text tak, aby velikost okna může být změněna, v případě potřeby.  
  
- **On_en_vscroll –** uživatel klikne na ovládací prvek upravit svislého posuvníku. Nadřazené okno oznámení předtím, než se aktualizuje na obrazovce.  
  
 Pokud vytvoříte `CEdit` objekt v rámci dialogového okna, `CEdit` objekt zničen automaticky při zavření dialogu.  
  
 Pokud vytvoříte `CEdit` objekt z prostředku dialogového okna, pomocí editoru dialogových oken `CEdit` objekt zničen automaticky při zavření dialogu.  
  
 Pokud vytvoříte `CEdit` objektu v okně a také můžete potřebovat jeho odstranění. Pokud vytvoříte `CEdit` objektu v zásobníku, byla automaticky. Pokud vytvoříte `CEdit` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte, jakmile uživatel ukončí Windows ovládacích prvků pro úpravy. Pokud přidělíte libovolná paměť v `CEdit` objektu, přepsat `CEdit` destruktor k odstranění přidělení.  
  
 K úpravě některých styly v ovládacím prvku úpravy (například **es_readonly –**) je nutné odeslat zprávy specifické pro do ovládacího prvku místo použití [ModifyStyle](cwnd-class.md#modifystyle). V tématu [upravit styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775464) v systému Windows SDK.  
  
 Další informace o `CEdit`, najdete v části:  
  
- [Ovládací prvky](../../mfc/controls-mfc.md)  
  
-   Článek znalostní báze Knowledge Base Q259949: informace: SetCaretPos() je není vhodný s CEdit nebo ovládací prvky CRichEditCtrl  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="canundo"></a>  CEdit::CanUndo  
 Volání této funkce k určení, pokud poslední operaci úpravy mohou být vráceny zpět.  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud poslední operace upravování můžete odvolat voláním **vrátit zpět** – členská funkce; 0, pokud ho nelze vrátit zpět.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::Undo](#undo).  
  
##  <a name="cedit"></a>  CEdit::CEdit  
 Vytvoří `CEdit` objektu.  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití [vytvořit](#create) k vytvoření okna pro ovládací prvek pro úpravy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="charfrompos"></a>  CEdit::CharFromPos  
 Volání této funkce k načtení řádků od nuly a znak indexy znaku nejbližší Zadaný bod v tomto `CEdit` ovládací prvek  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Souřadnice bodu v oblasti klienta tohoto `CEdit` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Znakový index v nejnižší **WORD**a index řádku v pořadí vysokou **WORD**.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tento člen funkce je k dispozici od verze systému Windows 95 a Windows NT 4.0.  
  
 Další informace najdete v tématu [EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="clear"></a>  CEdit::Clear  
 Volání této funkce pro odstranění (Vymazat) aktuální výběr (pokud existuje) v textové pole.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Poznámky  
 Odstranění provádí **zrušte** můžete odvolat voláním [vrátit zpět](#undo) – členská funkce.  
  
 Chcete-li odstranit aktuální výběr a umístit odstraněné obsah do schránky, zavolejte [Vyjmout](#cut) – členská funkce.  
  
 Další informace najdete v tématu [WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="copy"></a>  CEdit::Copy  
 Volání této funkce do coy aktuální výběr (pokud existuje) v ovládacím prvku upravit do schránky v **CF_TEXT** formátu.  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="create"></a>  CEdit::Create  
 Vytvoří ovládacího prvku úprav Windows a připojí jej k `CEdit` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládací prvek upravit. Použít libovolnou kombinaci [styly pro úpravy](styles-used-by-mfc.md#edit-styles) do ovládacího prvku.  
  
 `rect`  
 Určuje velikost a umístění textové pole. Může být `CRect` objekt nebo `RECT` struktury.  
  
 `pParentWnd`  
 Určuje textové pole nadřazeného okna (obvykle `CDialog`). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládací prvek upravit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného; inicializace jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CEdit` objektu ve dvou krocích. Nejprve volání `CEdit` konstruktor a pak volání **vytvořit**, který vytvoří ovládacího prvku úprav Windows a připojí jej k `CEdit` objektu.  
  
 Když **vytvořit** provede, odešle Windows [WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635), [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634), [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619), a [WM_ GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626) zprávy pro ovládací prvek upravit.  
  
 Tyto zprávy jsou zpracovávány ve výchozím nastavení [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate), a [ongetminmaxinfo –](cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Rozšíření zpracování zpráv výchozí, odvození třídy z `CEdit`, přidejte mapy zpráv do nové třídy a přepsat výše členské funkce obslužné rutiny zpráv. Přepsání `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Použít následující [styly oken](styles-used-by-mfc.md#window-styles) na ovládací prvek upravit.  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
- **Ws_group –** k seskupování ovládacích prvků  
  
- **Ws_tabstop –** zahrnout ovládacích prvků pro úpravy v pořadí, dají se procházet tabulátorem  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="cut"></a>  CEdit::Cut  
 Volání této funkce odstranit (vyjmutí) (pokud existuje) aktuální výběr v ovládacím prvku úpravy a zkopírujte odstraněný text do schránky v **CF_TEXT** formátu.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Poznámky  
 Odstranění provádí **Vyjmout** můžete odvolat voláním [vrátit zpět](#undo) – členská funkce.  
  
 Chcete-li odstranit aktuální výběr bez umístění odstraněný text do schránky, zavolejte [zrušte](#clear) – členská funkce.  
  
 Další informace najdete v tématu [WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer  
 Volání této funkce resetování (Vymazat) příznak zpět ovládacích prvků pro úpravy.  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>Poznámky  
 Textové pole bude nyní nelze vrátit zpět poslední akci. Příznak vrácení zpět je nastaven při každém operace v rámci prvku úpravy mohou být vráceny zpět.  
  
 Příznak vrácení zpět je automaticky vymazána vždy, když [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) nebo [SetHandle](#sethandle) `CWnd` se označují jako členské funkce.  
  
 Další informace najdete v tématu [EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="fmtlines"></a>  CEdit::FmtLines  
 Volání této funkce můžete nastavit zahrnutí znaků logicky koncem řádku zapnout nebo vypnout v rámci více řádků textové pole.  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>Parametry  
 *bAddEOL*  
 Určuje, zda logicky koncem řádku znaky má být vložen. Hodnota **TRUE** vloží znaků; hodnota **FALSE** odebere je.  
  
### <a name="return-value"></a>Návratová hodnota  
 Formátování dojde k nenulové hodnoty, pokud existuje; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Konec řádku logicky se skládá z dvě znak návratu konce řádku, vložit na konci řádku, který je poškozený z důvodu zalamování řádků. Konec řádku pevný se skládá z jedné návrat konce řádku. Řádky, které končí konec řádku pevný neovlivní `FmtLines`.  
  
 Systém Windows bude reagovat, jen pokud `CEdit` objektu je ovládací prvek upravit více řádků.  
  
 `FmtLines` ovlivňuje pouze vyrovnávací paměti vrácené [gethandle –](#gethandle) a text vrácený [WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627). Nemá žádný vliv na zobrazení textu v rámci ovládací prvek upravit.  
  
 Další informace najdete v tématu [EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="getcuebanner"></a>  CEdit::GetCueBanner  
 Načte text, který se zobrazí jako text cue nebo tip v ovládacím prvku upravit, pokud ovládací prvek je prázdný.  
  
```  
BOOL GetCueBanner(
    LPWSTR lpszText,  
    int cchText) const;  
  
CString GetCueBanner() const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `lpszText`  
 Ukazatel na řetězec, který obsahuje cue text.  
  
 [v] `cchText`  
 Počet znaků, které můžou přijímat. Tato hodnota zahrnuje ukončení `NULL` znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro první přetížení `true` Pokud je metoda úspěšná, jinak hodnota `false`.  
  
 Pro druhý přetížení [CString](../../atl-mfc-shared/using-cstring.md) obsahující text upozornění, pokud metoda úspěšná, jinak hodnota prázdný řetězec ("").  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572) zprávy, která je popsána v sadě Windows SDK. Další informace najdete v tématu [Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695) makro.  
  
##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine  
 Volání této funkce určete nejhornější viditelné řádku v ovládacím prvku upravit.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule nejhornější viditelné řádku. Pro ovládacích prvcích pro úpravy jeden řádek je vrácenou hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="gethandle"></a>  CEdit::GetHandle  
 Volání této funkce pro načtení popisovače paměti aktuálně přidělené pro ovládací prvek upravit více řádků.  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Místní paměť obslužná rutina, která identifikuje vyrovnávací paměti, která uchovává obsah ovládacích prvků pro úpravy. Pokud dojde k chybě, například odeslání zprávy do ovládacího prvku úprav jeden řádek vrácená hodnota je 0.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač je popisovač místní paměti a může být používán některé z **místní** paměti funkcí systému Windows, které přijímají místní paměti zpracovat jako parametr.  
  
 **Gethandle –** zpracovává jenom ovládacích prvcích pro úpravy více řádků.  
  
 Volání **gethandle –** pro ovládací prvek v dialogovém okně pouze v případě, že byl vytvořen dialogové okno Upravit více řádků **DS_LOCALEDIT** styl nastaven příznak. Pokud **DS_LOCALEDIT** styl není nastaven, budete stále dostávat vrácená nenulová hodnota, ale nebudete moct používat vrácené hodnoty.  
  
> [!NOTE]
> **Gethandle –** nebude fungovat se systém Windows 95/98. Když zavoláte **gethandle –** v systému Windows 95/98, vrátí **NULL**. **Gethandle –** bude fungovat, jak je uvedeno v systému Windows NT 3.51 a novější verze.  
  
 Další informace najdete v tématu [EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="gethighlight"></a>  CEdit::GetHighlight  
 Získá indexy první a poslední znak v rozsahu textu, který je označený na aktuální ovládací prvek upravit.  
  
```  
BOOL GetHighlight(
    int* pichStart,   
    int* pichEnd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] `pichStart`|Index prvního znaku v rozsahu text, který je označený nule.|  
|[out] `pichEnd`|Poslední znak v rozsahu text, který je označený index počítaný od nuly.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getlimittext"></a>  CEdit::GetLimitText  
 Volání této funkce člen získat limit text pro tento `CEdit` objektu.  
  
```  
UINT GetLimitText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální text limit, v bajtech pro tento `CEdit` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Limit textu je maximální objem textu v bajtech, které může přijmout ovládací prvek upravit.  
  
> [!NOTE]
>  Tento člen funkce je k dispozici od verze systému Windows 95 a Windows NT 4.0.  
  
 Další informace najdete v tématu [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="getline"></a>  CEdit::GetLine  
 Volání této funkce pro načtení na řádku textu z ovládacího prvku úprav a umístí jej do `lpszBuffer`.  
  
```  
int GetLine(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
int GetLine(
    int nIndex,  
    LPTSTR lpszBuffer,  
    int nMaxLength) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje číslo řádku k načtení z více řádků ovládacích prvků pro úpravy. Čísla řádků jsou od nuly; Hodnota 0 určuje první řádek. Tento parametr je ignorován v jednořádkové textové pole.  
  
 `lpszBuffer`  
 Body do vyrovnávací paměti, která obdrží kopii řádku. První slovo vyrovnávací paměti, musíte zadat maximální počet znaků, které je možné zkopírovat do vyrovnávací paměti.  
  
 `nMaxLength`  
 Určuje maximální počet bajtů, které je možné zkopírovat do vyrovnávací paměti. `GetLine` Tato hodnota umístí první slovo `lpszBuffer` před uskutečněním hovoru do systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů ve skutečnosti zkopírovat. Vrácená hodnota je 0, pokud číslo řádku určuje `nIndex` je větší než počet řádků v ovládacím prvku upravit.  
  
### <a name="remarks"></a>Poznámky  
 Zkopírovaného řádku neobsahuje znak ukončení hodnotu null.  
  
 Další informace najdete v tématu [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>  CEdit::GetLineCount  
 Volání této funkce se načíst počet řádků v ovládacím prvku upravit více řádků.  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo obsahující počet řádků v řádku více ovládacích prvků pro úpravy. Pokud nebyl zadán žádný text do textového pole, je vrácenou hodnotu 1.  
  
### <a name="remarks"></a>Poznámky  
 `GetLineCount` pouze zpracovává ovládacích prvcích pro úpravy více řádků.  
  
 Další informace najdete v tématu [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="getmargins"></a>  CEdit::GetMargins  
 Volání této funkce člen načíst levý a pravý okraj tento ovládací prvek upravit.  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka levého okraje v nejnižší **WORD** a šířka pravého okraje postupně vysokou **WORD**.  
  
### <a name="remarks"></a>Poznámky  
 Okraje se měří v pixelech.  
  
> [!NOTE]
>  Tento člen funkce je k dispozici od verze systému Windows 95 a Windows NT 4.0.  
  
 Další informace najdete v tématu [EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="getmodify"></a>  CEdit::GetModify  
 Volání této funkce určete, zda obsah ovládacích prvků pro úpravy byl změněn.  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud obsah ovládacího prvku úpravy byl změněn; 0, pokud budou mít zůstává beze změny.  
  
### <a name="remarks"></a>Poznámky  
 Windows udržuje interní příznak označující, zda se změnily obsah ovládacích prvků pro úpravy. Tento příznak není zaškrtnuto, když textové pole je poprvé vytvořen a může být také vymazán voláním [SetModify](#setmodify) – členská funkce.  
  
 Další informace najdete v tématu [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar  
 Volání této funkce se načíst heslo znak, který se zobrazí v ovládacím prvku upravit, pokud uživatel zadá text.  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje znak, který se má zobrazit místo znak, který uživatel zadal. Vrácená hodnota je `NULL` pokud existuje znak žádné heslo.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vytvoříte textové pole s **es_password –** styl, knihovny DLL, která podporuje ovládací prvek určuje výchozí znakovou heslo. Manifest nebo [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) metoda určuje, které knihovny DLL podporuje ovládací prvek upravit. Pokud user32.dll podporuje ovládací prvek úprav, výchozí heslo znak je znak HVĚZDIČKY ('* ', U + 002A). Pokud verze souboru comctl32.dll 6 podporuje ovládací prvek upravit, je výchozí znakovou ČERNÉ KRUHU ('●', U + 25CF). Další informace o který DLL a verze podporuje běžné ovládací prvky, najdete v části [prostředí a běžné ovládací prvky verze](http://msdn.microsoft.com/library/windows/desktop/bb776779).  
  
 Tato metoda odesílá [EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="getrect"></a>  CEdit::GetRect  
 Volání této funkce můžete získat formátování rámeček ovládacích prvků pro úpravy.  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura, která přijímá formátování rámeček.  
  
### <a name="remarks"></a>Poznámky  
 Formátování rámeček je limitující rámeček textu, která je nezávislá na velikosti okna textové pole.  
  
 Formátování rámeček ovládacích prvků pro úpravy více řádků mohou být upravena [setrect –](#setrect) a [SetRectNP](#setrectnp) členské funkce.  
  
 Další informace najdete v tématu [EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::LimitText](#limittext).  
  
##  <a name="getsel"></a>  CEdit::GetSel  
 Volání této funkce můžete získat počáteční a koncovou umístění znaku aktuálního výběru (pokud existuje) v ovládacím prvku upravit pomocí návratovou hodnotu nebo parametry.  
  
```  
DWORD GetSel() const;  
  
void GetSel(
    int& nStartChar,  
    int& nEndChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartChar`  
 Odkaz na celé číslo, které obdrží pozice prvního znaku v aktuálním výběru.  
  
 `nEndChar`  
 Odkaz na celé číslo, které obdrží pozice prvního znaku nevybrané za koncem aktuální výběr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Verze, která vrací `DWORD` vrátí hodnotu, která obsahuje počáteční pozice v aplikaci word nejnižší a pozice prvního znaku nevybrané po skončení výběr v aplikaci word vysokou pořadí.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip  
 Skryje všechny tipu s přidružené k aktuální ovládací prvek upravit.  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce odesílá [EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="limittext"></a>  CEdit::LimitText  
 Volání této funkce můžete omezit délku textu, který může uživatel zadat do ovládací prvek upravit.  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nChars`  
 Určuje text, který může uživatel zadat délku (v bajtech). Pokud má parametr hodnotu 0, délka textu je nastavena na **uint_max –** bajtů. Toto je výchozí chování.  
  
### <a name="remarks"></a>Poznámky  
 Změna textu limit omezuje pouze text, který může uživatel zadat. Je již nemá žádný vliv na jakýkoli text v textovém poli ani neovlivní délku textu zkopírovat do ovládacího prvku upravit podle [SetWindowText](cwnd-class.md#setwindowtext) – členská funkce v `CWnd`. Pokud aplikace používá `SetWindowText` umístit další text do ovládacího prvku úprav, než je zadaný ve volání funkce `LimitText`, uživatel může odstraní všechny textu v rámci ovládací prvek upravit. Text limit však bude brání uživateli, nahradí existující text novým textem, pokud odstraňování aktuální výběr způsobí, že text, který má klesnou pod text limit.  
  
> [!NOTE]
>  V systému Win32 (systému Windows NT a systém Windows 95/98), [SetLimitText](#setlimittext) nahrazuje tuto funkci.  
  
 Další informace najdete v tématu [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="linefromchar"></a>  CEdit::LineFromChar  
 Volání této funkce načíst řádek číslo řádku, který obsahuje index zadaný znak.  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje hodnotu index o základu 0 pro požadovaný znak v textu ovládacích prvků pro úpravy, nebo obsahuje hodnotu -1. Pokud `nIndex` je -1, určuje aktuálního řádku, tedy řádek, který obsahuje pomocí kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků od nuly řádek obsahující znakový index určeného `nIndex`. Pokud `nIndex` je -1, vrátí se číslo řádku, který obsahuje první znak výběru. Pokud není nic vybráno, bude vrácena aktuální číslo řádku.  
  
### <a name="remarks"></a>Poznámky  
 Znakový index je počet znaků od začátku ovládacích prvků pro úpravy.  
  
 Tento člen funkce slouží pouze ovládacích prvcích pro úpravy více řádků.  
  
 Další informace najdete v tématu [EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="lineindex"></a>  CEdit::LineIndex  
 Volání ovládacích prvků pro úpravy této funkci můžete načíst znakový index řádku v rámci více řádků.  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nLine`  
 Obsahuje hodnotu indexu pro požadovaný řádek v textu ovládacích prvků pro úpravy nebo -1. Pokud `nLine` je -1, určuje aktuálního řádku, tedy řádek, který obsahuje pomocí kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Znakový index řádku zadaný v `nLine` nebo -1, pokud zadané číslo řádku je větší než počet řádků v ovládacím prvku upravit.  
  
### <a name="remarks"></a>Poznámky  
 Znakový index je počet znaků od začátku ovládacích prvků pro úpravy, který má zadaný řádek.  
  
 Tato funkce člen pouze zpracovává ovládacích prvcích pro úpravy více řádků.  
  
 Další informace najdete v tématu [EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="linelength"></a>  CEdit::LineLength  
 Načte délka řádku v ovládacím prvku upravit.  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nLine`  
 Index založený na nule znaku v řádku, jehož délka má být načtena. Výchozí hodnota je -1.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota pro ovládacích prvcích pro úpravy jeden řádek, je délka, v `TCHAR`s textu v textovém poli.  
  
 Návratovou hodnotu pro ovládacích prvcích pro úpravy Víceřádkový, je délka, v `TCHAR`s řádku určeného `nLine` parametr. Pro [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] text, délka je počet bajtů v řádku; pro text v kódu Unicode, délka je počet znaků v řádku. Délka neobsahuje znak návratu na konec řádku.  
  
 Pokud `nLine` parametr je větší než počet znaků v ovládacím prvku, návratovou hodnotu nula.  
  
 Pokud `nLine` parametr -1, návratová hodnota je počet nezaškrtnuté znaků řádky, které obsahují vybrané znaky. Například pokud výběr rozšiřuje z čtvrtý znak jeden řádek prostřednictvím osmého znaků z konce na další řádek, návratová hodnota je 10. To znamená tři znaky na první řádek a 7 na další.  
  
 Další informace o `TCHAR` zadejte najdete `TCHAR` řádek v tabulce v [Windows datové typy](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda podporuje [EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::LineIndex](#lineindex).  
  
##  <a name="linescroll"></a>  CEdit::LineScroll  
 Volání ovládacích prvků pro úpravy této funkci můžete posuňte text více řádků.  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nLines`  
 Určuje počet řádků posunu svisle.  
  
 `nChars`  
 Určuje počet pozic znak, který má vodorovný posun. Tato hodnota je ignorována, pokud má ovládací prvek upravit buď **es_right –** nebo **es_center –** stylu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen zpracovává jenom ovládacích prvcích pro úpravy více řádků.  
  
 Ovládací prvek upravit neposouvá svisle za poslední řádek textu v textovém poli. Pokud aktuální řádek plus počet řádků určeného `nLines` větší než celkový počet řádků v ovládacím prvku úprav, hodnota se nastaví tak, aby poslední řádek ovládacích prvků pro úpravy je přechod na horní části okna textové pole.  
  
 `LineScroll` slouží k vodorovnému posouvání za jeho poslední znak kterýkoli řádek.  
  
 Další informace najdete v tématu [EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::GetFirstVisibleLine](#getfirstvisibleline).  
  
##  <a name="paste"></a>  CEdit::Paste  
 Volání této funkce můžete vložit data ze schránky do `CEdit` na pozici kurzoru.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Poznámky  
 Vloží se data jenom v případě, že schránky obsahuje data v **CF_TEXT** formátu.  
  
 Další informace najdete v tématu [WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="posfromchar"></a>  CEdit::PosFromChar  
 Volání této funkce se získá pozice (levého horního rohu) daného znaku v rámci to `CEdit` objektu.  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nChar`  
 Index založený na nule z určeného znaku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Souřadnice levého horního rohu určeného znaku `nChar`.  
  
### <a name="remarks"></a>Poznámky  
 Znak, který je zadán tím, že její hodnota index o základu 0. Pokud `nChar` je větší než index poslední znak v tomto `CEdit` objektu návratovou hodnotu určuje souřadnice znak na pozici právě za jeho poslední znak v tomto `CEdit` objektu.  
  
> [!NOTE]
>  Tento člen funkce je k dispozici od verze systému Windows 95 a Windows NT 4.0.  
  
 Další informace najdete v tématu [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::LineFromChar](#linefromchar).  
  
##  <a name="replacesel"></a>  CEdit::ReplaceSel  
 Volání této funkce nahradit aktuální výběr v ovládacím prvku upravit textem určeným parametrem `lpszNewText`.  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewText`  
 Body obsahující text, kterým do řetězce ukončené hodnotou null.  
  
 `bCanUndo`  
 Chcete-li určit, že tato funkce může být vrátit zpět, nastavte hodnotu tohoto parametru k **TRUE** . Výchozí hodnota je **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Nahradí pouze část textu v ovládacím prvku upravit. Pokud chcete nahradit celý text, použijte [CWnd::SetWindowText](cwnd-class.md#setwindowtext) – členská funkce.  
  
 Pokud není žádná aktuální výběr, text, kterým je vložen do aktuálního umístění kurzoru.  
  
 Další informace najdete v tématu [EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::LineIndex](#lineindex).  
  
##  <a name="setcuebanner"></a>  CEdit::SetCueBanner  
 Nastaví text, který se zobrazí jako text cue, nebo tip, v upravíte řídit, kdy ovládací prvek je prázdný.  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszText`  
 Ukazatel na řetězec, který obsahuje cue k zobrazení v ovládacím prvku upravit.  
  
 [v] `fDrawWhenFocused`  
 Pokud `false`, Banner informující o cue není vykreslován, když uživatel klikne v ovládacím prvku upravit a bude vybrán ovládacího prvku.  
  
 Pokud `true`, Banner informující o cue vykreslením i v případě, že má právě fokus, ovládacího prvku. Hlavička cue zmizí, když uživatel spustí na typ v ovládacím prvku.  
  
 Výchozí hodnota je `false`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je metoda úspěšná. v opačném případě `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639) zprávy, která je popsána v sadě Windows SDK. Další informace najdete v tématu [Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703) makro.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje [CEdit::SetCueBanner](#setcuebanner) metoda.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="sethandle"></a>  CEdit::SetHandle  
 Volání ovládacích prvků pro úpravy této funkce lze nastavit popisovač k místní paměti, který se použije více řádků.  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>Parametry  
 *hBuffer*  
 Obsahuje popisovač pro místní paměti. Tento popisovač musí být vytvořen pomocí předchozího volání [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) pomocí funkce Windows **LMEM_MOVEABLE** příznak. Paměť se předpokládá, že obsahují řetězce ukončené hodnotou null. Pokud tomu tak není, první bajt přidělené paměti by měla nastavena na hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvek upravit pak použije této vyrovnávací paměti k uložení aktuálně zobrazený text místo přidělení vyrovnávací paměti.  
  
 Tato funkce člen zpracovává jenom ovládacích prvcích pro úpravy více řádků.  
  
 Předtím, než aplikaci nastaví nový popisovač paměti, měli používat [gethandle –](#gethandle) – členská funkce se získat popisovač aktuální vyrovnávací paměti a volné této paměti pomocí **LocalFree** funkce systému Windows.  
  
 `SetHandle` Vymaže vrácení zpět vyrovnávací paměti ( [CanUndo](#canundo) – členská funkce vrátí 0) a příznak interní úpravy ( [GetModify](#getmodify) – členská funkce vrátí 0). Bude překreslen okno textové pole.  
  
 Můžete použít tuto funkci člen v ovládacím prvku upravit více řádků v dialogovém okně pouze v případě, že jste vytvořili dialogové okno s **DS_LOCALEDIT** styl nastaven příznak.  
  
> [!NOTE]
> **Gethandle –** nebude fungovat se systém Windows 95/98. Když zavoláte **gethandle –** v systému Windows 95/98, vrátí **NULL**. **Gethandle –** bude fungovat, jak je uvedeno v systému Windows NT 3.51 a novější verze.  
  
 Další informace najdete v tématu [EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641), [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), a [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="sethighlight"></a>  CEdit::SetHighlight  
 Označuje a rozsah text, který se zobrazí v aktuální ovládacích prvků pro úpravy.  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `ichStart`|Index prvního znaku v rozsahu textu, abyste měli na očích nule.|  
|[v] `ichEnd`|Index počítaný od nuly poslední znak v rozsahu textu, abyste měli na očích.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="setlimittext"></a>  CEdit::SetLimitText  
 Volání této funkce člen se nastavit limit text pro tento `CEdit` objektu.  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nMax`  
 Nový text limit, ve znacích.  
  
### <a name="remarks"></a>Poznámky  
 Limit textu je maximální objem textu ve znacích, které může přijmout ovládací prvek upravit.  
  
 Změna textu limit omezuje pouze text, který může uživatel zadat. Je již nemá žádný vliv na jakýkoli text v textovém poli ani neovlivní délku textu zkopírovat do ovládacího prvku upravit podle [SetWindowText](cwnd-class.md#setwindowtext) – členská funkce v `CWnd`. Pokud aplikace používá `SetWindowText` umístit další text do ovládacího prvku úprav, než je zadaný ve volání funkce `LimitText`, uživatel může odstraní všechny textu v rámci ovládací prvek upravit. Text limit však bude brání uživateli, nahradí existující text novým textem, pokud odstraňování aktuální výběr způsobí, že text, který má klesnou pod text limit.  
  
 Tato funkce nahrazuje [LimitText](#limittext) v Win32.  
  
 Další informace najdete v tématu [EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="setmargins"></a>  CEdit::SetMargins  
 Volejte tuto metodu a nastavit levý a pravý okraj tento ovládací prvek upravit.  
  
```  
void SetMargins(
    UINT nLeft,  
    UINT nRight);
```  
  
### <a name="parameters"></a>Parametry  
 *nLeft*  
 Šířka nové levým okrajem, v pixelech.  
  
 *nRight*  
 Šířka nové pravým okrajem, v pixelech.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tento člen funkce je k dispozici od verze systému Windows 95 a Windows NT 4.0.  
  
 Další informace najdete v tématu [EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="setmodify"></a>  CEdit::SetModify  
 Volání této funkce, nastavení nebo vymazání příznaku upravené pro ovládací prvek upravit.  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Hodnota **TRUE** byla změněna text a hodnota **FALSE** označuje je beze změny. Ve výchozím nastavení je upravený nastavený příznak.  
  
### <a name="remarks"></a>Poznámky  
 Příznak upravené označuje, zda byla změněna textu v rámci ovládací prvek upravit. Bude automaticky nastavena vždy, když uživatel změní text. Jeho hodnotu může načíst pomocí [GetModify](#getmodify) – členská funkce.  
  
 Další informace najdete v tématu [EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::GetModify](#getmodify).  
  
##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar  
 Volání této funkce, nastavení nebo odebrání heslo znak zobrazí v ovládacím prvku upravit, pokud uživatel zadá text.  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>Parametry  
 *ch*  
 Určuje znaku, který se zobrazí místo znaky zadané uživatelem. Pokud *ch* je 0, jsou zobrazeny skutečnými znaky zadané uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 Když je heslo znaková sada, zobrazí se tento znak pro každý znak typy uživatelů.  
  
 Tato funkce člen nemá žádný vliv na více řádků ovládacích prvků pro úpravy.  
  
 Když `SetPasswordChar` – členská funkce je volána, `CEdit` překreslí všechny viditelné znaky pomocí určeného znaku *ch*.  
  
 Pokud se vytvoří textové pole s [es_password –](styles-used-by-mfc.md#edit-styles) styl, výchozí znak hesla je nastaven na znak hvězdičky ( **\***). Tento styl se odebere, když `SetPasswordChar` je volán s *ch* nastaven na hodnotu 0.  
  
 Další informace najdete v tématu [EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="setreadonly"></a>  CEdit::SetReadOnly  
 Volání této funkce lze nastavit jen pro čtení stav ovládacích prvků pro úpravy.  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bReadOnly`  
 Určuje, zda chcete nastavit nebo odebrat jen pro čtení stavu ovládacích prvků pro úpravy. Hodnota **TRUE** nastaví stav jen pro čtení; hodnota **FALSE** nastaví stav pro čtení a zápis.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je operace úspěšná, nebo dojde k 0, pokud se chyba.  
  
### <a name="remarks"></a>Poznámky  
 Aktuální nastavení naleznete otestováním [es_readonly –](styles-used-by-mfc.md#edit-styles) příznak v návratové hodnotě [CWnd::GetStyle](cwnd-class.md#getstyle).  
  
 Další informace najdete v tématu [EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="setrect"></a>  CEdit::SetRect  
 Volejte tuto funkci nastavit dimenze obdélníku pomocí zadaných souřadnic.  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který určuje nové dimenze formátování rámečku.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen zpracovává jenom ovládacích prvcích pro úpravy více řádků.  
  
 Použití `SetRect` formátování obdélníku čáry více ovládacích prvků pro úpravy. Formátování rámeček je limitující rámeček textu, která je nezávislá na velikosti okna textové pole. Při prvním vytvoření ovládacího prvku úprav formátování rámeček je stejný jako klientské oblasti okna textové pole. Pomocí `SetRect` – členská funkce aplikace můžete nastavit formátování obdélníku, větší nebo menší než okno textové pole.  
  
 Pokud ovládací prvek upravit žádné posuvník, text bude oříznut, není zabalená, pokud formátování rámeček je větší než interval. Pokud ovládací prvek upravit obsahuje ohraničení, je formátování rámeček snížit velikost ohraničení. Pokud upravíte rámeček vrácený `GetRect` – členská funkce než předáte obdélníku do, musíte odebrat velikost ohraničení `SetRect`.  
  
 Když `SetRect` nazývá textové pole je text je také naformátována a zobrazí znovu.  
  
 Další informace najdete v tématu [EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="setrectnp"></a>  CEdit::SetRectNP  
 Volání ovládacích prvků pro úpravy této funkce můžete nastavit formátování obdélník více řádků.  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Odkazuje na `RECT` struktura nebo `CRect` objekt, který určuje nové dimenze rámečku.  
  
### <a name="remarks"></a>Poznámky  
 Formátování rámeček je limitující rámeček textu, která je nezávislá na velikosti okna textové pole.  
  
 `SetRectNP` je stejný jako `SetRect` člen fungovat s tím rozdílem, že není překreslen okno textové pole.  
  
 Při prvním vytvoření ovládacího prvku úprav formátování rámeček je stejný jako klientské oblasti okna textové pole. Při volání `SetRectNP` – členská funkce aplikace můžete nastavit formátování obdélníku, větší nebo menší než okno textové pole.  
  
 Pokud ovládací prvek upravit žádné posuvník, text bude oříznut, není zabalená, pokud formátování rámeček je větší než interval.  
  
 Tento člen zpracovává jenom ovládacích prvcích pro úpravy více řádků.  
  
 Další informace najdete v tématu [EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::SetRect](#setrect).  
  
##  <a name="setsel"></a>  CEdit::SetSel  
 Volání této funkce můžete vybrat rozsah znaků v ovládacím prvku upravit.  
  
```  
void SetSel(
    DWORD dwSelection,  
    BOOL bNoScroll = FALSE);

 
void SetSel(
    int nStartChar,  
    int nEndChar,  
    BOOL bNoScroll = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *dwSelection*  
 Určuje počáteční pozici v aplikaci word nejnižší a koncovou pozici v aplikaci word vysokou pořadí. Pokud aplikace word nejnižší 0 a horní word -1, je vybrána veškerého textu v textovém poli. Pokud aplikace word nejnižší hodnotu -1, odeberou se všechny aktuální výběr.  
  
 *bNoScroll*  
 Určuje, zda by měl být vsuvka přešli do zobrazení. Pokud **FALSE**, pomocí kurzoru přesunut do zobrazení oblasti. Pokud **TRUE**, pomocí kurzoru není přesunut do zobrazení oblasti.  
  
 `nStartChar`  
 Určuje počáteční pozici. Pokud `nStartChar` je 0 a `nEndChar` je -1, všechny je vybraný text v textovém poli. Pokud `nStartChar` je -1, všechny aktuální výběr je odebrat.  
  
 `nEndChar`  
 Určuje koncovou pozici.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEdit::GetSel](#getsel).  
  
##  <a name="settabstops"></a>  CEdit::SetTabStops  
 Volání ovládacích prvků pro úpravy této funkce můžete nastavit zarážky ve více řádků.  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>Parametry  
 `cxEachStop`  
 Určuje, že jsou zarážek nastavený na každý `cxEachStop` jednotky dialogu.  
  
 `nTabStops`  
 Určuje počet zarážek obsažené v `rgTabStops`. Toto číslo musí být větší než 1.  
  
 `rgTabStops`  
 Odkazuje na pole nepodepsané celých čísel zadání kartě zastaví v jednotky dialogu. Jednotky dialogu je vzdálenost vodorovně nebo svisle. Jednu jednotku vodorovné dialogové okno je rovna jedné čtvrtý aktuální základní šířka jednotky dialogu a osmina aktuální základní výška jednotky dialogu rovná 1 jednotka svislé dialogové okno. Základní jednotky dialogu se vypočítávají podle výšky a šířky aktuálním písmem systému. **GetDialogBaseUnits** funkce systému Windows vrátí dialogu aktuální základní jednotky v pixelech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla nastavena na karty; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Po zkopírování textu do ovládacího prvku úprav více řádků způsobí, že místa pro vygenerování až na další zarážku libovolný znak karta v textu.  
  
 K nastavení zarážek tabulátoru na výchozí velikost 32 jednotky dialogu, volání bez parametrů verze této funkce člen. Chcete-li nastavení zarážek velikost než 32, volejte verzi s `cxEachStop` parametr. Nastavení zarážek na pole velikosti, použijte verzi s dva parametry.  
  
 Tato funkce člen pouze zpracovává ovládacích prvcích pro úpravy více řádků.  
  
 `SetTabStops` není ho překreslit automaticky okna upravit. Pokud změníte tabulátorů pro text již v ovládacím prvku úprav, volání [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) k ho překreslit okna upravit.  
  
 Další informace najdete v tématu [EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663) a [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CEditView::SetTabStops](ceditview-class.md#settabstops).  
  
##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip  
 Zobrazí bublinách tip, který je přidružen aktuální ovládací prvek upravit.  
  
```  
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

 
BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,   
    LPCWSTR lpszText,   
    INT ttiIcon = TTI_NONE);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `pEditBalloonTip`|Ukazatel na [EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466) struktura, která popisuje balloon špičky.|  
|[v] `lpszTitle`|Ukazatel na řetězec znaků Unicode, který obsahuje název balloon špičky.|  
|[v] `lpszText`|Ukazatel na řetězec obsahující text tip bubliny.|  
|[v] `ttiIcon`|`INT` Určující typ tip bublinách přidružit ikonu. Výchozí hodnota je `TTI_NONE`. Další informace najdete v tématu `ttiIcon` členem [EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466) struktury.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce odesílá [EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668) zprávy, která je popsána v sadě Windows SDK. Další informace najdete v tématu [Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707) makro.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_cedit`, který používá pro přístup k aktuální ovládací prvek upravit. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu zobrazuje bublinách tip pro ovládací prvek upravit. [CEdit::ShowBalloonTip](#showballoontip) metoda určuje text nadpisu a bublinách tip.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="undo"></a>  CEdit::Undo  
 Volání této funkce můžete vrátit zpět poslední akci textové pole.  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pro ovládací prvek upravit jeden řádek je vždy návratovou hodnotu nenulové hodnoty. Pro ovládací prvek upravit více řádků, je vrácenou hodnotu nenulové hodnoty, pokud operace vrácení zpět je úspěšné, nebo 0, pokud dojde k selhání operace vrácení zpět.  
  
### <a name="remarks"></a>Poznámky  
 Operace vrácení zpět může být také vrátit zpět. Například můžete obnovit odstraněné textu s prvním volání **vrátit zpět**. Také neprobíhá žádná použité operace upravit, můžete odebrat text znovu s druhé volání **vrátit zpět**.  
  
 Další informace najdete v tématu [EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Ukázka CMNCTRL2 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](cwnd-class.md)   
 [CButton – třída](cbutton-class.md)   
 [CComboBox – třída](ccombobox-class.md)   
 [Clistbox – třída](clistbox-class.md)   
 [CScrollBar – třída](cscrollbar-class.md)   
 [CStatic – třída](cstatic-class.md)   
 [CDialog – třída](cdialog-class.md)
