---
title: Diagnostické služby
ms.date: 11/04/2016
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
ms.openlocfilehash: 8db12a73d64641a52fea3056de8ab3180c9239b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365797"
---
# <a name="diagnostic-services"></a>Diagnostické služby

Knihovna tříd Microsoft Foundation poskytuje mnoho diagnostických služeb, které usnadňují ladění programů. Tyto diagnostické služby zahrnují makra a globální funkce, které umožňují sledovat přidělení paměti programu, vypisovat obsah objektů za běhu a tisknout ladicí zprávy za běhu. Makra a globální funkce diagnostických služeb jsou seskupeny do následujících kategorií:

- Obecná diagnostická makra

- Obecné diagnostické funkce a proměnné

- Funkce diagnostiky objektů

Tato makra a funkce jsou k `CObject` dispozici pro všechny třídy odvozené z ladicí a vydané verze knihovny MFC. Však všechny kromě DEBUG_NEW a verify nedělat nic ve verzi vydání.

V knihovně ladění jsou všechny bloky přidělené paměti v závorkách s řadou "guard bajtů". Pokud jsou tyto bajty narušeny zápisem chybující paměti, pak diagnostické rutiny mohou nahlásit problém. Pokud zahrnete řádek:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

v souboru implementace budou všechna volání **nového** ukládat název souboru a číslo řádku, kde došlo k přidělení paměti. Funkce [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) zobrazí tyto další informace, což vám umožní identifikovat nevracení paměti. Naleznete také třídy [CDumpContext](../../mfc/reference/cdumpcontext-class.md) další informace o diagnostický výstup.

Kromě toho knihovna run-time C také podporuje sadu diagnostických funkcí, které můžete použít k ladění aplikací. Další informace naleznete v tématu [Ladění rutiny](../../c-runtime-library/debug-routines.md) v referenční knihovně run-time.

### <a name="mfc-general-diagnostic-macros"></a>Obecná diagnostická makra knihovny MFC

