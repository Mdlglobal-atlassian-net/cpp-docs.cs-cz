---
title: "Třída CMFCAutoHideButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
dev_langs: C++
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2252f27dfffd4bbbe7edebacad8af1c445a32e5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton – třída
Tlačítko, které zobrazí nebo skryje [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) nakonfigurovaný skrýt.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAutoHideButton::BringToTop](#bringtotop)||  
|[CMFCAutoHideButton::Create](#create)|Vytvoří a inicializuje automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Načte zarovnání automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Vrátí [CDockablePane](../../mfc/reference/cdockablepane-class.md) objekt přidružený k automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||  
|[CMFCAutoHideButton::GetRect](#getrect)||  
|[CMFCAutoHideButton::GetSize](#getsize)|Určuje velikost automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Vrátí velikost textový popisek pro tlačítko automaticky skrýt.|  
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Označuje automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::IsActive](#isactive)|Označuje, zda automaticky skrýt tlačítko je aktivní.|  
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Vrátí zvýrazněte stav skrýt tlačítko automaticky.|  
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Určuje, zda je tlačítko automaticky skrýt vodorovné nebo svislé.|  
|[CMFCAutoHideButton::IsTop](#istop)||  
|[CMFCAutoHideButton::IsVisible](#isvisible)|Určuje, zda je tlačítko viditelné.|  
|[CMFCAutoHideButton::Move](#move)||  
|[CMFCAutoHideButton::OnDraw](#ondraw)|Tato metoda volá framework při nakreslí automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Tato metoda volá framework při ohraničení automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Tato metoda volá framework při zaplňování na pozadí automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::ReplacePane](#replacepane)||  
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Zobrazí nebo skryje přidruženého [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCAutoHideButton::ShowButton](#showbutton)|Zobrazí nebo skryje automaticky skrýt tlačítko.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||  
  
## <a name="remarks"></a>Poznámky  
 Při vytváření `CMFCAutoHideButton` objekt je připojený k [CDockablePane Class](../../mfc/reference/cdockablepane-class.md). `CDockablePane` Objekt je skrytý nebo zobrazí jako uživatel komunikuje `CMFCAutoHideButton` objektu.  
  
 Ve výchozím nastavení, systém automaticky vytvoří `CMFCAutoHideButton` když uživatel zapne automaticky skrýt. Rozhraní framework můžete vytvořit element vlastní třídy uživatelského rozhraní místo `CMFCAutoHideButton` třídy. K určení, které vlastní třídy uživatelského rozhraní rozhraní by měl používat, nastavte proměnnou statický člen `CMFCAutoHideBar::m_pAutoHideButtonRTS` rovna vlastní třídu uživatelského rozhraní. Ve výchozím nastavení je tato proměnná nastavená na `CMFCAutoHideButton`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCAutoHideButton` objektu a pomocí různých metod v nástroji `CMFCAutoHideButton` třídy. Tento příklad ukazuje, jak k chybě při inicializaci `CMFCAutoHideButton` objekt pomocí jeho `Create` metoda, zobrazit přidruženého `CDockablePane` třídy a automaticky skrýt tlačítko zobrazit.  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAutoHideButton`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxautohidebutton.h  
  
##  <a name="bringtotop"></a>CMFCAutoHideButton::BringToTop  

  
```  
void BringToTop();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="create"></a>CMFCAutoHideButton::Create  
 Vytvoří a inicializuje automaticky skrýt tlačítko.  
  
```  
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,  
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pParentBar`  
 Ukazatel na panelu nástrojů nadřazené.  
  
 [v]`pAutoHideWnd`  
 Ukazatel [CDockablePane](../../mfc/reference/cdockablepane-class.md) objektu. Toto tlačítko automaticky skrýt skryje a ukazuje, že `CDockablePane`.  
  
 [v]`dwAlignment`  
 Hodnota, která určuje zarovnání na tlačítko se hlavního rámce okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Při vytváření `CMFCAutoHideButton` objekt, je nutné přidružit ke konkrétní automaticky skrýt tlačítko `CDockablePane`. Uživatel může použít tlačítko automaticky skrýt skrýt a zobrazit přidruženého `CDockablePane`.  
  
 `dwAlignment` Parametr označuje, kde se nachází automaticky skrýt tlačítko v aplikaci. Parametr může být jakýkoli z následujících hodnot:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getalignment"></a>CMFCAutoHideButton::GetAlignment  
 Načte zarovnání automaticky skrýt tlačítko.  
  
```  
DWORD GetAlignment() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` hodnotu, která obsahuje aktuální zarovnání automaticky skrýt tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Zarovnání automaticky skrýt tlačítko označuje, kde se nachází na tlačítko na aplikaci. Může být některého z následujících hodnot:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CRBS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow  
 Vrátí [CDockablePane](../../mfc/reference/cdockablepane-class.md) objekt přidružený k automaticky skrýt tlačítko.  
  
```  
CDockablePane* GetAutoHideWindow() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na přidruženého `CDockablePane` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pro přidružení automaticky skrýt tlačítko s `CDockablePane`, předat `CDockablePane` jako parametr, který se [CMFCAutoHideButton::Create](#create) metoda.  
  
##  <a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar  

  
```  
CMFCAutoHideBar* GetParentToolBar();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrect"></a>CMFCAutoHideButton::GetRect  

  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsize"></a>CMFCAutoHideButton::GetSize  
 Určuje velikost automaticky skrýt tlačítko.  
  
```  
CSize GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CSize` objekt, který obsahuje tlačítko velikost.  
  
### <a name="remarks"></a>Poznámky  
 Velikost počítané zahrnuje velikost ohraničení automaticky skrýt tlačítko.  
  
##  <a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize  
 Vrátí velikost textový popisek pro tlačítko automaticky skrýt.  
  
```  
virtual CSize GetTextSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje velikost text pro tlačítko automaticky skrýt.  
  
##  <a name="isactive"></a>CMFCAutoHideButton::IsActive  
 Označuje, zda automaticky skrýt tlačítko je aktivní.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud automaticky skrýt tlačítko je aktivní; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Automaticky skrýt tlačítko je aktivní, kdy přidruženého [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) okno se zobrazí.  
  
##  <a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal  
 Určuje, zda je tlačítko automaticky skrýt vodorovné nebo svislé.  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je tlačítko vodorovné; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework nastaví orientaci [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objektu při jeho vytvoření.  Orientaci můžete řídit pomocí `dwAlignment` parametr ve [CMFCAutoHideButton::Create](#create) metoda.  
  
##  <a name="istop"></a>CMFCAutoHideButton::IsTop  

  
```  
BOOL IsTop() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isvisible"></a>CMFCAutoHideButton::IsVisible  
 Určuje, zda je tlačítko automaticky skrýt viditelné.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je tlačítko viditelné; `FALSE` jinak.  
  
##  <a name="ondraw"></a>CMFCAutoHideButton::OnDraw  
 Tato metoda volá framework při nakreslí automaticky skrýt tlačítko.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete přizpůsobit vzhled tlačítek automaticky skrýt v aplikaci, vytvořte novou třídu odvozenou z `CMFCAutoHideButton`. Odvozené třídy potlačí tuto metodu.  
  
##  <a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder  
 Tato metoda volá framework při ohraničení automaticky skrýt tlačítko.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectBounds`  
 Ohraničující obdélník automaticky skrýt tlačítko.  
  
 [v]`rectBorderSize`  
 Tloušťka ohraničení pro každé straně automaticky skrýt tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete přizpůsobit ohraničení každé automaticky skrýt tlačítko v aplikaci, vytvořte novou třídu odvozenou z `CMFCAutoHideButton`. Odvozené třídy potlačí tuto metodu.  
  
##  <a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground  
 Tato metoda volá framework při zaplňování na pozadí automaticky skrýt tlačítko.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rect`  
 Ohraničující obdélník automaticky skrýt tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete přizpůsobit na pozadí pro tlačítka automaticky skrýt v aplikaci, vytvořte novou třídu odvozenou z `CMFCAutoHideButton`. Odvozené třídy potlačí tuto metodu.  
  
##  <a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow  
 Zobrazí nebo skryje přidruženého [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
```  
void ShowAttachedWindow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 Logická hodnota, která určuje, zda tato metoda zobrazuje připojený `CDockablePane`.  
  
##  <a name="showbutton"></a>CMFCAutoHideButton::ShowButton  
 Zobrazí nebo skryje automaticky skrýt tlačítko.  
  
```  
virtual void ShowButton(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 Logická hodnota, která určuje, zda chcete automaticky skrýt tlačítko zobrazit.  
  
##  <a name="move"></a>CMFCAutoHideButton::Move  

  
```  
void Move(int nOffset);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nOffset`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="replacepane"></a>CMFCAutoHideButton::ReplacePane  

  
```  
void ReplacePane(CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pNewBar`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="unsetautohidemode"></a>CMFCAutoHideButton::UnSetAutoHideMode  
 Zakážete automatické skrytí režimu.  
  
```  
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pFirstBarInGroup`  
 Ukazatel na prvním řádku ve skupině.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton  
 Označuje skrýt tlačítko automaticky.  
  
```  
virtual void HighlightButton(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parametry  
 `bHighlight`  
 Určuje nové automaticky skrýt tlačítko stavu. `TRUE`označuje tlačítko zvýrazní, `FALSE` označuje není zvýrazněná tlačítko.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ishighlighted"></a>CMFCAutoHideButton::IsHighlighted  
 Vrátí stav zvýraznění skrýt tlačítko automaticky.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud skrýt tlačítko automaticky zvýrazněná jinak `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCAutoHideBar – třída](../../mfc/reference/cmfcautohidebar-class.md)   
 [CAutoHideDockSite – třída](../../mfc/reference/cautohidedocksite-class.md)
