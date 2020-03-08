---
title: Makra ladění a zasílání zpráv o chybách
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
ms.openlocfilehash: b666ba3debe164118c9b40b90313646592b04876
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855275"
---
# <a name="debugging-and-error-reporting-macros"></a>Makra ladění a zasílání zpráv o chybách

Tato makra poskytují užitečná zařízení pro ladění a trasování.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zapisuje do okna výstup, jakékoliv nevrácené rozhraní, které je zjištěno při volání `_Module.Term`.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapisuje všechna volání `QueryInterface` do okna výstup.|
|[ATLASSERT](#atlassert)|Provede stejnou funkci jako makro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) , které se nachází v knihovně run-time jazyka C.|
|[ATLENSURE](#atlensure)|Provede ověření parametrů. V případě potřeby volejte `AtlThrow`|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Pošle zprávu na zařízení s výpisem paměti, že zadaná funkce není implementovaná.|
|[ATLTRACE](#atltrace)|Hlásí upozornění na výstupní zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní. Zahrnuto z důvodu zpětné kompatibility.|
|[ATLTRACE2](#atltrace2)|Hlásí upozornění na výstupní zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní.|

##  <a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

Definujte toto makro před zahrnutím souborů hlaviček ATL pro trasování všech `AddRef` a `Release` volání rozhraní komponent do okna výstup.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Poznámky

Výstup trasování se zobrazí, jak je znázorněno níže:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

První část každého trasování bude vždy `ATL: QIThunk`. Další hodnotou je identifikace konkrétního použitého *volání rozhraní* . Rozhraní, které je používáno k údržbě počtu odkazů a poskytuje možnost trasování, které jsou zde použity, je objekt. Nové rozhraní je vytvořeno při každém volání `QueryInterface` s výjimkou požadavků na rozhraní `IUnknown` (v tomto případě je stejná rutina s nevracením zpět vrácena vždy, když je to vyhověno pravidlům identity modelu COM).

Dále uvidíte `AddRef` nebo `Release`, které označují, která metoda byla volána. Za tímto se zobrazí hodnota identifikující objekt, jehož počet odkazů na rozhraní se změnil. Sledovaná hodnota je ukazatel **This** objektu.

Počet odkazů, které jsou trasovány, je počet odkazů na tento převod po volání `AddRef` nebo `Release`. Všimněte si, že tento počet odkazů nesmí odpovídat počtu odkazů pro daný objekt. Každé zpětné volání udržuje svůj vlastní počet odkazů, který vám umožní plně dodržovat pravidla pro počítání odkazů modelu COM.

Poslední část informací, které jsou sledovány, je název objektu a rozhraní, na které se vztahuje `AddRef` nebo `Release` volání.

Dojde k zaznamenání všech nevrácených rozhraní, která jsou zjištěna při ukončení serveru a `_Module.Term` se budou zaprotokolovat takto:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Informace, které jsou zde uvedeny, jsou mapovány přímo k informacím uvedeným v předchozích příkazech trasování, takže můžete kontrolovat počet odkazů po celou dobu životnosti rozhraní. Navíc získáte indikaci maximálního počtu odkazů na tomto rozhraní.

> [!NOTE]
> _ATL_DEBUG_INTERFACES lze použít v maloobchodních sestaveních.

##  <a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

Zapisuje všechna volání `QueryInterface` do okna výstup.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Poznámky

Pokud selže volání `QueryInterface`, zobrazí se okno výstup:

*název rozhraní* - `failed`

##  <a name="atlassert"></a>ATLASSERT

Makro ATLASSERT provádí stejné funkce jako makro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) , které bylo nalezeno v knihovně run-time jazyka C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Výraz (včetně ukazatelů), jejichž výsledkem je nenulová nebo 0.

### <a name="remarks"></a>Poznámky

V sestavení ladění ATLASSERT vyhodnocuje *booleanExpression* a vygeneruje sestavu ladění, pokud je výsledek nepravdivý.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldef. h

##  <a name="atlensure"></a>ATLENSURE

Toto makro slouží k ověření parametrů předaných funkci.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Určuje logický výraz, který se má testovat.

*oddělení*<br/>
Určuje kód chyby, který se má vrátit.

### <a name="remarks"></a>Poznámky

Tato makra poskytují mechanismus pro detekci a upozorňování uživatele na nesprávné použití parametrů.

Makro volá ATLASSERT a pokud podmínka neproběhne, volání `AtlThrow`.

V případě ATLENSURE se zavolá `AtlThrow` s E_FAIL.

V případě ATLENSURE_THROW je `AtlThrow` volána se zadaným HRESULT.

Rozdíl mezi ATLENSURE a ATLASSERT je, že ATLENSURE vyvolá výjimku v sestavení vydaných verzí i v sestaveních ladění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="atltracenotimpl"></a>ATLTRACENOTIMPL

V ladicích sestaveních ATL pošle řetězec " *FuncName* není implementován" do zařízení výpisu paměti a vrátí E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parametry

*FuncName*<br/>
pro Řetězec obsahující název funkce, která není implementována.

### <a name="remarks"></a>Poznámky

V sestavení vydaných verzí jednoduše vrátí E_NOTIMPL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLTRACE. h

##  <a name="atltrace"></a>ATLTRACE

Hlásí upozornění na výstupní zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní. Zahrnuto z důvodu zpětné kompatibility.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parametry

*oček*<br/>
pro Řetězec a proměnné, které se mají odeslat do okna výstupu nebo do jakékoli aplikace, která tyto zprávy provede.

*kategorií*<br/>
pro Typ události nebo metody, na které se má sestava nahlásit Seznam kategorií naleznete v tématu poznámky.

*obsah*<br/>
pro Úroveň trasování pro sestavu. Podrobnosti najdete v poznámkách.

*lpszFormat*<br/>
pro Formátovaný řetězec, který má být odeslán na zařízení s výpisem paměti.

### <a name="remarks"></a>Poznámky

Popis ATLTRACE najdete v tématu [ATLTRACE2](#atltrace2) . ATLTRACE a ATLTRACE2 mají stejné chování, ale ATLTRACE je zahrnutá z důvodu zpětné kompatibility.

##  <a name="atltrace2"></a>ATLTRACE2

Hlásí upozornění na výstupní zařízení, jako je například okno ladicího programu, podle uvedených příznaků a úrovní.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Parametry

*oček*<br/>
pro Řetězec, který má být odeslán do okna výstup nebo do jakékoli aplikace, která tyto zprávy zachytávání.

*kategorií*<br/>
pro Typ události nebo metody, na které se má sestava nahlásit Seznam kategorií naleznete v tématu poznámky.

*obsah*<br/>
pro Úroveň trasování pro sestavu. Podrobnosti najdete v poznámkách.

*lpszFormat*<br/>
pro Formátovací řetězec ve stylu `printf`, který se použije k vytvoření řetězce pro odeslání na zařízení s výpisem paměti.

### <a name="remarks"></a>Poznámky

Krátká forma ATLTRACE2 zapisuje řetězec do okna výstupu ladicího programu. Druhá forma ATLTRACE2 také zapisuje výstup do okna výstupu ladicího programu, ale podléhá nastavení trasovacího nástroje ATL/MFC (viz [Ukázka ATLTraceTool](../../overview/visual-cpp-samples.md)). Například pokud nastavíte *úroveň* na 4 a trasovací nástroj ATL/MFC na úroveň 0, zpráva se nezobrazí. *úroveň* může být 0, 1, 2, 3 nebo 4. Výchozí hodnota 0 hlásí pouze nejzávažnější problémy.

Parametr *Category* obsahuje seznam příznaků trasování, které mají být nastaveny. Tyto příznaky odpovídají typům metod, pro které chcete vykázat. Následující tabulky obsahují seznam platných příznaků trasování, které můžete použít pro parametr *Category* .

### <a name="atl-trace-flags"></a>Příznaky trasování ATL

|Kategorie ATL|Popis|
|------------------|-----------------|
|`atlTraceGeneral`|Sestavy všech aplikací ATL. Výchozí nastavení|
|`atlTraceCOM`|Sestavy metod modelu COM.|
|`atlTraceQI`|Oznamuje volání QueryInterface.|
|`atlTraceRegistrar`|Oznamuje registraci objektů.|
|`atlTraceRefcount`|Sestavy týkající se změny počtu odkazů|
|`atlTraceWindowing`|Sestavy pro metody Windows; například hlásí neplatné ID mapy zprávy.|
|`atlTraceControls`|Sestavy ovládacích prvků; například sestavy při zničení ovládacího prvku nebo jeho okna.|
|`atlTraceHosting`|Sestavy hostující zprávy; například sestavy, když je aktivován klient v kontejneru.|
|`atlTraceDBClient`|Sestavy o OLE DB šabloně spotřebitele; například když volání GetData selžou, výstup může obsahovat HRESULT.|
|`atlTraceDBProvider`|Sestavy pro šablonu poskytovatele OLE DB; například sestavy, pokud se nepovedlo vytvořit sloupec.|
|`atlTraceSnapin`|Sestavy pro aplikaci modulu snap-in konzoly MMC.|
|`atlTraceNotImpl`|Oznamuje, že uvedená funkce není implementovaná.|
|`atlTraceAllocation`|Oznamuje zprávy vytisknuté nástroji pro ladění paměti v atldbgmem. h.|

### <a name="mfc-trace-flags"></a>Příznaky trasování knihovny MFC

|MFC – kategorie|Popis|
|------------------|-----------------|
|`traceAppMsg`|Obecné účely, zprávy MFC. Doporučuje se vždycky.|
|`traceDumpContext`|Zprávy z [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Zprávy z kódu zpracování zpráv knihovny MFC.|
|`traceMemory`|Zprávy z kódu správy paměti knihovny MFC.|
|`traceCmdRouting`|Zprávy z kódu směrování příkazů MFC systému Windows.|
|`traceHtml`|Zprávy z podpory dialogového okna DHTML knihovny MFC.|
|`traceSocket`|Zprávy z podpory soketů knihovny MFC.|
|`traceOle`|Zprávy z knihovny MFC podporují technologii OLE.|
|`traceDatabase`|Zprávy z podpory databáze knihovny MFC.|
|`traceInternet`|Zprávy z MFC podpory pro Internet.|

Chcete-li deklarovat vlastní kategorii trasování, Deklarujte globální instanci třídy `CTraceCategory` následujícím způsobem:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Název kategorie, MY_CATEGORY v tomto příkladu, je název, který zadáte do parametru *Category* . První parametr je název kategorie, který se zobrazí v trasovacím nástroji ATL nebo MFC. Druhým parametrem je výchozí úroveň trasování. Tento parametr je nepovinný a výchozí úroveň trasování je 0.

Použití uživatelsky definované kategorie:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Chcete-li určit, že chcete filtrovat zprávy trasování, vložte definice pro tato makra do souboru stdafx. h před příkazem `#include <atlbase.h>`.

Případně můžete nastavit filtr v direktivách preprocesoru v dialogovém okně **stránky vlastností** . Klikněte na kartu **preprocesor** a poté vložte globální do pole upravit **Definice preprocesoru** .

Atlbase. h obsahuje výchozí definice maker ATLTRACE2 a tyto definice budou použity, pokud tyto symboly nedefinujete před zpracováním atlbase. h.

V sestavení vydaných verzí se ATLTRACE2 zkompiluje do `(void) 0`.

ATLTRACE2 omezuje obsah řetězce, který se má odeslat do zařízení s výpisem paměti, aby po formátování nepřesahoval více než 1023 znaků.

ATLTRACE a ATLTRACE2 mají stejné chování, ale ATLTRACE je zahrnutá z důvodu zpětné kompatibility.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)<br/>
[Globální funkce ladění a hlášení chyb](../../atl/reference/debugging-and-error-reporting-global-functions.md)
