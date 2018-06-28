---
title: Třída CMFCDropDownFrame | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c7264273f3db1dab1e6cab72333c0629a802e28
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041991"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame – třída
Poskytuje funkce okno rámce rozevíracího seznamu panely nástrojů rozevíracího seznamu a tlačítka panelu nástrojů rozevíracího seznamu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|Výchozí konstruktor.|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCDropDownFrame::Create](#create)|Vytvoří `CMFCDropDownFrame` objektu.|  
|`CMFCDropDownFrame::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Načte panelu nabídek nadřazené rámce rozevíracího seznamu.|  
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Načte nadřazené rozbalovací nabídce rámce rozevíracího seznamu.|  
|`CMFCDropDownFrame::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Přemístí rámečku rozevíracího seznamu.|  
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Nastaví, zda automaticky zničen podřízeného okna nástrojů rozevíracího seznamu.|  
  
### <a name="remarks"></a>Poznámky  
 Tato třída není určena pro použití přímo z vašeho kódu.  
  
 Rozhraní používá tuto třídu zajistit rámce chování `CMFCDropDownToolbar` a `CMFCDropDownToolbarButton` třídy. Další informace o těchto tříd naleznete v tématu [CMFCDropDownToolBar třída](../../mfc/reference/cmfcdropdowntoolbar-class.md) a [CMFCDropDownToolbarButton třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst ukazatel `CMFCDropDownFrame` objektu z `CFrameWnd` třídy a jak nastavit podřízená okna nástrojů rozevíracího seznamu zničení automaticky.  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdropdowntoolbar.h  
  
##  <a name="create"></a>  CMFCDropDownFrame::Create  
 Vytvoří `CMFCDropDownFrame` objektu.  
  
```  
virtual BOOL Create(
    CWnd* pWndParent,  
    int x,  
    int y,  
    CMFCDropDownToolBar* pWndOriginToolbar);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *pWndParent*|Nadřazené okno rámce rozevíracího seznamu.|  
|[v] *x*|Souřadnice obrazovky vodorovné umístění nižší dole.|  
|[v] *y*|Souřadnice svislé obrazovky pro umístění nižší dole.|  
|[v] *pWndOriginToolbar*|Panel nástrojů, má tato metoda používá k vyplnění nového objektu rámce rozevíracího seznamu tlačítka pro rozevírací seznam.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud rámce rozevíracího seznamu byl úspěšně vytvořen; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá základní [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metodu pro vytvoření okně s rámečkem rozevírací seznam s `WS_POPUP` stylu. Okně s rámečkem rozevírací seznam se zobrazuje na souřadnice zadaný obrazovky. Tato metoda selže, pokud [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) metoda vrátí `FALSE`.  
  
 `CMFCDropDownFrame` Třída se vytvoří kopie poskytnutého `CMFCDropDownToolBar` parametr. Tato metoda zkopíruje obrázky tlačítka a tlačítko stavy z `pWndOriginToolbar` parametru `m_pWndOriginToolbar` – datový člen.  
  
##  <a name="getparentmenubar"></a>  CMFCDropDownFrame::GetParentMenuBar  
 Načte panelu nabídek nadřazené rámce rozevíracího seznamu.  
  
```  
CMFCMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na panelu nabídek nadřazené rámečku rozevíracího seznamu, nebo `NULL` Pokud rámečku nemá nadřazený.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte z nadřazené tlačítko panelu nabídek nadřazené. Tato metoda vrátí hodnotu `NULL` Pokud rámečku rozevíracího seznamu má žádné tlačítko nadřazené nebo tlačítko nadřazené žádný nadřazený řádku nabídek.  
  
##  <a name="getparentpopupmenu"></a>  CMFCDropDownFrame::GetParentPopupMenu  
 Načte nadřazené rozbalovací nabídce rámce rozevíracího seznamu.  
  
```  
CMFCDropDownFrame* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nadřazené rozevírací nabídky rámečku rozevíracího seznamu, nebo `NULL` Pokud rámečku nemá nadřazený.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte nabídce nadřazené z nadřazené tlačítko. Tato metoda vrátí hodnotu `NULL` Pokud rámečku rozevíracího seznamu má žádné tlačítko nadřazené nebo tlačítko nadřazené žádné nabídky nadřazené.  
  
##  <a name="recalclayout"></a>  CMFCDropDownFrame::RecalcLayout  
 Přemístí rámečku rozevíracího seznamu.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|[v] *bNotify*|Nepoužívá se.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework rámečku rozevíracího seznamu je při vytváření nebo změně velikosti nadřazeného okna. Tato metoda se vypočítává pozice a velikosti rámce rozevíracího seznamu pozice a velikosti okna nadřazené.  
  
##  <a name="setautodestroy"></a>  CMFCDropDownFrame::SetAutoDestroy  
 Nastaví, zda automaticky zničen podřízeného okna nástrojů rozevíracího seznamu.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bAutoDestroy*  
 `TRUE` automaticky zrušení okna přidružené rozevírací seznam nástrojů; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bAutoDestroy* je `TRUE`, pak se `CMFCDropDownFrame` destruktor zničí okna přidružené nástrojů rozevíracího seznamu. Výchozí hodnota je `TRUE`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton – třída](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
