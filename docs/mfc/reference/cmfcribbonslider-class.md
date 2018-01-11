---
title: "Třída CMFCRibbonSlider | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
caps.latest.revision: "43"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e485afac346be1f21a0b3088367be5b9bf02e2ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider – třída
`CMFCRibbonSlider` Třída implementuje ovládací prvek typu jezdec, který můžete přidat na pásu karet řádek nebo pásu karet stavový řádek. V ovládacím prvku posuvník pásu karet se podobá posuvníků zvětšení, které se zobrazují v aplikacích Office 2007.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Vytvoří a inicializuje ovládací prvek typu jezdec pásu karet.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](#getpos)|Vrátí aktuální pozici v ovládacím prvku posuvník.|  
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Vrátí maximální hodnotu jezdce.|  
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Vrátí minimální hodnotu jezdce.|  
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Vrátí velikost regulární elementu pásu karet. (Přepisuje [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Vrátí velikost přírůstek zvětšení ovládacího prvku posuvník.|  
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Určuje, zda je jezdec tlačítka přiblížení.|  
|[CMFCRibbonSlider::OnDraw](#ondraw)|Voláno rámcem k vykreslení elementu pásu karet. (Přepisuje [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonSlider::SetPos](#setpos)|Nastaví aktuální umístění v ovládacím prvku posuvník.|  
|[CMFCRibbonSlider::SetRange](#setrange)|Určuje rozsah ovládacího prvku posuvník nastavením minimální a maximální hodnoty.|  
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Zobrazí nebo skryje tlačítka přiblížení.|  
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Nastaví velikost přírůstek zvětšení ovládacího prvku posuvník.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `SetRange` metoda konfigurace rozsahu přiblížení přírůstcích u posuvníku. Aktuální pozice posuvníku lze nastavit pomocí `SetPos` metoda.  
  
 Tlačítka cyklické přiblížení na levé a pravé straně ovládacího prvku posuvník můžete zobrazit pomocí `SetZoomButtons` metoda. Ve výchozím nastavení, posuvník je vodorovné, na levém přiblížení tlačítko zobrazí znaménkem minus a tlačítko správné přiblížení znaménkem plus.  
  
 `SetZoomIncrement` Metoda definuje přírůstek k přidávání nebo odečíst od aktuální pozice, když uživatel klikne tlačítka přiblížení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCRibbonSlider` třídy a nastavte vlastnosti posuvníku. Tento příklad ukazuje, jak vytvořit `CMFCRibbonSlider` objektu, zobrazení tlačítka přiblížení, nastavte aktuální umístění v ovládacím prvku posuvník a nastavte rozsah hodnot pro ovládací prvek posuvníku.  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxribbonslider.h  
  
##  <a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider  
 Vytvořte jezdce pásu karet.  
  
```  
CMFCRibbonSlider(
    UINT nID,  
    int nWidth=100);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 ID posuvníku.  
  
 [v]. `nWidth`  
 Šířka posuvníku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří posuvníku pásu karet, která je `nWidth` pixelů v panelu kategorie, kde se přidá posuvníku. Ve výchozím nastavení je vodorovný posuvníku.  
  
##  <a name="getpos"></a>CMFCRibbonSlider::GetPos  
 Vrátí aktuální pozici v ovládacím prvku posuvník.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální umístění v ovládacím prvku posuvník, což je pozice relativně k začátku posuvníku.  
  
##  <a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax  
 Získá maximální přírůstek dráze jezdce, která mohou projít jezdec na posuvníku.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální přírůstek dráze jezdce, která mohou projít jezdec na posuvníku.  
  
##  <a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin  
 Vrátí minimální přírůstek, která mohou projít jezdec na posuvníku.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minimální přírůstek, která mohou projít jezdec na posuvníku.  
  
##  <a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement  
 Získáte přírůstek zvětšení ovládacího prvku posuvník.  
  
```  
int GetZoomIncrement() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Přírůstek zvětšení ovládacího prvku posuvník.  
  
##  <a name="haszoombuttons"></a>CMFCRibbonSlider::HasZoomButtons  
 Určuje, zda je jezdec tlačítka přiblížení.  
  
```  
BOOL HasZoomButtons() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud má posuvník tlačítka přiblížení; `FALSE` jinak.  
  
##  <a name="ondraw"></a>CMFCRibbonSlider::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setpos"></a>CMFCRibbonSlider::SetPos  
 Nastavte aktuální pozici v ovládacím prvku posuvník.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nPos`  
 Určuje pozici pro posuvníku. Pozice je relativní vzhledem k začátku posuvníku.  
  
 [v]`bRedraw`  
 Pokud `TRUE`, bude překreslit posuvníku.  
  
##  <a name="setrange"></a>CMFCRibbonSlider::SetRange  
 Nastavte rozsah hodnot pro ovládací prvek posuvníku.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nMin`  
 Určuje minimální hodnotu jezdce.  
  
 [v]`nMax`  
 Určuje maximální hodnotu jezdce.  
  
### <a name="remarks"></a>Poznámky  
 Určuje rozsah hodnot pro ovládací prvek jezdec nastavením minimální a maximální hodnoty.  
  
##  <a name="setzoombuttons"></a>CMFCRibbonSlider::SetZoomButtons  
 Zobrazení nebo skrytí tlačítka přiblížení.  
  
```  
void SetZoomButtons(BOOL bSet=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]. `bSet`  
 `TRUE`k zobrazení tlačítka přiblížení; `FALSE` jejich skrytí.  
  
##  <a name="setzoomincrement"></a>CMFCRibbonSlider::SetZoomIncrement  
 Nastavte přírůstek zvětšení ovládacího prvku posuvník.  
  
```  
void SetZoomIncrement(int nZoomIncrement);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nZoomIncrement`  
 Určuje přírůstek zvětšení ovládacího prvku posuvník.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)