|||
|-|-|
|[Assert](#assert)|Vytiskne zprávu a potom přeruší program, pokud zadaný výraz vyhodnotí na FALSE v ladicí verzi knihovny.|
|[ASSERT_KINDOF](#assert_kindof)|Testuje, že objekt je objekt zadané třídy nebo třídy odvozené od zadané třídy.|
|[ASSERT_VALID](#assert_valid)|Testuje vnitřní platnost objektu voláním `AssertValid` jeho členské funkce; obvykle přepsána `CObject`z .|
|[DEBUG_NEW](#debug_new)|Poskytuje název souboru a číslo řádku pro všechna přidělení objektů v režimu ladění, které pomáhají najít nevracení paměti.|
|[DEBUG_ONLY](#debug_only)|Podobně jako ASSERT, ale netestuje hodnotu výrazu; užitečné pro kód, který by měl být spuštěn pouze v režimu ladění.|
|[ZAJISTIT a ENSURE_VALID](#ensure)|Slouží k ověření správnosti dat.|
|[THIS_FILE](#this_file)|Rozbalí se na název souboru, který je kompilován.|
|[Trasování](#trace)|Poskytuje `printf`-like schopnost v ladicí verzi knihovny.|
|[Ověřit](#verify)|Podobně jako ASSERT, ale vyhodnocuje výraz ve verzi vydání knihovny, stejně jako v ladicí verzi.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Obecné diagnostické proměnné a funkce knihovny MFC

|||
|-|-|
|[afxDump](#afxdump)|Globální proměnná, která odesílá informace [CDumpContext](../../mfc/reference/cdumpcontext-class.md) do výstupního okna ladicího programu nebo do terminálu ladění.|
|[afxMemDF](#afxmemdf)|Globální proměnná, která řídí chování alokátoru ladící paměti.|
|[AfxCheckError](#afxcheckerror)|Globální proměnná slouží k testování prošel SCODE zjistit, zda je chyba a pokud ano, vyvolá příslušnou chybu.|
|[Paměť AfxCheck](#afxcheckmemory)|Zkontroluje integritu všech aktuálně přidělené paměti.|
|[AfxDebugBreak](#afxdebugbreak)|Způsobí přerušení provádění.|
|[AfxDump](#cdumpcontext_in_mfc)|Pokud je volána v ladicím programu, vypisuje stav objektu při ladění.|
|[AfxDump](#afxdump)|Vnitřní funkce, která vypisuje stav objektu při ladění.|
|[AfxDumpStack](#afxdumpstack)|Vygenerujte obrázek aktuálního zásobníku. Tato funkce je vždy propojena staticky.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Povolí výpis nevracení paměti.|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|Zapíná a vypíná sledování paměti.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Ověří, zda byl blok paměti správně přidělen.|
|[AfxIsValidAdresa](#afxisvalidaddress)|Ověří, zda je rozsah adres paměti v mezích programu.|
|[AfxIsValidString](#afxisvalidstring)|Určuje, zda je platný ukazatel na řetězec.|
|[AfxSetAllocHh](#afxsetallochook)|Umožňuje volání funkce při každém přidělení paměti.|

### <a name="mfc-object-diagnostic-functions"></a>Diagnostické funkce objektu knihovny MFC

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|Provádí zadanou funkci `CObject`u všech odvozených tříd, které podporují kontrolu typu za běhu.|
|[AfxDoForAllObjects](#afxdoforallobjects)|Provede zadanou funkci `CObject`u všech odvozených objektů, které byly přiděleny s **new**.|

### <a name="mfc-compilation-macros"></a>Makra kompilace knihovny MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Potlačí upozornění kompilátoru pro použití zastaralé funkce knihovny MFC.|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Potlačí upozornění kompilátoru pro použití zastaralé funkce knihovny MFC.

### <a name="syntax"></a>Syntaxe

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Příklad

Tento ukázkový kód by způsobit upozornění kompilátoru, pokud _AFX_SECURE_NO_WARNINGS nebyly definovány.

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```

```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a>AfxDebugBreak

Volání této funkce způsobit přerušení (v umístění `AfxDebugBreak`volání) při provádění ladicí verze aplikace knihovny MFC.

### <a name="syntax"></a>Syntaxe

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Poznámky

`AfxDebugBreak`nemá žádný vliv ve verzích aplikace knihovny MFC a měl by být odebrán. Tato funkce by měla být použita pouze v aplikacích knihovny MFC. Pomocí verze rozhraní API `DebugBreak`Win32 , způsobit přerušení v aplikacích bez knihovny MFC.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxver_.h

## <a name="assert"></a><a name="assert"></a>Assert

Vyhodnotí jeho argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parametry

*logický výraz*<br/>
Určuje výraz (včetně hodnot ukazatele), který je vyhodnocen jako nenulový nebo 0.

### <a name="remarks"></a>Poznámky

Pokud je výsledek 0, makro vytiskne diagnostickou zprávu a přeruší program. Pokud je podmínka nenulová, neprovede žádnou akci.

Diagnostická zpráva má tvar

`assertion failed in file <name> in line <num>`

kde *název* je název zdrojového souboru a *num* je číslo řádku kontrolního výrazu, který ve zdrojovém souboru selhal.

Ve verzi verze knihovny MFC ASSERT nevyhodnotí výraz a proto nebude přerušit program. Pokud musí být výraz vyhodnocen bez ohledu na prostředí, použijte místo ASSERT makro VERIFY.

> [!NOTE]
> Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

Toto makro tvrdí, že objekt, na který je odkazováno, je objektem zadané třídy nebo je objektem třídy odvozené ze zadané třídy.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název `CObject`odvozené třídy.

*pobjekt*<br/>
Ukazatel na objekt třídy.

### <a name="remarks"></a>Poznámky

Parametr *pobject* by měl být ukazatelem na objekt a může být **const**. Objekt ukázal a třída musí `CObject` podporovat informace o třídě za běhu. Jako příklad, aby `pDocument` bylo zajištěno, že je `CMyDoc` ukazatel na objekt třídy nebo některý z jeho derivátů, můžete kód:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

Použití `ASSERT_KINDOF` makra je přesně stejné jako kódování:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Tato funkce funguje pouze pro třídy deklarované s [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic nebo [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makro.

> [!NOTE]
> Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

Slouží k testování předpokladů o platnosti vnitřního stavu objektu.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parametry

*pObjekt*<br/>
Určuje objekt třídy odvozené `CObject` z třídy, která `AssertValid` má přepsání verze členské funkce.

### <a name="remarks"></a>Poznámky

ASSERT_VALID volá `AssertValid` členskou funkci objektu předanou jako jeho argument.

Ve verzi verze knihovny MFC ASSERT_VALID neprovede žádné funkce. Ve verzi Ladění ověří ukazatel, zkontroluje proti NULL a volá `AssertValid` vlastní členské funkce objektu. Pokud některý z těchto testů selže, zobrazí se výstražná zpráva stejným způsobem jako [ASSERT](#assert).

> [!NOTE]
> Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.

Další informace a příklady naleznete [v tématu Ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>DEBUG_NEW

Pomáhá při hledání nevracení paměti.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Poznámky

Můžete použít DEBUG_NEW všude v programu, který by obvykle použít **nový** operátor přidělit úložiště haldy.

V režimu ladění (když je definován symbol **_DEBUG),** DEBUG_NEW sleduje název souboru a číslo řádku pro každý objekt, který přiděluje. Potom při použití [CMemoryState::DumpAllObjectsVzhled členské](cmemorystate-structure.md#dumpallobjectssince) funkce, každý objekt přidělený s DEBUG_NEW je zobrazen s názvem souboru a číslo řádku, kde byl přidělen.

Chcete-li použít DEBUG_NEW, vložte do zdrojových souborů následující direktivu:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Po vložení této směrnice preprocesor vloží DEBUG_NEW všude, kde použijete **nové**, a knihovna MFC provede zbytek. Při kompilaci vydané verze programu DEBUG_NEW překládá na jednoduchou **novou** operaci a nejsou generovány informace o názvu souboru a čísle řádku.

> [!NOTE]
> V předchozích verzích knihovny MFC (4.1 `#define` a starší) jste potřebovali vložit příkaz za všechny příkazy, které volaly IMPLEMENT_DYNCREATE nebo IMPLEMENT_SERIAL makra. To už není nutné.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

V režimu ladění (když je definován symbol **_DEBUG),** DEBUG_ONLY vyhodnotí jeho argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Poznámky

V sestavení verze DEBUG_ONLY nevyhodnotí jeho argument. To je užitečné, pokud máte kód, který by měl být spuštěn pouze v sestaveníladění.

Makro DEBUG_ONLY je ekvivalentní okolnímu `#endif` *výrazu* s `#ifdef _DEBUG` a .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>ZAJISTIT a ENSURE_VALID

Slouží k ověření správnosti dat.

### <a name="syntax"></a>Syntaxe

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parametry

*logický výraz*<br/>
Určuje logický výraz, který má být testován.

### <a name="remarks"></a>Poznámky

Účelem těchto maker je zlepšit validaci parametrů. Makra brání dalšímu zpracování nesprávných parametrů v kódu. Na rozdíl od maker ASSERT, zajistit makra vyvolat výjimku kromě generování kontrolního výrazu.

Makra se chovají dvěma způsoby podle konfigurace projektu. Makra volání ASSERT a potom vyvolat výjimku, pokud se kontrolní výraz nezdaří. Proto v konfiguracích ladění (to znamená, kde je definována _DEBUG) makra vytvoří kontrolní výraz a výjimku, zatímco v konfiguracích verze makra vytvoří pouze výjimku (ASSERT nevyhodnocuje výraz v konfiguracích vydání).

Makro ENSURE_ARG se chová jako makro ZAJISTIT.

ENSURE_VALID volá makro ASSERT_VALID (což má vliv pouze v sestaveních ladění). Kromě toho ENSURE_VALID vyvolá výjimku, pokud je ukazatel NULL. Test NULL se provádí v konfiguraci ladění i vydání.

Pokud některý z těchto testů selže, zobrazí se výstražná zpráva stejným způsobem jako ASSERT. Makro v případě potřeby vyvolá neplatnou výjimku argumentu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

Rozbalí se na název souboru, který je kompilován.

### <a name="syntax"></a>Syntaxe

```
THIS_FILE
```

### <a name="remarks"></a>Poznámky

Informace jsou používány makry ASSERT a VERIFY. Průvodce aplikací a průvodci kódem umístí makro do souborů zdrojového kódu, které vytvoří.

### <a name="example"></a>Příklad

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="trace"></a><a name="trace"></a>Trasování

Odešle zadaný řetězec do ladicího programu aktuální aplikace.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Poznámky

Popis trace naleznete [v atltrace2.](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) TRACE a ATLTRACE2 mají stejné chování.

V ladicí verzi knihovny MFC toto makro odešle zadaný řetězec ladicímu programu aktuální aplikace. V sestavení verze se toto makro zkompiluje k ničemu (žádný kód není generován vůbec).

Další informace naleznete [v tématu Ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="verify"></a><a name="verify"></a>Ověřit

V ladicí verzi knihovny MFC vyhodnotí jeho argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parametry

*logický výraz*<br/>
Určuje výraz (včetně hodnot ukazatele), který je vyhodnocen jako nenulový nebo 0.

### <a name="remarks"></a>Poznámky

Pokud je výsledek 0, makro vytiskne diagnostickou zprávu a zastaví program. Pokud je podmínka nenulová, neprovede žádnou akci.

Diagnostická zpráva má tvar

`assertion failed in file <name> in line <num>`

kde *název* je název zdrojového souboru a *num* je číslo řádku kontrolního výrazu, který ve zdrojovém souboru selhal.

Ve verzi verze knihovny MFC verify vyhodnotí výraz, ale nevytiskne ani nepřeruší program. Například pokud je výraz volání funkce, bude provedeno volání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext v knihovně MFC)

Poskytuje základní možnosti ukládání objektů ve vaší aplikaci.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Poznámky

`afxDump`je předdefinovaný objekt [CDumpContext,](../../mfc/reference/cdumpcontext-class.md) který `CDumpContext` umožňuje odesílat informace do výstupního okna ladicího programu nebo do terminálu ladění. Obvykle zadáte `afxDump` jako parametr . `CObject::Dump`

V systému Windows NT a `afxDump` všechny verze systému Windows výstup je odeslán do okna Výstup-ladění Visual C++ při ladění aplikace.

Tato proměnná je definována pouze v ladicí verzi knihovny MFC. Další informace `afxDump`naleznete v tématu [Ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump (interní)

Interní funkce, která používá knihovny MFC k výpisu stavu objektu při ladění.

### <a name="syntax"></a>Syntaxe

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Ukazatel na objekt třídy odvozené `CObject`z aplikace .

### <a name="remarks"></a>Poznámky

`AfxDump`volá člennou `Dump` funkci objektu a odesílá informace `afxDump` do umístění určeného proměnnou. `AfxDump`je k dispozici pouze v ladicí verzi knihovny MFC.

Programový kód by `AfxDump`neměl volat , `Dump` ale měl by místo toho volat členská funkce příslušného objektu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>afxMemDF

Tato proměnná je přístupná z ladicího programu nebo programu a umožňuje optimalizovat diagnostiku přidělení.

```
int  afxMemDF;
```

### <a name="remarks"></a>Poznámky

`afxMemDF`může mít následující hodnoty určené ve `afxMemDF`výčtu :

- `allocMemDF`Zapne ladění přidělování (výchozí nastavení v knihovně ladění).

- `delayFreeMemDF`Zpožďuje uvolnění paměti. Zatímco váš program uvolní blok paměti, alokátor nevrátí tuto paměť do základního operačního systému. To bude klást maximální napětí paměti na váš program.

- `checkAlwaysMemDF`Volání `AfxCheckMemory` pokaždé, když je přidělena nebo uvolněna paměť. To výrazně zpomalí přidělení paměti a deallocations.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError

Tato funkce testuje předané SCODE, chcete-li zjistit, zda se jedná o chybu.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Poznámky

Pokud se jedná o chybu, funkce vyvolá výjimku. Pokud je E_OUTOFMEMORY předaný Kód SCODE, funkce vyvolá [cmemoryexception](../../mfc/reference/cmemoryexception-class.md) voláním [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Jinak funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md) voláním [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Tuto funkci lze použít ke kontrole vrácených hodnot volání funkcí OLE ve vaší aplikaci. Testováním vrácené hodnoty s touto funkcí v aplikaci můžete správně reagovat na chybové stavy s minimálním množstvím kódu.

> [!NOTE]
> Tato funkce má stejný účinek v ladění a neladivací sestavení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>Paměť AfxCheck

Tato funkce ověřuje fond volné paměti a vytiskne chybové zprávy podle potřeby.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud žádné chyby paměti; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud funkce nezjistí žádné poškození paměti, nevytiskne nic.

Všechny bloky paměti aktuálně přidělené na haldě jsou kontrolovány, včetně těch, které jsou přiděleny **novými,** ale nikoli těmi, `GlobalAlloc` které jsou přiděleny přímými voláními podkladovým alokátorům paměti, jako je například funkce **malloc** nebo funkce systému Windows. Pokud je některý blok nalezen poškozený, je na výstupu ladicího programu vytištěna zpráva.

Pokud zahrnete řádek

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

v programovém modulu, `AfxCheckMemory` pak následné volání zobrazit název souboru a číslo řádku, kde byla přidělena paměť.

> [!NOTE]
> Pokud modul obsahuje jednu nebo více implementací serializovatelných `#define` tříd, je nutné umístit řádek za poslední IMPLEMENT_SERIAL volání makra.

Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump (Knihovna MFC)

Volání této funkce v ladicím programu vypisuje stav objektu při ladění.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Ukazatel na objekt třídy odvozené `CObject`z aplikace .

### <a name="remarks"></a>Poznámky

`AfxDump`volá člennou `Dump` funkci objektu a odesílá informace `afxDump` do umístění určeného proměnnou. `AfxDump`je k dispozici pouze v ladicí verzi knihovny MFC.

Programový kód by `AfxDump`neměl volat , `Dump` ale měl by místo toho volat členská funkce příslušného objektu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack

Tuto globální funkci lze použít ke generování bitové kopie aktuálního zásobníku.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dwCíl*<br/>
Označuje cíl výstupu výpisu. Možné hodnoty, které lze kombinovat pomocí operátoru BITWISE-OR ( **&#124;), **jsou následující:

- AFX_STACK_DUMP_TARGET_TRACE Odešle výstup pomocí makro [TRACE.](#trace) Makro TRACE generuje výstup pouze v sestaveních ladění. generuje žádný výstup v sestavení verze. Trace lze také přesměrovat na jiné cíle kromě ladicího programu.

- AFX_STACK_DUMP_TARGET_DEFAULT Odešle výstup výpisu na výchozí cíl. Pro sestavení ladění výstup přejde do makro TRACE. V sestavení verze výstup přejde do schránky.

- AFX_STACK_DUMP_TARGET_CLIPBOARD Odešle výstup pouze do schránky. Data jsou umístěna ve schránce jako prostý text ve formátu CF_TEXT schránky.

- AFX_STACK_DUMP_TARGET_BOTH Odešle výstup do schránky a do makra TRACE současně.

- AFX_STACK_DUMP_TARGET_ODS Odešle výstup přímo do ladicího programu `OutputDebugString()`pomocí funkce Win32 . Tato možnost bude generovat výstup ladicího programu v ladění a vydání sestavení při ladicí program je připojen k procesu. AFX_STACK_DUMP_TARGET_ODS vždy dosáhne ladicího programu (pokud je připojen) a nelze jej přesměrovat.

### <a name="remarks"></a>Poznámky

Následující příklad odráží jeden řádek výstupu generovaného `AfxDumpStack` voláním z obslužné rutiny tlačítka v aplikaci dialogového okna knihovny MFC:

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

Každý řádek ve výše uvedeném výstupu označuje adresu posledního volání funkce, úplný název cesty modulu, který obsahuje volání funkce, a prototyp funkce. Pokud volání funkce v zásobníku nedojde na přesnou adresu funkce, je zobrazen posun bajtů.

Například následující tabulka popisuje první řádek výše uvedeného výstupu:

|Výstup|Popis|
|------------|-----------------|
|`00427D55:`|Zpáteční adresa posledního volání funkce.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Úplný název cesty modulu, který obsahuje volání funkce.|
|`void AfxDumpStack(unsigned long)`|Volán prototyp funkce.|
|`+ 181 bytes`|Posun v bajtů od adresy prototypu funkce (v tomto případě `void AfxDumpStack(unsigned long)`) na `00427D55`zpáteční adresu (v tomto případě).|

`AfxDumpStack`je k dispozici v ladicích a neladivěných verzích knihoven knihovny MFC. funkce je však vždy propojena staticky, i když spustitelný soubor používá knihovnu MFC ve sdílené knihovně DLL. V implementacích sdílené knihovny se funkce nachází v knihovně MFCS42. knihovna LIB (a její varianty).

Úspěšné použití této funkce:

- Soubor IMAGEHLP. DLL musí být na vaší cestě. Pokud tuto dll nemají, funkce zobrazí chybovou zprávu. Informace o sadě funkcí, kterou poskytuje imagehlp, naleznete v [knihovně nápovědy](/windows/win32/Debug/image-help-library) k obrázkům.

- Moduly, které mají rámce v zásobníku musí obsahovat informace o ladění. Pokud neobsahují informace o ladění, funkce bude stále generovat trasování zásobníku, ale trasování bude méně podrobné.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Povolí a zakáže výpis nevracení paměti v AFX_DEBUG_STATE destruktoru.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parametry

*bDump*<br/>
[v] Pravda označuje, že výpis nevracení paměti je povolen; NEPRAVDA označuje, že výpis nevracení paměti je zakázán.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota pro tento příznak.

### <a name="remarks"></a>Poznámky

Když aplikace uvolní knihovnu knihovny MFC, knihovna knihovny Knihovny MFC zkontroluje nevracení paměti. V tomto okamžiku všechny nevracení paměti jsou hlášeny uživateli prostřednictvím okna **ladění** sady Visual Studio.

Pokud aplikace načte jinou knihovnu před knihovnou knihovny Knihovny MFC, některé přidělení paměti v této knihovně budou nesprávně hlášeny jako nevracení paměti. Nevracení falešné paměti může způsobit, že se aplikace pomalu zavře, jak je hlásí knihovna knihovny Knihovny MFC. V tomto případě `AfxEnableMemoryLeakDump` slouží k zakázání výpisu nevracení paměti.

> [!NOTE]
> Pokud použijete tuto metodu k vypnutí výpisu nevracení paměti, nebudete dostávat zprávy o platné nevracení paměti v aplikaci. Tuto metodu byste měli použít pouze v případě, že jste si jisti, že sestava nevracení paměti obsahuje nevracení nepaměti.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking

Sledování diagnostické paměti je obvykle povoleno v ladicí verzi knihovny MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parametry

*bSledovat*<br/>
Nastavení této hodnoty na hodnotu PRAVDA zapne sledování paměti. FALSE jej vypne.

### <a name="return-value"></a>Návratová hodnota

Předchozí nastavení příznaku povolení sledování.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete zakázat sledování v částech kódu, o kterých víte, že přidělují bloky správně.

Další informace `AfxEnableMemoryTracking`naleznete v tématu [Ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock

Testuje adresu paměti a ujistěte se, že představuje aktuálně aktivní blok paměti, který byl přidělen diagnostickou verzí **new**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Ukazuje na blok paměti, který má být testován.

*nBajtu bajtů*<br/>
Obsahuje délku bloku paměti v bajtů.

*číslo žádosti*<br/>
Odkazuje na **dlouhé** celé číslo, které bude vyplněno pořadovým číslem přidělení bloku paměti nebo nula, pokud nepředstavuje aktuálně aktivní blok paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je blok paměti aktuálně přidělen a délka je správná; jinak 0.

### <a name="remarks"></a>Poznámky

Také zkontroluje zadanou velikost proti původní přidělené velikosti. Pokud funkce vrátí nenulovou hodnotu, je pořadové číslo přidělení vráceno v *plRequestNumber*. Toto číslo představuje pořadí, ve kterém byl blok přidělen vzhledem ke všem ostatním **novým** přidělením.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAdresa

Testuje všechny adresy paměti, aby bylo zajištěno, že je obsažena zcela v paměťovém prostoru programu.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Odkazuje na adresu paměti, která má být testována.

*nBajtu bajtů*<br/>
Obsahuje počet bajtů paměti, které mají být testovány.

*bReadWrite*<br/>
Určuje, zda je paměť pro čtení a zápis (TRUE) nebo pouze pro čtení (FALSE).

### <a name="return-value"></a>Návratová hodnota

V sestavení chodu nenulová, pokud je zadaný blok paměti obsažen zcela v paměťovém prostoru programu; jinak 0.

V sestaveních bez ladění nenulová, pokud *lp* není NULL; jinak 0.

### <a name="remarks"></a>Poznámky

Adresa není omezena na bloky přidělené **novým**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString

Tato funkce slouží k určení, zda je platný ukazatel na řetězec.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Ukazatel na test.

*nDélka*<br/>
Určuje délku řetězce, který má být testován v bajtech. Hodnota -1 označuje, že řetězec bude ukončen a null.

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění, nenulová, pokud zadaný ukazatel odkazuje na řetězec zadané velikosti; jinak 0.

V sestaveních bez ladění nenulová, pokud *lpsz* není NULL; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHh

Nastaví háček, který umožňuje volání zadané funkce před přidělením každého bloku paměti.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parametry

*pfnAllocHook*<br/>
Určuje název funkce, kterou chcete volat. Viz poznámky pro prototyp alokační funkce.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud chcete povolit přidělení; jinak 0.

### <a name="remarks"></a>Poznámky

Alokátor ladění paměti knihovny tříd microsoft foundation může volat uživatelem definovanou funkci zavěšení, která uživateli umožňuje sledovat přidělení paměti a řídit, zda je přidělení povoleno. Funkce alokačního háku jsou prototypovány takto:

**BOOL AFXAPI AllocHook( size_t** `nSize` **, BOOL** `bObject` **, LONG);** `lRequestNumber` **);**

*nVelikost*<br/>
Velikost navrhované přidělení paměti.

*bObjekt*<br/>
TRUE, pokud je `CObject`přidělení pro odvozený objekt; jinak FALSE.

*lČíslo požadavku*<br/>
Pořadové číslo přidělení paměti.

Všimněte si, že konvence volání AFXAPI znamená, že volaný musí odebrat parametry ze zásobníku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses

Volá zadanou funkci iterace `CObject`pro všechny serializovatelné odvozené třídy v paměťovém prostoru aplikace.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*Pfn*<br/>
Odkazuje na iterace funkce, která má být volána pro každou třídu. Argumenty funkce jsou ukazatel `CRuntimeClass` na objekt a ukazatel void na další data, která volající poskytuje funkci.

*pKontext*<br/>
Odkazuje na volitelná data, která volající může zadat do funkce iterace. Tento ukazatel může být NULL.

### <a name="remarks"></a>Poznámky

Serializovatelné `CObject`odvozené třídy jsou třídy odvozené pomocí DECLARE_SERIAL makro. Ukazatel, který je `AfxDoForAllClasses` předán v *pContext* je předán a zadané iterace funkce pokaždé, když je volána.

> [!NOTE]
> Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects

Provede zadanou funkci iterace pro `CObject` všechny objekty odvozené z nich, které byly přiděleny s **new**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*Pfn*<br/>
Odkazuje na iterace funkce spustit pro každý objekt. Argumenty funkce jsou ukazatel `CObject` na a a void ukazatel na další data, která volající poskytuje funkci.

*pKontext*<br/>
Odkazuje na volitelná data, která volající může zadat do funkce iterace. Tento ukazatel může být NULL.

### <a name="remarks"></a>Poznámky

Stack, globální nebo vložené objekty nejsou výčtu. Ukazatel předaný `AfxDoForAllObjects` v *pContext* je předán zadané iterace funkce pokaždé, když je volána.

> [!NOTE]
> Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
