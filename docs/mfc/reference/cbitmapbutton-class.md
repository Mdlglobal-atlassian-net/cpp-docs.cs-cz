---
title: "Třída CBitmapButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs: C++
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 619ddd7805207f14bb44ed52d148f53e3aa79e57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cbitmapbutton-class"></a>CBitmapButton – třída
Vytvoří uzavření tlačítkem ovládací prvky označený verzí rastrových obrázků místo textu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBitmapButton : public CButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|Vytvoří `CBitmapButton` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](#autoload)|Přidruží tlačítka v dialogovém okně objektu `CBitmapButton` třídu, načte bitmap(s) podle názvu a velikosti na tlačítko Přizpůsobit bitové mapy.|  
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|Inicializuje objekt načítání jeden nebo více prostředků s názvem rastrový obrázek ze souboru prostředků aplikace a rastrových obrázků, které se připojuje k objektu.|  
|[CBitmapButton::SizeToContent](#sizetocontent)|Velikostí tlačítko pro uložení bitové mapy.|  
  
## <a name="remarks"></a>Poznámky  
 `CBitmapButton`objekty obsahovat až čtyři rastrové obrázky, které obsahují Image pro různé stavy tlačítko můžete předpokládat,: aktuálním (nebo normální), dolů (nebo vybrané), zaměřuje a zakáže. Pouze první rastrového obrázku není třeba; jiné jsou volitelné.  
  
 Rastrový obrázek tlačítko Image zahrnují ohraničení pro bitovou kopii a také bitovou kopii sám sebe. Ohraničení obvykle hraje součástí zobrazuje stav tlačítko. Například rastrový obrázek pro stav cílených obvykle je jako jeden aktuálním stavu, ale s přerušovanou obdélníku inset z ohraničení nebo na silné souvislou čáru na hranici. Bitmapy pro zakázaného stavu obvykle vypadá takto: jednu pro aktuálním stavu, ale má nižší kontrast (např. nabídky neaktivní nebo šedým výběr).  
  
 Tyto bitmap může mít libovolnou velikost, ale všechny zacházeno, jako kdyby byly stejnou velikost jako rastrový obrázek pro aktuálním stavu.  
  
 Různé aplikace potřebují různé kombinace rastrové obrázky:  
  
|Nahoru|Dolů|Zaměřuje|zakázáno|Aplikace|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Rastrový obrázek|  
|×|×|||Tlačítko bez **ws_tabstop –** styl|  
|×|×|×|×|Dialogové okno tlačítko s všechny stavy|  
|×|×|×||Dialogové okno tlačítka s **ws_tabstop –** styl|  
  
 Při vytváření ovládacího prvku tlačítko rastrového obrázku, nastavte **bs_ownerdraw –** styl, který určíte, že je tlačítko vykreslované uživatelem. To způsobí, že systému Windows pro odesílání `WM_MEASUREITEM` a `WM_DRAWITEM` zprávy pro tlačítko; rozhraní zpracovává tyto zprávy a spravuje vzhled tlačítka pro vás.  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>Vytvoření ovládacího prvku tlačítko rastrového obrázku v časového období klientské oblasti  
  
1.  Vytvořte jeden až čtyři bitové kopie rastrový obrázek pro tlačítko.  
  
2.  Vytvořit [CBitmapButton](#cbitmapbutton) objektu.  
  
3.  Volání [vytvořit](../../mfc/reference/cbutton-class.md#create) funkce vytvoření ovládacího prvku tlačítko Windows a připojte ji k `CBitmapButton` objektu.  
  
4.  Volání [LoadBitmaps](#loadbitmaps) – členská funkce načíst prostředky rastrový obrázek po sestavený tlačítko rastrového obrázku.  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>Vložení ovládacích prvků rastrového obrázku tlačítka v dialogovém okně  
  
1.  Vytvořte jeden až čtyři bitové kopie rastrový obrázek pro tlačítko.  
  
2.  Vytvoření šablony dialogového okna s tlačítkem vykreslování vlastníka umístěný, kam chcete tlačítko rastrového obrázku. Velikost tlačítka v šabloně nezáleží.  
  
3.  Popisek tlačítka například nastavit na hodnotu " **MYIMAGE**" a definovat symbol pro tlačítko například **IDC_MYIMAGE**.  
  
4.  Ve skriptu prostředek vaší aplikace poskytnout všechny bitové kopie, vytvořené pro tlačítko ID sestavený připojením mezi písmena "U", "D", "F," nebo "X" (pro nahoru, dolů, zaměřuje a zakázaná) řetězec používaný pro popisek tlačítka v kroku 3. Titulek tlačítko " **MYIMAGE**," ID by být například " **MYIMAGEU**," " **MYIMAGED**," " **MYIMAGEF**," a " **MYIMAGEX**. " Můžete **musí** zadejte ID vaší rastrové obrázky v rámci dvojité uvozovky. V opačném případě editoru prostředků bude k prostředku přiřadit celé číslo a MFC nebude při načítání bitovou kopii.  
  
5.  Ve třídě dialog vaší aplikace (získané z `CDialog`), přidat `CBitmapButton` člen objektu.  
  
6.  V `CDialog` objektu [OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog) rutiny, volání `CBitmapButton` objektu [AutoLoad](#autoload) fungovat, používání jako parametrů ID ovládacího prvku tlačítka a `CDialog` objektu **to** ukazatel.  
  
 Pokud budete chtít zpracování zpráv s oznámením Windows, jako například **BN_CLICKED**, odeslané pomocí ovládacího prvku tlačítko rastrového obrázku a jeho nadřazeným (obvykle třída odvozená z **CDialog)**, přidejte do `CDialog`-odvozené objekt map zpráv položku a obslužné rutiny zpráv členské funkce pro každou zprávu. Oznámení zaslaná z `CBitmapButton` objekt jsou stejné jako poslal [CButton](../../mfc/reference/cbutton-class.md) objektu.  
  
 Třída [ctoolbar –](../../mfc/reference/ctoolbar-class.md) přistupují k rastrového obrázku tlačítka.  
  
 Další informace o `CBitmapButton`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="autoload"></a>CBitmapButton::AutoLoad  
 Přidruží tlačítka v dialogovém okně objektu `CBitmapButton` třídu, načte bitmap(s) podle názvu a velikosti na tlačítko Přizpůsobit bitové mapy.  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID tlačítka ovládacího prvku.  
  
 `pParent`  
 Ukazatel na objekt, který vlastní tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `AutoLoad` funkce k chybě při inicializaci vykreslování vlastníka tlačítka v dialogovém okně jako rastrový obrázek tlačítka. Pokyny k použití této funkce jsou v poznámky pro `CBitmapButton` třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton  
 Vytvoří `CBitmapButton` objektu.  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření C++ `CBitmapButton` objektu, volání [CButton::Create](../../mfc/reference/cbutton-class.md#create) vytvoření ovládacího prvku tlačítko Windows a připojte ji k `CBitmapButton` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps  
 Tuto funkci použít, pokud chcete načíst rastrové obrázky se identifikovanou jejich názvy prostředků nebo čísla ID, nebo, pokud nelze použít `AutoLoad` fungovat, protože například vytváříte tlačítko rastrový obrázek, který není součástí dialogové okno.  
  
```  
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,  
    LPCTSTR lpszBitmapResourceSel = NULL,  
    LPCTSTR lpszBitmapResourceFocus = NULL,  
    LPCTSTR lpszBitmapResourceDisabled = NULL);

 
BOOL LoadBitmaps(
    UINT nIDBitmapResource,  
    UINT nIDBitmapResourceSel = 0,  
    UINT nIDBitmapResourceFocus = 0,  
    UINT nIDBitmapResourceDisabled = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszBitmapResource*  
 Body řetězce ukončené hodnotou null, který obsahuje název rastrového obrázku pro tlačítko rastrový obrázek normální nebo "zapnuto". Požadováno.  
  
 *lpszBitmapResourceSel*  
 Body řetězce ukončené hodnotou null, který obsahuje název rastrového obrázku pro tlačítko rastrového obrázku je vybrané nebo "stavu dolů". Může být **NULL**.  
  
 *lpszBitmapResourceFocus*  
 Body řetězce ukončené hodnotou null, který obsahuje název rastrového obrázku pro tlačítko rastrový obrázek zaměřuje stavu. Může být **NULL**.  
  
 *lpszBitmapResourceDisabled*  
 Body řetězce ukončené hodnotou null, který obsahuje název rastrového obrázku pro tlačítko rastrový obrázek zakázaném stavu. Může být **NULL**.  
  
 *nIDBitmapResource*  
 Určuje počet prostředků rastrový obrázek pro tlačítko rastrový obrázek normální nebo "zapnuto" pro ID prostředku. Požadováno.  
  
 *nIDBitmapResourceSel*  
 Určuje číslo ID prostředku prostředku rastrový obrázek pro tlačítko rastrového obrázku je vybrané nebo "dolů" stavu. Může být 0.  
  
 *nIDBitmapResourceFocus*  
 Určuje počet prostředků ID prostředku bitové mapy pro rastrový obrázek tlačítka cílených stavu. Může být 0.  
  
 *nIDBitmapResourceDisabled*  
 Určuje počet prostředků ID prostředku rastrový obrázek pro tlačítko rastrový obrázek zakázaném stavu. Může být 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>CBitmapButton::SizeToContent  
 Volání této funkce ke změně velikosti tlačítko rastrového obrázku na velikost bitové mapy.  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLTEST](../../visual-cpp-samples.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

