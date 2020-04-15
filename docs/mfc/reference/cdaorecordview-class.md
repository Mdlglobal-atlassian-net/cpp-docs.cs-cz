---
title: Třída CDaoRecordView
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: b8c411dbd29316219759351f1f1633b6e57b92e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377142"
---
# <a name="cdaorecordview-class"></a>Třída CDaoRecordView

Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Vytvoří `CDaoRecordView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam prvním záznamem v přidružené sadě záznamů.|
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam posledním záznamem v přidružené sadě záznamů.|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Vrátí ukazatel na objekt třídy odvozené z `CDaoRecordset`aplikace . ClassWizard přepíše tuto funkci za vás a v případě potřeby vytvoří sadu záznamů.|
|[CDaoRecordView::OnMove](#onmove)|Pokud se aktuální záznam změnil, aktualizuje jej ve zdroji dat a přesune se na zadaný záznam (další, předchozí, první nebo poslední).|

## <a name="remarks"></a>Poznámky

Zobrazení je formulářové zobrazení přímo `CDaoRecordset` připojené k objektu. Zobrazení je vytvořeno z prostředku šablony dialogu a `CDaoRecordset` zobrazuje pole objektu v ovládacích prvcích šablony dialogu. Objekt `CDaoRecordView` používá dialogovou výměnu dat (DDX) a DAO výměnu pole záznamu (DFX) k automatizaci pohybu dat mezi ovládacími prvky ve formuláři a poli sady záznamů. `CDaoRecordView`také poskytuje výchozí implementaci pro přechod na první, další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu, který je aktuálně v zobrazení.

> [!NOTE]
> Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Stále můžete přistupovat ke zdrojům dat ODBC pomocí tříd DAO; Třídy DAO obecně nabízejí vynikající možnosti, protože používají databázový stroj Microsoft Jet.

Nejběžnější způsob vytvoření zobrazení záznamů je pomocí Průvodce aplikací. Průvodce aplikací vytvoří třídu zobrazení záznamů i její přidruženou třídu sady záznamů jako součást počáteční aplikace kostry.

Pokud potřebujete pouze jeden formulář, přístup Průvodce aplikací je jednodušší. ClassWizard umožňuje rozhodnout se použít zobrazení záznamu později v procesu vývoje. Pokud nevytvoříte třídu zobrazení záznamů pomocí Průvodce aplikací, můžete ji vytvořit později pomocí Průvodce třídou. Použití ClassWizard vytvořit zobrazení záznamů a sadu záznamů samostatně a potom je připojit je nejpružnější přístup, protože poskytuje větší kontrolu při pojmenování třídy sady záznamů a jeho . H/. CPP soubory. Tento přístup také umožňuje mít více zobrazení záznamů ve stejné třídě sady záznamů.

Chcete-li koncovým uživatelům usnadnit přechod ze záznamu na záznam v zobrazení záznamu, průvodce aplikací vytvoří prostředky nabídky (a volitelně panelu nástrojů) pro přechod na první, další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu pomocí ClassWizard, budete muset vytvořit tyto prostředky sami s menu a bitmapové editory.

Informace o výchozí implementaci pro přechod ze `IsOnFirstRecord` záznamu `IsOnLastRecord` na záznam naleznete v tématu a `CRecordView` `CDaoRecordView`v článku Použití [zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md), který se vztahuje na obě aplikace , tak .

`CDaoRecordView`sleduje pozici uživatele v sadě záznamů, aby zobrazení záznamu bylo možné aktualizovat uživatelské rozhraní. Když se uživatel přesune na některý konec sady záznamů, zobrazení záznamu zakáže objekty uživatelského rozhraní , které se budou pohybovat dále ve stejném směru.

Další informace o deklarování a používání tříd zobrazení záznamů a sady záznamů naleznete v tématu "Návrh a vytvoření zobrazení záznamů" v článku [Zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o tom, jak zobrazení záznamů fungují a jak je používat, naleznete v článku [Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md). Všechny výše uvedené články se `CRecordView` `CDaoRecordView`vztahují na oba a .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[Cformview](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView

Když vytvoříte objekt typu odvozeného `CDaoRecordView`z , volání obou formulářů konstruktoru inicializuje objekt zobrazení a identifikuje prostředek dialogu, na kterém je zobrazení založeno.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec s ukončeným hodnotou null, který je názvem prostředku šablony dialogu.

*nIDŠablona*<br/>
Obsahuje číslo ID prostředku šablony dialogu.

### <a name="remarks"></a>Poznámky

Můžete buď identifikovat prostředek podle názvu (předat řetězec jako argument konstruktoru) nebo jeho ID (předat nepodepsané celé číslo jako argument). Doporučujeme použít ID prostředku.

> [!NOTE]
> Odvozené třídy musí dodávat vlastní konstruktor. V konstruktoru odvozené třídy volejte `CDaoRecordView::CDaoRecordView` konstruktor s názvem prostředku nebo ID jako argument.

`CDaoRecordView::OnInitialUpdate`volání `CWnd::UpdateData`, `CWnd::DoDataExchange`které volá . Toto počáteční `DoDataExchange` volání `CDaoRecordView` pro připojení ovládacích prvků (nepřímo) k `CDaoRecordset` datovým členům polí vytvořeným průvodcem ClassWizard. Tyto datové členy nelze použít, dokud `CFormView::OnInitialUpdate` po volání členské funkce základní třídy.

> [!NOTE]
> Pokud použijete ClassWizard, průvodce definuje hodnotu `CDaoRecordView::IDD` **výčtu** v deklaraci třídy a použije ji v seznamu inicializace členů pro konstruktor.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord

Volánítéto členské funkce k určení, zda aktuální záznam je první záznam v objektu sady záznamů přidružené k tomuto zobrazení záznamu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je aktuální záznam prvním záznamem v sadě záznamů; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro zápis vlastních implementací výchozích obslužných rutin aktualizace příkazů napsaných Průvodcem classwizard.

Pokud se uživatel přesune na první záznam, rozhraní framework zakáže všechny objekty uživatelského rozhraní (například položky nabídky nebo tlačítka panelu nástrojů), které máte pro přesunutí na první nebo předchozí záznam.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView::IsOnLastRecord

Volánítéto členské funkce k určení, zda aktuální záznam je poslední záznam v objektu sady záznamů přidružené k tomuto zobrazení záznamu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je aktuální záznam posledním záznamem v sadě záznamů; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro zápis vlastních implementací výchozích obslužných rutin aktualizace příkazů, které ClassWizard zapisuje pro podporu uživatelského rozhraní pro přechod ze záznamu na záznam.

> [!CAUTION]
> Výsledek této funkce je spolehlivý s tím rozdílem, že zobrazení nemusí být schopen rozpoznat konec sady záznamů, dokud uživatel přesunul kolem něj. Uživatel může být nutné přejít za poslední záznam, než zobrazení záznamu může zjistit, že musí zakázat všechny objekty uživatelského rozhraní pro přesunutí na další nebo poslední záznam. Pokud se uživatel přesune za poslední záznam a potom se přesune zpět na poslední záznam (nebo před ním), zobrazení záznamu můžete sledovat pozici uživatele v sadě záznamů a zakázat objekty uživatelského rozhraní správně.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset

Vrátí ukazatel na `CDaoRecordset`objekt -derived přidružený k zobrazení záznamu.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CDaoRecordset`-odvozený objekt, pokud byl objekt úspěšně vytvořen; jinak ukazatel NULL.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit nebo získat objekt sady záznamů a vrátit mu ukazatel, je nutné přepsat tuto členská funkci. Pokud deklarujete třídu zobrazení záznamu pomocí Průvodce třídou, průvodce za vás zapíše výchozí přepsání. ClassWizard výchozí implementace vrátí ukazatel sady záznamů uložené v zobrazení záznamu, pokud existuje. Pokud tomu tak není, vytvoří objekt sady záznamů typu, který `Open` jste zadali pomocí ClassWizard, a zavolá svou člennou funkci, aby otevřela tabulku nebo spustila dotaz, a potom vrátí ukazatel na objekt.

