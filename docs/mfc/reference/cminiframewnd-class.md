---
title: Třída CMiniFrameWnd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
dev_langs:
- C++
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 766faaa50e4efead96ff72c67aee71fec2386b18
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038579"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd – třída
Představuje okně s rámečkem poloviční výškou zpravidla se zobrazí kolem plovoucí panely nástrojů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Vytvoří `CMiniFrameWnd` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](#create)|Vytvoří `CMiniFrameWnd` objektu po konstrukce.|  
|[CMiniFrameWnd::CreateEx](#createex)|Vytvoří `CMiniFrameWnd` objektu (s další možnosti) po konstrukce.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto okna s rámečkem zkrácená chovají jako okna s rámečkem normální, s tím rozdílem, že nemají tlačítka minimalizovat maximalizovat nebo nabídky a můžete mít pouze jedním kliknutím v nabídce systému je zrušíte.  
  
 Použít `CMiniFrameWnd` objektu, nejprve definovat objekt. Potom zavolejte [vytvořit](#create) – členská funkce pro zobrazení okna zkrácená rámce.  
  
 Další informace o tom, jak používat `CMiniFrameWnd` objekty, najdete v článku [stabilní umístění a plovoucí panely nástrojů](../../mfc/docking-and-floating-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd  
 Vytvoří `CMiniFrameWnd` objektu, ale nevytvoří okna.  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit okno, volejte [CMiniFrameWnd::Create](#create).  
  
##  <a name="create"></a>  CMiniFrameWnd::Create  
 Zkrácená rámce okna Windows vytvoří a připojí jej k `CMiniFrameWnd` objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpClassName*  
 Bodů na řetězec znaků ukončené hodnotou null, který názvy třídy Windows. Název třídy může být jakýkoli název zaregistrována na globální [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) funkce. Pokud **NULL**, třídu okna se zaregistruje pro vás rámcem. MFC poskytuje výchozí třídu následující styly a atributy:  
  
-   Nastaví styl bit **CS_DBLCLKS**, které odesílá poklikejte na zprávy do okna postupu při poklepání myší.  
  
-   Nastaví styl bits **CS_HREDRAW** a **CS_VREDRAW**, který směrovat obsah klientské oblasti překreslit, když se změní velikost okna.  
  
-   Nastaví třídu kurzor na Windows standard **IDC_ARROW**.  
  
-   Nastaví štětec pozadí třída **NULL**, takže okno nebude vymazat jeho pozadí.  
  
-   Nastaví ikonu třídy na ikonu s logem Windows standard, s připravenými příznak.  
  
-   Nastaví okna na výchozí velikost a umístění, jak je uvedeno v systému Windows.  
  
 *lpWindowName*  
 Odkazuje na řetězec znaků ukončené hodnotou null, který obsahuje název okna.  
  
 *dwStyle*  
 Určuje styl atributů okna. Může jít o standardní okno Styly a jeden nebo více následujících speciální stylů:  
  
- **MFS_MOVEFRAME** umožňuje zkrácená rámce okna přesunování kliknutím na libovolné okno, nikoli pouze záhlaví.  
  
- **MFS_4THICKFRAME** zakáže změnu velikosti zkrácená rámce okna.  
  
- **MFS_SYNCACTIVE** synchronizuje aktivace zkrácená rámce okna k aktivaci jeho nadřazeného okna.  
  
- **MFS_THICKFRAME** umožňuje zkrácená rámce okna být dimenzovány malého povolit obsah klientské oblasti.  
  
- **MFS_BLOCKSYSMENU** zakáže přístup k nabídce systému a v nabídce ovládací prvek a převede je na součást titulek (záhlaví).  
  
 V tématu [CWnd::Create](../../mfc/reference/cwnd-class.md#create) popis možné okno Styl hodnoty. Je typické používanou ke okna s rámečkem zkrácená **ws_popup –&#124;ws_caption –&#124;ws_sysmenu –**.  
  
 *Rect –*  
 A `RECT` struktura určení požadované dimenzí okna.  
  
 *pParentWnd*  
 Body do nadřazeného okna. Použití **NULL** pro systém windows nejvyšší úrovně.  
  
 *nID*  
 Jako podřízeného okna při vytváření okna zkrácená rámečku, toto je identifikátor podřízeného ovládacího prvku; jinak 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 **Vytvoření** inicializuje okna na název třídy a název časového období a zaregistruje výchozí hodnoty pro svou styl a nadřazené.  
  
##  <a name="createex"></a>  CMiniFrameWnd::CreateEx  
 Vytvoří `CMiniFrameWnd` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Určuje styl rozšířené `CMiniFrameWnd` vytváří. Použít libovolný z [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) do okna.  
  
 *lpClassName*  
 Odkazuje na řetězec znaků ukončené hodnotou null, který pojmenuje třídě Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktura). Název třídy může být jakýkoli název zaregistrována na globální [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) funkce nebo některé názvy předdefinované třída ovládacích prvků. Nesmí být **NULL**.  
  
 *lpWindowName*  
 Odkazuje na řetězec znaků ukončené hodnotou null, který obsahuje název okna.  
  
 *dwStyle*  
 Určuje styl atributů okna. V tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CWnd::Create](../../mfc/reference/cwnd-class.md#create) popis možných hodnot.  
  
 *Rect –*  
 Velikost a umístění okna, v souřadnice klienta *pParentWnd*.  
  
 *pParentWnd*  
 Body v nadřazeném okně objektu.  
  
 *nID*  
 Identifikátor podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `CreateEx` Zadejte parametry **WNDCLASS**, styl oken a (volitelně) počáteční pozice a velikosti okna. `CreateEx` Určuje také nadřazené (pokud existuje) a ID okna.  
  
 Když `CreateEx` provede, odešle Windows [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) zprávy v okně.  
  
 Rozšíření zpracování zpráv výchozí, odvození třídy z `CMiniFrameWnd`, přidejte mapy zpráv do nové třídy a poskytují členské funkce pro výše uvedené zprávy. Přepsání `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Přepsání Další **na *** zpráva* zprávy obslužné rutiny přidat další funkce odvozené třídy.  
  
 Pokud **ws_visible –** je zadána styl, systém Windows odešle okno všechny zprávy pro aktivaci a zobrazí okno potřeba. Pokud styl okna určuje záhlaví, název okna na kterou odkazuje *lpszWindowName* parametr se zobrazí v záhlaví.  
  
 *DwStyle* parametr může být libovolnou kombinací [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 Stará sada nástrojů windows palety styl již nejsou podporovány. Původní styl, který nemá tlačítko Zavřít "X", byl podporován při spuštění aplikace knihovny MFC v dřívějších verzích systému Windows, ale už není podporovaná ve Visual C++ .NET. Pouze nové `WS_EX_TOOLWINDOW` styl se teď podporuje; popis tohoto stylu naleznete v tématu [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
## <a name="see-also"></a>Viz také  
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)
