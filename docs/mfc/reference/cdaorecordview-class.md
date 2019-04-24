---
title: CDaoRecordView Class
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
ms.openlocfilehash: f63aa8ed17619a9eef36e36bcc9243a3b973889a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207191"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView Class

Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Vytvoří `CDaoRecordView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulovou hodnotu, pokud je první záznam v přidružené sadě záznamů aktuální záznam.|
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam poslední záznam v přidružené sadě záznamů.|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Vrací ukazatel na objekt třídy odvozené z `CDaoRecordset`. ClassWizard přepsání této funkce a v případě potřeby vytvoří sadu záznamů.|
|[CDaoRecordView::OnMove](#onmove)|Pokud došlo ke změně aktuální záznam, aktualizuje na zdroji dat a pak přesune zadaný záznam (Další, předchozí, první nebo poslední).|

## <a name="remarks"></a>Poznámky

Zobrazení je připojený přímo k zobrazení formuláře `CDaoRecordset` objektu. Toto zobrazení je vytvořen z prostředků šablony dialogového okna a zobrazí pole `CDaoRecordset` objektu v ovládacích prvcích šablony dialogového okna. `CDaoRecordView` Objektu používá k automatizaci přesouvání dat mezi ovládacími prvky ve formuláři a polí záznamů výměna dat dialogových oken (DDX) a výměna polí záznamu DAO (DFX). `CDaoRecordView` také poskytuje výchozí implementaci pro přechod na první další, předchozí nebo poslední záznam a rozhraní pro aktualizace záznamu aktuálně v zobrazení.

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Můžete si pořád přístup ke zdrojům dat ODBC s tříd DAO; třídy DAO obecně umožňují vynikající funkce, protože používají databázový stroj Microsoft Jet.

Nejběžnější způsob, jak vytvořit zobrazení záznamu je pomocí Průvodce aplikací. Průvodce aplikace vytvoří tříd zobrazení záznamu a jeho přidružené třídy sady záznamů jako součást kostru Startovní aplikace.

Pokud potřebujete pouze jeden formulář, Průvodce aplikací přístup je jednodušší. ClassWizard vám umožňuje určit použití zobrazení záznamů později v procesu vývoje. Pokud nevytvoříte tříd zobrazení záznamu pomocí Průvodce aplikací, můžete je vytvořit později s ClassWizard. Použití ClassWizard při vytváření zobrazení záznamů a záznamů samostatně a pak je připojení je nejflexibilnějším přístupem, protože nabízí větší kontrolu v názvu třídy sady záznamů a vlastnost. H /. Soubory CPP. Tento přístup také umožňuje mít více zobrazení záznamů u stejné třídy sady záznamů.

Usnadňují koncovým uživatelům, aby přesunout ze záznamu v zobrazení záznamů, Průvodce aplikací vytvoří nabídky (a volitelně nástrojů) prostředky pro přechod na první další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu s ClassWizard, musíte vytvořit tyto prostředky sami pomocí nabídky a rastrový obrázek editory.

Informace o výchozí implementaci pro přechod ze záznamu najdete v tématu `IsOnFirstRecord` a `IsOnLastRecord` a článek [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md), které se vztahují na obě `CRecordView` a `CDaoRecordView`.

`CDaoRecordView` uchovává informace o poloze uživatele v sadě záznamů tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní. Když uživatel přesune na jednom konci sady záznamů, zobrazení záznamů zakáže objektů uživatelského rozhraní, jako je například položky nabídky nebo tlačítka na panelu nástrojů – pro přesun dále ve stejném směru.

Další informace o deklarování a použití zobrazení záznamů a záznamů třídy naleznete v tématu "Návrh a vytváření zobrazení záznamů" v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o jak zobrazení záznamu práce a způsob jejich použití naleznete v článku [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md). V článcích uvedených výše platit pro oboje `CRecordView` a `CDaoRecordView`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

##  <a name="cdaorecordview"></a>  CDaoRecordView::CDaoRecordView

Při vytváření objektu typu odvozené z `CDaoRecordView`, volání obou tvarech konstruktor k inicializaci objektu zobrazení a identifikaci prostředku dialogového okna, na kterých je založena zobrazení.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Parametry

*lpszTemplateName*<br/>
Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.

*nIDTemplate*<br/>
Obsahuje identifikační číslo prostředku šablony dialogového okna.

### <a name="remarks"></a>Poznámky

Prostředek můžete identifikovat buď pomocí názvu (pass řetězec jako argument konstruktoru) nebo pomocí jeho ID (pass celé číslo bez znaménka jako argument). Prostředek ID doporučuje se použít.

> [!NOTE]
>  Odvozené třídy musí zadat vlastní konstruktor. V konstruktoru odvozené třídy volání konstruktoru `CDaoRecordView::CDaoRecordView` s názvem prostředku nebo ID jako argument.

`CDaoRecordView::OnInitialUpdate` volání `CWnd::UpdateData`, který volá `CWnd::DoDataExchange`. Tento počáteční volání `DoDataExchange` připojí `CDaoRecordView` ovládací prvky (nepřímo) k `CDaoRecordset` pole datových členů vytvořené nástrojem ClassWizard. Tyto datové členy nelze použít, dokud po volání základní třídy `CFormView::OnInitialUpdate` členskou funkci.

> [!NOTE]
>  Pokud používáte ClassWizard, Průvodce definuje **výčtu** hodnotu `CDaoRecordView::IDD` v deklaraci třídy a používá se v inicializaci členů seznamu konstruktoru.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>  CDaoRecordView::IsOnFirstRecord

Voláním této členské funkce určuje, jestli aktuální záznam je první záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je první záznam v sadě záznamů; aktuální záznam jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro psaní vlastních implementací výchozí obslužné rutiny aktualizace příkazů zapsaných nástrojem ClassWizard.

Pokud uživatel přesune na první záznam, zakáže framework objektů uživatelského rozhraní (pro příklad, položky nabídky nebo tlačítka na panelu nástrojů), které je nutné pro přechod na první nebo předchozí záznam.

##  <a name="isonlastrecord"></a>  CDaoRecordView::IsOnLastRecord

Voláním této členské funkce určuje, jestli aktuální záznam je poslední záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je aktuální záznam poslední záznam v sadě záznamů; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná pro psaní vlastních implementací výchozí obslužné rutiny aktualizace příkazů, které ClassWizard zapíše pro podporu uživatelského rozhraní pro přesun mezi záznamy.

> [!CAUTION]
>  Výsledkem této funkce je spolehlivé, s tím rozdílem, že zobrazení nemusí být schopna zjistit konci sady záznamů, dokud uživatel byl přesunut za ho. Uživatel může být nutné přesunout nad rámec poslední záznam před zobrazení záznamu můžete říct, že musíte zakázat všechny objekty uživatelského rozhraní pro přechod na další nebo poslední záznam. Pokud uživatel přejde za poslední záznam a pak přejde zpět na poslední záznam (nebo před ní), můžete zobrazení záznamů sledování pozici uživatele v sadě záznamů nebo zakázat objektů uživatelského rozhraní správně.

##  <a name="ongetrecordset"></a>  CDaoRecordView::OnGetRecordset

Vrací ukazatel `CDaoRecordset`-odvozené objekt přidružený k zobrazení záznamu.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CDaoRecordset`-odvozenému objektu, pokud objekt byl úspěšně vytvořený; jinak vrátí hodnotu ukazatele s hodnotou NULL.

