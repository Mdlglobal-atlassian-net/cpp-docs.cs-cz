---
title: Ladění a zasílání zpráv o chybách makra
ms.date: 05/06/2019
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
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330191"
---
# <a name="debugging-and-error-reporting-macros"></a>Ladění a zasílání zpráv o chybách makra

Tato makra poskytují užitečné ladění a trasování zařízení.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zápisy do výstupního okna, všechny nevracení rozhraní, které jsou zjištěny při `_Module.Term` volání.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapíše všechna `QueryInterface` volání do výstupního okna.|
|[ATLASSERT](#atlassert)|Provádí stejné funkce jako [makro _ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) nalezené v knihovně run-time C.|
|[ZAJIŠTĚNÍ](#atlensure)|Provádí ověření parametrů. V `AtlThrow` případě potřeby zavolejte|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Odešle zprávu zařízení s výpisem stavu paměti, že zadaná funkce není implementována.|
|[ATLTRACE](#atltrace)|Hlásí upozornění do výstupního zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní. Součástí je zpětná kompatibilita.|
|[ATLTRACE2](#atltrace2)|Hlásí upozornění do výstupního zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

Definujte toto makro před zahrnutím `AddRef` `Release` všech souborů hlaviček knihovny ATL pro sledování všech a volání rozhraní komponent do výstupního okna.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Poznámky

Výstup trasování se zobrazí tak, jak je znázorněno níže:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

První část každé stopy `ATL: QIThunk`bude vždy . Dále je hodnota identifikující konkrétní *rozhraní thunk* používá. Thunk rozhraní je objekt používaný k udržení počtu odkazů a poskytují možnost itrasování, které jsou zde použity. Nové rozhraní thunk je vytvořen `QueryInterface` při každém volání `IUnknown` s výjimkou požadavků na rozhraní (v tomto případě je vrácena stejná thunk pokaždé, když v souladu s pravidly identity COM).

Dále uvidíte `AddRef` nebo `Release` uvedete, která metoda byla volána. Poté uvidíte hodnotu identifikující objekt, jehož počet odkazů na rozhraní byl změněn. Hodnota trasované je **tento** ukazatel objektu.

Počet odkazů, který je sledován, je počet odkazů `AddRef` `Release` na tento thunk po nebo byl volán. Všimněte si, že tento počet odkazů nemusí odpovídat počet odkazů pro objekt. Každý thunk udržuje svůj vlastní počet odkazů, které vám pomohou plně v souladu s pravidly com počítání odkazů.

Poslední část informace trasované je název objektu a rozhraní `AddRef` ovlivněna nebo `Release` volání.

Všechny nevracení rozhraní, které jsou zjištěny při vypnutí serveru a `_Module.Term` je volána bude zaznamenána takto:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Zde uvedené informace se mapují přímo na informace uvedené v předchozích příkazech trasování, takže můžete zkontrolovat počty odkazů po celou dobu životnosti rozhraní thunk. Kromě toho získáte údaj o maximální počet odkazů na toto rozhraní thunk.

> [!NOTE]
> _ATL_DEBUG_INTERFACES lze použít v maloobchodních sestaveních.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

Zapíše všechna `QueryInterface` volání do výstupního okna.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Poznámky

Pokud volání `QueryInterface` se nezdařilo, zobrazí se výstupní okno:

*název rozhraní* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT

Makro ATLASSERT provádí stejné funkce jako [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makro nalezené v knihovně run-time C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parametry

*logický výraz*<br/>
Výraz (včetně ukazatelů), který je vyhodnocen jako nenulový nebo 0.

### <a name="remarks"></a>Poznámky

V sestaveních ladění ATLASSERT vyhodnotí *logický výraz* a vygeneruje ladicí sestavu, pokud je výsledek nepravdivý.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ZAJIŠTĚNÍ

Toto makro se používá k ověření parametrů předaných funkci.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parametry

*logický výraz*<br/>
Určuje logický výraz, který má být testován.

*Hr*<br/>
Určuje kód chyby, který má být vrácen.

### <a name="remarks"></a>Poznámky

Tato makra poskytují mechanismus pro detekci a upozornění uživatele na nesprávné použití parametrů.

Makro volá ATLASSERT a pokud `AtlThrow`podmínka selže volání .

V případě ATLENSURE `AtlThrow` se nazývá s E_FAIL.

V případě ATLENSURE_THROW `AtlThrow` je volána se zadaným HRESULT.

Rozdíl mezi ATLENSURE a ATLASSERT je, že ATLENSURE vyvolá výjimku v sestavení verze, stejně jako v sestavení ladění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL

V ladění sestavení ATL odešle řetězec *"funcname* není implementován" do zařízení s výpisem stavu paměti a vrátí E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parametry

*funcname*<br/>
[v] Řetězec obsahující název funkce, která není implementována.

### <a name="remarks"></a>Poznámky

Ve verzi sestavení jednoduše vrátí E_NOTIMPL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE

Hlásí upozornění do výstupního zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní. Součástí je zpětná kompatibilita.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parametry

*Exp*<br/>
[v] Řetězec a proměnné odeslat do výstupního okna nebo jakékoli aplikace, která soutisk těchto zpráv.

*Kategorie*<br/>
[v] Typ události nebo metody, o které chcete podat zprávu. Seznam kategorií naleznete v seznamu poznámek.

*Úrovni*<br/>
[v] Úroveň trasování sestavy. Podrobnosti naleznete v poznámkách.

*lpszFormat*<br/>
[v] Formátovaný řetězec odeslat do zařízení s výpisem stavu paměti.

### <a name="remarks"></a>Poznámky

Popis [atltrace](#atltrace2) naleznete v attrace2. ATLTRACE a ATLTRACE2 mají stejné chování, ATLTRACE je součástí zpětné kompatibility.

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2

Hlásí upozornění do výstupního zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Parametry

*Exp*<br/>
[v] Řetězec odeslat do výstupního okna nebo jakékoli aplikace, která snímat pasti tyto zprávy.

*Kategorie*<br/>
[v] Typ události nebo metody, o které chcete podat zprávu. Seznam kategorií naleznete v seznamu poznámek.

*Úrovni*<br/>
[v] Úroveň trasování sestavy. Podrobnosti naleznete v poznámkách.

*lpszFormat*<br/>
[v] Formát `printf`-style řetězec použít k vytvoření řetězce pro odeslání do zařízení s výpisem stavu paměti.

### <a name="remarks"></a>Poznámky

Krátká forma ATLTRACE2 zapíše řetězec do výstupního okna ladicího programu. Druhá forma ATLTRACE2 také zapisuje výstup do výstupního okna ladicího programu, ale podléhá nastavení nástroje trace ATL/MFC (viz [ukázka nástroje ATLTraceTool).](../../overview/visual-cpp-samples.md) Pokud například nastavíte *úroveň* 4 a nástroj trace ATL/MFC na úroveň 0, zpráva se nezobrazí. *může* být 0, 1, 2, 3 nebo 4. Výchozí hodnota 0 hlásí pouze nejzávažnější problémy.

Parametr *kategorie* uvádí příznaky trasování, které mají být nastaveny. Tyto příznaky odpovídají typům metod, pro které chcete vykazovat. V následujících tabulkách jsou uvedeny platné příznaky trasování, které můžete použít pro parametr *kategorie.*

### <a name="atl-trace-flags"></a>Příznaky trasování atl

|Kategorie ATL|Popis|
|------------------|-----------------|
|`atlTraceGeneral`|Zprávy o všech aplikacích ATL. Výchozí nastavení|
|`atlTraceCOM`|Zprávy o metodách COM.|
|`atlTraceQI`|Sestavy pro volání QueryInterface.|
|`atlTraceRegistrar`|Zprávy o registraci objektů.|
|`atlTraceRefcount`|Zprávy o změně počtu odkazů.|
|`atlTraceWindowing`|Zprávy o metodách systému Windows; například hlásí neplatné ID mapy zpráv.|
|`atlTraceControls`|Zprávy o kontrolách; například hlásí, když je zničen ovládací prvek nebo jeho okno.|
|`atlTraceHosting`|Zprávy hostování zpráv; například hlásí, když je aktivován klient v kontejneru.|
|`atlTraceDBClient`|Sestavy šablony příjemce technologie OLE DB; například při volání GetData selže, výstup může obsahovat HRESULT.|
|`atlTraceDBProvider`|Sestavy šablony zprostředkovatele TECHNOLOGIE OLE DB; například sestavy, pokud se vytvoření sloupce nezdařilo.|
|`atlTraceSnapin`|Sestavy pro aplikaci MMC SnapIn.|
|`atlTraceNotImpl`|Hlásí, že uvedená funkce není implementována.|
|`atlTraceAllocation`|Hlásí zprávy vytištěné nástroji pro ladění paměti v souboru atldbgmem.h.|

### <a name="mfc-trace-flags"></a>Příznaky trasování knihovny MFC

|Kategorie knihovny MFC|Popis|
|------------------|-----------------|
|`traceAppMsg`|Obecné účely, zprávy Knihovny MFC. Vždy doporučujeme.|
|`traceDumpContext`|Zprávy z [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Zprávy z kódu zpracování zpráv knihovny MFC.|
|`traceMemory`|Zprávy z kódu správy paměti knihovny MFC.|
|`traceCmdRouting`|Zprávy z směrovacího kódu příkazu systému Windows knihovny MFC.|
|`traceHtml`|Zprávy z knihovny MFC podporu dialogového okna DHTML.|
|`traceSocket`|Zprávy z podpory soketu knihovny MFC.|
|`traceOle`|Zprávy z podpory OLE knihovny MFC.|
|`traceDatabase`|Zprávy z knihovny MFC databáze podporují.|
|`traceInternet`|Zprávy z internetové podpory knihovny MFC.|

Chcete-li deklarovat vlastní kategorii trasování, deklarujte globální instanci `CTraceCategory` třídy následujícím způsobem:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Název kategorie, MY_CATEGORY v tomto příkladu, je název, který zadáte pro parametr *kategorie.* První parametr je název kategorie, který se zobrazí v nástroji trace ATL/MFC. Druhý parametr je výchozí úroveň trasování. Tento parametr je volitelný a výchozí úroveň trasování je 0.

Použití uživatelem definované kategorie:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Chcete-li určit, že chcete filtrovat trasovací zprávy, vložte definice těchto `#include <atlbase.h>` maker do souboru Stdafx.h před příkaz.

Případně můžete filtr nastavit v direktivách preprocesoru v dialogovém okně **Stránky vlastností.** Klikněte na kartu **Preprocesor** a vložte globální do pole **Pro úpravy definice preprocesoru.**

Soubor Atlbase.h obsahuje výchozí definice maker ATLTRACE2 a tyto definice budou použity, pokud tyto symboly nedefinujete před zpracováním souboru atlbase.h.

V sestaveních verze ATLTRACE2 `(void) 0`zkompiluje do .

ATLTRACE2 omezuje obsah řetězce, který má být odeslán do zařízení s výpisem stavu paměti, na maximálně 1023 znaků po formátování.

ATLTRACE a ATLTRACE2 mají stejné chování, ATLTRACE je součástí zpětné kompatibility.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[Ladění a zasílání zpráv o chybách globální funkce](../../atl/reference/debugging-and-error-reporting-global-functions.md)
