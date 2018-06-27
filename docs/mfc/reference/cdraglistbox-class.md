---
title: Třída CDragListBox | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
dev_langs:
- C++
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78f2c1843602c1c1db6b05a16bbea0aceec70df2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955986"
---
# <a name="cdraglistbox-class"></a>CDragListBox – třída
Kromě zajištění funkce Windows pole se seznamem `CDragListBox` třída umožňuje uživateli přesunout položky seznamu pole, jako jsou názvy souborů, v rámci pole se seznamem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|Vytvoří `CDragListBox` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|Voláno rámcem při zahájení operace přetažení.|  
|[CDragListBox::CancelDrag](#canceldrag)|Voláno rámcem při přetažení operace byla zrušena.|  
|[CDragListBox::Dragging](#dragging)|Voláno rámcem během operace přetažení.|  
|[CDragListBox::DrawInsert](#drawinsert)|Nakreslí vložení Průvodce přetáhněte pole seznamu.|  
|[CDragListBox::Dropped](#dropped)|Voláno rámcem po položce byla vyřazena.|  
|[CDragListBox::ItemFromPt](#itemfrompt)|Vrátí souřadnice přetažen položky.|  
  
## <a name="remarks"></a>Poznámky  
 Seznamy díky této funkci umožňují uživatelům pořadí položek v seznamu v jakýmkoli způsobem je velmi užitečné k nim. Ve výchozím nastavení bude pole se seznamem přesunout položku do nového umístění v seznamu. Ale `CDragListBox` objektů můžete přizpůsobit tak, aby kopírovat položky místo jejich přesunutí.  
  
 Ovládací prvek seznam přidružené `CDragListBox` třída nesmí mít **lbs_sort –** nebo **LBS_MULTIPLESELECT** stylu. Popis seznamu styly najdete v tématu [styly seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).  
  
 Pokud chcete používat přetáhněte pole se seznamem v existující dialogovém okně vaší aplikace, do šablony dialogové okno editoru dialogové okno Přidat ovládací prvek seznamu a pak mu přiřaďte členské proměnné (kategorie `Control` a proměnná typu `CDragListBox`) odpovídající pole se seznamem řízení v šabloně dialogové okno.  
  
 Další informace o přiřazení k členské proměnné ovládacích prvků, najdete v části [zástupce pro definování členských proměnných pro ovládací prvky dialogového okna](../../windows/defining-member-variables-for-dialog-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Clistbox –](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="begindrag"></a>  CDragListBox::BeginDrag  
 Volá framework při výskytu události, který by mohl spustit operaci přetažení, jako je například stisknutím levé tlačítko.  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice přetažen položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud přetahování je povolen, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pokud chcete řídit, co se stane, když začne operaci přetažení. Výchozí implementace zaznamená myši a zůstane v režimu přetažení, dokud uživatel klikne na tlačítko myši doleva nebo doprava nebo stiskem tlačítka ESC, které během operace přetažení zrušena.  
  
##  <a name="canceldrag"></a>  CDragListBox::CancelDrag  
 Voláno rámcem při přetažení operace byla zrušena.  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice přetažen položky.  
  
### <a name="remarks"></a>Poznámky  
 Funkci pro zpracování žádné speciální zpracování pro vaše ovládací prvek seznam přepište.  
  
##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox  
 Vytvoří `CDragListBox` objektu.  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>  CDragListBox::Dragging  
 Voláno rámcem při položku v seznamu je přetažen v rámci `CDragListBox` objektu.  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje x a y obrazovky souřadnice kurzor.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID prostředku kurzoru, který se má zobrazit. Následující hodnoty jsou možné:  
  
- `DL_COPYCURSOR` Určuje, zda bude položka zkopírována.  
  
- `DL_MOVECURSOR` Označuje, že položka bude přesunuta.  
  
- `DL_STOPCURSOR` Označuje, že aktuální cíle přetažení není platný.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí výchozí chování `DL_MOVECURSOR`. Tato funkce přepsání, pokud byste chtěli poskytnout další funkce.  
  
##  <a name="drawinsert"></a>  CDragListBox::DrawInsert  
 Voláno rámcem k vykreslení průvodci vložení před položka s označený index.  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 *nItem*  
 Index počítaný od nuly kurzor.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota - 1 vymaže průvodci vložení. Přepsání této funkci můžete změnit vzhled nebo chování příručky pro vložení.  
  
##  <a name="dropped"></a>  CDragListBox::Dropped  
 Voláno rámcem při přetažení položky v rámci `CDragListBox` objektu.  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcIndex*  
 Určuje index založený na nule vynechaných řetězce.  
  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice rozevírací lokality.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování zkopíruje položku seznamu a jeho data do nového umístění a poté se odstraní původní položce. Přepsání této funkci můžete přizpůsobit výchozí chování, například povolení kopie položky seznamu pole přetáhnout do jiných umístění v seznamu.  
  
##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt  
 Volání této funkce můžete získat index založený na nule položky seznamu, pole umístěné v *pt*.  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt obsahující souřadnice bodu v rámci pole se seznamem.  
  
 *bAutoScroll*  
 Nenulové hodnoty, pokud posouvání je povolen, jinak hodnota 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index pole položky seznamu, přetáhněte nule.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC TSTCON](../../visual-cpp-samples.md)   
 [Clistbox – třída](../../mfc/reference/clistbox-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CListBox – třída](../../mfc/reference/clistbox-class.md)
