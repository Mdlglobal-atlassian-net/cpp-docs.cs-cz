---
title: CRecordView – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5908427a256595a032821d947ddad79ec588b6a
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853497"
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
|[CRecordView::CRecordView](#crecordview)|Vytvoří `CRecordView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulovou hodnotu, pokud je první záznam v přidružené sadě záznamů aktuální záznam.|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Vrátí nenulovou hodnotu, pokud je aktuální záznam poslední záznam v přidružené sadě záznamů.|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|Vrací ukazatel na objekt třídy odvozené z `CRecordset`. ClassWizard přepsání této funkce a v případě potřeby vytvoří sadu záznamů.|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|Pokud došlo ke změně aktuální záznam, aktualizuje na zdroji dat a pak přesune zadaný záznam (Další, předchozí, první nebo poslední).|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazení je připojený přímo k zobrazení formuláře `CRecordset` objektu. Toto zobrazení je vytvořen z prostředků šablony dialogového okna a zobrazí pole `CRecordset` objektu v ovládacích prvcích šablony dialogového okna. `CRecordView` Objektu používá k automatizaci přesouvání dat mezi ovládacími prvky ve formuláři a polí záznamů výměna dat dialogových oken (DDX) a výměna pole záznamu (RFX). `CRecordView` také poskytuje výchozí implementaci pro přechod na první další, předchozí nebo poslední záznam a rozhraní pro aktualizace záznamu aktuálně pro zobrazení.  
  
> [!NOTE]
>  Pokud pracujete s třídami objektů DAO (Data Access), a ne třídy připojení ODBC (Open Database), použijte třídu [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) místo. Další informace najdete v článku [přehled: databáze programování](../../data/data-access-programming-mfc-atl.md).  
  
 Nejběžnější způsob, jak vytvořit zobrazení záznamu je pomocí Průvodce aplikací. Třídy zobrazení záznamu a jeho přidružené třídy sady záznamů jako součást kostru Startovní aplikace vytvoří Tge Application Wizard. Pokud nevytvoříte tříd zobrazení záznamu pomocí Průvodce aplikací, můžete je vytvořit později s ClassWizard. Pokud potřebujete pouze jeden formulář, Průvodce aplikací přístup je jednodušší. ClassWizard vám umožňuje určit použití zobrazení záznamů později v procesu vývoje. Použití ClassWizard při vytváření zobrazení záznamů a záznamů samostatně a pak je připojení je nejflexibilnějším přístupem, protože nabízí větší kontrolu v názvu třídy sady záznamů a vlastnost. H /. Soubory CPP. Tento přístup také umožňuje mít více zobrazení záznamů u stejné třídy sady záznamů.  
  
 Usnadňují koncovým uživatelům, aby přesunout ze záznamu v zobrazení záznamů, Průvodce aplikací vytvoří nabídky (a volitelně nástrojů) prostředky pro přechod na první další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu s ClassWizard, musíte vytvořit tyto prostředky sami pomocí nabídky a rastrový obrázek editory.  
  
 Informace o výchozí implementaci pro přechod ze záznamu najdete v tématu `IsOnFirstRecord` a `IsOnLastRecord` a článek [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
 `CRecordView` uchovává informace o poloze uživatele v sadě záznamů tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní. Když uživatel přesune na jednom konci sady záznamů, zobrazení záznamů zakáže objektů uživatelského rozhraní, jako je například položky nabídky nebo tlačítka na panelu nástrojů – pro přesun dále ve stejném směru.  
  
 Další informace o deklarování a použití zobrazení záznamů a záznamů třídy naleznete v tématu "Návrh a vytváření zobrazení záznamů" v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o jak zobrazení záznamu práce a způsob jejich použití naleznete v článku [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [Cscrollview –](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="crecordview"></a>  CRecordView::CRecordView  
 Při vytváření objektu typu odvozené z `CRecordView`, volání obou tvarech konstruktor k inicializaci objektu zobrazení a identifikaci prostředku dialogového okna, na kterých je založena zobrazení.  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszTemplateName*  
 Obsahuje řetězec zakončený hodnotou null, který je název prostředku šablony dialogového okna.  
  
 *nIDTemplate*  
 Obsahuje identifikační číslo prostředku šablony dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Prostředek můžete identifikovat buď pomocí názvu (pass řetězec jako argument konstruktoru) nebo pomocí jeho ID (pass celé číslo bez znaménka jako argument). Prostředek ID doporučuje se použít.  
  
> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru odvozené třídy volání konstruktoru `CRecordView::CRecordView` s názvem prostředku nebo ID jako argument, jak je znázorněno v následujícím příkladu.  
  
 `CRecordView::OnInitialUpdate` volání `UpdateData`, který volá `DoDataExchange`. Tento počáteční volání `DoDataExchange` připojí `CRecordView` ovládací prvky (nepřímo) k `CRecordset` pole datových členů vytvořené nástrojem ClassWizard. Tyto datové členy nelze použít, dokud po volání základní třídy `CFormView::OnInitialUpdate` členskou funkci.  
  
> [!NOTE]
>  Pokud používáte ClassWizard, Průvodce definuje **výčtu** hodnota `CRecordView::IDD`, určuje v deklaraci třídy a používá ho v seznamu inicializace členů pro konstruktor.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord  
 Voláním této členské funkce určuje, jestli aktuální záznam je první záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je první záznam v sadě záznamů; aktuální záznam jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro psaní vlastních implementací výchozí obslužné rutiny aktualizace příkazů zapsaných nástrojem ClassWizard.  
  
 Pokud se uživatel přesune na první záznam, rozhraní zakáže všechny objekty uživatelského rozhraní, které máte pro přechod na první nebo předchozí záznam.  
  
##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord  
 Voláním této členské funkce určuje, jestli aktuální záznam je poslední záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je aktuální záznam poslední záznam v sadě záznamů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro psaní vlastních implementací výchozí obslužné rutiny aktualizace příkazů, které ClassWizard zapíše pro podporu uživatelského rozhraní pro přesun mezi záznamy.  
  
> [!CAUTION]
>  Výsledkem této funkce je spolehlivé, s tím rozdílem, že zobrazení nelze zjistit konci sady záznamů, dokud uživatel byl přesunut za ho. Uživatel musí přesunout mimo poslední záznam před zobrazení záznamu můžete říct, že musíte zakázat všechny objekty uživatelského rozhraní pro přechod na další nebo poslední záznam. Pokud uživatel přejde za poslední záznam a pak přejde zpět na poslední záznam (nebo před ní), můžete zobrazení záznamů sledování pozici uživatele v sadě záznamů nebo zakázat objektů uživatelského rozhraní správně. `IsOnLastRecord` je také po volání funkce implementace nespolehlivé `OnRecordLast`, která zpracovává příkaz ID_RECORD_LAST nebo `CRecordset::MoveLast`.  
  
##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset  
 Vrací ukazatel `CRecordset`-odvozené objekt přidružený k zobrazení záznamu.  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CRecordset`-odvozenému objektu, pokud objekt byl úspěšně vytvořený; jinak vrátí hodnotu ukazatele s hodnotou NULL.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné přepsat tuto členskou funkci sestavit nebo získání objektu sady záznamů a vrátí ukazatel na ni. Pokud deklarujete vaší třídy zobrazení záznamu s ClassWizard, zapíše průvodce přepsáním výchozího nastavení. ClassWizard výchozí implementace vrací ukazatel záznamů uložené v zobrazení záznamů, pokud existuje. Pokud ne, vytvoří objekt sady záznamů typu zadán s ClassWizard a volání jeho `Open` členské funkce Otevřít v tabulce nebo spustit dotaz a pak vrací ukazatel na objekt.  
  
 Další informace a příklady najdete v článku [zobrazení záznamu: použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>  CRecordView::OnMove  
 Voláním této členské funkce přesunout na jiný záznam v sadě záznamů a zobrazí se její pole do ovládacích prvků pro zobrazení záznamu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDMoveCommand*  
 Jeden z následujících hodnot ID standardních příkazů:  
  
- ID_RECORD_FIRST přesunout na první záznam v sadě záznamů.  
  
- ID_RECORD_LAST přesunout na poslední záznam v sadě záznamů.  
  
- ID_RECORD_NEXT přesunout na další záznam v sadě záznamů.  
  
- ID_RECORD_PREV přesunout na předchozí záznam v sadě záznamů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo přesunutí úspěšné; jinak 0, pokud žádost o přesunutí byl odepřen.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá odpovídající `Move` členskou funkci `CRecordset` objekt přidružený k zobrazení záznamu.  
  
 Ve výchozím nastavení `OnMove` aktualizuje aktuální záznam ve zdroji dat, pokud uživatel byl změněn v zobrazení záznamů.  
  
 Průvodce aplikace vytvoří prostředek nabídky s první záznam, poslední záznam, další záznam a předchozí záznam položky nabídky. Pokud vyberete možnost Ukotvitelné nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítky odpovídající tyto příkazy.  
  
 Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamů stále zobrazuje poslední záznam. Pokud přejdete zpět za první záznam, zobrazení záznamů nepřestává zobrazovat první záznam.  
  
> [!CAUTION]
>  Volání `OnMove` vyvolá výjimku, pokud sada záznamů neobsahuje žádné záznamy. Volání funkce obslužné rutiny aktualizace příslušných uživatelských rozhraní – `OnUpdateRecordFirst`, `OnUpdateRecordLast`, `OnUpdateRecordNext`, nebo `OnUpdateRecordPrev` – před odpovídajícími operace k určení, zda sada záznamů obsahuje záznamy, které přesunutí.  
  
## <a name="see-also"></a>Viz také  
 [CFormView – třída](../../mfc/reference/cformview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)   
 [CFormView – třída](../../mfc/reference/cformview-class.md)
