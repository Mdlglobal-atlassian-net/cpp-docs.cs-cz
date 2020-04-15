---
title: CRecordView – třída
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368358"
---
# <a name="crecordview-class"></a>CRecordView – třída

Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CRecordView::CRecordView](#crecordview)|Vytvoří `CRecordView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam prvním záznamem v přidružené sadě záznamů.|
|[CRecordView::IsonLastRecord](#isonlastrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam posledním záznamem v přidružené sadě záznamů.|
|[CRecordView::OnGetRecordset](#ongetrecordset)|Vrátí ukazatel na objekt třídy odvozené z `CRecordset`aplikace . ClassWizard přepíše tuto funkci za vás a v případě potřeby vytvoří sadu záznamů.|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|Pokud se aktuální záznam změnil, aktualizuje jej ve zdroji dat a přesune se na zadaný záznam (další, předchozí, první nebo poslední).|

## <a name="remarks"></a>Poznámky

Zobrazení je formulářové zobrazení přímo `CRecordset` připojené k objektu. Zobrazení je vytvořeno z prostředku šablony dialogu a `CRecordset` zobrazuje pole objektu v ovládacích prvcích šablony dialogu. Objekt `CRecordView` používá dialogovou výměnu dat (DDX) a výměnu pole záznamu (RFX) k automatizaci pohybu dat mezi ovládacími prvky ve formuláři a poli sady záznamů. `CRecordView`také poskytuje výchozí implementaci pro přechod na první, další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu aktuálně v zobrazení.

> [!NOTE]
> Pokud pracujete s třídami DAO (Data Access Objects) místo s třídami Open Database Connectivity (ODBC), použijte místo toho třídu [CDaoRecordView.](../../mfc/reference/cdaorecordview-class.md) Další informace naleznete v článku [Přehled: Programování databáze](../../data/data-access-programming-mfc-atl.md).

Nejběžnější způsob vytvoření zobrazení záznamů je pomocí Průvodce aplikací. Průvodce aplikací vytvoří třídu zobrazení záznamů i její přidruženou třídu sady záznamů jako součást počáteční aplikace kostry. Pokud nevytvoříte třídu zobrazení záznamů pomocí Průvodce aplikací, můžete ji vytvořit později pomocí Průvodce třídou. Pokud potřebujete pouze jeden formulář, přístup Průvodce aplikací je jednodušší. ClassWizard umožňuje rozhodnout se použít zobrazení záznamu později v procesu vývoje. Použití ClassWizard vytvořit zobrazení záznamů a sadu záznamů samostatně a potom je připojit je nejpružnější přístup, protože poskytuje větší kontrolu při pojmenování třídy sady záznamů a jeho . H/. CPP soubory. Tento přístup také umožňuje mít více zobrazení záznamů ve stejné třídě sady záznamů.

Chcete-li koncovým uživatelům usnadnit přechod ze záznamu na záznam v zobrazení záznamu, průvodce aplikací vytvoří prostředky nabídky (a volitelně panelu nástrojů) pro přechod na první, další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu pomocí ClassWizard, budete muset vytvořit tyto prostředky sami s menu a bitmapové editory.

Informace o výchozí implementaci pro přechod ze `IsOnFirstRecord` záznamu `IsOnLastRecord` na záznam naleznete v tématu a v článku [Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView`sleduje pozici uživatele v sadě záznamů, aby zobrazení záznamu bylo možné aktualizovat uživatelské rozhraní. Když se uživatel přesune na některý konec sady záznamů, zobrazení záznamu zakáže objekty uživatelského rozhraní , které se budou pohybovat dále ve stejném směru.

Další informace o deklarování a používání tříd zobrazení záznamů a sady záznamů naleznete v tématu "Návrh a vytvoření zobrazení záznamů" v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o tom, jak zobrazení záznamů fungují a jak je používat, naleznete v článku [Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView::CRecordView

Když vytvoříte objekt typu odvozeného `CRecordView`z , volání obou formulářů konstruktoru inicializuje objekt zobrazení a identifikuje prostředek dialogu, na kterém je zobrazení založeno.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec s ukončeným hodnotou null, který je názvem prostředku šablony dialogu.

*nIDŠablona*<br/>
Obsahuje číslo ID prostředku šablony dialogu.

### <a name="remarks"></a>Poznámky

Můžete buď identifikovat prostředek podle názvu (předat řetězec jako argument konstruktoru) nebo jeho ID (předat nepodepsané celé číslo jako argument). Doporučujeme použít ID prostředku.

> [!NOTE]
> Odvozené třídy *musí* dodávat vlastní konstruktor. V konstruktoru odvozené třídy volejte `CRecordView::CRecordView` konstruktor s názvem prostředku nebo ID jako argument, jak je znázorněno v příkladu níže.

`CRecordView::OnInitialUpdate`volání `UpdateData`, `DoDataExchange`které volá . Toto počáteční `DoDataExchange` volání `CRecordView` pro připojení ovládacích prvků (nepřímo) k `CRecordset` datovým členům polí vytvořeným průvodcem ClassWizard. Tyto datové členy nelze použít, dokud `CFormView::OnInitialUpdate` po volání členské funkce základní třídy.

> [!NOTE]
> Pokud použijete ClassWizard, průvodce definuje hodnotu `CRecordView::IDD` **výčtu** , určuje ji v deklaraci třídy a používá ji v seznamu inicializace členů pro konstruktor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView::IsOnFirstRecord

Volánítéto členské funkce k určení, zda aktuální záznam je první záznam v objektu sady záznamů přidružené k tomuto zobrazení záznamu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je aktuální záznam prvním záznamem v sadě záznamů; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro zápis vlastních implementací výchozích obslužných rutin aktualizace příkazů napsaných Průvodcem classwizard.

Pokud se uživatel přesune na první záznam, rozhraní framework zakáže všechny objekty uživatelského rozhraní, které máte pro přesunutí na první nebo předchozí záznam.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView::IsonLastRecord

Volánítéto členské funkce k určení, zda aktuální záznam je poslední záznam v objektu sady záznamů přidružené k tomuto zobrazení záznamu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je aktuální záznam posledním záznamem v sadě záznamů; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro zápis vlastních implementací výchozích obslužných rutin aktualizace příkazů, které ClassWizard zapisuje pro podporu uživatelského rozhraní pro přechod ze záznamu na záznam.

> [!CAUTION]
> Výsledek této funkce je spolehlivý s tím rozdílem, že zobrazení nemůže zjistit konec sady záznamů, dokud uživatel nepřešel za něj. Uživatel musí přejít za poslední záznam, než zobrazení záznamu může zjistit, že musí zakázat všechny objekty uživatelského rozhraní pro přesunutí na další nebo poslední záznam. Pokud se uživatel přesune za poslední záznam a potom se přesune zpět na poslední záznam (nebo před ním), zobrazení záznamu můžete sledovat pozici uživatele v sadě záznamů a zakázat objekty uživatelského rozhraní správně. `IsOnLastRecord`je také nespolehlivé po volání `OnRecordLast`funkce implementace , která zpracovává `CRecordset::MoveLast`příkaz ID_RECORD_LAST nebo .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView::OnGetRecordset

Vrátí ukazatel na `CRecordset`objekt -derived přidružený k zobrazení záznamu.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CRecordset`-odvozený objekt, pokud byl objekt úspěšně vytvořen; jinak ukazatel NULL.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit nebo získat objekt sady záznamů a vrátit mu ukazatel, je nutné přepsat tuto členská funkci. Pokud deklarujete třídu zobrazení záznamu pomocí Průvodce třídou, průvodce za vás zapíše výchozí přepsání. ClassWizard výchozí implementace vrátí ukazatel sady záznamů uložené v zobrazení záznamu, pokud existuje. Pokud tomu tak není, vytvoří objekt sady záznamů typu, který `Open` jste zadali pomocí ClassWizard, a zavolá svou člennou funkci, aby otevřela tabulku nebo spustila dotaz, a potom vrátí ukazatel na objekt.

Další informace a příklady naleznete v článku [Zobrazení záznamů: Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView::OnMove

Volání této členské funkce přesunout na jiný záznam v sadě záznamů a zobrazit jeho pole v ovládacích prvcích zobrazení záznamu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jedna z následujících standardních hodnot ID příkazu:

- ID_RECORD_FIRST Přechod na první záznam v sadě záznamů.

- ID_RECORD_LAST Přesunout na poslední záznam v sadě záznamů.

- ID_RECORD_NEXT Přechod na další záznam v sadě záznamů.

- ID_RECORD_PREV Přechod na předchozí záznam v sadě záznamů

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl přesun úspěšný; jinak 0, pokud byl požadavek na přesunutí odepřen.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá `Move` příslušnou členovou `CRecordset` funkci objektu přidruženého k zobrazení záznamu.

Ve výchozím `OnMove` nastavení aktualizuje aktuální záznam ve zdroji dat, pokud jej uživatel změnil v zobrazení záznamu.

Průvodce aplikací vytvoří zdroj nabídky s položkami nabídky První záznam, Poslední záznam, Další záznam a Předchozí záznam. Pokud vyberete volbu Zakotvitelný panel nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídajícími těmto příkazům.

Pokud se přesunete za poslední záznam v sadě záznamů, zobrazení záznamu bude nadále zobrazovat poslední záznam. Pokud se posunete zpět za první záznam, zobrazení záznamu bude nadále zobrazovat první záznam.

> [!CAUTION]
> Volání `OnMove` vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Před odpovídající operací přesunutí zavolejte `OnUpdateRecordNext`příslušnou `OnUpdateRecordPrev` funkci obslužné rutiny aktualizace uživatelského rozhraní – `OnUpdateRecordFirst`, `OnUpdateRecordLast`, nebo ) a zjistěte, zda má sada záznamů nějaké záznamy.

## <a name="see-also"></a>Viz také

[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
