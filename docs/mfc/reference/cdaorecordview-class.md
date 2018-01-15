---
title: "CDaoRecordView – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
dev_langs: C++
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2fffeed33d5b966faf511f60da740c39f2b91581
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaorecordview-class"></a>CDaoRecordView – třída
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
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Vrátí nenulové hodnoty, pokud je aktuální záznam na první záznam v přidružených záznamů.|  
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Vrátí nenulové hodnoty, pokud je aktuální záznam poslední záznam v přidružených záznamů.|  
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Vrátí ukazatel na objekt třídy odvozené od `CDaoRecordset`. ClassWizard přepsání této funkce pro vás a vytvoří sadu záznamů v případě potřeby.|  
|[CDaoRecordView::OnMove](#onmove)|Pokud došlo ke změně aktuální záznam aktualizací ve zdroji dat a pak přejde na zadaný záznam (Další, předchozí, první nebo poslední).|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazení je přímo připojený k zobrazení formuláře `CDaoRecordset` objektu. Zobrazení je vytvořený z prostředku šablony dialogovém okně a zobrazí pole `CDaoRecordset` objektu v ovládacích prvcích šablony dialogového okna. `CDaoRecordView` Objektu používá výměna dialogových dat (DDX) a rozhraní DAO výměna pole záznamu (DFX) k automatizaci přesun dat mezi ovládacími prvky na formuláři a pole sady záznamů. `CDaoRecordView`také poskytuje výchozí implementaci pro přesun na první další, předchozí nebo poslední záznam a rozhraní pro aktualizaci záznamu aktuálně v zobrazení.  
  
> [!NOTE]
>  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Můžete i nadále přístup ke zdrojům dat ODBC s třídy DAO; třídy DAO obecně nabízí vynikající funkcí, protože používají databázový stroj Microsoft Jet.  
  
 Nejběžnější způsob, jak vytvořit zobrazení záznamu je pomocí Průvodce aplikací. Třídy zobrazení záznamu a jeho přidružené třídy sady záznamů v rámci kostru Startovní aplikace vytvoří průvodce.  
  
 Pokud potřebujete jednoduše jednoho formuláře, Průvodce vytvořením aplikace přístup je jednodušší. ClassWizard umožňuje se rozhodnete použít zobrazení záznamů později v procesu vývoje. Pokud nevytvoříte tříd zobrazení záznamu pomocí Průvodce aplikací, můžete je vytvořit později s ClassWizard. Použití ClassWizard samostatně vytvořit zobrazení záznamů a sady záznamů a jejich připojení je nejvíce flexibilní přístup, protože nabízí další ovládací prvek v pojmenování třídy sady záznamů a jeho. H /. CPP souborů. Tento přístup také umožňuje mít víc zobrazení záznamů u stejné třídy sady záznamů.  
  
 Chcete-li snadno koncoví uživatelé přesouvat mezi záznamy v zobrazení záznamů, vytvoří Průvodce nabídky (a volitelně panelu nástrojů) prostředky pro přesun na první další, předchozí nebo poslední záznam. Pokud vytvoříte třídu zobrazení záznamu s ClassWizard, musíte vytvořit tyto prostředky sami pomocí nabídky a rastrový obrázek editory.  
  
 Informace o výchozí implementace pro přesun mezi záznamy najdete v tématu `IsOnFirstRecord` a `IsOnLastRecord` a v článku [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md), které se vztahují na obou `CRecordView` a `CDaoRecordView`.  
  
 `CDaoRecordView`uchovává informace o umístění uživatele v sadě záznamů tak, aby zobrazení záznamů můžete aktualizovat uživatelské rozhraní. Pokud se uživatel přesune na obou koncích sady záznamů, zobrazení záznamu zakáže objekty uživatelského rozhraní – například položek nabídky nebo tlačítka panelu nástrojů – pro přesun další ve stejném směru.  
  
 Další informace o deklarování a použití zobrazení záznamů a záznamů třídy najdete v tématu "Navrhování a vytváření záznam zobrazení" v článku [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o způsobu zobrazení záznamu pracovní a jejich použití naleznete v článku [použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md). Všechny články zmíněné platí pro `CRecordView` a `CDaoRecordView`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [Třídy CFormView](../../mfc/reference/cformview-class.md)  
  
 `CDaoRecordView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView  
 Když vytvoříte objekt typ odvozený z `CDaoRecordView`, volání buď formu konstruktor k inicializaci objektu zobrazení a identifikovat prostředku dialogového okna, na kterých je založena zobrazení.  
  
```  
explicit CDaoRecordView(LPCTSTR lpszTemplateName);  
explicit CDaoRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony dialogové okno.  
  
 `nIDTemplate`  
 Obsahuje počet ID prostředku šablony dialogové okno.  
  
### <a name="remarks"></a>Poznámky  
 Prostředek můžete identifikovat buď pomocí názvu (pass řetězec jako argument konstruktoru) nebo pomocí jejího ID (pass celé číslo bez znaménka jako argument). Prostředek ID se nedoporučuje používat.  
  
> [!NOTE]
>  Odvozené třídy musí zadat svůj vlastní konstruktor. V konstruktoru odvozené třídy, volat konstruktor `CDaoRecordView::CDaoRecordView` s názvem prostředků nebo ID jako argument.  
  
 **CDaoRecordView::OnInitialUpdate** volání `CWnd::UpdateData`, který volá `CWnd::DoDataExchange`. Počáteční volání `DoDataExchange` připojí `CDaoRecordView` (nepřímo) na ovládací prvky `CDaoRecordset` pole datových členů vytvořené ClassWizard. Tyto datové členy nelze použít až po zavolání metody základní třídy **CFormView::OnInitialUpdate** – členská funkce.  
  
> [!NOTE]
>  Pokud používáte ClassWizard, Průvodce definuje `enum` hodnotu `CDaoRecordView::IDD` v deklaraci třídy a používá ho inicializace členů seznamu konstruktoru.  
  
 [!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord  
 Volání této funkce člen můžete určit, zda je na aktuální záznam na první záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuální záznam na první záznam v sadě záznamů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro psaní vlastního implementace výchozí obslužné rutiny aktualizace příkazů podle ClassWizard zapisují.  
  
 Pokud se uživatel přesune na první záznam, zakáže framework žádné uživatelské rozhraní objekty (pro příklad položky nabídky nebo tlačítka panelu nástrojů) máte pro přesun na první nebo předchozího záznamu.  
  
##  <a name="isonlastrecord"></a>CDaoRecordView::IsOnLastRecord  
 Volání této funkce člen můžete určit, zda je na aktuální záznam poslední záznam v objektu sady záznamů spojeného s tímto zobrazením záznamu.  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuální záznam poslední záznam v sadě záznamů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečná pro psaní vlastního implementace výchozí obslužné rutiny aktualizace příkazů, které ClassWizard zapíše pro podporu uživatelského rozhraní pro přesun mezi záznamy.  
  
> [!CAUTION]
>  Výsledkem této funkce je spolehlivé, s tím rozdílem, že zobrazení nemusí být možné zjistit konec sady záznamů, dokud uživatel má přesunuty za ho. Uživatel může mít přesunout mimo poslední záznam před zobrazení záznamu zjistíte, že je nutné zakázat všechny objekty uživatelského rozhraní pro přesun na další nebo poslední záznam. Pokud uživatel přesune za poslední záznam a pak přejde zpět na poslední záznam (nebo před ním), můžete zobrazení záznamů sledovat pozici uživatele v sadě záznamů a správně zakázat objekty uživatelského rozhraní.  
  
##  <a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset  
 Vrátí ukazatel `CDaoRecordset`-odvozené objekt přidružený k zobrazení záznamu.  
  
```  
virtual CDaoRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CDaoRecordset`-odvozené objektu, pokud objekt byl úspěšně vytvořený; jinak hodnota **NULL** ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci Vytvořit nebo získat objekt sady záznamů a vrátíte se k němu ukazatel musí přepsat. Pokud je deklarovat třídě zobrazení záznamu s ClassWizard, zapíše průvodce přepsat výchozí. ClassWizard pro výchozí implementace vrací uložené v zobrazení záznamů, pokud existuje sada záznamů ukazatele. Pokud ne, vytvoří objekt sady záznamů typu zadán s ClassWizard a volání jeho **otevřete** člen funkce Otevřít v tabulce nebo spustit dotaz a pak vrátí ukazatel na objekt.  
  
 Další informace a příklady naleznete v článku [zobrazení záznamu: použití zobrazení záznamů](../../data/using-a-record-view-mfc-data-access.md).  
  
##  <a name="onmove"></a>CDaoRecordView::OnMove  
 Volání této funkce člen přesunout na jiný záznam v sadě záznamů a zobrazte její pole v ovládací prvky zobrazení záznamu.  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDMoveCommand`  
 Jedna z následujících hodnot ID standardních příkazů:  
  
- `ID_RECORD_FIRST`Přesunout na první záznam v sadě záznamů.  
  
- `ID_RECORD_LAST`Přechod na poslední záznam v sadě záznamů.  
  
- `ID_RECORD_NEXT`Přejděte na další záznam v sadě záznamů.  
  
- `ID_RECORD_PREV`Přesuňte do předchozího záznamu v sadě záznamů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl přesun úspěšný; jinak hodnota 0, pokud žádost o přesunutí byl odepřen.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace volá odpovídající přesunutí členské funkce `CDaoRecordset` objekt přidružený k zobrazení záznamu.  
  
 Ve výchozím nastavení `OnMove` aktualizuje na aktuální záznam ve zdroji dat, pokud uživatel se změnilo v zobrazení záznamů.  
  
 V Průvodce vytvořením aplikace vytvoří prostředek nabídky k položkám nabídky první záznam, poslední záznam, další záznam a předchozího záznamu. Pokud vyberete možnost Počáteční panel nástrojů, Průvodce aplikací také vytvoří panel nástrojů s tlačítka odpovídající tyto příkazy.  
  
 Pokud přesunete za poslední záznam v sadě záznamů, zobrazení záznamů stále zobrazuje poslední záznam. Pokud přesunete zpátky po první záznam, zobrazení záznamů stále zobrazuje na první záznam.  
  
> [!CAUTION]
>  Volání metody `OnMove` vyvolá výjimku, pokud má sada záznamů žádné záznamy. Volání funkce obslužné rutiny aktualizace odpovídající uživatelské rozhraní – **OnUpdateRecordFirst**, **OnUpdateRecordLast**, **OnUpdateRecordNext**, nebo  **OnUpdateRecordPrev** – před odpovídající operace přesunutí, aby určit, zda má sadu záznamů žádné záznamy.  
  
## <a name="see-also"></a>Viz také  
 [Třídy CFormView – třída](../../mfc/reference/cformview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset – třída](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef – třída](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef – třída](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase – třída](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace – třída](../../mfc/reference/cdaoworkspace-class.md)   
 [CFormView – třída](../../mfc/reference/cformview-class.md)
