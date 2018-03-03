---
title: "Makra ladění a zasílání zpráv o chybách | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9098b944f70ab4e4448fe40aa2347b0128e6e1a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-macros"></a>Makra ladění a zasílání zpráv o chybách
Tyto makra poskytují užitečné ladění a trasování zařízení.  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zapíše do okna výstupu nevracení všechny rozhraní, která při zjištění `_Module.Term` je volána.|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapíše všechna volání `QueryInterface` do okna výstupu.|  
|[ATLASSERT](#atlassert)|Provádí stejné funkce jako [_asserte –](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makro v běhové knihovny jazyka C nalezeno.|  
|[ATLENSURE](#atlensure)|Provede ověření parametry. Volání `AtlThrow` v případě potřeby|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|Odešle zprávu do zařízení výpisu, že zadaná funkce není implementována.|  
|[ATLTRACE](#alttrace)|Sestavy upozornění na výstupní zařízení, jako je například okna ladicího programu podle uvedeného příznaky a úrovně. Zahrnuté z důvodu zpětné kompatibility.|  
|[ATLTRACE2](#atltrace2)|Sestavy upozornění na výstupní zařízení, jako je například okna ladicího programu podle uvedeného příznaky a úrovně.|  
  
##  <a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 Toto makro definovat před zahrnutím chcete trasovat všechny soubory záhlaví ATL `AddRef` a **verze** volání na rozhraní vaší součásti, které se ve výstupním okně.  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>Poznámky  
 Výstup bude vypadat takto:  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 První část každý trasování bude vždy `ATL: QIThunk`. Dále je identifikace konkrétní hodnotu *rozhraní převodu* používá. Převodu rozhraní je objekt sloužící k udržování počet odkazů a zabezpečení trasování umožňuje použít se zde. Nové rozhraní převodu se vytvoří při každém volání do `QueryInterface` s výjimkou požadavky **IUnknown** rozhraní (v tomto případě stejné převodu je vrácen pokaždé, když do souladu s pravidly na COM identity).  
  
 Dále uvidíte `AddRef` nebo **verze** indikující, která metoda byla volána. Následující, zobrazí se hodnota identifikace objekt, jehož počet odkazů rozhraní byl změněn. Je hodnota trasovat **to** ukazatele objektu.  
  
 Počet odkazů, trasovaný je počet odkazů na této převodu po `AddRef` nebo **verze** byla volána. Všimněte si, že tento počet odkazů nemusí odpovídat počet odkazů pro daný objekt. Každý převodu udržuje vlastní počet odkazů můžete plně souladu s pravidly na COM počítání odkazů.  
  
 Poslední díl informace trasovat je název objektu a rozhraní ovlivnění `AddRef` nebo **verze** volání.  
  
 Žádné rozhraní nevracení, které jsou zjištěny při vypnutí serveru a `_Module.Term` se nazývá budou zaznamenány do protokolu takto:  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 Zde uvedené informace mapy přímo na informacích uvedených v předchozí trasovacích příkazů, tak můžete zkontrolovat v celém celou dobu životnosti převodu rozhraní počty odkaz. Kromě toho získáte údajem o maximálního počtu odkazů na jinou bitovou šířku tohoto rozhraní.  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`lze použít v prodejní sestavení.  
  
##  <a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 Zapíše všechna volání `QueryInterface` do okna výstupu.  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud volání `QueryInterface` se nezdařilo, v okně výstupu se zobrazí:  
  
 *Název rozhraní* - `failed`  
  
##  <a name="atlassert"></a>ATLASSERT  
 `ATLASSERT` Makro provádí stejné funkce jako [_asserte –](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makro najít v běhové knihovny jazyka C.  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Výraz (včetně ukazatele), který se vyhodnocuje nenulové hodnoty nebo rovna 0.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění `ATLASSERT` vyhodnotí `booleanExpression` a generuje sestavy ladění, když je výsledkem false.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldef.h  
    
##  <a name="atlensure"></a>ATLENSURE  
 Toto makro slouží k ověření parametry předaný funkci.  
  
```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Určuje logický výraz, který má být testována.  
  
 `hr`  
 Určuje kód chyby vrátit.  
  
### <a name="remarks"></a>Poznámky  
 Tyto makra poskytují mechanismus ke zjišťování a upozornit uživatele využití nesprávný parametr.  
  
 Makro volání `ATLASSERT` a pokud podmínka selže volání `AtlThrow`.  
  
 V **ATLENSURE** případě `AtlThrow` je volán s E_FAIL.  
  
 V **ATLENSURE_THROW** případě `AtlThrow` je volán s zadaný HRESULT.  
  
 Rozdíl mezi **ATLENSURE** a `ATLASSERT` je, že **ATLENSURE** vyvolá výjimku ve verzi sestavení stejně jako v sestavení pro ladění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  

##  <a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 V sestavení pro ladění z knihovny ATL odešle řetězec " `funcname` není implementována" výpisu zařízení a vrátí **E_NOTIMPL**.  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>Parametry  
 `funcname`  
 [v] Řetězec obsahující název funkce, která není implementována.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro vydání, jednoduše vrátí **E_NOTIMPL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltrace.h 

##  <a name="atltrace"></a>ATLTRACE
 Sestavy upozornění na výstupní zařízení, jako je například okna ladicího programu podle uvedeného příznaky a úrovně. Zahrnuté z důvodu zpětné kompatibility.  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `exp`  
 [v] Řetězec a proměnné, které chcete odeslat ve výstupním okně Visual C++ nebo jakékoli aplikace, která traps tyto zprávy.  
  
 `category`  
 [v] Typ události nebo metoda, na kterém do sestavy. V části poznámky seznam kategorií.  
  
 `level`  
 [v] Úroveň trasování do sestavy. V části poznámky podrobnosti.  
  
 `lpszFormat`  
 [v] Formátovaný řetězec, který poslat výpisu zařízení.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [ATLTRACE2](#atltrace2) popis **ATLTRACE**. **ATLTRACE** a `ATLTRACE2` mají stejné chování **ATLTRACE** je zahrnuté pro zpětné kompatibility.  
  
##  <a name="atltrace2"></a>ATLTRACE2  
 Sestavy upozornění na výstupní zařízení, jako je například okna ladicího programu podle uvedeného příznaky a úrovně.  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>Parametry  
 `exp`  
 [v] Řetězec, který se má odeslat ve výstupním okně Visual C++ nebo jakékoli aplikace, která traps tyto zprávy.  
  
 `category`  
 [v] Typ události nebo metoda, na kterém do sestavy. V části poznámky seznam kategorií.  
  
 `level`  
 [v] Úroveň trasování do sestavy. V části poznámky podrobnosti.  
  
 `lpszFormat`  
 [v] `printf`– Styl řetězec formátu sloužící k vytvoření řetězce k odeslání do zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Zkratka pro `ATLTRACE2` zapíše řetězec tak, aby ladicí program výstupu okno. O druhou podobu `ATLTRACE2` také zapíše výstup do okna výstupu ladicího programu, ale podléhá nastavení nástroj trasování ATL a MFC (viz [ATLTraceTool ukázka](../../visual-cpp-samples.md)). Například pokud nastavíte `level` 4 a nástroj trasování ATL a MFC na úrovni 0, nebudou zobrazí se zpráva. *úroveň* může být 0, 1, 2, 3 nebo 4. Výchozí hodnota 0, sestavy pouze nejvážnější problémy.  
  
 `category` Parametr uvádí příznaky trasování nastavit. Tyto příznaky odpovídají typům metod, pro které chcete do sestavy. Následující tabulky seznam příznaky platný trasování můžete použít pro `category` parametr.  
  
### <a name="atl-trace-flags"></a>Příznaky trasování ATL  
  
|Kategorie knihovny ATL|Popis|  
|------------------|-----------------|  
|`atlTraceGeneral`|Sestavy o všech ATL aplikací. Výchozí nastavení|  
|`atlTraceCOM`|Sestavy o COM metody.|  
|`atlTraceQI`|Sestavy o QueryInterface volání.|  
|`atlTraceRegistrar`|Zprávy o registraci objekty.|  
|`atlTraceRefcount`|Sestavy o změně počet odkazů.|  
|`atlTraceWindowing`|Sestavy o windows metody; například sestavy identifikátor neplatná zpráva mapy.|  
|`atlTraceControls`|Sestavy na ovládací prvky; Například nahlásí, když je zničení ovládacího prvku nebo její okno.|  
|`atlTraceHosting`|Sestavy hostování zprávy; Například nahlásí, když se aktivuje klienta v kontejneru.|  
|`atlTraceDBClient`|Sestavy o šablony příjemce technologie OLE DB; například při volání GetData selže, může obsahovat výstup hodnota HRESULT.|  
|`atlTraceDBProvider`|Sestavy o šablon zprostředkovatele technologie OLE DB; například sestavy, pokud vytvoření sloupce se nezdařilo.|  
|`atlTraceSnapin`|Sestavy pro aplikaci modul snap-in konzoly MMC.|  
|`atlTraceNotImpl`|Hlásí, že uvedené funkce není implementována.|  
|**atlTraceAllocation**|Tištěné paměti nástroje pro ladění v atldbgmem.h zprávy sestavy.|  
  
### <a name="mfc-trace-flags"></a>Příznaky trasování MFC  
  
|Kategorie MFC|Popis|  
|------------------|-----------------|  
|**traceAppMsg**|Obecné účely MFC zprávy. Vždy doporučujeme.|  
|**traceDumpContext**|Zprávy z [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|  
|**traceWinMsg**|Zprávy ze zpráv knihovny MFC kód pro zpracování.|  
|**traceMemory**|Zprávy ze společnosti MFC kódu správy paměti.|  
|**traceCmdRouting**|Zprávy ze systému Windows na MFC příkaz směrování kódu.|  
|**traceHtml**|Zprávy z knihovny MFC jazyka DHTML dialogové okno podpory.|  
|**traceSocket**|Zprávy ze Podpora MFC pro soket.|  
|**traceOle**|Zprávy ze Podpora MFC pro OLE.|  
|**traceDatabase**|Zprávy ze podpory databáze MFC společnosti.|  
|**traceInternet**|Zprávy ze podpory MFC na Internetu.|  
  
 Deklarovat kategorie vlastního trasování, deklarovat globální instance `CTraceCategory` třídy následujícím způsobem:  
  
 [!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 Název kategorie `MY_CATEGORY` v tomto příkladu je název zadáte `category` parametr. První parametr je název kategorie, které se zobrazí v nástroj trasování ATL a MFC. Druhý parametr je výchozí úroveň trasování. Tento parametr je volitelný a výchozí úroveň trasování je 0.  
  
 Použití uživatelem definované kategorie:  
  
 [!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 K určení, zda chcete filtrovat zprávy trasování, vložit do Stdafx.h před definice pro tyto makra `#include <atlbase.h>` příkaz.  
  
 Alternativně můžete nastavit filtr v preprocesor – direktivy v **stránky vlastností** dialogové okno. Klikněte na tlačítko **preprocesor** kartě a vložte do globální **Definice preprocesoru** textové pole.  
  
 Atlbase.h obsahuje výchozí definice `ATLTRACE2` makra a tyto definice bude použit, pokud předtím, než je zpracován atlbase.h nedefinujete těchto symbolů.  
  
 V sestavení pro vydání `ATLTRACE2` zkompiluje do `(void) 0`.  
  
 `ATLTRACE2`omezuje obsah řetězce k odeslání do zařízení, na více než 1023 znaků po formátování.  
  
 **ATLTRACE** a `ATLTRACE2` mají stejné chování **ATLTRACE** je zahrnuté pro zpětné kompatibility.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)   
 [Globální funkce ladění a hlášení chyb](../../atl/reference/debugging-and-error-reporting-global-functions.md)
