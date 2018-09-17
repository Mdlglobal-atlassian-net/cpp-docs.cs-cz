---
title: Cmfcribbonprogressbar – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 286c95b775b95d44ad8fd9dc216b161aed717796
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711981"
---
# <a name="cmfcribbonprogressbar-class"></a>Cmfcribbonprogressbar – třída
Implementuje ovládací prvek, který vizuálně označuje průběh déletrvající operace.  
  
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
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|Vrátí maximální hodnotu aktuálního rozsahu.|  
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|Vrátí minimální hodnotu rozsahu aktuální.|  
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|Vrátí regulární velikost elementu pásu karet. (Přepíše [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|Určuje, zda je indikátor průběhu práce v nekonečné režimu.|  
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|Volá se rozhraním, chcete-li nakreslit prvek pásu karet. (Přepíše [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|Nastaví indikátoru průběhu pro práci v nekonečné režimu.|  
|[CMFCRibbonProgressBar::SetPos](#setpos)|Nastaví aktuální průběh.|  
|[CMFCRibbonProgressBar::SetRange](#setrange)|Nastaví minimální a maximální hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 A `CMFCRibbonProgressBar` můžete pracovat ve dvou režimech: pravidelné a nekonečné. V pravidelných režimu indikátor průběhu naplní zleva doprava a zastaví, když dosáhl maximální hodnoty. V nekonečné režimu je indikátor průběhu vyplněna na základě minimální hodnota na maximální hodnotu opakovaně. Nekonečné režimu můžete použít k označení, že probíhá operace, ale, že čas dokončení neznámý.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít různé metody v `CMFCRibbonProgressBar` třídy. Příklad ukazuje, jak nastavit indikátoru průběhu pro práci v nekonečné režimu (kde čas dokončení operace neznámá), nastavit minimální a maximální hodnoty pro indikátor průběhu a nastavit aktuální pozici indikátor průběhu. Tento fragment kódu je součástí [MS Office 2007 demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonprogressbar –](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonProgressBar.h  
  
##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar  
 Vytvoří a inicializuje [cmfcribbonprogressbar –](../../mfc/reference/cmfcribbonprogressbar-class.md) objektu.  
  
```  
CMFCRibbonProgressBar();

 
CMFCRibbonProgressBar(
    UINT nID,  
    int nWidth = 90,  
    int nHeight = 22);
```  
  
### <a name="parameters"></a>Parametry  
*nID*<br/>
[in] Určuje ID příkazu pro indikátor průběhu pásu karet.  
  
*nWidth*<br/>
[in] Určuje šířku v pixelech, indikátor průběhu pásu karet.  
  
*nHeight*<br/>
[in] Určuje výšku v pixelech, indikátor průběhu pásu karet.  
  
##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos  
 Vrátí aktuální pozici indikátor průběhu.  
  
```  
int GetPos () const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota představující aktuální pozici indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah nastavování musí být v rozsahu určeném [CMFCRibbonProgressBar::SetRange](#setrange) metody.  
  
##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax  
 Vrátí uživatele indikátor průběhu aktuální maximální hodnota.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální hodnota v aktuálním rozsahu.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin  
 Vrátí uživatele indikátor průběhu aktuální minimální hodnotu rozsahu.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minimální hodnota v aktuálním rozsahu.  
  
##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize  
 Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode  
 Určuje, zda je indikátor průběhu práce v nekonečné režimu.  
  
```  
BOOL IsInfiniteMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je indikátor průběhu v nekonečné režimu. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 V nekonečné režimu indikátor průběhu vyplní opakovaně od minimální hodnoty na maximální hodnotu. Nekonečné režimu můžete použít k označení, že probíhá operace, ale, že čas dokončení neznámý.  
  
##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw  
 Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode  
 Nastaví indikátoru průběhu pro práci v nekonečné režimu.  
  
```  
void SetInfiniteMode(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bSet*<br/>
[in] TRUE, pokud chcete určit, že indikátor průběhu v nekonečné režimu. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle Pokud indikátor průběhu v nekonečné režimu, je sděluje uživateli, že probíhá operace, ale, že čas dokončení neznámý. Tak indikátor průběhu vyplní opakovaně od minimální hodnoty na maximální hodnotu.  
  
##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos  
 Nastaví aktuální pozici indikátor průběhu.  
  
```  
void SetPos(
    int nPos,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*nPos –*<br/>
[in] Určuje umístění, ke kterému je nastaven indikátor průběhu.  
  
*bRedraw*<br/>
[in] Určuje, zda by měl překreslit indikátor průběhu.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah nastavování musí být v rozsahu určeném [CMFCRibbonProgressBar::SetRange](#setrange) metody.  
  
##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange  
 Nastaví minimální a maximální hodnoty pro indikátor průběhu.  
  
```  
void SetRange(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
*Nminimum*<br/>
[in] Určuje minimální hodnotu rozsahu.  
  
*Nmaximum*<br/>
[in] Určuje maximální hodnotu rozsahu.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k definování rozsahu indikátoru průběhu nastavením minimální a maximální hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfcribbonbaseelement – třída](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar – třída](../../mfc/reference/cmfcribbonbar-class.md)
