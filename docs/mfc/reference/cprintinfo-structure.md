---
title: CPrintInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: cf0a1e6b7e742e950663f1ed9cc9ff2ddabd9d6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364028"
---
# <a name="cprintinfo-structure"></a>CPrintInfo – struktura

Ukládá informace o úloze tisku nebo náhledu.

## <a name="syntax"></a>Syntaxe

```
struct CPrintInfo
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintInfo::GetFromPage](#getfrompage)|Vrátí číslo první stránky, která se tiskne.|
|[CPrintInfo::GetMaxPage](#getmaxpage)|Vrátí číslo poslední stránky dokumentu.|
|[CPrintInfo::GetMinPage](#getminpage)|Vrátí číslo první stránky dokumentu.|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Vrátí číslo stránek předcházejících první stránce položky DocObject vytištěné v kombinované tiskové úloze DocObject.|
|[CPrintInfo::GetToPage](#gettopage)|Vrátí číslo poslední stránky, která se tiskne.|
|[CPrintInfo::SetMaxPage](#setmaxpage)|Nastaví číslo poslední stránky dokumentu.|
|[CPrintInfo::SetMinPage](#setminpage)|Nastaví číslo první stránky dokumentu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Obsahuje příznak označující, zda by měl rámec pokračovat v tiskové smyčce.|
|[CPrintInfo::m_bDirect](#m_bdirect)|Obsahuje příznak označující, zda je dokument tištěn přímo (bez zobrazení tiskového dialogového okna).|
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Obsahuje příznak označující, zda je dokument, který se tiskne, DocObject.|
|[CPrintInfo::m_bPreview](#m_bpreview)|Obsahuje příznak označující, zda je dokument zobrazen v náhledu.|
|[CPrintInfo::m_dwFlags](#m_dwflags)|Určuje tiskové operace DocObject.|
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Obsahuje ukazatel na strukturu vytvořenou uživatelem.|
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Určuje číslo aktuálně vytištěné stránky.|
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Určuje číslo úlohy přiřazené operačním systémem pro aktuální tiskovou úlohu.|
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Identifikuje počet stránek zobrazených v okně náhledu; buď 1 nebo 2.|
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Určuje posun první stránky konkrétní hoobjektu DocObject v kombinované tiskové úloze DocObject.|
|[CPrintInfo::m_pPD](#m_ppd)|Obsahuje ukazatel na `CPrintDialog` objekt použitý pro tiskové dialogové okno.|
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Určuje obdélník definující aktuální použitelnou oblast stránky.|
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Obsahuje formátovací řetězec pro zobrazení čísla stránky.|

## <a name="remarks"></a>Poznámky

`CPrintInfo`je struktura a nemá základní třídu.

Rozhraní framework vytvoří `CPrintInfo` objekt pokaždé, když je vybrán příkaz Print nebo Print Preview, a zničí ho po dokončení příkazu.

`CPrintInfo`obsahuje informace o tiskové úloze jako celku, například o rozsahu stránek, které mají být vytištěny, a o aktuálním stavu tiskové úlohy, například o právě vytištěné stránce. Některé informace jsou uloženy v přidruženém objektu [CPrintDialog;](../../mfc/reference/cprintdialog-class.md) tento objekt obsahuje hodnoty zadané uživatelem v tiskovém dialogovém okně.

Objekt `CPrintInfo` je předán mezi rámci a vaše zobrazení třídy během procesu tisku a slouží k výměně informací mezi těmito dvěma. Například framework informuje třídu zobrazení, kterou stránku dokumentu chcete vytisknout, přiřazením hodnoty `m_nCurPage` členu `CPrintInfo`; třída zobrazení načte hodnotu a provede skutečný tisk zadané stránky.

Dalším příkladem je případ, kdy délka dokumentu není známa, dokud není vytištěn. V takovém případě testy třídy zobrazení pro konec dokumentu při každém tisku stránky. Po dosažení konce, view třída `m_bContinuePrinting` nastaví `CPrintInfo` člen NA FALSE; To informuje rámec pro zastavení tiskové smyčky.

`CPrintInfo`je používán členské funkce `CView` uvedené v části "Viz také." Další informace o architektuře tisku poskytované knihovnou tříd microsoft foundation naleznete v [tématu Frame Windows](../../mfc/frame-windows.md) and [Document/View Architecture](../../mfc/document-view-architecture.md) a articles [Printing](../../mfc/printing.md) and [Printing: Multipage Documents](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CPrintInfo`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetFromPage

