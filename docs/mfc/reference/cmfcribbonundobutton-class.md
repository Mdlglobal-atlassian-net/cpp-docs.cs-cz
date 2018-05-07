---
title: Třída CMFCRibbonUndoButton | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CMFCRibbonUndoButton
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::AddUndoAction
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::CleanUpUndoList
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::GetActionNumber
- AFXRIBBONUNDOBUTTON/CMFCRibbonUndoButton::HasMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonUndoButton [MFC], CMFCRibbonUndoButton
- CMFCRibbonUndoButton [MFC], AddUndoAction
- CMFCRibbonUndoButton [MFC], CleanUpUndoList
- CMFCRibbonUndoButton [MFC], GetActionNumber
- CMFCRibbonUndoButton [MFC], HasMenu
ms.assetid: 5c42adf7-871d-4239-901e-47ae7fb816fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 233f37fc0ab31afcd8ba112677af8cd144d01c2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonundobutton-class"></a>CMFCRibbonUndoButton – třída
`CMFCRibbonUndoButton` Třída implementuje rozevíracího seznamu tlačítka, které obsahuje nejnovější příkazy uživatele. Uživatelé mohou vybrat jednu nebo více nejnovější příkazů z rozevíracího seznamu vrátit nebo vrátit zpět, je.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonUndoButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::CMFCRibbonUndoButton](#cmfcribbonundobutton)|Vytvoří nový `CMFCRibbonUndoButton` objekt pomocí ID příkazu, který zadáte, textový popisek a obrázků ze seznamu obrázků nadřazeného objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonUndoButton::AddUndoAction](#addundoaction)|Přidá novou akci do seznamu akcí.|  
|[CMFCRibbonUndoButton::CleanUpUndoList](#cleanupundolist)|Vymaže seznam akcí, který je rozevíracím seznamu.|  
|[CMFCRibbonUndoButton::GetActionNumber](#getactionnumber)|Určuje počet položek, které uživatel vybere ze seznamu rozevíracího seznamu.|  
|[CMFCRibbonUndoButton::HasMenu](#hasmenu)|Určuje, zda objekt obsahuje nabídky.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCRibbonUndoButton` Třída používá k reprezentaci rozevíracího seznamu zásobníku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonUndoButton` třídu a přidejte novou akci do seznamu akcí. Tento fragment kódu je součástí [pásu karet miniaplikacemi ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#2](../../mfc/reference/codesnippet/cpp/cmfcribbonundobutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonUndoButton](../../mfc/reference/cmfcribbonundobutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribbonundobutton.h  
  
##  <a name="addundoaction"></a>  CMFCRibbonUndoButton::AddUndoAction  
 Přidá novou akci do seznamu akcí.  
  
```  
void AddUndoAction(LPCTSTR lpszLabel);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLabel`  
 Popisek akce, která se zobrazí v rozevíracím seznamu.  
  
##  <a name="cleanupundolist"></a>  CMFCRibbonUndoButton::CleanUpUndoList  
 Vymaže seznam akcí, který je rozevíracím seznamu.  
  
```  
void CleanUpUndoList();
```  
  
##  <a name="cmfcribbonundobutton"></a>  CMFCRibbonUndoButton::CMFCRibbonUndoButton  
 Vytvoří nový `CMFCRibbonUndoButton` objekt pomocí ID příkazu, který zadáte, textový popisek a obrázků ze seznamu obrázků nadřazeného objektu.  
  
```  
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex=-1,  
    int nLargeImageIndex=-1);

 
CMFCRibbonUndoButton(
    UINT nID,  
    LPCTSTR lpszText,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nID`  
 Určuje identifikátor příkazu.  
  
 [v] `lpszText`  
 Určuje textový popisek tlačítka.  
  
 [v] `nSmallImageIndex`  
 Index v seznamu obrázků nadřazeného objektu, pro malý obrázek na tlačítko nule.  
  
 [v] `nLargeImageIndex`  
 Index počítaný od nuly v seznamu obrázků nadřazeného objektu, pro velké obrázku tlačítka.  
  
 [v] `hIcon`  
 Popisovač pro ikonu, která můžete použít jako obrázek na tlačítko.  
  
##  <a name="getactionnumber"></a>  CMFCRibbonUndoButton::GetActionNumber  
 Určuje počet položek, které uživatel vybere ze seznamu rozevíracího seznamu.  
  
```  
int GetActionNumber() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek, které vybrané uživatele.  
  
##  <a name="hasmenu"></a>  CMFCRibbonUndoButton::HasMenu  
 Určuje, zda objekt obsahuje nabídky.  
  
```  
virtual BOOL HasMenu() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
