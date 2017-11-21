---
title: "Cprintinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CPrintInfo
dev_langs: C++
helpviewer_keywords: CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a97145953cdd5d11f2adc2109f11f3a45298a53c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cprintinfo-structure"></a>Cprintinfo – struktura
Obsahuje informace o náhledu nebo tiskové úlohy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CPrintInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](#getfrompage)|Vrátí číslo první stránky tisku.|  
|[CPrintInfo::GetMaxPage](#getmaxpage)|Vrátí číslo poslední stránky z dokumentu.|  
|[CPrintInfo::GetMinPage](#getminpage)|Vrátí číslo první stránky z dokumentu.|  
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Vrátí počet stránek předcházející na první stránku položku DocObject vytištěna v kombinované DocObject tiskové úlohy.|  
|[CPrintInfo::GetToPage](#gettopage)|Vrátí číslo poslední stránky tisku.|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|Nastaví číslo poslední stránky z dokumentu.|  
|[CPrintInfo::SetMinPage](#setminpage)|Nastaví číslo první stránky z dokumentu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Obsahuje příznak, který udává, zda rozhraní by měly pokračovat tiskové smyčky.|  
|[CPrintInfo::m_bDirect](#m_bdirect)|Obsahuje příznak, který udává, zda je přímo (bez zobrazení dialogového okna Tisk) tisku dokumentu.|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Obsahuje příznak, který udává, zda je dokument tisku DocObject.|  
|[CPrintInfo::m_bPreview](#m_bpreview)|Obsahuje příznak, který udává, zda je náhledu dokumentu.|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|Určuje DocObject tisk operace.|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Obsahuje ukazatel na strukturu vytvořené uživatelem.|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Označuje počet právě tištěné stránky.|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Určuje číslo projektu přiřadila operační systém pro aktuální tiskové úlohy|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Určuje, kolik stránek se zobrazí v okně náhledu; 1 nebo 2.|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Určuje posun první stránka konkrétní DocObject v kombinované DocObject tiskové úlohy.|  
|[CPrintInfo::m_pPD](#m_ppd)|Obsahuje odkazy `CPrintDialog` objekt použitý pro dialogové okno tisku.|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Určuje obdélníku definování oblasti aktuální použitelné stránky.|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Obsahuje řetězec formátu pro číslo stránky zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 `CPrintInfo`je struktura a nemá základní třídu.  
  
 Rozhraní framework vytvoří objekt `CPrintInfo` pokaždé, když Print nebo příkaz Náhled je zvolen a zničí ji po dokončení příkazu.  
  
 `CPrintInfo`obsahuje informace o se tisková úloha jako celek, například rozsah stránek pro tisk a aktuální stav tiskové úlohy, jako je například právě tištěné stránky. Některé informace jsou uloženy v přidružené [CPrintDialog](../../mfc/reference/cprintdialog-class.md) objektu; tento objekt obsahuje hodnoty zadá uživatel v dialogovém okně tisku.  
  
 A `CPrintInfo` objekt je předán mezi rozhraní a zobrazení třídy během procesu tisku a slouží k výměně informací mezi nimi. Například rozhraní informuje třídy zobrazení kterou stránku dokumentu tisknout přiřazením hodnoty do `m_nCurPage` členem `CPrintInfo`; zobrazení třídy načte hodnotu a provede skutečný tisk na určenou stránku.  
  
 Dalším příkladem je případ nezná délka dokumentu dokud vytištění. V takovém případě testů třídy zobrazení pro konec dokumentu pokaždé, když tisknout. Když je dosaženo konce, nastaví třídu zobrazení `m_bContinuePrinting` členem `CPrintInfo` k **FALSE**; tento příkaz informuje rozhraní zastavit tiskové smyčky.  
  
 `CPrintInfo`Členské funkce používá `CView` uvedené v části "Viz také." Další informace o architektura pro tisk poskytované knihovny Microsoft Foundation Class najdete v tématu [okna s rámečkem](../../mfc/frame-windows.md) a [Document/View – architektura](../../mfc/document-view-architecture.md) a články [ Tisk](../../mfc/printing.md) a [tisk: vícestránkové dokumenty](../../mfc/multipage-documents.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CPrintInfo`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="getfrompage"></a>CPrintInfo::GetFromPage  
 Volání této funkce načíst číslo první stránky k tisku.  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo první stránky k tisku.  
  
### <a name="remarks"></a>Poznámky  
 Toto je hodnota zadaná uživatelem v dialogovém okně tisku a uloží se do `CPrintDialog` objekt odkazuje `m_pPD` člen. Pokud uživatel nemá zadanou hodnotu, výchozí hodnota je na první stránku dokumentu.  
  
##  <a name="getmaxpage"></a>CPrintInfo::GetMaxPage  
 Volání této funkce načíst číslo poslední stránky z dokumentu.  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo poslední stránky z dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota je uložena v `CPrintDialog` objekt odkazuje `m_pPD` člen.  
  
##  <a name="getminpage"></a>CPrintInfo::GetMinPage  
 Volání této funkce načíst číslo první stránky z dokumentu.  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet na první stránku dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota je uložena v `CPrintDialog` objekt odkazuje `m_pPD` člen.  
  
##  <a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage  
 Volání této funkce se při tisku více položek DocObject z klienta DocObject načíst posun.  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet stránek předcházející na první stránku položku DocObject vytištěna v kombinované DocObject tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se odkazuje **m_nOffsetPage** člen. Na první stránku dokumentu bude mít číslované **m_nOffsetPage** hodnota + 1 při tisku jako DocObject s další aktivní dokumenty. **M_nOffsetPage** člen je platná pouze v případě **m_bDocObject** hodnota je **TRUE**.  
  
##  <a name="gettopage"></a>CPrintInfo::GetToPage  
 Volání této funkce načíst číslo poslední stránky k tisku.  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo poslední stránky k tisku.  
  
### <a name="remarks"></a>Poznámky  
 Toto je hodnota zadaná uživatelem v dialogovém okně tisku a uloží se do `CPrintDialog` objekt odkazuje `m_pPD` člen. Pokud uživatel nemá zadanou hodnotu, výchozí hodnota je na poslední stránku dokumentu.  
  
##  <a name="m_bcontinueprinting"></a>CPrintInfo::m_bContinuePrinting  
 Obsahuje příznak, který udává, zda rozhraní by měly pokračovat tiskové smyčky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud byste stránkování čas tisku, můžete nastavit tento člen na **FALSE** v přepsání z `CView::OnPrepareDC` po bylo dosaženo konce dokumentu. Není nutné upravit tato proměnná, pokud jste zadali délka dokumentu na začátku pomocí tiskové úlohy `SetMaxPage` – členská funkce. `m_bContinuePrinting` Člen je veřejné proměnné typu **BOOL**.  
  
##  <a name="m_bdirect"></a>CPrintInfo::m_bDirect  
 Rozhraní framework nastaví tento člen **TRUE** Pokud dialogové okno tisku bude možné obejít pro přímý tisk z; **FALSE** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno tisku normálně přeskočí při tisku z prostředí nebo pokud se provádí tisk pomocí ID příkazu, který **ID_FILE_PRINT_DIRECT**.  
  
 Jste normálně neměnit tento člen, ale pokud změníte, změňte jej před volání [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) v přepsání z [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="m_bdocobject"></a>CPrintInfo::m_bDocObject  
 Obsahuje příznak, který udává, zda je dokument tisku DocObject.  
  
### <a name="remarks"></a>Poznámky  
 Datové členy `m_dwFlags` a **m_nOffsetPage** jsou neplatné, pokud je tento příznak **TRUE**.  
  
##  <a name="m_bpreview"></a>CPrintInfo::m_bPreview  
 Obsahuje příznak, který udává, zda je náhledu dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Toto nastavení podle rozhraní v závislosti na tom, který příkaz uživatel provést. Pro úlohu náhledu není zobrazí dialogové okno tisku. **M_bPreview** člen je veřejné proměnné typu **BOOL**.  
  
##  <a name="m_dwflags"></a>CPrintInfo::m_dwFlags  
 Obsahuje kombinaci příznaky určující DocObject tisk operace.  
  
### <a name="remarks"></a>Poznámky  
 Platné jenom v případě – datový člen **m_bDocObject** je **TRUE**.  
  
 V příznacích může být jeden nebo více z následujících hodnot:  
  
- **PRINTFLAG_MAYBOTHERUSER**  
  
- **PRINTFLAG_PROMPTUSER**  
  
- **PRINTFLAG_USERMAYCHANGEPRINTER**  
  
- **PRINTFLAG_RECOMPOSETODEVICE**  
  
- **PRINTFLAG_DONTACTUALLYPRINT**  
  
- **PRINTFLAG_FORCEPROPERTIES**  
  
- **PRINTFLAG_PRINTTOFILE**  
  
##  <a name="m_lpuserdata"></a>CPrintInfo::m_lpUserData  
 Obsahuje ukazatel na strukturu vytvořené uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít k ukládání dat specifické pro tisk, které nechcete ukládat ve třídě zobrazení. **M_lpUserData** člen je veřejné proměnné typu **LPVOID**.  
  
##  <a name="m_ncurpage"></a>CPrintInfo::m_nCurPage  
 Obsahuje počet aktuální stránku.  
  
### <a name="remarks"></a>Poznámky  
 Volání framework `CView::OnPrepareDC` a `CView::OnPrint` jednou pro každou stránku dokumentu, zadáním jiné hodnoty pro tento člen pokaždé, když; jeho hodnoty v rozsahu od hodnoty vrácené `GetFromPage` na který vrácený `GetToPage`. Použít tento člen vaší přepsání z `CView::OnPrepareDC` a `CView::OnPrint` tisknout zadané stránky z dokumentu.  
  
 Při prvním vyvolání režim náhledu, rozhraní přečte hodnotu této vlastnosti k určení, které stránky dokumentu by měl zobrazit jejich náhled původně. Můžete nastavit hodnotu člen v přepsání z `CView::OnPreparePrinting` zachovat aktuální pozici uživatele v dokumentu, při zadávání režim náhledu. `m_nCurPage` Člen je veřejné proměnné typu **Celé_číslo**.  
  
##  <a name="m_njobnumber"></a>CPrintInfo::m_nJobNumber  
 Označuje číslo projektu přiřadila operační systém pro aktuální tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota může být **SP_ERROR** Pokud úloha nebyla dosud vytištěna (tj. Pokud `CPrintInfo` je nově vytvořený objekt a nebyl dosud použit k vytištění), nebo pokud došlo k chybě při spouštění úlohy.  
  
##  <a name="m_nnumpreviewpages"></a>CPrintInfo::m_nNumPreviewPages  
 Obsahuje počet stránek zobrazených v režimu náhledu; může být buď 1 nebo 2.  
  
### <a name="remarks"></a>Poznámky  
 **M_nNumPreviewPages** člen je veřejné proměnné typu **Celé_číslo**.  
  
##  <a name="m_noffsetpage"></a>CPrintInfo::m_nOffsetPage  
 Obsahuje počet stránek před první stránka konkrétní DocObject v kombinované DocObject tiskové úlohy.  
  
##  <a name="m_ppd"></a>CPrintInfo::m_pPD  
 Obsahuje odkazy `CPrintDialog` objekt použitý k zobrazení dialogového okna tisku pro tisková úloha.  
  
### <a name="remarks"></a>Poznámky  
 `m_pPD` Člen je deklarován jako ukazatel na veřejné proměnné `CPrintDialog`.  
  
##  <a name="m_rectdraw"></a>CPrintInfo::m_rectDraw  
 Určuje oblasti použitelné vykreslení stránky v logické souřadnice.  
  
### <a name="remarks"></a>Poznámky  
 Můžete chtít podívejte se na to v přepsání z `CView::OnPrint`. Tento člen můžete použít ke sledování jaké oblasti zůstává použitelný po tisku záhlaví, zápatí a tak dále. **M_rectDraw** člen je veřejné proměnné typu `CRect`.  
  
##  <a name="m_strpagedesc"></a>CPrintInfo::m_strPageDesc  
 Obsahuje řetězec formátu použitý k zobrazení číslo stránky během náhledu tisku; Tento řetězec se skládá z dvě dílčích řetězců, jeden pro zobrazení jednostránkové a jeden pro zobrazení stránky double, každý ukončena znakem '\n'.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá jako výchozí hodnota "Stránka %u\nPages % u-%u\n". Pokud chcete do jiného formátu pro číslo stránky, zadejte řetězec formátu v přepsání z `CView::OnPreparePrinting`. **M_strPageDesc** člen je veřejné proměnné typu `CString`.  
  
##  <a name="setmaxpage"></a>CPrintInfo::SetMaxPage  
 Volání této funkce můžete zadat číslo poslední stránky z dokumentu.  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>Parametry  
 *nMaxPage*  
 Číslo poslední stránky z dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota je uložena v `CPrintDialog` objekt odkazuje `m_pPD` člen. Pokud je délka dokumentu znám před tiskem, volání této funkce z vaší přepsání `CView::OnPreparePrinting`. Pokud délka dokumentu závisí na nastavení, které uživatel v dialogovém okně tisku, volání této funkce z vaší přepsání `CView::OnBeginPrinting`. Pokud délka dokumentu není znám, dokud vytištění, použijte `m_bContinuePrinting` člen k řízení tiskové smyčky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="setminpage"></a>CPrintInfo::SetMinPage  
 Volání této funkce můžete zadat číslo první stránky z dokumentu.  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>Parametry  
 *nMinPage*  
 Počet na první stránku dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Čísla stránek za normálních okolností začínají znakem 1. Tato hodnota je uložena v `CPrintDialog` objekt odkazuje `m_pPD` člen.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)



