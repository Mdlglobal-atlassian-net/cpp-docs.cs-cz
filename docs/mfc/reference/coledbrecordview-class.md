---
title: COleDBRecordView – třída
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366106"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView – třída

Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

## <a name="syntax"></a>Syntaxe

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[ColeDBRecordView::COleDBRecordView](#coledbrecordview)|Vytvoří `COleDBRecordView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Vrátí standardní hodnotu HRESULT.|
|[COleDBRecordView::OnMove](#onmove)|Aktualizuje aktuální záznam (pokud je znečištěný) ve zdroji dat a potom se přesune na zadaný záznam (další, předchozí, první nebo poslední).|

## <a name="remarks"></a>Poznámky

Zobrazení je formulářové zobrazení přímo `CRowset` připojené k objektu. Zobrazení je vytvořeno z prostředku šablony dialogu a `CRowset` zobrazuje pole objektu v ovládacích prvcích šablony dialogu. Objekt `COleDBRecordView` používá dialogovou výměnu dat (DDX) a `CRowset`navigační funkce integrované do aplikace k automatizaci pohybu dat mezi ovládacími prvky ve formuláři a poli sady řádků. `COleDBRecordView`také poskytuje výchozí implementaci pro přechod na první, další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu aktuálně v zobrazení.

Pomocí funkcí `COleDbRecordView` DDX můžete získat data přímo ze sady záznamů databáze a zobrazit je v ovládacím prvku dialogového okna. Měli byste `DDX_*` použít metody `DDX_Text`(například `DDX_Field*` ), nikoli `DDX_FieldText`funkce `COleDbRecordView`(například ) s . `DDX_FieldText`nebude pracovat `COleDbRecordView` s, protože `DDX_FieldText` má `CRecordset*` další `CRecordView`argument `CDaoRecordset*` typu `CDaoRecordView`(pro ) nebo (pro).

> [!NOTE]
> Pokud pracujete s třídami DAO (Data Access Objects) místo s třídami ŠABLONY příjemce TECHNOLOGIE OLE DB, použijte místo toho třídu [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Další informace naleznete v článku [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView`sleduje pozici uživatele v sadě řádků, aby zobrazení záznamu bylo možné aktualizovat uživatelské rozhraní. Když se uživatel přesune na některý konec sady řádků, zobrazení záznamu zakáže objekty uživatelského rozhraní , které se budou pohybovat dále ve stejném směru.

Další informace o třídách sad řádků naleznete v článku [Použití šablon příjemce technologie OLE DB.](../../data/oledb/ole-db-consumer-templates-cpp.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>ColeDBRecordView::COleDBRecordView

Vytvoří `COleDBRecordView` objekt.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec s ukončeným hodnotou null, který je názvem prostředku šablony dialogu.

*nIDŠablona*<br/>
Obsahuje id číslo prostředku šablony dialogu.

### <a name="remarks"></a>Poznámky

Když vytvoříte objekt typu odvozeného `COleDBRecordView`z , vyvoláte jeden z konstruktorů k vytvoření objektu zobrazení a identifikaci prostředku dialogu, na kterém je zobrazení založeno. Prostředek můžete identifikovat buď podle názvu (předejte řetězec jako argument konstruktoru) nebo jeho ID (předat nepodepsané celé číslo jako argument).

> [!NOTE]
> Odvozené třídy *musí* dodávat vlastní konstruktor. V konstruktoru vyvoláte konstruktor , `COleDBRecordView::COleDBRecordView`s názvem prostředku nebo ID jako argument.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDBRecordView::OnGetRowset

Vrátí popisovač pro **objekt CRowset<>** přidružený k zobrazení záznamu.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit nebo získat objekt sady řádků a vrátit mu popisovač, je nutné přepsat tuto členská funkci. Pokud deklarujete třídu zobrazení záznamu pomocí Průvodce třídou, průvodce za vás zapíše výchozí přepsání. ClassWizard výchozí implementace vrátí popisovač sady řádků uložené v zobrazení záznamů, pokud existuje. Pokud tomu tak není, vytvoří objekt sady řádků typu, který `Open` jste zadali pomocí ClassWizard, a zavolá svou člennou funkci, aby otevřela tabulku nebo spustila dotaz, a potom vrátí objektu popisovač.

> [!NOTE]
> Před knihovnou MFC `OnGetRowset` 7.0 `CRowset`vrátil ukazatel na . Pokud máte kód, `OnGetRowset`který volá , je třeba změnit návratový typ na templatized třídy **CRowset<>**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Další informace a příklady naleznete v článku [Zobrazení záznamů: Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDBRecordView::OnMove

Přesune se na jiný záznam v sadě řádků a zobrazí jeho pole v ovládacích prvcích zobrazení záznamů.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jedna z následujících standardních hodnot ID příkazu:

- ID_RECORD_FIRST — Přechod na první záznam v sadě záznamů.

- ID_RECORD_LAST — Přechod na poslední záznam v sadě záznamů.

- ID_RECORD_NEXT — Přechod na další záznam v sadě záznamů.

- ID_RECORD_PREV — Přechod na předchozí záznam v sadě záznamů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl přesun úspěšný; jinak 0, pokud byl požadavek na přesunutí odepřen.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá `Move` příslušnou členovou `CRowset` funkci objektu přidruženého k zobrazení záznamu.

Ve výchozím `OnMove` nastavení aktualizuje aktuální záznam ve zdroji dat, pokud jej uživatel změnil v zobrazení záznamu.

Průvodce aplikací vytvoří zdroj nabídky s položkami nabídky První záznam, Poslední záznam, Další záznam a Předchozí záznam. Pokud vyberete volbu Zakotvitelný panel nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídajícími těmto příkazům.

Pokud se přesunete za poslední záznam v sadě záznamů, zobrazení záznamu bude nadále zobrazovat poslední záznam. Pokud se posunete zpět za první záznam, zobrazení záznamu bude nadále zobrazovat první záznam.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
