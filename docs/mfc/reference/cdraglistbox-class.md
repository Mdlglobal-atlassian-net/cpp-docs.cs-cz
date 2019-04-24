---
title: Cdraglistbox – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: d8afc5b14f5f52ca7a4d28a3d3c3c5440b7c819f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164043"
---
# <a name="cdraglistbox-class"></a>Cdraglistbox – třída

Kromě zajištění funkcí seznamu Windows, `CDragListBox` třída umožňuje uživateli seznam položek pole, jako jsou názvy souborů, přesouvat v rámci pole se seznamem.

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
|[CDragListBox::BeginDrag](#begindrag)|Volá se rozhraním, když začne operace přetažení.|
|[CDragListBox::CancelDrag](#canceldrag)|Volá se rozhraním, když operace přetažení zruší.|
|[CDragListBox::Dragging](#dragging)|Volá se rozhraním, během operace přetažení.|
|[CDragListBox::DrawInsert](#drawinsert)|Vykreslí se vykreslilo vodítko přetáhněte pole se seznamem.|
|[CDragListBox::Dropped](#dropped)|Volá se rozhraním po položce byla vyřazena.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Vrátí souřadnice položky právě přetáhli.|

## <a name="remarks"></a>Poznámky

Pole se seznamem díky tomu umožňuje uživatelům pořadí položek v seznamu v jakýmkoli způsobem je pro ně nejvhodnější. Ve výchozím nastavení bude pole se seznamem přesunout položku do nového umístění v seznamu. Ale `CDragListBox` objekty lze přizpůsobit, aby kopírovat položky místo jejich přesunutí.

Přidružený ovládací prvek seznam `CDragListBox` třída nesmí mít LBS_SORT nebo styl LBS_MULTIPLESELECT. Popis seznamu styly, naleznete v tématu [styly seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Použití seznamu přetáhněte v existující dialogové okno s vaší aplikace, do šablony dialogového okna pomocí editoru dialogového okna přidat ovládací prvek seznamu a pak přiřaďte členské proměnné (kategorie `Control` a proměnné typu `CDragListBox`) odpovídající pole se seznamem ovládací prvek v šabloně dialogu.

Další informace o přiřazování k proměnné členů ovládacích prvků naleznete v tématu [klávesovou zkratku pro definování členských proměnných pro ovládací prvky dialogového okna](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="begindrag"></a>  CDragListBox::BeginDrag

Volá framework při výskytu události, která by mohla spustit operaci přetažení, jako je například stisknutí levého tlačítka myši.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice položky právě přetáhli.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud přetažení je povoleno, jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud chcete řídit, co se stane, když začne operace přetažení. Výchozí implementace zachytí myš a zůstane v režimu přetažení, dokud uživatel stiskne tlačítko myši doleva nebo doprava nebo stiskne klávesu ESC, které během operace přetažení zrušena.

##  <a name="canceldrag"></a>  CDragListBox::CancelDrag

Volá se rozhraním, když operace přetažení zruší.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice položky právě přetáhli.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci pro zpracování všechna speciální zpracování pro ovládací prvek seznamu pole.

##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox

Vytvoří `CDragListBox` objektu.

```
CDragListBox();
```

##  <a name="dragging"></a>  CDragListBox::Dragging

Volá se rozhraním, když se ocitne položky seznamu v rámci `CDragListBox` objektu.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje x a y obrazovky souřadnice kurzoru.

### <a name="return-value"></a>Návratová hodnota

ID prostředku kurzoru, který se má zobrazit. Možné jsou následující hodnoty:

- DL_COPYCURSOR označuje, že bude položka zkopírována.

- DL_MOVECURSOR označuje, že položka bude přesunut.

- DL_STOPCURSOR označuje, že aktuální cíl přetažení je nepřijatelné.

### <a name="remarks"></a>Poznámky

Výchozí chování vrátí DL_MOVECURSOR. Tato funkce přepište, pokud chcete poskytovat další funkce.

##  <a name="drawinsert"></a>  CDragListBox::DrawInsert

Volá se rozhraním, aby se vykreslilo vodítko před položkou s uvedeným indexem.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index založený na nule kurzor.

### <a name="remarks"></a>Poznámky

Hodnota - 1 vymaže se vykreslilo vodítko ukazatele. Přepsání této funkce můžete změnit vzhled nebo chování se vykreslilo vodítko ukazatele.

##  <a name="dropped"></a>  CDragListBox::Dropped

Volá se rozhraním při přetažení položky v rámci `CDragListBox` objektu.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parametry

*nSrcIndex*<br/>
Určuje index založený na nule vynechaných řetězec.

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice místa přetažení.

### <a name="remarks"></a>Poznámky

Výchozí chování zkopíruje položky seznamu a její data do nového umístění a poté odstraní původní položka. Přepsání této funkce můžete přizpůsobit výchozí chování, například povolení kopie seznam položek pole přetáhnout do jiných umístění v rámci seznamu.

##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt

Volání této funkce načtete index založený na nule položky seznamu nachází v *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parametry

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice bodu v rámci tohoto pole se seznamem.

*bAutoScroll*<br/>
Nenulové, pokud posouvání je povoleno, jinak 0.

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index položky seznamu přetažení.

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC lze kontejner TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)
