---
title: Makra ladění a hlášení chyb
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 0f556e64160c61f2fb15c5f5d6f9e170c2008ac8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287320"
---
# <a name="debugging-and-error-reporting-macros"></a>Makra ladění a hlášení chyb

Tato makra poskytují užitečné funkce ladění a trasování.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zapíše do okna výstup, který nevrací žádné rozhraní při zjištění `_Module.Term` je volána.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapíše všechna volání `QueryInterface` v okně výstupu.|
|[ATLASSERT](#atlassert)|Provádí stejné funkce jako [_asserte –](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) – makro najdete v knihovně C Runtime.|
|[ATLENSURE](#atlensure)|Provede ověření parametrů. Volání `AtlThrow` v případě potřeby|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Odešle zprávu do zařízení s výpisem paměti, že zadaná funkce není implementována.|
|[ATLTRACE](#alttrace)|Zprávy upozornění na výstupní zařízení, jako je například okna ladicího programu, podle uvedeného příznaky a úrovně. Zahrnuto z důvodu zpětné kompatibility.|
|[ATLTRACE2](#atltrace2)|Zprávy upozornění na výstupní zařízení, jako je například okna ladicího programu, podle uvedeného příznaky a úrovně.|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

Toto makro definovat před zahrnutím všech hlavičkové soubory ATL. chcete trasovat všechny `AddRef` a `Release` volá na vaše komponenty rozhraní v okně výstupu.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Poznámky

Trasování výstupu se zobrazí, jak je znázorněno níže:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

První část každé trasování bude vždy `ATL: QIThunk`. Dále je hodnota identifikaci konkrétní *rozhraní převodní rutina* používá. Rozhraní převodní rutina je objekt umožňuje spravovat počet odkazů a poskytovat možnost trasování se tady použít. Nové rozhraní převodní rutina se vytvoří při každém volání do `QueryInterface` s výjimkou žádostí o `IUnknown` rozhraní (v tomto případě stejné převodní rutina se vrátí pokaždé, když se do souladu s pravidly modelu COM identitu).

Dále uvidíte `AddRef` nebo `Release` určující, která metoda se volala. Pod se zobrazí hodnota identifikaci objektů, jejichž počet odkazů rozhraní byl změněn. Hodnota trasovány **to** ukazatel na objekt.

Počet odkazů, která je sledována je počet odkazů na tomto převodní rutina po `AddRef` nebo `Release` byla volána. Všimněte si, že tento počet odkazů nemusí odpovídat počet odkazů pro objekt. Každý převodní rutina udržuje svůj vlastní počet odkazů můžete zcela v souladu s pravidly počítání odkazů modelu COM.

Název objektu a interface byly ovlivněny je poslední část informací trasovány `AddRef` nebo `Release` volání.

Žádné rozhraní úniku informací, které se zjistily při vypnutí serveru a `_Module.Term` volání zaznamenávané takto:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Informace uvedené tady mapuje přímo na informace uvedené v předchozí příkazy trasování, tak můžete zkoumat, odkaz se počítá v průběhu celého životního převodní rutina rozhraní. Kromě toho zajistit indikaci maximálního počtu odkazů na převodní rutina tohoto rozhraní.

> [!NOTE]
> _ATL_DEBUG_INTERFACES je možné v prodejní buildy.

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

Zapíše všechna volání `QueryInterface` v okně výstupu.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Poznámky

Pokud je volání `QueryInterface` se nezdařila, v okně výstupu se zobrazí:

*Název rozhraní* - `failed`

##  <a name="atlassert"></a>  ATLASSERT

Makra ATLASSERT provádí stejné funkce jako [_asserte –](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) – makro najdete v knihovně C Runtime.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Výraz (včetně odkazů), který se vyhodnotí na nenulovou hodnotu nebo 0.

### <a name="remarks"></a>Poznámky

V ladicím buildu ATLASSERT vyhodnotí *booleanExpression* a vygeneruje sestavu ladění, pokud je výsledek false.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef.h

##  <a name="atlensure"></a>  ATLENSURE

Toto makro se používá k ověření parametry předané do funkce.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Určuje logický výraz, který má být testována.

*hr*<br/>
Určuje kód chyby se vraťte.

### <a name="remarks"></a>Poznámky

Tato makra poskytují mechanismus pro zjišťování a upozornit uživatele nesprávný parametr využití.

Makro volá ATLASSERT a pokud je podmínka selže volání `AtlThrow`.

V případě ATLENSURE `AtlThrow` volána s E_FAIL.

V případě ATLENSURE_THROW `AtlThrow` volána s zadaná hodnota HRESULT.

Rozdíl mezi ATLENSURE a ATLASSERT je, že ATLENSURE vyvolá výjimku v sestaveních pro vydání stejně jako v sestaveních ladění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL

V sestavení ladění knihovny ATL, odešle řetězec " *funcname* neimplementována" na zařízení s výpisem paměti a vrátí E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parametry

*FuncName*<br/>
[in] Řetězec obsahující název funkce, která není implementována.

### <a name="remarks"></a>Poznámky

V sestaveních pro vydání jednoduše vrací E_NOTIMPL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltrace.h

##  <a name="atltrace"></a>  ATLTRACE

Zprávy upozornění na výstupní zařízení, jako je například okna ladicího programu, podle uvedeného příznaky a úrovně. Zahrnuto z důvodu zpětné kompatibility.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parametry

*exp*<br/>
[in] Řetězec a proměnné pro odeslání v okně Výstup Visual C++ nebo jakékoliv aplikace, která zachycuje tyto zprávy.

*Kategorie*<br/>
[in] Typ události nebo metody, na kterém do sestavy. Viz poznámky pro seznam kategorií.

*úroveň*<br/>
[in] Úroveň trasování pro sestavu. Viz poznámky podrobnosti.

*lpszFormat*<br/>
[in] Formátovaný řetězec, který chcete odeslat do zařízení s výpisem paměti.

### <a name="remarks"></a>Poznámky

Zobrazit [ATLTRACE2](#atltrace2) popis ATLTRACE. ATLTRACE a ATLTRACE2 mají stejné chování, zůstane ATLTRACE z důvodu zpětné kompatibility.

##  <a name="atltrace2"></a>  ATLTRACE2

Zprávy upozornění na výstupní zařízení, jako je například okna ladicího programu, podle uvedeného příznaky a úrovně.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```

### <a name="parameters"></a>Parametry

*exp*<br/>
[in] Řetězec, který se má poslat v okně Výstup Visual C++ nebo jakékoliv aplikace, která zachycuje tyto zprávy.

*Kategorie*<br/>
[in] Typ události nebo metody, na kterém do sestavy. Viz poznámky pro seznam kategorií.

*úroveň*<br/>
[in] Úroveň trasování pro sestavu. Viz poznámky podrobnosti.

*lpszFormat*<br/>
[in] `printf`-Stylu formátovací řetězec použitý k vytvoření řetězce odesílání do zařízení s výpisem paměti.

### <a name="remarks"></a>Poznámky

Krátký tvar ATLTRACE2 zapíše řetězec do okna výstup ladicího programu. Tedy o druhou podobu ATLTRACE2 také zapíše výstup do okna výstup ladicího programu, ale je v souladu s nastavení trasovací nástroj ATL/MFC (viz [ATLTraceTool ukázka](../../visual-cpp-samples.md)). Například pokud nastavíte *úroveň* na 4 a nástroj trasování ATL/MFC na úrovni 0, nebudou se zobrazí zpráva. *úroveň* může být 0, 1, 2, 3 nebo 4. Výchozí hodnotou 0, hlásí pouze nejzávažnější problémy.

*Kategorie* parametrů jsou uvedeny příznaky trasování pro nastavení. Tyto příznaky odpovídají typům metod, pro které chcete do sestavy. V tabulce dole najdete seznam příznaků platný trasování můžete použít pro *kategorie* parametru.

### <a name="atl-trace-flags"></a>Příznaky trasování ATL

|Kategorie ATL|Popis|
|------------------|-----------------|
|`atlTraceGeneral`|Sestavy na všechny aplikace ATL Výchozí nastavení|
|`atlTraceCOM`|Zprávy o COM metody.|
|`atlTraceQI`|Zprávy o volání QueryInterface.|
|`atlTraceRegistrar`|Zprávy o registraci objektů.|
|`atlTraceRefcount`|Sestavy o změně počet odkazů.|
|`atlTraceWindowing`|Sestavy v metodách windows; například sestavy identifikátor neplatná zpráva mapy.|
|`atlTraceControls`|Sestavy v ovládacích prvcích; například sestavy při zničení ovládacího prvku nebo její okno.|
|`atlTraceHosting`|Sestavy hostování zprávy. například sestavy při aktivaci klientů v kontejneru.|
|`atlTraceDBClient`|Zprávy o šablona příjemce technologie OLE DB; například při volání GetData selže, může obsahovat výstup HRESULT.|
|`atlTraceDBProvider`|Zprávy o šablon zprostředkovatele OLE DB; například sestavy, pokud vytváření sloupce se nezdařilo.|
|`atlTraceSnapin`|Sestavy aplikace modulu snap-in konzoly MMC.|
|`atlTraceNotImpl`|Hlásí, že uvedené funkce není implementována.|
|`atlTraceAllocation`|Zprávy vytištěné funkcí paměti nástroje pro ladění v atldbgmem.h zprávy sestavy.|

### <a name="mfc-trace-flags"></a>Příznaky trasování knihovny MFC

|Kategorie knihovny MFC|Popis|
|------------------|-----------------|
|`traceAppMsg`|Pro obecné účely, zpráv knihovny MFC. Vždy doporučujeme.|
|`traceDumpContext`|Zprávy od [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Zprávy z kódu pro zpracování zpráv knihovny MFC.|
|`traceMemory`|Zprávy z kódu MFC paměti správy.|
|`traceCmdRouting`|Zprávy z knihovny MFC Windows příkaz směrování kódu.|
|`traceHtml`|Zprávy z podpory DHTML dialogového okna knihovny MFC.|
|`traceSocket`|Zprávy ze soketu podpory knihovny MFC.|
|`traceOle`|Zprávy z podpory knihovny MFC OLE.|
|`traceDatabase`|Zprávy z podpory databáze knihovny MFC.|
|`traceInternet`|Zprávy z Internetu podpory knihovny MFC.|

Chcete-li deklarovat kategorie vlastního trasování, deklarujte globální instanci `CTraceCategory` třídy následujícím způsobem:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Název kategorie, MY_CATEGORY v tomto příkladu je název určíte, *kategorie* parametru. První parametr je název kategorie, který se zobrazí trasovací nástroj ATL nebo MFC. Druhý parametr je výchozí úroveň trasování. Tento parametr je nepovinný a výchozí úrovně trasování je 0.

Použití uživatelem definované kategorie:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Chcete-li určit, že chcete filtrovat zprávy trasování, vložit do Stdafx.h před definice těchto maker `#include <atlbase.h>` příkazu.

Alternativně můžete nastavit filtr v direktivách preprocesoru v **stránky vlastností** dialogové okno. Klikněte na tlačítko **preprocesor** kartu a pak je vložíte do globální **Definice preprocesoru** textové pole.

Atlbase.h obsahuje výchozí definice maker ATLTRACE2 a tyto definice se použije, pokud nebudete definovat tyto symboly před zpracováním atlbase.h.

V sestaveních pro vydání, ATLTRACE2 kompiluje `(void) 0`.

ATLTRACE2 omezuje obsah řetězce k odeslání do zařízení, na více než 1 023 znaky, po formátování.

ATLTRACE a ATLTRACE2 mají stejné chování, zůstane ATLTRACE z důvodu zpětné kompatibility.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Viz také:

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globální funkce ladění a hlášení chyb](../../atl/reference/debugging-and-error-reporting-global-functions.md)
