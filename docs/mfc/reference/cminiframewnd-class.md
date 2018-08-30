---
title: Cminiframewnd – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 2772ec96558c4aa1d1f5fcb573166a37a31c0592
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201202"
---
# <a name="cminiframewnd-class"></a>Cminiframewnd – třída
Představuje okno rámce poloviční výšky obvykle viděné okolo plovoucích panelů nástrojů.  
  
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
|[CMiniFrameWnd::Create](#create)|Vytvoří `CMiniFrameWnd` po konstrukci objektu.|  
|[CMiniFrameWnd::CreateEx](#createex)|Vytvoří `CMiniFrameWnd` objektu (Další možnosti) po konstrukci.|  
  
## <a name="remarks"></a>Poznámky  
 Tato okna s minirámcem okna se chovat jako normální rámečkem, s tím rozdílem, že nemají minimalizovat/maximalizovat tlačítka nebo nabídky a je jenom nutné jedním kliknutím v nabídce systému chcete je zavřít.  
  
 Použití `CMiniFrameWnd` objektu, nejprve definování tohoto objektu. Zavolejte [vytvořit](#create) členské funkce k zobrazení okna okna s minirámcem.  
  
 Další informace o tom, jak používat `CMiniFrameWnd` objekty, najdete v článku [ukotvení a plovoucí panely nástrojů](../../mfc/docking-and-floating-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd  
 Vytvoří `CMiniFrameWnd` objektu, ale nevytváří žádné okno.  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit okno, zavolejte [CMiniFrameWnd::Create](#create).  
  
##  <a name="create"></a>  CMiniFrameWnd::Create  
 Vytvoří okno s minirámcem Windows a připojí ho k `CMiniFrameWnd` objektu.  
  
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
 Odkazuje na řetězec znaků zakončené znakem null, která pojmenuje třídu Windows. Název třídy může být jakýkoli název registrované s globální [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) funkce. Pokud má hodnotu NULL, se zaregistruje třídu okna pro vás rozhraní. Knihovna MFC poskytuje výchozí třídu následující styly a atributy:  
  
-   Nastaví styl bitové CS_DBLCLKS, která odešle dvakrát klikněte na panel zpráv pro proceduru okna při poklepání myši.  
  
-   Nastaví styl bity CS_HREDRAW a CS_VREDRAW, která instruují obsah od klientské oblasti, které vyžadovaly překreslení při změně velikosti okna.  
  
-   Nastaví kurzor třídy na standardní IDC_ARROW Windows.  
  
-   Nastaví štětec pozadí třídy na hodnotu NULL, takže okna nebude vymazání jeho pozadí.  
  
-   Ikona loga Windows standard, Mávající příznak nastaví ikonu třídy.  
  
-   Nastaví okna na výchozí velikost a umístění, jak je uvedeno ve Windows.  
  
 *lpWindowName*  
 Odkazuje na řetězec znaků zakončené znakem null, který obsahuje název okna.  
  
 *dwStyle*  
 Určuje atributy stylu okna. Může jít o standardní okno Styly a jeden nebo více následujících speciálních stylů:  
  
- MFS_MOVEFRAME umožňuje okno minirámcem přesunování po kliknutí na libovolné okraji okna, nikoli pouze záhlaví.  
  
- Zakáže MFS_4THICKFRAME změně velikosti okna okna s minirámcem.  
  
- MFS_SYNCACTIVE synchronizuje Aktivace okna s minirámcem okno na aktivaci nezašle nadřazenému oknu.  
  
- Umožňuje MFS_THICKFRAME povolit velikost malá jako obsah od klientské oblasti okna okna s minirámcem.  
  
- MFS_BLOCKSYSMENU zakáže přístup k systémové nabídky a nabídky ovládací prvek a převede je do součástí titulek (záhlaví).  
  
 Zobrazit [CWnd::Create](../../mfc/reference/cwnd-class.md#create) popis hodnot stylu okna je to možné. Typické kombinací pro okna s minirámcem windows je WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.  
  
 *Rect*  
 A `RECT` struktura určující požadované velikosti okna.  
  
 *pParentWnd*  
 Body do nadřazeného okna. Použijte hodnotu NULL pro okna nejvyšší úrovně.  
  
 *nID*  
 Pokud jako podřízeného okna se vytvoří okno s minirámcem, toto je identifikátor podřízeného ovládacího prvku; jinak 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Create` Inicializuje název třídy okna a okna názvu a zaregistruje výchozí hodnoty pro jeho styl a nadřazené.  
  
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
 Určuje rozšířený styl `CMiniFrameWnd` vytváří. Některý [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) do okna.  
  
 *lpClassName*  
 Odkazuje na řetězec znaků zakončené znakem null, který názvy třídy Windows ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktura). Název třídy může být jakýkoli název registrované s globální [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) funkce nebo názvy předdefinovaných třídy ovládacího prvku. Nesmí být NULL.  
  
 *lpWindowName*  
 Odkazuje na řetězec znaků zakončené znakem null, který obsahuje název okna.  
  
 *dwStyle*  
 Určuje atributy stylu okna. Zobrazit [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CWnd::Create](../../mfc/reference/cwnd-class.md#create) popis možných hodnot.  
  
 *Rect*  
 Velikost a umístění okna, v souřadnicích klienta z *pParentWnd*.  
  
 *pParentWnd*  
 Odkazuje na nadřazený objekt okna.  
  
 *nID*  
 Identifikátor podřízené okno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 `CreateEx` Parametry zadejte WNDCLASS, styl okna a (volitelně) počáteční pozice a velikost okna. `CreateEx` také určuje, v okně nadřazené (pokud existuje) a ID.  
  
 Když `CreateEx` spustí, odešle Windows [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) zprávu do okna.  
  
 Pokud chcete rozšířit výchozí zpracování zpráv, odvoďte třídu z `CMiniFrameWnd`, přidejte mapy zpráv pro novou třídu a členské funkce zadání výše uvedených zpráv. Přepsat `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Přepsání dalších `On` *zpráva* zprávy obslužné rutiny přidávat další funkce do vaší odvozené třídy.  
  
 WS_VISIBLE style je směru, je-li Windows odešle všechny zprávy, které jsou potřebné k aktivaci a zobrazí okno v okně. Pokud styl okna určuje záhlaví, název okna na které odkazují *lpszWindowName* parametrů se zobrazí v záhlaví okna.  
  
 *DwStyle* parametr může být libovolná kombinace [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 Okna nástrojů palety starý styl již nejsou podporovány. Starý styl, který nemá na tlačítko Zavřít "X", se nepodporuje při spouštění aplikace knihovny MFC v předchozích verzích Windows, ale už není podporovaná ve Visual C++ .NET. Nově se podporuje jenom nový styl WS_EX_TOOLWINDOW; Popis tohoto stylu najdete v tématu [rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
## <a name="see-also"></a>Viz také  
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)
