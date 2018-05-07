---
title: CStatusBarCtrl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f34711389478997b3e2c43cb2d812b1b961df714
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl – třída
Poskytuje funkce ovládacího panelu Windows běžné stavu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Vytvoří `CStatusBarCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|Vytvoří ovládací panel stav a připojí jej k `CStatusBarCtrl` objektu.|  
|[CStatusBarCtrl::CreateEx](#createex)|Vytvoří ovládací prvek panelu stavu s zadaný Windows rozšířené styly a připojí jej k `CStatusBarCtrl` objektu.|  
|[CStatusBarCtrl::DrawItem](#drawitem)|Volá se při visual aspektů změny ovládací prvek panelu stavu vykreslování vlastníka.|  
|[CStatusBarCtrl::GetBorders](#getborders)|Načte aktuální šířky vodorovného a svislého ohraničení ovládacího prvku panel stav.|  
|[CStatusBarCtrl::GetIcon](#geticon)|Načte ikonu pro část (také označované jako podokno) v ovládacím panelu aktuální stav.|  
|[CStatusBarCtrl::GetParts](#getparts)|Načte počet částí v ovládacím prvku panel stav.|  
|[CStatusBarCtrl::GetRect](#getrect)|Načte ohraničující obdélník součástí v ovládacím prvku panel stav.|  
|[CStatusBarCtrl::GetText](#gettext)|Načte text z části daného ovládacího prvku panel stav.|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Načtěte délka ve znacích textu z části daného ovládacího prvku panel stav.|  
|[CStatusBarCtrl::GetTipText](#gettiptext)|Načte text popisku pro podokně ve stavovém řádku.|  
|[CStatusBarCtrl::IsSimple](#issimple)|Ověří prvku okno Stav zjistit, pokud je v jednoduchém režimu.|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ve stavovém řádku.|  
|[CStatusBarCtrl::SetIcon](#seticon)|Nastaví na ikonu podokno ve stavovém řádku.|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Nastaví minimální výšku stav panelu oblast vykreslování ovládacího prvku.|  
|[CStatusBarCtrl::SetParts](#setparts)|Nastaví počet částí ve stavovém řádku řízení a souřadnice pravého okraje jednotlivých součástí.|  
|[CStatusBarCtrl::SetSimple](#setsimple)|Určuje, zda ovládacího prvku stav panelu zobrazí jednoduchý text nebo zobrazí všechny části řízení nastavit voláním předchozí `SetParts`.|  
|[CStatusBarCtrl::SetText](#settext)|Nastaví text, pro danou část ovládacího prvku panel stav.|  
|[CStatusBarCtrl::SetTipText](#settiptext)|Nastaví text popisku pro podokno ve stavovém řádku.|  
  
## <a name="remarks"></a>Poznámky  
 "Stav panel ovládacího prvku" je v časovém období vodorovné, obvykle zobrazují v dolní části nadřazeného okna, ve kterém aplikace můžete zobrazit různé typy informací o stavu. Ovládací prvek panelu stavu můžete rozdělit na části zobrazíte víc než jeden typ informací.  
  
 Tento ovládací prvek (a proto `CStatusBarCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Další informace o používání `CStatusBarCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="create"></a>  CStatusBarCtrl::Create  
 Vytvoří ovládací panel stav a připojí jej k `CStatusBarCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl panelu řízení stavu. Použít libovolnou kombinaci stavový řádek – styly ovládacích prvků uvedených v [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) ve Windows SDK. Tento parametr musí obsahovat **ws_child –** stylu. Měl by obsahovat také **ws_visible –** stylu.  
  
 `rect`  
 Určuje velikost a umístění ovládacích prvků panelu stavu. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura.  
  
 `pParentWnd`  
 Určuje stav panelu ovládacího prvku nadřazeného okna, obvykle `CDialog`. Nesmí být **hodnotu NULL.**  
  
 `nID`  
 Určuje ID ovládacího prvku panel stav.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CStatusBarCtrl` ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří ovládacího prvku panel stav a připojí jej k `CStatusBarCtrl` objektu.  
  
 Výchozí umístění stavu okna je podél dolního okraje nadřazeného okna, ale můžete zadat `CCS_TOP` styl, který se následně zobrazí v horní části okna nadřazené klientské oblasti. Můžete zadat **SBARS_SIZEGRIP** styl zahrnout úchyt na pravém konci stavové okno. Kombinování `CCS_TOP` a **SBARS_SIZEGRIP** styly se nedoporučuje, protože výsledná úchyt není funkční, i když systém nevykresluje se v okně Stav.  
  
 Chcete-li vytvořit stavového řádku s rozšířené styly oken, volejte [CStatusBarCtrl::CreateEx](#createex) místo **vytvořit**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CStatusBarCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CStatusBarCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje styl panelu řízení stavu. Použít libovolnou kombinaci stavový řádek – styly ovládacích prvků uvedených v [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) ve Windows SDK. Tento parametr musí obsahovat **ws_child –** stylu. Měl by obsahovat také **ws_visible –** stylu.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl  
 Vytvoří `CStatusBarCtrl` objektu.  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem  
 Voláno rámcem při visual aspektů změny ovládací prvek panelu stavu vykreslování vlastníka.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Dlouhé ukazatel [drawitemstruct –](http://msdn.microsoft.com/library/windows/desktop/bb775802) struktura, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** členem `DRAWITEMSTRUCT` struktura definuje kreslení akci, která má být provedena.  
  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CStatusBarCtrl` objektu.  
  
 Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před tento člen funkce ukončí.  
  
