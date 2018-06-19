---
title: CRecordView – třída | Microsoft Docs
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
ms.openlocfilehash: 3784bfd637c40f326a67807d0002fae66177ac37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373482"
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
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulové hodnoty, pokud je aktuální záznam na první záznam v přidružených záznamů.|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|Vrátí nenulové hodnoty, pokud je aktuální záznam poslední záznam v přidružených záznamů.|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|Vrátí ukazatel na objekt třídy odvozené od `CRecordset`. ClassWizard přepsání této funkce pro vás a vytvoří sadu záznamů v případě potřeby.|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|Pokud došlo ke změně aktuální záznam aktualizací ve zdroji dat a pak přejde na zadaný záznam (Další, předchozí, první nebo poslední).|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazení je přímo připojený k zobrazení formuláře `CRecordset` objektu. Zobrazení je vytvořený z prostředku šablony dialogovém okně a zobrazí pole `CRecordset` objektu v ovládacích prvcích šablony dialogového okna. `CRecordView` Objektu používá výměna dialogových dat (DDX) a pole záznamu (exchange – RFX) k automatizaci přesun dat mezi ovládacími prvky na formuláři a pole sady záznamů. `CRecordView` také poskytuje výchozí implementaci pro přesun na první další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu aktuálně pro zobrazení.  
  
