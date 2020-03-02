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
ms.openlocfilehash: 409739d97c9f7ae9a730ac8f05bd86e647da2c71
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215535"
---
# <a name="crecordview-class"></a>CRecordView – třída

Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRecordView:: CRecordView](#crecordview)|Vytvoří objekt `CRecordView`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRecordView:: IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam prvním záznamem v přidružené sadě záznamů.|
|[CRecordView:: IsOnLastRecord](#isonlastrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam posledním záznamem v přidružené sadě záznamů.|
|[CRecordView:: OnGetRecordset](#ongetrecordset)|Vrací ukazatel na objekt třídy odvozené z `CRecordset`. ClassWizard tuto funkci potlačí a v případě potřeby vytvoří sadu záznamů.|
|[CRecordView::-Move](#onmove)||

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CRecordView::-Move](#onmove)|Pokud se aktuální záznam změní, aktualizuje ho ve zdroji dat a pak se přesune na zadaný záznam (další, předchozí, první nebo poslední).|

## <a name="remarks"></a>Poznámky

Zobrazení je formulářové zobrazení, které je přímo připojeno k objektu `CRecordset`. Zobrazení je vytvořeno z šablony dialogového okna prostředku a zobrazí pole objektu `CRecordset` v ovládacích prvcích šablony dialogového okna. Objekt `CRecordView` používá výměnu dat dialogových oken (DDX) a záznam výměny pole (RFX) pro automatizaci přesunu dat mezi ovládacími prvky formuláře a poli sady záznamů. `CRecordView` také poskytuje výchozí implementaci pro přechod na první, další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu, který je aktuálně zobrazen.

> [!NOTE]
>  Pokud pracujete s třídami objektů pro přístup k datům (DAO), nikoli s třídami rozhraní ODBC (Open Database Connectivity), místo toho použijte třídu [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) . Další informace najdete v článku [Přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).

Nejběžnější způsob, jak vytvořit zobrazení záznamu, je pomocí Průvodce aplikací. Průvodce aplikací vytvoří jak třídu zobrazení záznamu, tak přidruženou třídu sady záznamů jako součást úvodní aplikace v rámci vaší kostry. Pokud nevytvoříte třídu zobrazení záznamu pomocí Průvodce aplikací, můžete ji vytvořit později pomocí ClassWizard. Potřebujete-li jednoduše pouze jeden formulář, je přístup k Průvodci aplikací jednodušší. ClassWizard umožňuje později použít zobrazení záznamu v procesu vývoje. Použití ClassWizard k vytvoření zobrazení záznamu a sady záznamů samostatně a jejich připojení je nejpružnější přístup, protože poskytuje větší kontrolu při pojmenovávání třídy sady záznamů a její. H/. Soubory CPP. Tento přístup také umožňuje mít v rámci stejné třídy sady záznamů více zobrazení záznamů.

Aby se koncoví uživatelé mohli snadno přesunout ze záznamu na záznam v zobrazení záznamu, vytvoří Průvodce aplikací nabídku (a volitelně panel nástrojů), aby se přesunuly na první, další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu s ClassWizard, musíte tyto prostředky vytvořit sami pomocí nabídky a editorů rastrových obrázků.

Informace o výchozí implementaci pro přesun ze záznamu na záznam naleznete v tématu `IsOnFirstRecord` a `IsOnLastRecord` a článku [použití zobrazení záznamu](../../data/using-a-record-view-mfc-data-access.md).

`CRecordView` sleduje pozici uživatele v sadě záznamů, takže zobrazení záznamu může aktualizovat uživatelské rozhraní. Když se uživatel přesune na konec sady záznamů, zobrazení záznamu zakáže objekty uživatelského rozhraní, jako jsou položky nabídky nebo tlačítka panelu nástrojů, pro pokračování ve stejném směru.

Další informace o deklaraci a použití zobrazení záznamů a tříd sady záznamů naleznete v tématu návrh a vytvoření zobrazení záznamů v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o způsobu práce zobrazení záznamů a způsobu jejich použití najdete v článku [použití zobrazení záznamu](../../data/using-a-record-view-mfc-data-access.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[Třídy CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDB. h

##  <a name="crecordview"></a>CRecordView:: CRecordView

Při vytváření objektu typu odvozeného z `CRecordView`volejte buď formu konstruktoru pro inicializaci objektu zobrazení a Identifikujte prostředek dialogového okna, na kterém je zobrazení založené.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je názvem prostředku šablony dialogového okna.

*nIDTemplate*<br/>
Obsahuje číslo ID prostředku šablony dialogového okna.

### <a name="remarks"></a>Poznámky

Prostředek můžete identifikovat podle názvu (předat řetězec jako argument konstruktoru) nebo podle jeho ID (předat unsigned integer jako argument). Doporučuje se použít ID prostředku.

> [!NOTE]
>  Vaše odvozená třída *musí* poskytovat svůj vlastní konstruktor. V konstruktoru odvozené třídy zavolejte konstruktor `CRecordView::CRecordView` s názvem prostředku nebo ID jako argument, jak je znázorněno v následujícím příkladu.

`CRecordView::OnInitialUpdate` volá `UpdateData`, která volá `DoDataExchange`. Toto počáteční volání `DoDataExchange` připojuje `CRecordView` ovládací prvky (nepřímo) k `CRecordset` datovým členům pole vytvořeným pomocí ClassWizard. Tyto datové členy nelze použít, dokud nebudete volat základní třídu `CFormView::OnInitialUpdate` členskou funkcí.

> [!NOTE]
>  Použijete-li ClassWizard, Průvodce definuje hodnotu **výčtu** `CRecordView::IDD`, určí ji v deklaraci třídy a použije ji v seznamu inicializace členů pro konstruktor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>CRecordView:: IsOnFirstRecord

Voláním této členské funkce určíte, zda je aktuální záznam prvním záznamem v objektu sady záznamů přidruženém k tomuto zobrazení záznamu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je aktuální záznam prvním záznamem v sadě záznamů; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro psaní vlastních implementací výchozích obslužných rutin aktualizace příkazu zapsaných v ClassWizard.

Pokud uživatel přejde na první záznam, rozhraní zakáže všechny objekty uživatelského rozhraní, které máte k přechodu na první nebo předchozí záznam.

##  <a name="isonlastrecord"></a>CRecordView:: IsOnLastRecord

Voláním této členské funkce určíte, zda je aktuální záznam posledním záznamem v objektu sady záznamů přidruženém k tomuto zobrazení záznamu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je aktuální záznam posledním záznamem v sadě záznamů; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro psaní vlastních implementací výchozích obslužných rutin aktualizace příkazů, které ClassWizard zápisy pro podporu uživatelského rozhraní pro přesun ze záznamu na záznam.

> [!CAUTION]
>  Výsledek této funkce je spolehlivý, s tím rozdílem, že zobrazení nemůže detekovat konec sady záznamů, dokud uživatel nepřesunul za něj. Uživatel musí přesunout za poslední záznam před tím, než bude moci zobrazení záznamu zjistit, že musí zakázat všechny objekty uživatelského rozhraní pro přechod na další nebo poslední záznam. Pokud uživatel přesune poslední záznam a přesune se zpět k poslednímu záznamu (nebo před ním), může zobrazení záznamu sledovat pozici uživatele v sadě záznamů a správně zakázat objekty uživatelského rozhraní. `IsOnLastRecord` je také nespolehlivé po volání funkce implementace `OnRecordLast`, která zpracovává příkaz ID_RECORD_LAST nebo `CRecordset::MoveLast`.

##  <a name="ongetrecordset"></a>CRecordView:: OnGetRecordset

Vrátí ukazatel na objekt odvozený `CRecordset`přidružený k zobrazení záznamu.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt odvozený od `CRecordset`, pokud byl objekt úspěšně vytvořen; v opačném případě ukazatel s hodnotou NULL.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci musíte přepsat, chcete-li vytvořit nebo získat objekt sady záznamů a vrátit na něj ukazatel. Pokud deklarujete třídu zobrazení záznamu pomocí ClassWizard, průvodce zapíše výchozí přepsání za vás. Výchozí implementace ClassWizard vrací ukazatel sady záznamů uložený v zobrazení záznamu, pokud existuje. Pokud ne, vytvoří objekt sady záznamů typu, který jste zadali v ClassWizard, a zavolá jeho členskou funkci `Open` pro otevření tabulky nebo spuštění dotazu a vrátí ukazatel na objekt.

Další informace a příklady najdete v článku [zobrazení záznamů: použití zobrazení záznamu](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>CRecordView::-Move

Zavolejte tuto členskou funkci pro přesun na jiný záznam v sadě záznamů a zobrazení jeho polí v ovládacích prvcích v zobrazení záznamu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jedna z následujících hodnot ID příkazu Standard:

- ID_RECORD_FIRST přesun do prvního záznamu v sadě záznamů.

- ID_RECORD_LAST přesun na poslední záznam v sadě záznamů.

- ID_RECORD_NEXT přejít k dalšímu záznamu v sadě záznamů.

- ID_RECORD_PREV přesun na předchozí záznam v sadě záznamů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo přesun úspěšné; v opačném případě 0, pokud byla žádost o přesun zamítnuta.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá příslušnou `Move` členskou funkci objektu `CRecordset` přidruženého k zobrazení záznamu.

Ve výchozím nastavení `OnMove` aktualizuje aktuální záznam ve zdroji dat, pokud ho uživatel změnil v zobrazení záznamu.

Průvodce aplikací vytvoří prostředek nabídky s položkami nabídky první záznam, poslední záznam, další záznam a předchozí záznam. Pokud vyberete možnost panelu nástrojů ukotvit, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídajícími těmto příkazům.

Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamu bude nadále zobrazovat poslední záznam. Pokud přejdete zpět za první záznam, zobrazení záznamu bude nadále zobrazovat první záznam.

> [!CAUTION]
>  Volání `OnMove` vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Chcete-li určit, zda sada záznamů obsahuje nějaké záznamy, zavolejte příslušnou funkci obslužné rutiny aktualizace uživatelského rozhraní – `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`nebo `OnUpdateRecordPrev` – před odpovídající operací přesunutí.

## <a name="see-also"></a>Viz také:

[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