Volánítéto funkce načíst číslo první stránky, která má být vytištěna.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo první stránky, která má být vytištěna.

### <a name="remarks"></a>Poznámky

Toto je hodnota určená uživatelem v tiskovém dialogovém `CPrintDialog` okně a `m_pPD` je uložena v objektu, na který člen odkazuje. Pokud uživatel nezadal hodnotu, výchozí je první stránka dokumentu.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage

Voláním této funkce načtěte číslo poslední stránky dokumentu.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo poslední stránky dokumentu.

### <a name="remarks"></a>Poznámky

Tato hodnota je `CPrintDialog` uložena v `m_pPD` objektu, na který člen odkazuje.

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage

Voláním této funkce načtěte číslo první stránky dokumentu.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo první stránky dokumentu.

### <a name="remarks"></a>Poznámky

Tato hodnota je `CPrintDialog` uložena v `m_pPD` objektu, na který člen odkazuje.

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage

Volání této funkce načíst posun při tisku více DocObject položky z klienta DocObject.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet stránek předcházejících první stránce položky DocObject vytištěné v kombinované tiskové úloze DocObject.

### <a name="remarks"></a>Poznámky

Na tuto hodnotu `m_nOffsetPage` odkazuje člen. První stránka dokumentu bude očíslovat hodnotu `m_nOffsetPage` + 1 při tisku jako DocObject s jinými aktivními dokumenty. Člen `m_nOffsetPage` je platný pouze `m_bDocObject` v případě, že hodnota je TRUE.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage

Voláním této funkce načtěte číslo poslední stránky, která má být vytištěna.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Číslo poslední stránky, která má být vytištěna.

### <a name="remarks"></a>Poznámky

Toto je hodnota určená uživatelem v tiskovém dialogovém `CPrintDialog` okně a `m_pPD` je uložena v objektu, na který člen odkazuje. Pokud uživatel nezadal hodnotu, výchozí je poslední stránka dokumentu.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting

Obsahuje příznak označující, zda by měl rámec pokračovat v tiskové smyčce.

### <a name="remarks"></a>Poznámky

Pokud provádíte stránkování v době tisku, můžete nastavit tento člen `CView::OnPrepareDC` na HODNOTU NEPRAVDA v přepsání po dosažení konce dokumentu. Tuto proměnnou není nutné upravovat, pokud jste zadali délku dokumentu na `SetMaxPage` začátku tiskové úlohy pomocí členské funkce. Člen `m_bContinuePrinting` je veřejná proměnná typu BOOL.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrintInfo::m_bDirect

Rámec nastaví tento člen na HODNOTU TRUE, pokud bude tiskové dialogové okno vynecháno pro přímý tisk; FALSE jinak.

### <a name="remarks"></a>Poznámky

Tisk dialog je obvykle vynechánpři tisku ze skořepiny nebo při tisku pomocí příkazu ID ID_FILE_PRINT_DIRECT.

