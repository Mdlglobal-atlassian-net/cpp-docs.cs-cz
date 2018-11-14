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
ms.openlocfilehash: fbbaaae72c7b58f898735d768c019a02cdb7d7e5
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518577"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView – třída

Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

## <a name="syntax"></a>Syntaxe

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|Vytvoří `COleDBRecordView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|Vrací standardní hodnotu HRESULT.|
|[COleDBRecordView::OnMove](#onmove)|Aktualizuje aktuální záznam ve zdroji dat (Pokud) a pak přesune zadaný záznam (Další, předchozí, první nebo poslední).|

## <a name="remarks"></a>Poznámky

Zobrazení je připojený přímo k zobrazení formuláře `CRowset` objektu. Toto zobrazení je vytvořen z prostředků šablony dialogového okna a zobrazí pole `CRowset` objektu v ovládacích prvcích šablony dialogového okna. `COleDBRecordView` Objektu používá výměna dat dialogových oken (DDX) a navigačních funkce součástí `CRowset`, automatizovat přesouvání dat mezi ovládacími prvky ve formuláři a polí v sadě řádků. `COleDBRecordView` také poskytuje výchozí implementaci pro přechod na první další, předchozí nebo poslední záznam a rozhraní pro aktualizace záznamu aktuálně pro zobrazení.

Můžete použít funkce DDX s `COleDbRecordView` získat data přímo ze sady záznamů databáze a zobrazit je v ovládacím prvku dialogu. Byste měli použít `DDX_*` metody (například `DDX_Text`), nikoli `DDX_Field*` funkce (například `DDX_FieldText`) s `COleDbRecordView`. `DDX_FieldText` nebude fungovat s `COleDbRecordView` protože `DDX_FieldText` přijímá další argument typu `CRecordset*` (pro `CRecordView`) nebo `CDaoRecordset*` (pro `CDaoRecordView`).

> [!NOTE]
>  Pokud pracujete s třídami objektů DAO (Data Access), a ne třídy šablona příjemce technologie OLE DB, použijte třídu [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) místo. Další informace najdete v článku [přehled: databáze programování](../../data/data-access-programming-mfc-atl.md).

`COleDBRecordView` uchovává informace o poloze uživatele v dané sadě řádků tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní. Když uživatel přesune na oba konce řádků, zobrazení záznamů zakáže objektů uživatelského rozhraní, jako je například položky nabídky nebo tlačítka na panelu nástrojů – pro přesun dále ve stejném směru.

Další informace o třídy sady řádků, najdete v článku [pomocí OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md) článku.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[Cscrollview –](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxoledb.h

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

Vytvoří `COleDBRecordView` objektu.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

### <a name="remarks"></a>Poznámky

Při vytváření objektu typu odvozené z `COleDBRecordView`, vyvolat jeden z konstruktorů k vytvoření objektu zobrazení a k identifikaci prostředku dialogového okna, na kterých je založena zobrazení. Název (pass řetězec jako argument konstruktoru) nebo jeho ID (pass celé číslo bez znaménka jako argument) můžete identifikovat prostředek.

> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru, vyvolání konstruktoru, `COleDBRecordView::COleDBRecordView`, s názvem prostředku nebo ID jako argument.

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

Vrátí obslužnou rutinu pro **CRowset <>** objekt přidružený k zobrazení záznamu.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Je nutné přepsat tuto členskou funkci sestavit nebo získání objektu sady řádků a vrátí popisovač do něj. Pokud deklarujete vaší třídy zobrazení záznamu s ClassWizard, zapíše průvodce přepsáním výchozího nastavení. ClassWizard výchozí implementace vrací popisovač řádků uložené v zobrazení záznamů, pokud existuje. Pokud ne, vytvoří objektu sady řádků typu zadán s ClassWizard a volání jeho `Open` členské funkce Otevřít v tabulce nebo spustit dotaz a vrátí popisovač objektu.

> [!NOTE]
>  Vytváření knihovny MFC 7.0 `OnGetRowset` vrátí ukazatel na `CRowset`. Pokud máte kód, který volá `OnGetRowset`, budete muset změnit návratový typ pro třídu přepsaly **CRowset <>**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

Další informace a příklady najdete v článku [zobrazení záznamu: použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  COleDBRecordView::OnMove

Zobrazení polí v ovládacích prvcích záznamu přesune na jiný záznam v sadě řádků a zobrazení.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jeden z následujících hodnot ID standardních příkazů:

- ID_RECORD_FIRST – Přesunout na první záznam v sadě záznamů.

- ID_RECORD_LAST – Přechod na poslední záznam v sadě záznamů.

- ID_RECORD_NEXT – Přesune na další záznam v sadě záznamů.

- ID_RECORD_PREV – Přesunout na předchozí záznam v sadě záznamů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo přesunutí úspěšné; jinak 0, pokud žádost o přesunutí byl odepřen.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá odpovídající `Move` členskou funkci `CRowset` objekt přidružený k zobrazení záznamu.

Ve výchozím nastavení `OnMove` aktualizuje aktuální záznam ve zdroji dat, pokud uživatel byl změněn v zobrazení záznamů.

Průvodce aplikace vytvoří prostředek nabídky s první záznam, poslední záznam, další záznam a předchozí záznam položky nabídky. Pokud vyberete možnost Ukotvitelné nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídající tyto příkazy.

Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamů stále zobrazuje poslední záznam. Pokud přejdete zpět za první záznam, zobrazení záznamů nepřestává zobrazovat první záznam.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)