### <a name="remarks"></a>Poznámky

Je nutné přepsat tuto členskou funkci sestavit nebo získání objektu sady záznamů a vrátí ukazatel na ni. Pokud deklarujete vaší třídy zobrazení záznamu s ClassWizard, zapíše průvodce přepsáním výchozího nastavení. ClassWizard výchozí implementace vrací ukazatel záznamů uložené v zobrazení záznamů, pokud existuje. Pokud ne, vytvoří objekt sady záznamů typu zadán s ClassWizard a volání jeho `Open` členské funkce Otevřít v tabulce nebo spustit dotaz a pak vrací ukazatel na objekt.

Další informace a příklady najdete v článku [zobrazení záznamů: Použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).

##  <a name="onmove"></a>  CDaoRecordView::OnMove

Voláním této členské funkce přesunout na jiný záznam v sadě záznamů a zobrazí se její pole do ovládacích prvků pro zobrazení záznamu.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Parametry

*nIDMoveCommand*<br/>
Jeden z následujících hodnot ID standardních příkazů:

- ID_RECORD_FIRST přesunout na první záznam v sadě záznamů.

- ID_RECORD_LAST přesunout na poslední záznam v sadě záznamů.

- ID_RECORD_NEXT přesunout na další záznam v sadě záznamů.

- ID_RECORD_PREV přesunout na předchozí záznam v sadě záznamů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo přesunutí úspěšné; jinak 0, pokud žádost o přesunutí byl odepřen.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá příslušnou přesunout členskou funkci `CDaoRecordset` objekt přidružený k zobrazení záznamu.

Ve výchozím nastavení `OnMove` aktualizuje aktuální záznam ve zdroji dat, pokud uživatel byl změněn v zobrazení záznamů.

Průvodce aplikace vytvoří prostředek nabídky s první záznam, poslední záznam, další záznam a předchozí záznam položky nabídky. Pokud vyberete možnost počáteční nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídající tyto příkazy.

Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamů stále zobrazuje poslední záznam. Pokud přejdete zpět za první záznam, zobrazení záznamů nepřestává zobrazovat první záznam.

> [!CAUTION]
>  Volání `OnMove` vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Volání funkce obslužné rutiny aktualizace příslušných uživatelských rozhraní – `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`, nebo `OnUpdateRecordPrev` – před odpovídajícími operace k určení, zda sada záznamů obsahuje záznamy, které přesunutí.

## <a name="see-also"></a>Viz také:

[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)
