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
ms.openlocfilehash: 6880a6a3d25738bd0480168902044530d06f7e7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446214"
---
# <a name="diagnostic-services"></a>Diagnostické služby

Knihovna Microsoft Foundation Class poskytuje spoustu diagnostických služeb, které usnadňují ladění vašich programů. Tyto diagnostické služby zahrnují makra a globální funkce, které vám umožňují sledovat přidělení paměti programu, vypsat obsah objektů za běhu a tisknout zprávy ladění během běhu. Makra a globální funkce pro diagnostické služby jsou seskupené do následujících kategorií:

- Obecná diagnostická makra

- Obecné diagnostické funkce a proměnné

- Funkce diagnostiky objektů

Tato makra a funkce jsou k dispozici pro všechny třídy, které jsou odvozeny z `CObject` ve verzích ladění a vydání knihovny MFC. Všechny kromě DEBUG_NEW a ověření ale nedělají nic ve vydané verzi.

V knihovně ladění jsou všechny přidělené paměťové bloky v závorkách s řadou "Guard bajty". Pokud jsou tyto bajty vyrušovány zápisem do paměti errant, diagnostické rutiny mohou nahlásit problém. Pokud zadáte řádek:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

v souboru implementace všechna volání do **nového** uloží název souboru a číslo řádku, kde došlo k přidělení paměti. Funkce [CMemoryState::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) zobrazí tyto další informace, které vám umožní identifikovat nevracení paměti. Další informace o diagnostických výstupech naleznete v tématu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) třídy.

Kromě toho knihovna run-time jazyka C také podporuje sadu diagnostických funkcí, které můžete použít k ladění aplikací. Další informace naleznete v tématu [rutiny ladění](../../c-runtime-library/debug-routines.md) v referenci knihovny run-time.

### <a name="mfc-general-diagnostic-macros"></a>Obecná diagnostická makra MFC

