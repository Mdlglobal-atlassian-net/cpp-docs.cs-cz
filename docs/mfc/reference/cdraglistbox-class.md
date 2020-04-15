---
title: Třída CDragListBox
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
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374033"
---
# <a name="cdraglistbox-class"></a>Třída CDragListBox

Kromě poskytování funkcí seznamu systému Windows `CDragListBox` umožňuje třída uživateli přesunout položky seznamu, například názvy souborů, v seznamu.

## <a name="syntax"></a>Syntaxe

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Vytvoří `CDragListBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Volat rámci při spuštění operace přetažení.|
|[CDragListBox::CancelDrag](#canceldrag)|Volat rámci při operaci přetažení byla zrušena.|
|[CDragListBox::Dragging](#dragging)|Volat rámci během operace přetažení.|
|[CDragListBox::DrawInsert](#drawinsert)|Nakreslí vodítko pro vložení seznamu přetažení.|
|[CDragListBox::D](#dropped)|Volat rámci po položka byla vynechána.|
|[CDragListBox::ItemFrompt](#itemfrompt)|Vrátí souřadnice přetahované položky.|

## <a name="remarks"></a>Poznámky

Seznamy s touto funkcí umožňují uživatelům objednat položky v seznamu jakýmkoli způsobem, který je pro ně nejužitečnější. Ve výchozím nastavení bude seznam přesunout položku do nového umístění v seznamu. Objekty `CDragListBox` však lze přizpůsobit tak, aby zkopírovaly položky namísto jejich přesouvání.

Ovládací prvek seznamu přidružený `CDragListBox` ke třídě nesmí obsahovat LBS_SORT nebo LBS_MULTIPLESELECT stylu. Popis stylů seznamu naleznete v tématu [Styly seznamu](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Chcete-li použít seznam přetažení v existujícím dialogovém okně aplikace, přidejte ovládací prvek seznamu do šablony dialogového okna pomocí editoru dialogů a přiřaďte členská proměnná (Kategorie `Control` a Typ `CDragListBox`proměnné) odpovídající ovládacímu prvku seznamu v šabloně dialogového okna.

Další informace o přiřazování ovládacích prvků členským proměnným naleznete v [tématu Zástupce pro definování členských proměnných pro ovládací prvky dialogových dialogů](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox::BeginDrag

Volat rámci při dojde k události, která by mohla zahájit operaci přetažení, jako je například stisknutí levého tlačítka myši.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice položky přetahované.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je přetažení povoleno, jinak 0.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete řídit, co se stane při zahájení operace přetažení. Výchozí implementace zachytí myš a zůstane v režimu přetažení, dokud uživatel neklepne na levé nebo pravé tlačítko myši nebo stiskne ESC, kdy je operace přetažení zrušena.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox::CancelDrag

Volat rámci při operaci přetažení byla zrušena.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice položky přetahované.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci pro zpracování jakékoli speciální zpracování pro ovládací prvek seznamu.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox::CDragListBox

Vytvoří `CDragListBox` objekt.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox::Dragging

Volat rámci při přetahování položky seznamu `CDragListBox` v rámci objektu.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje x a y souřadnice obrazovky kurzoru.

### <a name="return-value"></a>Návratová hodnota

ID prostředku kurzoru, který má být zobrazen. Jsou možné následující hodnoty:

- DL_COPYCURSOR Označuje, že položka bude zkopírována.

- DL_MOVECURSOR Označuje, že položka bude přesunuta.

- DL_STOPCURSOR Označuje, že aktuální cíl přetažení není přijatelné.

### <a name="remarks"></a>Poznámky

Výchozí chování vrátí DL_MOVECURSOR. Přepsat tuto funkci, pokud chcete poskytnout další funkce.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox::DrawInsert

Volat rámci nakreslit vodítko vložení před položku s uvedeným indexem.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Nulový index kurzoru.

### <a name="remarks"></a>Poznámky

Hodnota - 1 vymaže vodítko vložení. Přepsáním této funkce můžete upravit vzhled nebo chování vodítka vložení.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox::D

Volat rámci při položka je vynechána v rámci objektu. `CDragListBox`

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parametry

*nSrcIndex*<br/>
Určuje nulový index vynechaného řetězce.

*Pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt, který obsahuje souřadnice přetažení webu.

### <a name="remarks"></a>Poznámky

Výchozí chování zkopíruje položku seznamu a její data do nového umístění a odstraní původní položku. Přepsáním této funkce můžete přizpůsobit výchozí chování, například povolit přetažení kopií položek seznamu do jiných umístění v seznamu.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDragListBox::ItemFrompt

Volánítéto funkce načíst nula index položky seznamu umístěné na *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objekt obsahující souřadnice bodu v seznamu.

*bAutomatický posun*<br/>
Nenulová, pokud je povoleno posouvání, jinak 0.

### <a name="return-value"></a>Návratová hodnota

Nulový index položky seznamu přetažení.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)
