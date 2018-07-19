---
title: Cprintinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPrintInfo
dev_langs:
- C++
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cac063d2ee2aeed563137dcb42d3007e81b1bd5
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851610"
---
# <a name="cprintinfo-structure"></a>Cprintinfo – struktura
Ukládá informace o úloze tisk nebo náhled tisku.  
  
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
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Vrátí počet stránek před první stránka DocObject položky tisku v kombinované tiskové úlohy DocObject.|  
|[CPrintInfo::GetToPage](#gettopage)|Vrátí číslo poslední stránky tisku.|  
|[CPrintInfo::SetMaxPage](#setmaxpage)|Nastaví číslo poslední stránky z dokumentu.|  
|[CPrintInfo::SetMinPage](#setminpage)|Nastaví číslo první stránky z dokumentu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintInfo::m_bContinuePrinting](#m_bcontinueprinting)|Obsahuje příznak označující, zda rozhraní by měly pokračovat ve tisku smyčky.|  
|[CPrintInfo::m_bDirect](#m_bdirect)|Obsahuje příznak označující, zda je přímo (bez zobrazení dialogového okna Tisk) tisku dokumentu.|  
|[CPrintInfo::m_bDocObject](#m_bdocobject)|Obsahuje příznak označující, zda je dokument Tisk DocObject.|  
|[CPrintInfo::m_bPreview](#m_bpreview)|Obsahuje příznak označující, zda je náhledu dokumentu.|  
|[CPrintInfo::m_dwFlags](#m_dwflags)|Určuje tiskové operace DocObject.|  
|[CPrintInfo::m_lpUserData](#m_lpuserdata)|Obsahuje ukazatel na strukturu vytvořené uživatelem.|  
|[CPrintInfo::m_nCurPage](#m_ncurpage)|Určuje počet právě tištěné stránky.|  
|[CPrintInfo::m_nJobNumber](#m_njobnumber)|Určuje číslo projektu, přiřazeny podle operačního systému pro aktuální tiskové úlohy|  
|[CPrintInfo::m_nNumPreviewPages](#m_nnumpreviewpages)|Určuje počet stránek zobrazených v okně verze preview; 1 nebo 2.|  
|[CPrintInfo::m_nOffsetPage](#m_noffsetpage)|Určuje posun první stránka konkrétní DocObject v kombinované tiskové úlohy DocObject.|  
|[CPrintInfo::m_pPD](#m_ppd)|Obsahuje ukazatel `CPrintDialog` objektu se používá pro dialogové okno Tisk.|  
|[CPrintInfo::m_rectDraw](#m_rectdraw)|Určuje obdélník definování aktuální oblasti použitelné stránky.|  
|[CPrintInfo::m_strPageDesc](#m_strpagedesc)|Obsahuje řetězec formátu k zobrazení číslo stránky.|  
  
## <a name="remarks"></a>Poznámky  
 `CPrintInfo` Struktura a nemá žádné základní třídy.  
  
 Vytvoří objekt rozhraní framework `CPrintInfo` pokaždé, když tisk nebo náhled tisku příkaz je vybrána a odstraní se po dokončení příkazu.  
  
 `CPrintInfo` obsahuje informace o tiskové úlohy jako celek, jako je například rozsah stránek, které se mají vytisknout a aktuální stav tiskové úlohy, jako je například právě tištěné stránky. Některé informace jsou uloženy v přidružené [cprintdialog –](../../mfc/reference/cprintdialog-class.md) objekt; tento objekt obsahuje hodnoty zadaného uživatelem, v dialogovém okně tisku.  
  
 A `CPrintInfo` objekt je předán mezi rozhraní framework a zobrazit třídu během tisku a slouží k výměně informací mezi nimi. Například rozhraní informuje zobrazení třídy stránce dokumentem k vytištění přiřazením hodnoty, které `m_nCurPage` člen `CPrintInfo`; zobrazení třídy načte hodnotu a provede skutečný tisk zadanou stránku.  
  
 Dalším příkladem je případ nezná délka dokumentu, dokud je vytištěna. V takovém případě testuje třídu zobrazení na konci dokumentu pokaždé, když se vytiskne stránka. Když je dosaženo konce, nastaví zobrazení třídy `m_bContinuePrinting` členem `CPrintInfo` na hodnotu FALSE; tento příkaz informuje framework zastavit smyčka tisku.  
  
 `CPrintInfo` Členské funkce používá `CView` uvedené v části "Viz také." Další informace o architektura pro tisk poskytované knihovny Microsoft Foundation Class, naleznete v tématu [rámce Windows](../../mfc/frame-windows.md) a [architekturu Document/View](../../mfc/document-view-architecture.md) a články [ Tisk](../../mfc/printing.md) a [tisku: vícestránkové dokumenty](../../mfc/multipage-documents.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CPrintInfo`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="getfrompage"></a>  CPrintInfo::GetFromPage  
 Voláním této funkce načtete číslo první stránky, které se mají vytisknout.  
  
```  
UINT GetFromPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo první stránky, které se mají vytisknout.  
  
### <a name="remarks"></a>Poznámky  
 Jedná se o hodnotu zadanou uživatelem v dialogovém okně tisku a je uložen ve `CPrintDialog` objekt odkazovaný zadaným parametrem `m_pPD` člena. Pokud uživatel nemá zadanou hodnotu, výchozí hodnota je první stránka dokumentu.  
  
##  <a name="getmaxpage"></a>  CPrintInfo::GetMaxPage  
 Voláním této funkce načtete číslo poslední stránky dokumentu.  
  
```  
UINT GetMaxPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo poslední stránky z dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota bude uložena v `CPrintDialog` objekt odkazovaný zadaným parametrem `m_pPD` člena.  
  
##  <a name="getminpage"></a>  CPrintInfo::GetMinPage  
 Volání této funkce načtete číslo první stránky z dokumentu.  
  
```  
UINT GetMinPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo první stránky dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota bude uložena v `CPrintDialog` objekt odkazovaný zadaným parametrem `m_pPD` člena.  
  
##  <a name="getoffsetpage"></a>  CPrintInfo::GetOffsetPage  
 Volání této funkce načtete posun při tisku více položek DocObject z klienta DocObject.  
  
```  
UINT GetOffsetPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet stránek před první stránka DocObject položky tisku v kombinované tiskové úlohy DocObject.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se odkazuje `m_nOffsetPage` člena. První stránka dokumentu bude číslované `m_nOffsetPage` hodnota + 1 po vytištění jako DocObject s jinými aktivní dokumenty. `m_nOffsetPage` Člen je platný pouze tehdy, pokud `m_bDocObject` hodnota je TRUE.  
  
##  <a name="gettopage"></a>  CPrintInfo::GetToPage  
 Voláním této funkce načtete číslo poslední stránky k tisku.  
  
```  
UINT GetToPage() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo poslední stránky k tisku.  
  
### <a name="remarks"></a>Poznámky  
 Jedná se o hodnotu zadanou uživatelem v dialogovém okně tisku a je uložen ve `CPrintDialog` objekt odkazovaný zadaným parametrem `m_pPD` člena. Pokud uživatel nemá zadanou hodnotu, výchozí hodnota je poslední stránky z dokumentu.  
  
##  <a name="m_bcontinueprinting"></a>  CPrintInfo::m_bContinuePrinting  
 Obsahuje příznak označující, zda rozhraní by měly pokračovat ve tisku smyčky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud provádíte čas tisku stránkování, tento člen můžete nastavit na hodnotu FALSE v přepsání metody `CView::OnPrepareDC` Jakmile bylo dosaženo konce dokumentu. Není potřeba změny této proměnné, pokud jste zadali délku dokumentu na začátku používání tiskových úloh `SetMaxPage` členskou funkci. `m_bContinuePrinting` Člen je veřejná proměnná typu BOOL.  
  
##  <a name="m_bdirect"></a>  CPrintInfo::m_bDirect  
 Tento člen rozhraní nastaví na hodnotu TRUE, pokud pro přímý tisk z; se obejdou dialogového okna Tisk FALSE v opačném případě.  
  
### <a name="remarks"></a>Poznámky  
 Dialogové okno Tisk obvykle přeskočí při tisku z prostředí nebo když probíhá tisk pomocí příkazu ID ID_FILE_PRINT_DIRECT.  
  
 Je obvykle neměnit tento člen, ale pokud změníte, změňte ho před volání [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) v přepsání metody [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="m_bdocobject"></a>  CPrintInfo::m_bDocObject  
 Obsahuje příznak označující, zda je dokument Tisk DocObject.  
  
### <a name="remarks"></a>Poznámky  
 Datové členy `m_dwFlags` a `m_nOffsetPage` jsou neplatné, pokud tento příznak má hodnotu TRUE.  
  
##  <a name="m_bpreview"></a>  CPrintInfo::m_bPreview  
 Obsahuje příznak označující, zda je náhledu dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Je nastavené rozhraním, v závislosti na provedení příkazu uživatele. Dialogové okno Tisk se nezobrazuje u úlohy náhled tisku. `m_bPreview` Člen je veřejná proměnná typu BOOL.  
  
##  <a name="m_dwflags"></a>  CPrintInfo::m_dwFlags  
 Obsahuje kombinaci příznaky určující operací tisku DocObject.  
  
### <a name="remarks"></a>Poznámky  
 Platí, pouze pokud datový člen `m_bDocObject` má hodnotu TRUE.  
  
 Příznaky může být jeden nebo více z následujících hodnot:  
  
- PRINTFLAG_MAYBOTHERUSER  
  
- PRINTFLAG_PROMPTUSER  
  
- PRINTFLAG_USERMAYCHANGEPRINTER  
  
- PRINTFLAG_RECOMPOSETODEVICE  
  
- PRINTFLAG_DONTACTUALLYPRINT  
  
- PRINTFLAG_FORCEPROPERTIES  
  
- PRINTFLAG_PRINTTOFILE  
  
##  <a name="m_lpuserdata"></a>  CPrintInfo::m_lpUserData  
 Obsahuje ukazatel na strukturu vytvořené uživatelem.  
  
### <a name="remarks"></a>Poznámky  
 To můžete použít k ukládání dat specifické pro tisk, které nechcete ukládat ve třídě zobrazení. `m_lpUserData` Člen je veřejná proměnná typu lpvoid –.  
  
##  <a name="m_ncurpage"></a>  CPrintInfo::m_nCurPage  
 Obsahuje číslo aktuální stránky.  
  
### <a name="remarks"></a>Poznámky  
 Rámec volá `CView::OnPrepareDC` a `CView::OnPrint` jednou pro každou stránku z dokumentu, zadáním jiné hodnoty pro tento člen pokaždé, když; jeho hodnoty v rozsahu od hodnoty vrácené `GetFromPage` na vrácený rutinou `GetToPage`. Pomocí tohoto člena v vaše přepsání `CView::OnPrepareDC` a `CView::OnPrint` tisknout zadanou stránku z dokumentu.  
  
 Při prvním vyvolání režimu náhledu, rozhraní přečte hodnotu této vlastnosti k určení stránka dokumentu, který by měl být zobrazen původně. Hodnota této vlastnosti můžete nastavit v přepsání metody `CView::OnPreparePrinting` udržovat aktuální pozici uživatele v dokumentu, při vstupu do režimu náhledu. `m_nCurPage` Člen je veřejná proměnná typu UINT.  
  
##  <a name="m_njobnumber"></a>  CPrintInfo::m_nJobNumber  
 Označuje číslo projektu, přiřazeny podle operačního systému pro aktuální tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota může být SP_ERROR, pokud úloha nebyla dosud vytištěna (tj. Pokud `CPrintInfo` objektu je nově vytvořena a nebyla použita ještě pro tisk), nebo pokud došlo k chybě při spouštění úlohy.  
  
##  <a name="m_nnumpreviewpages"></a>  CPrintInfo::m_nNumPreviewPages  
 Obsahuje počet stránek zobrazených v režimu náhledu. může být buď 1 nebo 2.  
  
### <a name="remarks"></a>Poznámky  
 `m_nNumPreviewPages` Člen je veřejná proměnná typu UINT.  
  
##  <a name="m_noffsetpage"></a>  CPrintInfo::m_nOffsetPage  
 Obsahuje počet stránek před první stránka konkrétní DocObject v kombinované tiskové úlohy DocObject.  
  
##  <a name="m_ppd"></a>  CPrintInfo::m_pPD  
 Obsahuje ukazatel `CPrintDialog` objektu se používá k zobrazení dialogového okna Tisk tiskové úlohy.  
  
### <a name="remarks"></a>Poznámky  
 `m_pPD` Je veřejná proměnná deklarována jako ukazatel na člen `CPrintDialog`.  
  
##  <a name="m_rectdraw"></a>  CPrintInfo::m_rectDraw  
 Určuje použitelné vykreslování části stránky v logické souřadnice.  
  
### <a name="remarks"></a>Poznámky  
 Možná budete chtít projít tento v přepsání metody `CView::OnPrint`. Tento člen můžete sledovat, jaká oblast zůstává použitelný po vytištění záhlaví, zápatí a tak dále. `m_rectDraw` Člen je veřejná proměnná typu `CRect`.  
  
##  <a name="m_strpagedesc"></a>  CPrintInfo::m_strPageDesc  
 Obsahuje řetězec formátu použitý pro zobrazení čísla stránek během náhled tisku; Tento řetězec skládá ze dvou podřetězců, jeden pro zobrazení jednostránkové a jeden pro zobrazení stránky double, každý ukončen znakem '\n'.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní používá jako výchozí hodnotu "Stránka %u\nPages % u-%u\n". Pokud chcete do jiného formátu pro číslo stránky, zadejte řetězec formátu v přepsání metody `CView::OnPreparePrinting`. `m_strPageDesc` Člen je veřejná proměnná typu `CString`.  
  
##  <a name="setmaxpage"></a>  CPrintInfo::SetMaxPage  
 Voláním této funkce zadejte číslo poslední stránky z dokumentu.  
  
```  
void SetMaxPage(UINT nMaxPage);
```  
  
### <a name="parameters"></a>Parametry  
 *nMaxPage*  
 Číslo poslední stránky z dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota bude uložena v `CPrintDialog` objekt odkazovaný zadaným parametrem `m_pPD` člena. Pokud je délka dokumentu znám před tiskem, voláním této funkce z přepsání metody `CView::OnPreparePrinting`. Pokud délka dokumentu závisí na nastavení zadaný uživatelem v dialogovém okně tisku, voláním této funkce z přepsání metody `CView::OnBeginPrinting`. Pokud délka dokumentu není znám, dokud ho vytisknout, použijte `m_bContinuePrinting` člena pro řízení smyčky tisku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).  
  
##  <a name="setminpage"></a>  CPrintInfo::SetMinPage  
 Voláním této funkce zadejte číslo první stránky z dokumentu.  
  
```  
void SetMinPage(UINT nMinPage);
```  
  
### <a name="parameters"></a>Parametry  
 *nMinPage*  
 Číslo první stránky z dokumentu.  
  
### <a name="remarks"></a>Poznámky  
 Čísla stránek obvykle začínají znakem 1. Tato hodnota bude uložena v `CPrintDialog` objekt odkazovaný zadaným parametrem `m_pPD` člena.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)   
 [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)   
 [CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)   
 [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)   
 [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)   
 [CView::OnPrint](../../mfc/reference/cview-class.md#onprint)