> [!NOTE]
>  Pokud pracujete s třídy objektů DAO (Data Access), nikoli třídy připojení ODBC (Open Database), použijte třídu [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) místo. Další informace najdete v článku [přehled: programování databáze](../../data/data-access-programming-mfc-atl.md).  
  
 Nejběžnější způsob, jak vytvořit zobrazení záznamu je pomocí Průvodce aplikací. Průvodce vytvořením aplikace Tge vytvoří tříd zobrazení záznamu a jeho přidružené třídy sady záznamů v rámci kostru Startovní aplikace. Pokud nevytvoříte tříd zobrazení záznamu pomocí Průvodce aplikací, můžete je vytvořit později s ClassWizard. Pokud potřebujete jednoduše jednoho formuláře, Průvodce vytvořením aplikace přístup je jednodušší. ClassWizard umožňuje se rozhodnete použít zobrazení záznamů později v procesu vývoje. Použití ClassWizard samostatně vytvořit zobrazení záznamů a sady záznamů a jejich připojení je nejvíce flexibilní přístup, protože nabízí další ovládací prvek v pojmenování třídy sady záznamů a jeho. H /. CPP souborů. Tento přístup také umožňuje mít víc zobrazení záznamů u stejné třídy sady záznamů.  
  
 Chcete-li snadno koncoví uživatelé přesouvat mezi záznamy v zobrazení záznamů, vytvoří Průvodce nabídky (a volitelně panelu nástrojů) prostředky pro přesun na první další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu s ClassWizard, musíte vytvořit tyto prostředky sami pomocí nabídky a rastrový obrázek editory.  
  
 Informace o výchozí implementace pro přesun mezi záznamy najdete v tématu `IsOnFirstRecord` a `IsOnLastRecord` a v článku [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
 `CRecordView` uchovává informace o umístění uživatele v sadě záznamů tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní. Pokud se uživatel přesune na obou koncích sady záznamů, zobrazení záznamu zakáže objekty uživatelského rozhraní – například položek nabídky nebo tlačítka panelu nástrojů – pro přesun další ve stejném směru.  
  
 Další informace o deklarování a použití zobrazení záznamů a záznamů třídy najdete v tématu "Navrhování a vytváření záznam zobrazení" v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o způsobu zobrazení záznamu pracovní a jejich použití naleznete v článku [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [Třídy CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="crecordview"></a>  CRecordView::CRecordView  
 Když vytvoříte objekt typ odvozený z `CRecordView`, volání buď formu konstruktor k inicializaci objektu zobrazení a identifikovat prostředku dialogového okna, na kterých je založena zobrazení.  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony dialogové okno.  
  
 `nIDTemplate`  
 Obsahuje počet ID prostředku šablony dialogové okno.  
  
### <a name="remarks"></a>Poznámky  
 Prostředek můžete identifikovat buď pomocí názvu (pass řetězec jako argument konstruktoru) nebo pomocí jejího ID (pass celé číslo bez znaménka jako argument). Prostředek ID se nedoporučuje používat.  
  
> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru odvozené třídy, volat konstruktor `CRecordView::CRecordView` s názvem prostředků nebo ID jako argument, jak je znázorněno v následujícím příkladu.  
  
 **CRecordView::OnInitialUpdate** volání `UpdateData`, který volá `DoDataExchange`. Počáteční volání `DoDataExchange` připojí `CRecordView` (nepřímo) na ovládací prvky `CRecordset` pole datových členů vytvořené ClassWizard. Tyto datové členy nelze použít až po zavolání metody základní třídy **CFormView::OnInitialUpdate** – členská funkce.  
  
> [!NOTE]
>  Pokud používáte ClassWizard, Průvodce definuje `enum` hodnotu `CRecordView::IDD`, určuje v deklaraci třídy a používá ho v seznamu členů inicializace pro konstruktor.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord  
 Volání této funkce člen můžete určit, zda je na aktuální záznam na první záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuální záznam na první záznam v sadě záznamů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro psaní vlastního implementace výchozí obslužné rutiny aktualizace příkazů podle ClassWizard zapisují.  
  
 Pokud se uživatel přesune na první záznam, rozhraní zakáže všechny objekty uživatelského rozhraní, které máte pro přesun na první nebo předchozího záznamu.  
  
##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord  
 Volání této funkce člen můžete určit, zda je na aktuální záznam poslední záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuální záznam poslední záznam v sadě záznamů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro psaní vlastního implementace výchozí obslužné rutiny aktualizace příkazů, které ClassWizard zapíše pro podporu uživatelského rozhraní pro přesun mezi záznamy.  
  
> [!CAUTION]
>  Výsledkem této funkce je spolehlivé, s tím rozdílem, že zobrazení nedokáže detekovat konec sady záznamů, dokud uživatel má přesunuty za ho. Uživatel musí přesunout mimo poslední záznam před zobrazení záznamu zjistíte, že je nutné zakázat všechny objekty uživatelského rozhraní pro přesun na další nebo poslední záznam. Pokud uživatel přesune za poslední záznam a pak přejde zpět na poslední záznam (nebo před ním), můžete zobrazení záznamů sledovat pozici uživatele v sadě záznamů a správně zakázat objekty uživatelského rozhraní. `IsOnLastRecord` je také po volání funkce implementace nespolehlivé **OnRecordLast**, která zpracovává `ID_RECORD_LAST` příkazu, nebo `CRecordset::MoveLast`.  
  
##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset  
 Vrátí ukazatel `CRecordset`-odvozené objekt přidružený k zobrazení záznamu.  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CRecordset`-odvozené objektu, pokud objekt byl úspěšně vytvořený; jinak hodnota **NULL** ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci Vytvořit nebo získat objekt sady záznamů a vrátíte se k němu ukazatel musí přepsat. Pokud je deklarovat třídě zobrazení záznamu s ClassWizard, zapíše průvodce přepsat výchozí. ClassWizard pro výchozí implementace vrací uložené v zobrazení záznamů, pokud existuje sada záznamů ukazatele. Pokud ne, vytvoří objekt sady záznamů typu zadán s ClassWizard a volání jeho **otevřete** člen funkce Otevřít v tabulce nebo spustit dotaz a pak vrátí ukazatel na objekt.  
  
 Další informace a příklady naleznete v článku [zobrazení záznamu: použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>  CRecordView::OnMove  
 Volání této funkce člen přesunout na jiný záznam v sadě záznamů a zobrazte její pole v ovládací prvky zobrazení záznamu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDMoveCommand`  
 Jedna z následujících hodnot ID standardních příkazů:  
  
- `ID_RECORD_FIRST` Přesunout na první záznam v sadě záznamů.  
  
- `ID_RECORD_LAST` Přechod na poslední záznam v sadě záznamů.  
  
- `ID_RECORD_NEXT` Přejděte na další záznam v sadě záznamů.  
  
- `ID_RECORD_PREV` Přesuňte do předchozího záznamu v sadě záznamů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl přesun úspěšný; jinak hodnota 0, pokud žádost o přesunutí byl odepřen.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá odpovídající **přesunout** členské funkce `CRecordset` objekt přidružený k zobrazení záznamu.  
  
 Ve výchozím nastavení `OnMove` aktualizuje na aktuální záznam ve zdroji dat, pokud uživatel se změnilo v zobrazení záznamů.  
  
 V Průvodce vytvořením aplikace vytvoří prostředek nabídky k položkám nabídky první záznam, poslední záznam, další záznam a předchozího záznamu. Pokud vyberete možnost lze ukotvit nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítka odpovídající tyto příkazy.  
  
 Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamů stále zobrazuje poslední záznam. Pokud přesunete zpátky po první záznam, zobrazení záznamů stále zobrazuje na první záznam.  
  
> [!CAUTION]
>  Volání metody `OnMove` vyvolá výjimku, pokud má sada záznamů žádné záznamy. Volání funkce obslužné rutiny aktualizace odpovídající uživatelské rozhraní – **OnUpdateRecordFirst**, **OnUpdateRecordLast**, **OnUpdateRecordNext**, nebo  **OnUpdateRecordPrev** – před odpovídající operace přesunutí, aby určit, zda má sadu záznamů žádné záznamy.  
  
## <a name="see-also"></a>Viz také  
 [Třídy CFormView – třída](../../mfc/reference/cformview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)   
 [CFormView – třída](../../mfc/reference/cformview-class.md)
