---
title: "CComboBoxEx – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
dev_langs: C++
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: def9fca45f36a6e161bbd4b24431c9afd20d77c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomboboxex-class"></a>CComboBoxEx – třída
Rozšiřuje ovládacího prvku pole se seznamem se tím, že poskytuje podporu pro seznamy obrázků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Vytvoří `CComboBoxEx` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComboBoxEx::Create](#create)|Pole se seznamem vytvoří a připojí jej k `CComboBoxEx` objektu.|  
|[CComboBoxEx::CreateEx](#createex)|Vytvoří pole se seznamem s zadaný Windows rozšířené styly a připojí jej k **ComboBoxEx** objektu.|  
|[CComboBoxEx::DeleteItem](#deleteitem)|Odebere položku z **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Načte ukazatel do ovládacího prvku pole se seznamem podřízené.|  
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Načte popisovač pro část ovládacího prvku úprav **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Rozšířené styly, které se používají pro načte **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::GetImageList](#getimagelist)|Načte ukazatel na seznamu obrázků se přiřadila **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::GetItem](#getitem)|Načte položku informace o danou **ComboBoxEx** položky.|  
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Určuje, jestli uživatel změnil obsah **ComboBoxEx** ovládacích prvků pro úpravy zadáním.|  
|[CComboBoxEx::InsertItem](#insertitem)|Vloží novou položku v **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly v rámci **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::SetImageList](#setimagelist)|Nastaví pro seznamu obrázků **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::SetItem](#setitem)|Nastaví atributy pro položku v **ComboBoxEx** ovládacího prvku.|  
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl rozšířeného pole se seznamem ovládacích prvků pole.|  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `CComboBoxEx` vytvořit ovládací prvky pole se seznamem, potřebujete už implementovat vlastní kreslení kód obrázku. Místo toho použijte `CComboBoxEx` do bitových kopií přístup ze seznamu obrázků.  
  
## <a name="image-list-support"></a>Podpora seznamu obrázků  
 V poli se seznamem standardní vlastník pole se seznamem zodpovídá za kreslení obrázku tak, že vytvoříte pole se seznamem jako ovládací prvek vykreslování vlastníka. Při použití `CComboBoxEx`, není nutné nastavovat kreslení styly **cbs_ownerdrawfixed –** a **cbs_hasstrings –** vzhledem k tomu, že implicitní. Jinak musíte napsat kód k provádění operací kreslení. A `CComboBoxEx` řízení podporuje až tři bitové kopie na každou položku: jeden pro vybraném stavu, jeden pro nezaškrtnuté stavu a jeden pro bitovou kopii překrytí.  
  
## <a name="styles"></a>Styly  
 `CComboBoxEx`podporuje styly **cbs_simple –**, **cbs_dropdown –**, **cbs_dropdownlist –**, a **ws_child –**. Všechny ostatní styly se předá, když vytvoříte okna se ignorují pomocí ovládacího prvku. Po vytvoření okně můžete zadat další pole se seznamem styly voláním `CComboBoxEx` – členská funkce [SetExtendedStyle](#setextendedstyle). Tyto styly můžete:  
  
-   Sada řetězec hledání v seznamu být malá a velká písmena.  
  
-   Vytvoření seznamem, používá lomítko ('/'), zpětné lomítko ('\\') a období ('. ') znaků jako oddělovače aplikace word. To umožní uživatelům přechod z aplikace word pro word, pomocí klávesové zkratky CTRL + ŠIPKA.  
  
-   Nastavení se seznamem se ovládacího prvku pole můžete zobrazit nebo nezobrazí bitovou kopii. Pokud se zobrazí žádný obrázek, můžete odebrat pole se seznamem odsazení textu, která bude vyhovovat bitovou kopii.  
  
-   Vytvoření ovládacího prvku pole se seznamem úzké, včetně Změna velikosti, takže ho klipy širší pole se seznamem, které obsahuje.  
  
 Tyto příznaky styl jsou popsány dále v [pomocí CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## <a name="item-retention-and-callback-item-attributes"></a>Uchování položky a atributů položky zpětného volání  
 Informace o položky, například indexů pro položky a bitové kopie, hodnoty odsazení a textové řetězce jsou uložené ve struktuře Win32 [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746), jak je popsáno v sadě Windows SDK. Struktura také obsahuje členy, které odpovídají příznaky zpětného volání.  
  
 Podrobné, koncepční informace, naleznete v [pomocí CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx  
 Volání této funkce člen k vytvoření `CComboBoxEx` objektu.  
  
```  
CComboBoxEx();
```  
  
##  <a name="create"></a>CComboBoxEx::Create  
 Pole se seznamem vytvoří a připojí jej k `CComboBoxEx` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje kombinaci pole se seznamem styly u pole se seznamem. V tématu **poznámky** níže Další informace o stylů.  
  
 `rect`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, což je pozice a velikosti pole se seznamem.  
  
 `pParentWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazeného okna pole se seznamem (obvykle `CDialog`). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku pole se seznamem  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je objekt vytvořený úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření `CComboBoxEx` objektu ve dvou krocích:  
  
1.  Volání [CComboBoxEx](#ccomboboxex) k vytvoření `CComboBoxEx` objektu.  
  
2.  Volání této funkce člen, který vytvoří rozšířené pole se seznamem Windows a připojí jej k `CComboBoxEx` objektu.  
  
 Při volání **vytvořit**, MFC inicializuje běžné ovládací prvky.  
  
 Když vytvoříte pole se seznamem, můžete určit některé nebo všechny následující pole se seznamem styly:  
  
- **CBS_SIMPLE –**  
  
- **CBS_DROPDOWN –**  
  
- **CBS_DROPDOWNLIST –**  
  
- **CBS_AUTOHSCROLL –**  
  
- **WS_CHILD –**  
  
 Všechny ostatní styly se předá, když vytvoříte okna se ignorují. **ComboBoxEx** ovládací prvek také podporuje rozšířené styly, které poskytují další funkce. Tyto styly jsou popsané v [ComboBoxEx řízení rozšířené styly](http://msdn.microsoft.com/library/windows/desktop/bb775742), v sadě Windows SDK. Nastavit tyto styly voláním [SetExtendedStyle](#setextendedstyle).  
  
 Pokud chcete použít rozšířené windows styly s ovládacím prvkem, zavolejte [CreateEx](#createex) místo **vytvořit**.  
  
##  <a name="createex"></a>CComboBoxEx::CreateEx  
 Volání této funkce vytvoření ovládacího prvku rozšířené pole se seznamem (podřízeného okna) a její přidružení `CComboBoxEx` objektu.  
  
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
 Styl ovládacího prvku pole se seznamem. V tématu [vytvořit](#create) seznam stylů.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo **vytvořit** použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
 `CreateEx`Vytvoří ovládacího prvku rozšířené styly Windows určeného `dwExStyle`. Musíte nastavit rozšířené styly konkrétní k pomocí ovládacího prvku rozšířené pole se seznamem pole [SetExtendedStyle](#setextendedstyle). Například použít `CreateEx` nastavit tyto styly jako **ws_ex_contexthelp –**, ale použít `SetExtendedStyle` nastavit tyto styly jako **CBES_EX_CASESENSITIVE**. Další informace najdete v tématu styly popsané v tématu [– styly ovládacího prvku rozšířené ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775742) ve Windows SDK.  
  
##  <a name="deleteitem"></a>CComboBoxEx::DeleteItem  
 Odebere položku z **ComboBoxEx** ovládacího prvku.  
  
```  
int DeleteItem(int iIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Index položky k odebrání nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v ovládacím prvku zbývající. Pokud `iIndex` je neplatná, funkce vrátí hodnotu **CB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje funkce zprávy [CBEM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb775768), jak je popsáno v sadě Windows SDK. Při volání DeleteItem, [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zpráv s **CBEN_DELETEITEM** odešle upozornění do nadřazeného okna.  
  
##  <a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl  
 Volání této funkce člen získání ukazatele do ovládacího prvku pole se seznamem v rámci `CComboBoxEx` objektu.  
  
```  
CComboBox* GetComboBoxCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CComboBox` objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CComboBoxEx` Řízení se skládá z nadřazeného okna, který zapouzdřuje `CComboBox`.  
  
 `CComboBox` Objekt ukazuje návratová hodnota je dočasný objekt a zničen během další dobu nečinnosti, po zpracování.  
  
##  <a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl  
 Volání této funkce člen získání ukazatele na ovládací prvek úprav pro pole se seznamem.  
  
```  
CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CEdit](../../mfc/reference/cedit-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 A `CComboBoxEx` řízení používá textové pole, kdy je vytvořena s **cbs_dropdown –** stylu.  
  
 `CEdit` Objekt ukazuje návratová hodnota je dočasný objekt a zničen během další dobu nečinnosti, po zpracování.  
  
##  <a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle  
 Volání této funkce člen získat rozšířené styly využívané pro `CComboBoxEx` ovládacího prvku.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `DWORD` Hodnotu, která obsahuje rozšířené styly, které se používají pro ovládacího prvku pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [– styly ovládacího prvku rozšířené ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775742) ve Windows SDK pro další informace o těchto stylů.  
  
##  <a name="getimagelist"></a>CComboBoxEx::GetImageList  
 Volání této funkce člen k získání ukazatele na seznamu obrázků používané `CComboBoxEx` ovládacího prvku.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objektu. Pokud selže, vrátí tato funkce člen **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 `CImageList` Objekt ukazuje návratová hodnota je dočasný objekt a zničen během další dobu nečinnosti, po zpracování.  
  
##  <a name="getitem"></a>CComboBoxEx::GetItem  
 Načte položku informace o danou **ComboBoxEx** položky.  
  
```  
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pCBItem`  
 Ukazatel [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktura, která bude přijímat informace o položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla operace úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje funkce zprávy [CBEM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775779), jak je popsáno v sadě Windows SDK.  
  
##  <a name="haseditchanged"></a>CComboBoxEx::HasEditChanged  
 Určuje, jestli uživatel změnil obsah **ComboBoxEx** ovládacích prvků pro úpravy zadáním.  
  
```  
BOOL HasEditChanged();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel zadal do ovládacího prvku textového pole; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje funkce zprávy [CBEM_HASEDITCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb775782), jak je popsáno v sadě Windows SDK.  
  
##  <a name="insertitem"></a>CComboBoxEx::InsertItem  
 Vloží novou položku v **ComboBoxEx** ovládacího prvku.  
  
```  
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pCBItem`  
 Ukazatel [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktura, která bude přijímat informace o položce. Tato struktura obsahuje hodnoty příznak zpětného volání pro položku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index, kdy byl vložit novou položku v případě úspěšného; jinak-1.  
  
### <a name="remarks"></a>Poznámky  
 Při volání `InsertItem`, [wm_notify –](http://msdn.microsoft.com/library/windows/desktop/bb775583) zpráv s [CBEN_INSERTITEM](http://msdn.microsoft.com/library/windows/desktop/bb775764) odešle upozornění do nadřazeného okna.  
  
##  <a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle  
 Volání této funkce člen nastavit rozšířené styly využívané pro ovládacího prvku rozšířené pole se seznamem.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,  
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExMask`  
 A `DWORD` hodnotu, která určuje, jaké styly v `dwExStyles` mají mít vliv. Rozšířené styly pouze v `dwExMask` se změní. Všechny ostatní styly se zachová, jako je. Pokud má parametr hodnotu nula, pak všechny styly v `dwExStyles` bude mít vliv.  
  
 `dwExStyles`  
 A `DWORD` hodnotu, která obsahuje pole se seznamem řízení rozšířené styly pro ovládací prvek.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` hodnotu, která obsahuje rozšířené styly použil pro ovládací prvek.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [– styly ovládacího prvku rozšířené ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775742) ve Windows SDK pro další informace o těchto stylů.  
  
 K vytvoření pole se seznamem rozšířené ovládací prvek s styly rozšířené windows, použijte [CreateEx](#createex).  
  
##  <a name="setimagelist"></a>CComboBoxEx::SetImageList  
 Nastaví pro seznamu obrázků **ComboBoxEx** ovládacího prvku.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Ukazatel `CImageList` objekt obsahující obrázky, které chcete používat s `CComboBoxEx` ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objekt obsahující obrázky dříve využívaných `CComboBoxEx` ovládacího prvku. **NULL** Pokud byla dříve nastavena žádná seznamu obrázků.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje funkce zprávy [CBEM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775787), jak je popsáno v sadě Windows SDK. Pokud změníte výšku ovládacích prvků pro úpravy výchozí, volání funkce Win32 [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) se změnit velikost vlastního ovládacího prvku po zavolání metody `SetImageList`, nebo nezobrazí správně.  
  
 `CImageList` Objekt ukazuje návratová hodnota je dočasný objekt a zničen během další dobu nečinnosti, po zpracování.  
  
##  <a name="setitem"></a>CComboBoxEx::SetItem  
 Nastaví atributy pro položku v **ComboBoxEx** ovládacího prvku.  
  
```  
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pCBItem`  
 Ukazatel [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) struktura, která bude přijímat informace o položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byla operace úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje funkce zprávy [CBEM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775788), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme  
 Nastaví vizuální styl rozšířeného pole se seznamem ovládacích prvků pole.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 `pszSubAppName`  
 Ukazatel na řetězec znaků Unicode, který obsahuje vizuální styl rozšířeného pole se seznamem pole nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, není použita.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [CBEM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb775790) zprávy, jak je popsáno v sadě Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MFCIE](../../visual-cpp-samples.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)