Další informace a příklady naleznete v článku [Zobrazení záznamů: Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView::OnMove

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

Výchozí implementace volá příslušnou člennou `CDaoRecordset` funkci Move objektu přidruženého k zobrazení záznamu.

Ve výchozím `OnMove` nastavení aktualizuje aktuální záznam ve zdroji dat, pokud jej uživatel změnil v zobrazení záznamu.

Průvodce aplikací vytvoří zdroj nabídky s položkami nabídky První záznam, Poslední záznam, Další záznam a Předchozí záznam. Pokud vyberete možnost Počáteční panel nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídajícími těmto příkazům.

Pokud se přesunete za poslední záznam v sadě záznamů, zobrazení záznamu bude nadále zobrazovat poslední záznam. Pokud se posunete zpět za první záznam, zobrazení záznamu bude nadále zobrazovat první záznam.

> [!CAUTION]
> Volání `OnMove` vyvolá výjimku, pokud sada záznamů nemá žádné záznamy. Před odpovídající operací přesunutí zavolejte `OnUpdateRecordNext`příslušnou `OnUpdateRecordPrev` funkci obslužné rutiny aktualizace uživatelského rozhraní – `OnUpdateRecordFirst`, `OnUpdateRecordLast`, nebo ) a zjistěte, zda má sada záznamů nějaké záznamy.

## <a name="see-also"></a>Viz také

[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