##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders  
 Načte ovládací prvek panelu Stav aktuální šířky vodorovného a svislého ohraničení a mezery mezi obdélníky.  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pBorders*  
 Adresa má tři prvky pole celé číslo. Šířka ohraničení vodorovné přijme první prvek, druhý obdrží šířka ohraničení svislé a třetí obdrží šířka ohraničení mezi obdélníky.  
  
 *nHorz*  
 Odkaz na celé číslo, které obdrží šířka ohraničení vodorovné.  
  
 *Veďte*  
 Odkaz na celé číslo, které obdrží šířka ohraničení svislý.  
  
 *nSpacing*  
 Odkaz na celé číslo, které obdrží šířka ohraničení mezi obdélníky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Tyto hranice určuje mezery mezi vnějšího okraje ovládacího prvku a obdélníky v ovládacím prvku, které obsahují text.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon  
 Načte ikonu pro část (také označované jako podokno) v ovládacím panelu aktuální stav.  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `iPart`|Index založený na nule části, která obsahuje ikonu, která mají být načteny. Pokud má parametr hodnotu -1, se předpokládá stavového řádku, jako jednoduchý režim stavového řádku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač ikonu Pokud metoda úspěšná. v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744) zprávy, která je popsána v sadě Windows SDK.  
  
 Ovládací prvek panelu stavu se skládá z řádek podokna výstup textu, které se také označují jako částí. Další informace o stavový řádek najdete v tématu [stav implementace řádku v prostředí MFC](../../mfc/status-bar-implementation-in-mfc.md) a [nastavení režimu objektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_statusBar`, který používá pro přístup k aktuální stav panel ovládacího prvku. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu zkopíruje ikonu na dvě podokna ovládacího panelu aktuální stav. V předcházející části příklad kódu jsme vytvořili ovládací prvek panelu stavu s tři podokna a pak přidá do podokna první ikonu. Tento příklad načte ikonu z podokna první a přidá ji do druhé a třetí podokně.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>  CStatusBarCtrl::GetParts  
 Načte počet částí v ovládacím prvku panel stav.  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nParts`  
 Počet částí, pro které chcete načíst souřadnice. Pokud tento parametr je vyšší než počet částí v ovládacím prvku, načte zprávu souřadnice pouze existující části.  
  
 *pParts*  
 Adresa celočíselné pole mají stejný počet elementů jako počet částí určeného `nParts`. Každý prvek v poli, obdrží klient souřadnice pravého okraje odpovídající části. Pokud element je nastaven na hodnotu - 1, pozice pravý okraj pro tuto část rozšiřuje na pravý okraj stavový řádek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet částí v ovládacím prvku v případě úspěchu nebo nula, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen také načte souřadnice pravého okraje zadaný počet částí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>  CStatusBarCtrl::GetRect  
 Načte ohraničující obdélník součástí v ovládacím prvku panel stav.  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Index nule části, jejichž ohraničující obdélník je mají být načteny.  
  
 `lpRect`  
 Adresa [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která přijímá ohraničující obdélník.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>  CStatusBarCtrl::GetText  
 Načte text z části daného ovládacího prvku panel stav.  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Adresa vyrovnávací paměti, která přijímá text. Tento parametr je řetězce ukončené hodnotou null.  
  
 `nPane`  
 Index nule části, ze kterého chcete načíst text.  
  
 `pType`  
 Ukazatel na celé číslo, které obdrží informace o typu. Typ může být jedna z těchto hodnot:  
  
- **0** text se vykresluje ohraničení zobrazí nižší než roviny tohoto stavový řádek.  
  
- `SBT_NOBORDERS` Text se nevykreslí bez ohraničení.  
  
- `SBT_POPOUT` Text je vykresluje ohraničení zobrazí vyšší než roviny tohoto stavový řádek.  
  
- `SBT_OWNERDRAW` Pokud má text `SBT_OWNERDRAW` kreslení typu `pType` obdrží tuto zprávu a vrátí hodnotu 32-bit přidružené textu místo typ délku a operace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka ve znacích textu nebo [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující aktuální text.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>  CStatusBarCtrl::GetTextLength  
 Načte délka ve znacích textu z části daného ovládacího prvku panel stav.  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Index nule části, ze kterého chcete načíst text.  
  
 `pType`  
 Ukazatel na celé číslo, které obdrží informace o typu. Typ může být jedna z těchto hodnot:  
  
- **0** text se vykresluje ohraničení zobrazí nižší než roviny tohoto stavový řádek.  
  
- `SBT_NOBORDERS` Text se nevykreslí bez ohraničení.  
  
- `SBT_OWNERDRAW` Text je vykreslen pomocí nadřazeného okna.  
  
- `SBT_POPOUT` Text je vykresluje ohraničení zobrazí vyšší než roviny tohoto stavový řádek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka ve znacích textu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>  CStatusBarCtrl::GetTipText  
 Načte text popisku pro podokně ve stavovém řádku.  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Index založený na nule panelu řádku stav přijímat text popisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující text, který se použije v popisu tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple  
 Ověří prvku okno Stav zjistit, pokud je v jednoduchém režimu.  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je kontrola okno Stav v jednoduchém režimu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor  
 Nastaví barvu pozadí ve stavovém řádku.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parametry  
 `cr`  
 **COLORREF** hodnotu, která určuje barvu pozadí nové. Zadejte `CLR_DEFAULT` hodnoty způsobila stavovém řádku použijte jeho výchozí barvu pozadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která představuje předchozí výchozí barvu pozadí.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon  
 Nastaví na ikonu podokno ve stavovém řádku.  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Index založený na nule podokna, která bude přijímat ikonu. Pokud má parametr hodnotu -1, stavový řádek se považuje za jednoduché stavového řádku.  
  
 `hIcon`  
 Zpracování na ikonu nastavení. Pokud je tato hodnota **NULL**, na ikonu se odebere z části.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CStatusBarCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight  
 Nastaví minimální výšku stav panelu oblast vykreslování ovládacího prvku.  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Minimální výška v pixelech, ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Minimální výška je součet hodnot `nMin` a dvakrát šířku v pixelech svislé ohraničení ovládacího prvku panel stav.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>  CStatusBarCtrl::SetParts  
 Nastaví počet částí ve stavovém řádku řízení a souřadnice pravého okraje jednotlivých součástí.  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>Parametry  
 `nParts`  
 Počet částí nastavit. Počet částí nemůže být větší než 255.  
  
 *pWidths*  
 Adresa celočíselné pole mají stejný počet elementů jako části určené v `nParts`. Každý prvek v poli určuje pozici souřadnice klienta, je pravý okraj odpovídající části. Pokud je element - 1, pozice pravý okraj pro tuto část rozšiřuje na pravý okraj ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple  
 Určuje, zda ovládacího prvku stav panelu zobrazí jednoduchý text nebo zobrazí všechny části řízení nastavit voláním předchozí [SetParts](#setparts).  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bSimple`  
 Příznak zobrazení type. Pokud tento parametr je `TRUE`, tento ovládací prvek zobrazí jednoduchý text; Pokud je `FALSE`, zobrazí se více částí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace změní ovládacího prvku panel stav z nejednoduchý na jednoduchý nebo naopak, systém okamžitě překreslí ovládacího prvku.  
  
##  <a name="settext"></a>  CStatusBarCtrl::SetText  
 Nastaví text, pro danou část ovládacího prvku panel stav.  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Adresa zadání text, který chcete nastavit řetězce ukončené hodnotou null. Pokud `nType` je `SBT_OWNERDRAW`, `lpszText` představuje 32 bity data.  
  
 `nPane`  
 Index počítaný od nuly část můžete nastavit. Pokud tato hodnota je 255, ovládacího prvku panel stav se považuje za jednoduchý ovládací prvek s pouze jednou ze součástí.  
  
 `nType`  
 Typ vykreslování operaci. V tématu [SB_SETTEXT zpráva](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx) seznam možných hodnot.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Zpráva by způsobila neplatnost část ovládací prvek, který změnil způsobuje zobrazit nového textu přijetí ovládacího prvku další `WM_PAINT` zprávy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>  CStatusBarCtrl::SetTipText  
 Nastaví text popisku pro podokno ve stavovém řádku.  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parametry  
 `nPane`  
 Index založený na nule panelu řádku stav přijímat text popisku.  
  
 *pszTipText*  
 Ukazatel na řetězec obsahující text popisku.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl – třída](../../mfc/reference/ctoolbarctrl-class.md)