|||
|-|-|
|[UPLATŇUJE](#assert)|Vytiskne zprávu a přeruší program, pokud se zadaný výraz vyhodnotí jako FALSE v ladicí verzi knihovny.|
|[ASSERT_KINDOF](#assert_kindof)|Testuje, zda je objekt objektem zadané třídy nebo třídy odvozené ze zadané třídy.|
|[ASSERT_VALID](#assert_valid)|Testuje vnitřní platnost objektu voláním jeho členské funkce `AssertValid`; obvykle přepsáno z `CObject`.|
|[DEBUG_NEW](#debug_new)|Poskytuje název souboru a číslo řádku pro všechny alokace objektů v režimu ladění, aby bylo možné najít nevracení paměti.|
|[DEBUG_ONLY](#debug_only)|Podobný jako ASSERT, ale netestuje hodnotu výrazu; užitečné pro kód, který by se měl spustit pouze v režimu ladění.|
|[Zajistěte a ENSURE_VALID](#ensure)|Slouží k ověření správnosti dat.|
|[THIS_FILE](#this_file)|Rozbalí se na název souboru, který se kompiluje.|
|[Přehled](#trace)|Poskytuje funkce podobné `printf`v ladicí verzi knihovny.|
|[OVĚŘÍTE](#verify)|Podobný jako ASSERT, ale vyhodnotí výraz v prodejní verzi knihovny i v ladicí verzi.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Obecné diagnostické proměnné a funkce knihovny MFC

|||
|-|-|
|[afxDump](#afxdump)|Globální proměnná, která odesílá informace o [CDumpContext](../../mfc/reference/cdumpcontext-class.md) do okna výstupu ladicího programu nebo do ladicího terminálu.|
|[afxMemDF](#afxmemdf)|Globální proměnná, která řídí chování modulu ladění paměti ladění.|
|[AfxCheckError](#afxcheckerror)|Globální proměnná slouží k otestování předaných Code, aby bylo možné zjistit, zda se jedná o chybu, a pokud ano, vyvolá příslušnou chybu.|
|[AfxCheckMemory](#afxcheckmemory)|Kontroluje integritu veškeré aktuálně přidělené paměti.|
|[AfxDebugBreak](#afxdebugbreak)|Způsobí přerušení provádění.|
|[AfxDump](#cdumpcontext_in_mfc)|Pokud je volána v ladicím programu, vypíše stav objektu při ladění.|
|[AfxDump](#afxdump)|Vnitřní funkce, která při ladění vypíše stav objektu.|
|[AfxDumpStack](#afxdumpstack)|Vygeneruje obraz aktuálního zásobníku. Tato funkce je vždy propojena staticky.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Povoluje výpis nevracení paměti.|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|Zapne nebo vypne sledování paměti.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Ověřuje, zda byl blok paměti správně přidělen.|
|[AfxIsValidAddress](#afxisvalidaddress)|Ověřuje, že rozsah adres paměti spadá do hranic programu.|
|[AfxIsValidString](#afxisvalidstring)|Určuje, zda je ukazatel na řetězec platný.|
|[AfxSetAllocHook](#afxsetallochook)|Povoluje volání funkce při každém přidělení paměti.|

### <a name="mfc-object-diagnostic-functions"></a>Diagnostické funkce objektů MFC

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|Provede zadanou funkci na všech třídách odvozených od `CObject`, které podporují kontrolu typu run-time.|
|[AfxDoForAllObjects](#afxdoforallobjects)|Provede zadanou funkci na všech objektech odvozených od `CObject`, které byly přiděleny s **novým**.|

### <a name="mfc-compilation-macros"></a>Makra kompilace MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Potlačí upozornění kompilátoru pro použití zastaralých funkcí MFC.|

## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Potlačí upozornění kompilátoru pro použití zastaralých funkcí MFC.

### <a name="syntax"></a>Syntaxe

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Příklad

Tato ukázka kódu způsobí upozornění kompilátoru, pokud _AFX_SECURE_NO_WARNINGS nebyly definovány.

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

## <a name="afxdebugbreak"></a>AfxDebugBreak

Voláním této funkce dojde k přerušení (v umístění volání `AfxDebugBreak`) při provádění ladicí verze vaší aplikace MFC.

### <a name="syntax"></a>Syntaxe

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Poznámky

`AfxDebugBreak` nemá žádný vliv na vydané verze aplikace MFC a měla by být odebrána. Tato funkce by měla být použita pouze v aplikacích MFC. Použijte verzi Win32 API `DebugBreak`, chcete-li způsobit přerušení v aplikacích, které nejsou součástí knihovny MFC.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxver_. h

##  <a name="assert"></a>UPLATŇUJE

Vyhodnotí svůj argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Určuje výraz (včetně hodnot ukazatelů), které se vyhodnotí jako nenulové nebo 0.

### <a name="remarks"></a>Poznámky

Pokud je výsledek 0, makro vytiskne diagnostickou zprávu a program přeruší. Pokud je podmínka nenulová, neprovede nic.

Diagnostická zpráva má tvar

`assertion failed in file <name> in line <num>`

kde *název* *je název zdrojového souboru a číslo* řádku kontrolního výrazu, který selhal ve zdrojovém souboru.

V vydané verzi knihovny MFC nevyhodnocují výrazy ASSERT výraz, takže program nebude přerušen. Pokud je nutné vyhodnotit výraz bez ohledu na prostředí, použijte místo KONTROLNÍho výrazu makro VERIFY.

> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="assert_kindof"></a>ASSERT_KINDOF

Toto makro vyhodnotí, že objekt odkazoval na je objekt zadané třídy, nebo je objekt třídy odvozené ze zadané třídy.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parametry

*NázevTřídy*<br/>
Název třídy odvozené od `CObject`.

*pobject*<br/>
Ukazatel na objekt třídy.

### <a name="remarks"></a>Poznámky

Parametr *pObject* by měl být ukazatel na objekt a může být **const**. Objekt, na který ukazuje, a třída musí podporovat `CObject` běhové informace třídy. Jako příklad, aby bylo zajištěno, že `pDocument` je ukazatel na objekt `CMyDoc` třídy nebo jakýkoli z jeho derivátů, můžete kód:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

Použití makra `ASSERT_KINDOF` je přesně stejné jako kódování:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Tato funkce funguje pouze pro třídy deklarované s makrem [DECLARE_DYNAMIC] (Run-Time-Object-Model-Services. MD # declare_dynamic nebo [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="assert_valid"></a>ASSERT_VALID

Použijte k otestování svých předpokladů o platnosti vnitřního stavu objektu.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Určuje objekt třídy odvozené od `CObject`, která má překrytou verzi `AssertValid` členské funkce.

### <a name="remarks"></a>Poznámky

ASSERT_VALID volá členskou funkci `AssertValid` objektu předaného jako argument.

V prodejní verzi knihovny MFC ASSERT_VALID neprovede žádnou akci. V ladicí verzi ověřuje ukazatel, kontroluje proti hodnotě NULL a volá vlastní `AssertValid` členské funkce objektu. Pokud některý z těchto testů neproběhne úspěšně, zobrazí se zpráva s upozorněním stejným způsobem jako [Assert](#assert).

> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.

Další informace a příklady naleznete v tématu [ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="debug_new"></a>DEBUG_NEW

Pomáhá při hledání nevracení paměti.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Poznámky

Můžete použít DEBUG_NEW všude v programu, které byste obvykle použili operátor **New** k přidělení úložiště haldy.

V režimu ladění (je-li definován symbol **_DEBUG** ), DEBUG_NEW sleduje název souboru a číslo řádku pro každý objekt, který přiděluje. Pak při použití členské funkce [CMemoryState::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) se každý objekt přidělený pomocí DEBUG_NEW zobrazí s názvem souboru a číslem řádku, kde byl přidělen.

Pokud chcete použít DEBUG_NEW, vložte do zdrojových souborů následující direktivu:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Po vložení této direktivy bude preprocesor vkládat DEBUG_NEW bez ohledu na to, kde použijete **Nový**, a prostředí MFC zbývající. Když kompilujete verzi programu, DEBUG_NEW se přeloží na jednoduchou **novou** operaci a informace o názvu souboru a řádku se nevygenerují.

> [!NOTE]
>  V předchozích verzích knihovny MFC (4,1 a starší) bylo nutné vložit příkaz `#define` po všech příkazech, které se nazývají makra IMPLEMENT_DYNCREATE nebo IMPLEMENT_SERIAL. To již není nezbytné.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="debug_only"></a>DEBUG_ONLY

V režimu ladění (při definování **_DEBUG** symbol) DEBUG_ONLY vyhodnotí svůj argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Poznámky

V sestavení pro vydání vyDEBUG_ONLY nevyhodnotí svůj argument. To je užitečné, když máte kód, který by měl být proveden pouze v sestavení ladění.

Makro DEBUG_ONLY je ekvivalentem okolního *výrazu* s `#ifdef _DEBUG` a `#endif`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

### <a name="ensure"></a>Zajistěte a ENSURE_VALID

Slouží k ověření správnosti dat.

### <a name="syntax"></a>Syntaxe

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Určuje logický výraz, který se má testovat.

### <a name="remarks"></a>Poznámky

Účelem těchto maker je vylepšit ověřování parametrů. Makra zabraňují dalšímu zpracování nesprávných parametrů ve vašem kódu. Na rozdíl od maker kontrolního výrazu, zajistěte, aby makra zavolaly výjimku kromě generování kontrolního výrazu.

Makra se chovají dvěma způsoby v závislosti na konfiguraci projektu. Makra volají vyhodnocení a poté vyvolávají výjimku, pokud se kontrolní výraz nezdařil. Proto v konfiguracích ladění (to znamená, kde je definována _DEBUG) makra vytvoří kontrolní výraz a výjimku v konfiguraci vydání, makra vyprodukuje pouze výjimku (ASSERT nevyhodnotí výraz v konfiguracích vydané verze).

Makro ENSURE_ARG funguje jako makro zajistěte.

ENSURE_VALID volá makro ASSERT_VALID (které má vliv pouze na sestavení ladění). Kromě toho ENSURE_VALID vyvolá výjimku, pokud má ukazatel hodnotu NULL. Test NULL se provádí v konfiguraci ladění i vydaných verzí.

Pokud některý z těchto testů neproběhne úspěšně, zobrazí se zpráva s upozorněním stejným způsobem jako ASSERT. Makro vyvolá výjimku neplatného argumentu v případě potřeby.
### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

## <a name="this_file"></a>THIS_FILE

Rozbalí se na název souboru, který se kompiluje.

### <a name="syntax"></a>Syntaxe

```
THIS_FILE
```

### <a name="remarks"></a>Poznámky

Tyto informace jsou používány KONTROLNÍm výrazem a OVĚŘUJÍ makra. Průvodce aplikací a průvodci kódem umísťují makro do souborů se zdrojovým kódem, které vytvoří.

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

**Záhlaví:** AFX –. h

##  <a name="trace"></a>Přehled

Odešle zadaný řetězec ladicímu programu aktuální aplikace.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Poznámky

Popis trasování naleznete v tématu [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) . TRASOVÁNÍ a ATLTRACE2 mají stejné chování.

V ladicí verzi knihovny MFC toto makro odešle zadaný řetězec ladicímu programu aktuální aplikace. V buildu pro vydání se toto makro zkompiluje do žádného (není vůbec vygenerován žádný kód).

Další informace naleznete v tématu [ladění aplikací knihovny MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="verify"></a>OVĚŘÍTE

V ladicí verzi knihovny MFC vyhodnocuje svůj argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Určuje výraz (včetně hodnot ukazatelů), které se vyhodnotí jako nenulové nebo 0.

### <a name="remarks"></a>Poznámky

Pokud je výsledek 0, makro vytiskne diagnostickou zprávu a program zastaví. Pokud je podmínka nenulová, neprovede nic.

Diagnostická zpráva má tvar

`assertion failed in file <name> in line <num>`

kde *Name* je název zdrojového souboru a hodnota *NUM* je číslo řádku kontrolního výrazu, který selhal ve zdrojovém souboru.

V prodejní verzi knihovny MFC ověřte, že je výraz vyhodnocen, ale netiskne ani nepřerušil program. Například pokud je výraz volání funkce, bude provedeno volání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext v MFC)

Poskytuje základní objektově-dumpingové možnosti ve vaší aplikaci.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Poznámky

`afxDump` je předdefinovaný objekt [CDumpContext](../../mfc/reference/cdumpcontext-class.md) , který umožňuje odeslat `CDumpContext` informace do okna výstupu ladicího programu nebo do terminálu ladění. Obvykle zadáváte `afxDump` jako parametr pro `CObject::Dump`.

V rámci systému Windows NT a všech verzí systému Windows se `afxDump` výstup odesílá do okna ladění výstupu vizuálu C++ při ladění aplikace.

Tato proměnná je definována pouze v ladicí verzi knihovny MFC. Další informace o `afxDump`naleznete v tématu [DEBUGGING MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

## <a name="afxdump"></a>AfxDump (interní)

Vnitřní funkce, kterou knihovna MFC používá k výpisu stavu objektu při ladění.

### <a name="syntax"></a>Syntaxe

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Ukazatel na objekt třídy odvozené z `CObject`.

### <a name="remarks"></a>Poznámky

`AfxDump` volá členskou funkci objektu `Dump` a odesílá informace do umístění určeného proměnnou `afxDump`. `AfxDump` je k dispozici pouze v ladicí verzi knihovny MFC.

Váš kód programu by neměl volat `AfxDump`, ale měl by místo toho volat členskou funkci `Dump` příslušného objektu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxmemdf"></a>afxMemDF

Tato proměnná je přístupná z ladicího programu nebo programu a umožňuje vyladit diagnostiku přidělení.

```
int  afxMemDF;
```

### <a name="remarks"></a>Poznámky

`afxMemDF` může mít následující hodnoty určené `afxMemDF`výčtu:

- `allocMemDF` zapne Alokátor ladění (výchozí nastavení v knihovně ladění).

- `delayFreeMemDF` zpoždění uvolnění paměti. I když program uvolní blok paměti, Alokátor nevrátí tuto paměť do základního operačního systému. Tím se do programu umístí maximální nároky na paměť.

- `checkAlwaysMemDF` volá `AfxCheckMemory` při každém přidělení nebo uvolnění paměti. Tím dojde k výraznému zpomalení přidělování a navracení paměti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxcheckerror"></a>AfxCheckError

Tato funkce testuje předaný Code, aby bylo možné zjistit, zda se jedná o chybu.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Poznámky

Pokud se jedná o chybu, funkce vyvolá výjimku. Pokud je předaná Code E_OUTOFMEMORY, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) voláním [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). V opačném případě funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md) voláním [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Tato funkce slouží ke kontrole vrácených hodnot volání funkcí OLE ve vaší aplikaci. Otestováním návratové hodnoty pomocí této funkce ve vaší aplikaci můžete správně reagovat na chybové podmínky s minimálním množstvím kódu.

> [!NOTE]
>  Tato funkce má stejný účinek jako sestavení ladění a bez ladění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxcheckmemory"></a>AfxCheckMemory

Tato funkce ověří fond volných paměti a vytiskne chybové zprávy podle potřeby.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud nejsou k dispozici žádné chyby paměti; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud funkce nezjistí poškození paměti, vytiskne se nic.

Jsou zaškrtnuty všechny bloky paměti, které jsou aktuálně přiděleny na haldě, včetně těch, které jsou přiděleny **novým** , ale nikoli těch, které jsou přiděleny přímým voláním pro základní přidělování paměti, jako je **například funkce typu sami nebo funkce Windows** `GlobalAlloc` Pokud je nalezen libovolný blok, zpráva bude vytištěna do výstupu ladicího programu.

Pokud zadáte řádek

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

v modulu programu pak následná volání `AfxCheckMemory` zobrazí název souboru a číslo řádku, kde byla paměť přidělena.

> [!NOTE]
>  Pokud modul obsahuje jednu nebo více implementací serializovatelných tříd, je nutné umístit `#define` řádek za poslední volání makra IMPLEMENT_SERIAL.

Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxdump"></a>AfxDump (MFC)

Voláním této funkce v ladicím programu vypíšete stav objektu během ladění.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Ukazatel na objekt třídy odvozené z `CObject`.

### <a name="remarks"></a>Poznámky

`AfxDump` volá členskou funkci objektu `Dump` a odesílá informace do umístění určeného proměnnou `afxDump`. `AfxDump` je k dispozici pouze v ladicí verzi knihovny MFC.

Váš kód programu by neměl volat `AfxDump`, ale měl by místo toho volat členskou funkci `Dump` příslušného objektu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxdumpstack"></a>AfxDumpStack

Tato globální funkce se dá použít k vygenerování obrázku aktuálního zásobníku.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dwTarget*<br/>
Určuje cíl výstupu výpisu paměti. Možné hodnoty, které lze kombinovat pomocí operátoru bitového operátoru **&#124;** or (), jsou následující:

- AFX_STACK_DUMP_TARGET_TRACE odesílá výstup prostřednictvím makra [Trace](#trace) . Makro TRACE vygeneruje výstup pouze v sestaveních pro ladění; negeneruje žádný výstup pro sestavení vydaných verzí. TRASOVÁNÍ lze také přesměrovat na jiné cíle kromě ladicího programu.

- AFX_STACK_DUMP_TARGET_DEFAULT odešle výstup výpisu paměti do výchozího cíle. Pro sestavení ladění výstup přejde do makra TRACE. V sestavení pro vydání vychází výstup do schránky.

- AFX_STACK_DUMP_TARGET_CLIPBOARD odesílá výstup pouze do schránky. Data jsou umístěna ve schránce jako prostý text pomocí formátu schránky CF_TEXT.

- AFX_STACK_DUMP_TARGET_BOTH odesílá výstup do schránky a do makra TRACE současně.

- AFX_STACK_DUMP_TARGET_ODS odesílá výstup přímo do ladicího programu pomocí funkce Win32 `OutputDebugString()`. Tato možnost vytvoří výstup ladicího programu v sestavení ladění i vydaných verzích, pokud je k procesu připojen ladicí program. AFX_STACK_DUMP_TARGET_ODS vždy přispěje k ladicímu programu (Pokud je připojen) a nelze jej přesměrovat.

### <a name="remarks"></a>Poznámky

Následující příklad odráží jeden řádek výstupu vygenerovaný z volání `AfxDumpStack` z obslužné rutiny tlačítka v aplikaci MFC dialog:

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

Každý řádek ve výstupu výše označuje adresu posledního volání funkce, úplný název cesty modulu, který obsahuje volání funkce, a prototyp funkce s názvem. Pokud volání funkce v zásobníku neproběhne na přesné adrese funkce, je zobrazen posun bajtů.

Například následující tabulka popisuje první řádek výše uvedeného výstupu:

|Výstup|Popis|
|------------|-----------------|
|`00427D55:`|Návratová adresa posledního volání funkce.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Úplný název cesty modulu, který obsahuje volání funkce.|
|`void AfxDumpStack(unsigned long)`|Prototyp funkce se nazývá.|
|`+ 181 bytes`|Posun v bajtech z adresy prototypu funkce (v tomto případě `void AfxDumpStack(unsigned long)`) na zpáteční adresu (v tomto případě `00427D55`).|

`AfxDumpStack` je k dispozici v ladicích a neladicích verzích knihoven MFC; funkce je však vždy propojena staticky, a to i v případě, že spustitelný soubor používá knihovnu MFC ve sdílené knihovně DLL. V implementacích sdílené knihovny se funkce nachází v MFCS42. Knihovna LIB (a její varianty).

Úspěšné použití této funkce:

- Soubor IMAGEHLP. Knihovna DLL musí být ve vaší cestě. Pokud tuto knihovnu DLL nemáte, zobrazí se v této funkci chybová zpráva. Informace o sadě funkcí poskytované rozhraním IMAGEHLP naleznete v tématu [Knihovna nápovědu k imagi](/windows/win32/Debug/image-help-library) .

- Moduly, které mají snímky v zásobníku, musí zahrnovat informace o ladění. Pokud neobsahují informace o ladění, funkce bude stále generovat trasování zásobníku, ale trasování bude méně podrobné.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Povolí nebo zakáže výpis nevracení paměti v destruktoru AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parametry

*bDump*<br/>
pro Hodnota TRUE označuje, že je povolen výpis nevrácené paměti; Hodnota FALSE znamená, že výpis nevrácené paměti je zakázán.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota tohoto příznaku

### <a name="remarks"></a>Poznámky

Když aplikace uvolní knihovnu MFC, knihovna MFC kontroluje nevracení paměti. V tomto okamžiku jsou všechny nevrácené paměti hlášeny uživateli prostřednictvím okna **ladění** aplikace Visual Studio.

Pokud vaše aplikace načte jinou knihovnu před knihovnou MFC, některá přidělení paměti v této knihovně budou nesprávně hlášena jako nevracení paměti. Falešná nevracení paměti může způsobit, že se vaše aplikace bude pomalu zavřít, protože knihovny MFC je hlásí. V takovém případě použijte `AfxEnableMemoryLeakDump` k zakázání výpisu nevracení paměti.

> [!NOTE]
>  Pokud tuto metodu použijete k vypnutí výpisu nevracení paměti, nebudete dostávat zprávy o platných nevraceních paměti ve vaší aplikaci. Tuto metodu byste měli použít pouze v případě, že máte jistotu, že sestava nevracení paměti obsahuje falešně nevracení paměti.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxenablememorytracking"></a>AfxEnableMemoryTracking

Trasování diagnostiky paměti je obvykle povoleno v ladicí verzi knihovny MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parametry

*bTrack*<br/>
Nastavení této hodnoty na TRUE zapne sledování paměti; Hodnota FALSE vypne tuto hodnotu.

### <a name="return-value"></a>Návratová hodnota

Předchozí nastavení příznaku sledování – povolit.

### <a name="remarks"></a>Poznámky

Pomocí této funkce zakážete sledování v částech kódu, o kterých víte, že se bloky přiděluje správně.

Další informace o `AfxEnableMemoryTracking`naleznete v tématu [DEBUGGING MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxismemoryblock"></a>AfxIsMemoryBlock

Testuje adresu paměti, aby se zajistilo, že představuje aktuálně aktivní blok paměti, který byl přidělený diagnostickou verzí **New**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parametry

*trub*<br/>
Odkazuje na blok paměti, která má být testována.

*nBytes*<br/>
Obsahuje délku bloku paměti v bajtech.

*plRequestNumber*<br/>
Odkazuje na **dlouhé** celé číslo, které bude vyplněno číslem pořadí přidělení paměťového bloku, nebo nula, pokud nepředstavuje aktuálně aktivní blok paměti.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je blok paměti aktuálně přidělen a délka je správná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Také zkontroluje zadanou velikost oproti původní přidělené velikosti. Pokud funkce vrátí nenulovou hodnotu, pořadové číslo přidělení je vráceno v *plRequestNumber*. Toto číslo představuje pořadí, ve kterém byl blok přidělen vzhledem ke všem ostatním **novým** přidělením.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxisvalidaddress"></a>AfxIsValidAddress

Testuje všechny adresy paměti, aby bylo zajištěno, že je obsažena výhradně v paměťovém prostoru programu.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parametry

*úloh*<br/>
Odkazuje na adresu paměti, která má být testována.

*nBytes*<br/>
Obsahuje počet bajtů paměti, která má být testována.

*bReadWrite*<br/>
Určuje, zda je paměť určena pro čtení i zápis (TRUE) nebo pouze pro čtení (FALSE).

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění, nenulové, pokud je zadaný blok paměti zcela obsažen v paměťovém prostoru programu; v opačném případě 0.

V sestaveních bez ladění, nenulová, pokud hodnota *LP* není null; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Adresa není omezena na bloky přidělené **novým**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxisvalidstring"></a>AfxIsValidString

Pomocí této funkce lze určit, zda je ukazatel na řetězec platný.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Ukazatel, který chcete otestovat.

*nLength*<br/>
Určuje délku testovaného řetězce (v bajtech). Hodnota-1 označuje, že řetězec bude zakončený hodnotou null.

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění, nenulové, pokud zadaný ukazatel odkazuje na řetězec zadané velikosti; v opačném případě 0.

V sestaveních bez ladění, nenulová, pokud *lpsz* není null; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxsetallochook"></a>AfxSetAllocHook

Nastaví zavěšení, které umožňuje volání zadané funkce před přidělením každého bloku paměti.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parametry

*pfnAllocHook*<br/>
Určuje název funkce, která má být volána. Podívejte se na poznámky k prototypu funkce alokace.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud chcete povolit přidělování; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Knihovna Microsoft Foundation Class modul pro ladění paměti může zavolat uživatelsky definovanou funkci zavěšení, aby mohl uživatel monitorovat přidělení paměti a určovat, zda je přidělení povoleno. Funkce zavěšení přidělení jsou prototypy takto:

**Bool AFXAPI AllocHook (size_t** `nSize` **, bool** `bObject` **, Long** `lRequestNumber` **);**

*nSize*<br/>
Velikost navrhovaného přidělení paměti.

*bObject*<br/>
TRUE, pokud je přidělení pro objekt odvozený `CObject`; v opačném případě FALSE.

*lRequestNumber*<br/>
Pořadové číslo přidělení paměti.

Všimněte si, že konvence volání AFXAPI předpokládá, že volaný musí odebrat parametry ze zásobníku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxdoforallclasses"></a>AfxDoForAllClasses

Volá zadanou funkci iterace pro všechny serializovatelný třídy odvozené `CObject`v paměťovém prostoru aplikace.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*PFN*<br/>
Odkazuje na funkci iterace, která má být volána pro každou třídu. Argumenty funkce jsou ukazatel na objekt `CRuntimeClass` a ukazatel void na další data, která volající dodává do funkce.

*pContext*<br/>
Odkazuje na volitelná data, která volající může předat funkci iterace. Tento ukazatel může mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Serializovatelný `CObject`– odvozené třídy jsou třídy odvozené pomocí DECLARE_SERIALho makra. Ukazatel, který je předán `AfxDoForAllClasses` v *pContext* , je předán do zadané funkce iterace pokaždé, když je volána.

> [!NOTE]
>  Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxdoforallobjects"></a>AfxDoForAllObjects

Spustí zadanou funkci iterace pro všechny objekty odvozené od `CObject`, které byly přiděleny s **novým**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*PFN*<br/>
Odkazuje na funkci iterace, která se má provést pro každý objekt. Argumenty funkce jsou ukazatel na `CObject` a ukazatel void na další data, která volající dodává do funkce.

*pContext*<br/>
Odkazuje na volitelná data, která volající může předat funkci iterace. Tento ukazatel může mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Zásobníky, globální nebo vložené objekty nejsou vyčísleny. Ukazatel předaný do `AfxDoForAllObjects` v *pContext* je předán do zadané funkce iterace pokaždé, když je volána.

> [!NOTE]
>  Tato funkce funguje pouze v ladicí verzi knihovny MFC.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CObject::D UMP](cobject-class.md#dump)
