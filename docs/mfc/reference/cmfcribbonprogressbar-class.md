---
title: "Třída CMFCRibbonProgressBar | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1354b0b15837a733a890c438c7771ffe39526773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar – třída
Implementuje ovládací prvek, který označuje vizuálně průběh operace může trvat dlouho.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|Vytvoří a inicializuje `CMFCRibbonProgressBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](#getpos)|Vrátí aktuální průběh.|  
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Vrátí maximální hodnotu rozsahu, aktuální.|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Vrátí minimální hodnotu rozsahu, aktuální.|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Vrátí velikost regulární elementu pásu karet. (Přepisuje [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Určuje, zda se indikátor průběhu pracuje v nekonečné režimu.|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Voláno rámcem k vykreslení elementu pásu karet. (Přepisuje [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Nastaví indikátor průběhu pro práci v nekonečné režimu.|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|Nastaví aktuální průběh.|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|Nastaví minimální a maximální hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 A `CMFCRibbonProgressBar` mohou pracovat ve dvou režimech: obyčejnými a nekonečné. V pravidelných režimu indikátoru průběhu vyplněno zleva doprava a zastaví, když dorazí do maximální hodnota. V nekonečné režimu indikátoru průběhu opakovaně vyplněno z minimální hodnota na maximální hodnotu. Nekonečné režim můžete použít k označení, že probíhá operace, ale že čas dokončení neznámý.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCRibbonProgressBar` třídy. Tento příklad ukazuje, jak nastavit indikátor průběhu pro práci v nekonečné režimu (kde čas dokončení operace neznámý), nastavit minimální a maximální hodnoty indikátoru průběhu a aktuální pozici indikátoru průběhu. Tento fragment kódu je součástí [MS Office 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 Vytvoří a inicializuje [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) objektu.  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nID`  
 Určuje ID příkazu pro indikátor průběhu pásu karet.  
  
 [v]`nWidth`  
 Určuje šířku v pixelech indikátor průběhu pásu karet.  
  
 [v]`nHeight`  
 Určuje výšku v pixelech indikátor průběhu pásu karet.  
  
##  <a name="getpos"></a>CMFCRibbonProgressBar::GetPos  
 Vrátí aktuální pozici indikátor průběhu.  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu představující aktuální pozici indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Probíhá nastavení rozsahu musí být v rozsahu určeném [CMFCRibbonProgressBar::SetRange](#setrange) metoda.  
  
##  <a name="getrangemax"></a>CMFCRibbonProgressBar::GetRangeMax  
 Vrátí indikátoru průběhu je aktuální maximální hodnota.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální hodnota, která aktuálním rozsahu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrangemin"></a>CMFCRibbonProgressBar::GetRangeMin  
 Vrátí indikátoru průběhu je aktuální minimální hodnotu rozsahu.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minimální hodnota aktuálním rozsahu.  
  
##  <a name="getregularsize"></a>CMFCRibbonProgressBar::GetRegularSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isinfinitemode"></a>CMFCRibbonProgressBar::IsInfiniteMode  
 Určuje, zda se indikátor průběhu pracuje v nekonečné režimu.  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud indikátor průběhu je v režimu nekonečné; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V nekonečné režimu indikátoru průběhu doplní opakovaně s minimální hodnotou maximální hodnotě. Nekonečné režim můžete použít k označení, že probíhá operace, ale že čas dokončení neznámý.  
  
##  <a name="ondraw"></a>CMFCRibbonProgressBar::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setinfinitemode"></a>CMFCRibbonProgressBar::SetInfiniteMode  
 Nastaví indikátor průběhu pro práci v nekonečné režimu.  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bSet`  
 `TRUE`k určení, že indikátor průběhu je v režimu nekonečné; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle Pokud indikátor průběhu v nekonečné režimu, ho je o tom, že probíhá operace, ale že čas dokončení neznámý. Proto indikátoru průběhu doplní opakovaně s minimální hodnotou maximální hodnotě.  
  
##  <a name="setpos"></a>CMFCRibbonProgressBar::SetPos  
 Nastaví aktuální umístění indikátoru průběhu.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nPos`  
 Určuje pozici, na kterou je nastavena indikátor průběhu.  
  
 [v]`bRedraw`  
 Určuje, zda by měl být překreslen indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Probíhá nastavení rozsahu musí být v rozsahu určeném [CMFCRibbonProgressBar::SetRange](#setrange) metoda.  
  
##  <a name="setrange"></a>CMFCRibbonProgressBar::SetRange  
 Nastaví minimální a maximální hodnoty indikátoru průběhu.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nMin`  
 Určuje minimální hodnotu rozsahu.  
  
 [v]`nMax`  
 Určuje maximální hodnotu rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k definování rozsahu indikátoru průběhu nastavením minimální a maximální hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