Obvykle tento člen nezměníte, ale pokud jej změníte, změňte jej před voláním [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) v přepsání [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrintInfo::m_bDocObject

Obsahuje příznak označující, zda je dokument, který se tiskne, DocObject.

### <a name="remarks"></a>Poznámky

Datové `m_dwFlags` členy `m_nOffsetPage` a jsou neplatné, pokud tento příznak není TRUE.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrintInfo::m_bPreview

Obsahuje příznak označující, zda je dokument zobrazen v náhledu.

### <a name="remarks"></a>Poznámky

To je nastaveno rámci v závislosti na příkazu, který uživatel provedl. Tiskové dialogové okno se nezobrazí pro úlohu náhledu tisku. Člen `m_bPreview` je veřejná proměnná typu BOOL.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrintInfo::m_dwFlags

Obsahuje kombinaci příznaků určujících operace tisku DocObject.

### <a name="remarks"></a>Poznámky

Platí pouze v `m_bDocObject` případě, že datový člen je TRUE.

Příznaky mohou být jedna nebo více z následujících hodnot:

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData

Obsahuje ukazatel na strukturu vytvořenou uživatelem.

### <a name="remarks"></a>Poznámky

Můžete použít k uložení dat specifických pro tisk, které nechcete uložit do třídy zobrazení. Člen `m_lpUserData` je veřejná proměnná typu LPVOID.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrintInfo::m_nCurPage

Obsahuje číslo aktuální stránky.

### <a name="remarks"></a>Poznámky

Rozhraní framework `CView::OnPrepareDC` `CView::OnPrint` volání a jednou pro každou stránku dokumentu, určující jinou hodnotu pro tento člen pokaždé; jeho hodnoty jsou v `GetFromPage` rozsahu od `GetToPage`hodnoty vrácené hodnotou vrácenou společností . Tento člen použijte v `CView::OnPrepareDC` přepsání a `CView::OnPrint` vytisknout zadanou stránku dokumentu.

Při prvním vyvolání režimu náhledu rozhraní přečte hodnotu tohoto člena, aby určil, která stránka dokumentu by měla být zpočátku zobrazena v náhledu. Můžete nastavit hodnotu tohoto člena v `CView::OnPreparePrinting` přepsání zachovat aktuální pozici uživatele v dokumentu při vstupu do režimu náhledu. Člen `m_nCurPage` je veřejná proměnná typu UINT.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber

Označuje číslo úlohy přiřazené operačním systémem pro aktuální tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Tato hodnota může být SP_ERROR, pokud úloha ještě nebyla `CPrintInfo` vytištěna (to znamená, pokud je objekt nově vytvořen a ještě nebyl použit k tisku) nebo pokud došlo k chybě při spuštění úlohy.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages

Obsahuje počet stránek zobrazených v režimu náhledu; může to být buď 1 nebo 2.

### <a name="remarks"></a>Poznámky

Člen `m_nNumPreviewPages` je veřejná proměnná typu UINT.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage

Obsahuje počet stránek předcházejících první stránce určité objektu DocObject v kombinované tiskové úloze DocObject.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrintInfo::m_pPD

Obsahuje ukazatel na `CPrintDialog` objekt použitý k zobrazení tiskového dialogového okna pro tiskovou úlohu.

### <a name="remarks"></a>Poznámky

Člen `m_pPD` je veřejná proměnná deklarovaná jako ukazatel na `CPrintDialog`.

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrintInfo::m_rectDraw

Určuje použitelnou kreslicí plochu stránky v logických souřadnicích.

### <a name="remarks"></a>Poznámky

Můžete odkazovat na to v přepsání `CView::OnPrint`. Tento člen můžete použít ke sledování oblasti, která zůstává použitelná po tisku záhlaví, zápatí a tak dále. Člen `m_rectDraw` je veřejná proměnná typu `CRect`.

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc

Obsahuje formátovací řetězec používaný k zobrazení čísel stránek během náhledu; Tento řetězec se skládá ze dvou podřetězců, jednoho pro jednostránkové zobrazení a jednoho pro dvoustránkové zobrazení, z nichž každý je ukončen znakem \n.

### <a name="remarks"></a>Poznámky

Jako výchozí hodnotu používá rozhraní Framework "Page %u\nPages %u-%u\n". Pokud chcete pro čísla stránek formátovat jinak, zadejte formátovací řetězec v přepsání aplikace `CView::OnPreparePrinting`. Člen `m_strPageDesc` je veřejná proměnná typu `CString`.

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage

Voláním této funkce určete číslo poslední stránky dokumentu.

```
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Parametry

*nMaxPage*<br/>
Číslo poslední stránky dokumentu.

### <a name="remarks"></a>Poznámky

Tato hodnota je `CPrintDialog` uložena v `m_pPD` objektu, na který člen odkazuje. Pokud je délka dokumentu známa před jeho vytištěním, volání `CView::OnPreparePrinting`této funkce z přepsání aplikace . Pokud délka dokumentu závisí na nastavení určeném uživatelem v tiskovém dialogovém okně, `CView::OnBeginPrinting`volání této funkce z přepsání aplikace . Pokud délka dokumentu není známa, dokud není vytištěn, použijte `m_bContinuePrinting` člen k ovládání tiskové smyčky.

### <a name="example"></a>Příklad

  Viz příklad [cview::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage

Voláním této funkce určete číslo první stránky dokumentu.

```
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Parametry

*nMinPage*<br/>
Číslo první stránky dokumentu.

### <a name="remarks"></a>Poznámky

Čísla stránek obvykle začínají na 1. Tato hodnota je `CPrintDialog` uložena v `m_pPD` objektu, na který člen odkazuje.

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[cview::OnendPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[cview::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
