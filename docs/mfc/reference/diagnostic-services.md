---
title: Diagnostické služby | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2332090032a93152b6c841336538bf9d45984300
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="diagnostic-services"></a>Diagnostické služby
Knihovny Microsoft Foundation Class poskytuje mnoho diagnostiky službách, díky kterým ladění programy jednodušší. Tyto diagnostické služby zahrnují makra a globální funkce, které vám umožní sledovat paměti pro vaše programy přidělení, dump obsah objektů za běhu a Tisk zprávy ladění za běhu. Makra a globální funkce pro diagnostické služby jsou seskupené do následujících kategorií:  
  
-   Obecná diagnostická makra  
  
-   Obecné diagnostické funkce a proměnné  
  
-   Diagnostické funkce objektů  
  
 Tyto makra a funkce jsou k dispozici, pro všechny třídy odvozené od `CObject` v ladění a vydání verze knihovny MFC. Ale všechny kromě `DEBUG_NEW` a **OVĚŘTE** nedělat nic ve vydané verzi.  
  
 V knihovně ladění všechny bloky přidělené paměti jsou v závorkách s řadou "ochrana bajtů." Pokud tyto bajtů jsou narušen vyvolání chybové paměti zápisu, můžete rutiny diagnostiky nahlásit problém. Pokud zahrnete řádek:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 v souboru implementace veškerá volání **nové** uloží číslo a název souboru a řádku, kde přidělení paměti byla provedena. Funkce [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) se zobrazí tato doplňující informace, abyste mohli identifikovat nevracení paměti. Také odkazovat na třídu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) Další informace o výstup diagnostiky.  
  
 Kromě toho běhové knihovny jazyka C také podporuje sadu diagnostické funkce, které můžete použít k ladění aplikací. Další informace najdete v tématu [ladění rutiny](../../c-runtime-library/debug-routines.md) v referenci běhové knihovny.  
  
### <a name="mfc-general-diagnostic-macros"></a>MFC – obecné diagnostiky makra  
  
|||  
|-|-|  
|[ASSERT](#assert)|Vytiskne zprávu a pak zruší program, pokud zadaný výraz vyhodnocen jako **FALSE** v ladicí verze knihovny.|  
|[ASSERT_KINDOF –](#assert_kindof)|Testy, které je objekt objektu pro zadanou třídu nebo třídy odvozené od pro zadanou třídu.|  
|[ASSERT_VALID –](#assert_valid)|Testy interní platnosti objektu voláním jeho `AssertValid` členské funkce; obvykle přepsaného z `CObject`.|
|[DEBUG_NEW –](#debug_new)|Poskytuje název souboru a řádku číslo pro všechny přidělení objektů v režimu ladění vám pomohou najít nevracení paměti.|  
|[DEBUG_ONLY –](#debug_only)|Podobně jako **ASSERT** testování hodnotu výrazu; ale užitečná pro kód, který má být spuštěn pouze v režimu ladění.|  
|[Zajistěte, aby a ENSURE_VALID](#ensure)|Slouží k ověření správnosti data.|
|[THIS_FILE –](#this_file)|Rozšíří na název souboru, který se bude kompilovat.|
|[TRASOVÁNÍ](#trace)|Poskytuje `printf`-jako funkce v ladicí verze knihovny.|  
|[OVĚŘENÍ](#verify)|Podobně jako **ASSERT** ale vyhodnotí výraz ve verzi knihovny také jako ladicí verzi.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC obecné diagnostiky proměnné a funkce  
  
|||  
|-|-|  
|[afxdump –](#afxdump)|Globální proměnné, která odešle [CDumpContext](../../mfc/reference/cdumpcontext-class.md) informace do okna výstupu ladicí program nebo ladění terminálu.|  
|[afxmemdf –](#afxmemdf)|Globální proměnné, která řídí chování ladění přidělení paměti.|  
|[Afxcheckerror –](#afxcheckerror)|Globální proměnná používá k testování předaný **kód SCODE** pokud ho k chybě, a pokud ano, vyvolá příslušná chybová.|  
|[Afxcheckmemory –](#afxcheckmemory)|Ověří že integritu všechny aktuálně přidělené paměti.|  
|[Afxdebugbreak –](#afxdebugbreak)|Způsobí, že zalomení při provádění.|
|[Afxdump –](#cdumpcontext_in_mfc)|Pokud je volána při v ladicím programu, vypíše stav objektu při ladění.|  
|[Afxdump –](#afxdump)|Vnitřní funkce, která Vypíše stav objektu při ladění.|
|[Afxdumpstack –](#afxdumpstack)|Generovat bitové kopie aktuálního zásobníku. Tato funkce je vždy staticky propojený.|  
|[Afxenablememoryleakdump –](#afxenablememoryleakdump)|Umožňuje k úniku výpisu paměti.|  
|[Afxenablememorytracking –](#afxenablememorytracking)|Zapne sledování zapnout a vypnout paměti.|  
|[Afxismemoryblock –](#afxismemoryblock)|Ověřuje, správně přidělené blok paměti.|  
|[Afxisvalidaddress –](#afxisvalidaddress)|Ověřuje, že jste rozsah adres paměti je v rámci programu hranice.|  
|[Afxisvalidstring –](#afxisvalidstring)|Určuje, zda je ukazatel na řetězec platný.|  
|[Afxsetallochook –](#afxsetallochook)|Umožňuje volání funkce při každém přidělení paměti.|  
  
### <a name="mfc-object-diagnostic-functions"></a>Diagnostické funkce objektů MFC  
  
|||  
|-|-|  
|[AfxDoForAllClasses –](#afxdoforallclasses)|Provede zadané funkce na všech `CObject`-odvozené třídy, které podporují kontrola běhu typu.|  
|[Afxdoforallobjects –](#afxdoforallobjects)|Provede zadané funkce na všech `CObject`-odvozené objekty, které byly přiděleny s **nové**.|  

### <a name="mfc-compilation-macros"></a>MFC – makra kompilace
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Upozornění kompilátoru pro použití zastaralé funkce MFC potlačí.|  


## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS
Upozornění kompilátoru pro použití zastaralé funkce MFC potlačí.  
   
### <a name="syntax"></a>Syntaxe   
```  
_AFX_SECURE_NO_WARNINGS  
```     
### <a name="example"></a>Příklad  
 Tato ukázka kódu by způsobilo upozornění kompilátoru, pokud nebyly definovány _AFX_SECURE_NO_WARNINGS.  
  
 ```cpp
// define this before including any afx files in stdafx.h
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a> Afxdebugbreak –
Volání této funkce způsobí zalomení (v umístění volání `AfxDebugBreak`) v provádění ladicí verzi vaší aplikace knihovny MFC.  

### <a name="syntax"></a>Syntaxe    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>Poznámky  
 `AfxDebugBreak` nemá žádný vliv v verze aplikace MFC a měla by být odebrána. Tato funkce slouží pouze v aplikacích MFC. Použijte verzi rozhraní API Win32 **debugbreak –**, aby způsobí přerušení mimo MFC aplikace.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxver_.h   

##  <a name="assert"></a>  ASSERT
 Vyhodnotí jeho argumentem.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Určuje výraz (včetně hodnot ukazatele), který se vyhodnocuje nenulové hodnoty nebo rovna 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je výsledek 0, makro vytiskne hlášení diagnostiky a zruší program. Pokud je podmínka vyhodnocena nenulové hodnoty, neprovede žádnou akci.  
  
 Diagnostická zpráva má tvar  
  
 `assertion failed in file <name> in line <num>`  
  
 kde *název* je název zdrojového souboru, a *num* je číslo řádku kontrolní výraz, který selhal v zdrojový soubor.  
  
 Ve verzi knihovny MFC **ASSERT** výraz nelze vyhodnotit a tím nepřeruší program. Pokud tento výraz musí být vyhodnocen bez ohledu na prostředí, použijte **OVĚŘTE** makro místě **ASSERT**.  
  
> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verze knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="assert_kindof"></a>  ASSERT_KINDOF –  
 Toto makro vyhodnotí objekt ukazuje je objekt pro zadanou třídu, zda je objekt třídy odvozené od pro zadanou třídu.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název `CObject`-odvozené třídy.  
  
 *pobject*  
 Ukazatel na objekt třídy.  
  
### <a name="remarks"></a>Poznámky  
 *Pobject* parametr by měl být ukazatel na objekt a může být **const**. Objekt ukazuje a musí podporovat třídu `CObject` run-time třída informace. Jako příklad, abyste ověřili, že `pDocument` ukazatel na objekt `CMyDoc` třídy, nebo libovolná z odvozené, může kód:  
  
 [!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 Pomocí `ASSERT_KINDOF` makro je přesně stejný jako kódování:  
  
 [!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Tato funkce funguje pouze pro třídy deklarovat s [DECLARE_DYNAMIC] (spustit čas objekt model-services.md #declare_dynamic nebo [declare_serial –](run-time-object-model-services.md#declare_serial) makro.  
  
> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verze knihovny MFC.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="assert_valid"></a>  ASSERT_VALID –  
 Použijte k testování předpokladů o platnost vnitřní stav objektu.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Určuje objekt třídy odvozené od `CObject` s přepsání verzi `AssertValid` – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 `ASSERT_VALID` volání `AssertValid` jako její argument předaná – členská funkce objektu.  
  
 Ve verzi knihovny MFC `ASSERT_VALID` se nic nestane. V ladicí verze, ověřuje ukazatele, ověří proti **NULL**a zavolá metodu objektu vlastní `AssertValid` členské funkce. Pokud některý z těchto testů selže, se zobrazí zpráva s upozorněním stejným způsobem jako [ASSERT](#assert).  
  
> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verze knihovny MFC.  
  
 Další informace a příklady naleznete v tématu [ladění aplikace MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW –  
 Pomáhá v hledání nevrácené paměti.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít `DEBUG_NEW` everywhere v programu, které by normálně používat **nové** operátor pro přidělení haldy úložiště.  
  
 V režimu ladění (Pokud **_DEBUG –** symbol je definována), `DEBUG_NEW` uchovává informace o číslo a název souboru a řádek pro každý objekt, který přiděluje. Potom při použití [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) – členská funkce každého objektu je přiřazen `DEBUG_NEW` se zobrazí s číslo a název souboru a řádku, kde byl přidělen.  
  
 Chcete-li použít `DEBUG_NEW`, vložte následující direktiva do zdrojových souborů:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Po vložení tato direktiva preprocesor vloží `DEBUG_NEW` kdekoli použijete **nové**, a MFC nedojde zbytek. Když zkompilujete verzi vašeho programu `DEBUG_NEW` přeloží na jednoduchý **nové** nejsou generované operace a název souboru a řádku číslo informace.  
  
> [!NOTE]
>  V předchozích verzích MFC (4.1 a starší) potřebné k odstranění `#define` příkaz po všechny příkazy, které volá `IMPLEMENT_DYNCREATE` nebo `IMPLEMENT_SERIAL` makra. To již není nezbytné.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY –  
 V režimu ladění (když **_DEBUG –** symbol je definována), `DEBUG_ONLY` vyhodnotí jako její argument.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro vydání **debug_only –** nevyhodnocuje jeho argumentem. To je užitečné, když máte kód, který se má provést jenom u sestavení ladicí verze.  
  
 `DEBUG_ONLY` Makro je ekvivalentní okolním *výraz* s **_DEBUG #ifdef –** a `#endif`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

 ### <a name="ensure"></a>  Zajistěte, aby a ENSURE_VALID
Slouží k ověření správnosti data.  
   
### <a name="syntax"></a>Syntaxe    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Určuje logický výraz, který má být testována.  
   
### <a name="remarks"></a>Poznámky  
 Účelem těchto makra je ke zlepšení ověření parametrů. Makra brání dalšímu zpracování nesprávné parametry v kódu. Na rozdíl od **ASSERT** makra, **zajistěte, aby** makra výjimku kromě vytváření kontrolní výrazy.  
  
 Makra chovat dvěma způsoby podle konfigurací projektu. Makra volání **ASSERT** a pak vyvolat výjimku, pokud se nezdaří kontrolní výraz. Proto v konfiguracích ladění (to znamená, kde **_DEBUG –** je definována) makra vytvořit kontrolní výraz a výjimky ve verzi konfigurace, makra vytvořit pouze výjimka (**ASSERT** neexistuje vyhodnocení výrazu v konfiguracích verzi).  
  
 Makro **ENSURE_ARG** funguje jako **zajistěte, aby** makro.  
  
 **ENSURE_VALID** volání `ASSERT_VALID` – makro (která má vliv jenom u sestavení ladicí verze). Kromě toho **ENSURE_VALID** vyvolá výjimku, pokud je ukazatel hodnotu NULL. NULL test se provádí v konfigurace Debug a Release.  
  
 Pokud některý z těchto testů selže, se zobrazí zpráva s upozorněním stejným způsobem jako **ASSERT**. Makro vyvolá výjimku neplatný argument. v případě potřeby.  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [OVĚŘENÍ](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE –
Rozšíří na název souboru, který se bude kompilovat.  
   
### <a name="syntax"></a>Syntaxe    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>Poznámky  
 Informace je používán **ASSERT** a **OVĚŘTE** makra. Průvodce vytvořením aplikace a kód průvodců umístit makro soubory zdrojového kódu, které vytvoří.  
   
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
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [ASSERT](#assert)   
 [OVĚŘENÍ](#verify)


##  <a name="trace"></a>  TRASOVÁNÍ  
 Zadaný řetězec se odešle do ladicího programu aktuální aplikace.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) popis **trasování**. **TRASOVÁNÍ** a `ATLTRACE2` mají stejné chování.  
  
 V ladicí verze knihovny MFC odešle toto makro zadaný řetězec ladicí program aktuální aplikace. V sestavení pro vydání tento makro zkompiluje na hodnotu nothing (bez generování kódu vůbec).  
  
 Další informace najdete v tématu [ladění aplikace MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="verify"></a>  OVĚŘENÍ  
 V ladicí verze knihovny MFC vyhodnotí jeho argumentem.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Určuje výraz (včetně hodnot ukazatele), který se vyhodnocuje nenulové hodnoty nebo rovna 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je výsledek 0, makro vytiskne hlášení diagnostiky a zastaví program. Pokud je podmínka vyhodnocena nenulové hodnoty, neprovede žádnou akci.  
  
 Diagnostická zpráva má tvar  
  
 `assertion failed in file <name> in line <num>`  
  
 kde *název* je název zdrojového souboru a *num* je číslo řádku kontrolní výraz, který selhal v zdrojový soubor.  
  
 Ve verzi knihovny MFC **OVĚŘTE** vyhodnotí výraz ale ne k tisku nebo přerušení program. Například pokud výraz volání funkce, bude provedeno volání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxdump – (cdumpcontext v prostředí MFC)  
 Poskytuje základní objekt vypsání možnost ve vaší aplikaci.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Poznámky  
 `afxDump` je i předdefinovanou [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objekt, který umožňuje odeslat `CDumpContext` informace do okna výstupu ladicí program nebo k ladění terminálu. Obvykle je zadat `afxDump` jako parametr pro `CObject::Dump`.  
  
 V systému Windows NT a všechny verze systému Windows `afxDump` výstup je odeslán do okna výstupu ladění jazyka Visual C++ při ladění aplikace.  
  
 Tato proměnná je definována pouze ve verzi ladění MFC. Další informace o `afxDump`, najdete v části [ladění aplikace MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h


## <a name="afxdump"></a> Afxdump – (interní)
Vnitřní funkce, která používá MFC vypsat stav objektu při ladění.  

### <a name="syntax"></a>Syntaxe    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>Parametry  
 `pOb`  
 Ukazatel na objekt třídy odvozené od `CObject`.  
   
### <a name="remarks"></a>Poznámky  
 **Afxdump –** volání objektu `Dump` – členská funkce a odesílá informace do umístění určeného `afxDump` proměnné. **Afxdump –** je k dispozici pouze v ladicí verze knihovny MFC.  
  
 Váš kód programu by neměl volat **afxdump –**, ale místo toho by měly volat `Dump` – členská funkce příslušného objektu.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
   
### <a name="see-also"></a>Viz také  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>  afxmemdf –  
 Tato proměnná je dostupné z ladicí program nebo program a umožňuje vám umožní ladit přidělení diagnostiky.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Poznámky  
 `afxMemDF` může mít následující hodnoty podle specifikace výčtu `afxMemDF`:  
  
- **allocmemdf –** Zapne ladění allocator (výchozí nastavení v ladicí knihovny).  
  
- **delayfreememdf –** zpozdí uvolnění paměti. Když váš program uvolní blok paměti, přidělujícího modulu nevrací že paměť pro příslušný operační systém. To bude umístit přízvuk maximální paměť na váš program.  
  
- **checkalwaysmemdf –** volání `AfxCheckMemory` pokaždé, když je paměti přidělené nebo vydání. Tím se výrazně zpomalit přidělování paměti a navrácení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="afxcheckerror"></a>  Afxcheckerror –  
 Tato funkce testy předaný **kód SCODE** chcete zobrazit, pokud je k chybě.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je chyba, funkce vyvolá výjimku. Pokud je předaná `SCODE` je **E_OUTOFMEMORY**, funkce vyvolá [CMemoryException](../../mfc/reference/cmemoryexception-class.md) voláním [afxthrowmemoryexception –](exception-processing.md#afxthrowmemoryexception). Jinak, funkce vyvolá [COleException](../../mfc/reference/coleexception-class.md) voláním [afxthrowoleexception –](exception-processing.md#afxthrowoleexception).  
  
 Tato funkce slouží ke kontrole vrácené hodnoty volání funkce OLE ve vaší aplikaci. Otestováním návratovou hodnotu pomocí této funkce ve vaší aplikaci můžete správně reagovat na chybové stavy s minimální velikostí kódu.  
  
> [!NOTE]
>  Tato funkce je obdobou ladění a bez ladění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="afxcheckmemory"></a>  Afxcheckmemory –  
 Tato funkce ověří volné paměti fondu a vypíše chybové zprávy podle potřeby.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud žádné chyby paměti; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud funkci zjistí žádné poškození paměti, vytiskne nic.  
  
 Všechny bloky paměti aktuálně přidělené v haldě jsou zaškrtnutá políčka, včetně těch, které přidělené **nové** , ale ne ty, které jsou přidělené přímé volání základní alokátorů paměti, jako například `malloc` funkce nebo  **GlobalAlloc** funkce systému Windows. Pokud se najde všechny bloky poškozen, je zprávu vytištěno na výstup ladicí program.  
  
 Pokud obsahuje řádek  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 v modulu program, pak následující volání `AfxCheckMemory` zobrazit číslo a název souboru a řádku, kde byl přidělen do paměti.  
  
> [!NOTE]
>  Pokud modul obsahuje jeden nebo více implementace serializovatelných tříd, pak musíte umístit `#define` za poslední řádek `IMPLEMENT_SERIAL` makro volání.  
  
 Tato funkce funguje pouze v ladicí verze knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
 
##  <a name="afxdump"></a>  Afxdump – (MFC)  
 Volání této funkce v ladicím programu pro výpis stavu objektu při ladění.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Parametry  
 `pOb`  
 Ukazatel na objekt třídy odvozené od `CObject`.  
  
### <a name="remarks"></a>Poznámky  
 **Afxdump –** volání objektu `Dump` – členská funkce a odesílá informace do umístění určeného `afxDump` proměnné. **Afxdump –** je k dispozici pouze v ladicí verze knihovny MFC.  
  
 Váš kód programu by neměl volat **afxdump –**, ale místo toho by měly volat `Dump` – členská funkce příslušného objektu.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  

### <a name="see-also"></a>Viz také  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>  Afxdumpstack –  
 Globální funkce slouží ke generování bitové kopie aktuálního zásobníku.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Parametry  
 *dwTarget*  
 Určuje cíl výstupu výpis. Možné hodnoty, které lze spojovat pomocí bitové operace OR ( **&#124;**) operátor, jsou následující:  
  
- **AFX_STACK_DUMP_TARGET_TRACE** odesílá výstup prostřednictvím [trasování](#trace) makro. **Trasování** makro generuje výstup se v sestavení pro ladění; v sestavení pro vydání vygeneruje žádný výstup. Navíc **trasování** může být přesměrován na jiné cíle kromě ladicího programu.  
  
- **AFX_STACK_DUMP_TARGET_DEFAULT** zasílá dump výstup do výchozího cíle. Pro sestavení ladicí verze, výstup přejde na **trasování** makro. V sestavení pro vydání výstup přejde do schránky.  
  
- **AFX_STACK_DUMP_TARGET_CLIPBOARD** odesílá výstup na pouze do schránky. Data je umístěn do schránky jako prostý text použití **CF_TEXT** formát schránky.  
  
- **AFX_STACK_DUMP_TARGET_BOTH** odesílá výstup do schránky a na **trasování** makro, současně.  
  
- **AFX_STACK_DUMP_TARGET_ODS** odesílá výstup přímo na ladicího programu prostřednictvím funkce Win32 **OutputDebugString()**. Tato možnost bude generovat ladicí program výstup v obou ladění a sestavení pro vydání při procesu je připojen ladicí program. **AFX_STACK_DUMP_TARGET_ODS** vždy dosáhne ladicího programu (Pokud je připojena) a nemůže být přesměrována.  
  
### <a name="remarks"></a>Poznámky  
 Následující příklad zobrazuje jeden řádek výstupu generované z volání `AfxDumpStack` z rutiny tlačítko v aplikaci dialogové okno knihovny MFC:  
  
 `=== begin AfxDumpStack output ===`  
  
 `00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes`  
  
 `0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes`  
  
 `0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,`  
  
 `unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct AFX_CMDHANDLE`  
  
 `0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes`  
  
 `00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes`  
  
 `00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned`  
  
 `int,long) + 312 bytes`  
  
 `00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned`  
  
 `int,unsigned int,long,long *) + 83 bytes`  
  
 `00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned`  
  
 `int,unsigned int,long) + 46 bytes`  
  
 `004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct`  
  
 `HWND__ *,unsigned int,unsigned int,long) + 237 bytes`  
  
 `00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned`  
  
 `int,unsigned int,long) + 129 bytes`  
  
 `BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes`  
  
 `BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes`  
  
 `=== end AfxDumpStack() output ===`  
  
 Každý řádek ve výstupu výše označuje adresu poslední volání funkce úplnou cestu pro modul, který obsahuje volání funkce a prototyp funkce volána. Pokud volání funkce v zásobníku se neodehrává na přesnou adresu funkce, zobrazí se posun bajtů.  
  
 Například následující tabulka popisuje první řádek výstupu výše:  
  
|Výstup|Popis|  
|------------|-----------------|  
|`00427D55:`|Zpětná adresa posledním volání funkce.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|Úplná cesta a název modul, který obsahuje volání funkce.|  
|`void AfxDumpStack(unsigned long)`|Prototyp funkce volána.|  
|`+ 181 bytes`|Posun v bajtech z adresy prototyp funkce (v tomto případě `void AfxDumpStack(unsigned long)`) na návratovou adresu (v tomto případě `00427D55`).|  
  
 `AfxDumpStack` je k dispozici v ladění a nondebug verze knihovny MFC; však funkce vždy souvisí staticky, i v případě, že spustitelný soubor používá MFC v sdílenou knihovnu DLL. V implementacích sdílené knihovny funkce nachází v MFCS42. Knihovny LIB (a jeho variant).  
  
 Úspěšné použití této funkce:  
  
-   Soubor IMAGEHLP. Knihovny DLL musí být ve své cestě. Pokud jste tuto knihovnu DLL, funkce se zobrazí chybová zpráva. V tématu [pomoci knihovna obrázků](http://msdn.microsoft.com/library/windows/desktop/ms680321) informace o sadě funkce poskytované IMAGEHLP.  
  
-   Moduly, které mají rámce v zásobníku musí obsahovat ladicí informace. Pokud nebudou obsahovat informace o ladění, funkce stále vygeneruje trasování zásobníku, ale bude menší podrobné trasování.  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxenablememoryleakdump"></a>  Afxenablememoryleakdump –  
 Povolí nebo zakáže stav nevracení paměti v `AFX_DEBUG_STATE` destruktor.  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bDump`  
 `TRUE` Určuje, jestli že je zapnutá výpisu paměti k úniku; `FALSE` označuje stav nevracení paměti je vypnuto.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnotu pro tento příznak.  
  
### <a name="remarks"></a>Poznámky  
 Při aplikaci uvolnění knihovny MFC, knihovny MFC zkontroluje nevracení paměti. V tomto okamžiku jsou všechny nevracení paměti oznamovány uživatele prostřednictvím **ladění** okno [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  
  
 Pokud vaše aplikace načte jinou knihovnou před knihovny MFC, budou některé přidělení paměti v této knihovny správně hlášené jako nevracení paměti. Nevracení paměti False může způsobit, že aplikace zavřete pomalu jako knihovny MFC sestavy je. V takovém případě použijte `AfxEnableMemoryLeakDump` zakázat stav nevracení paměti.  
  
> [!NOTE]
>  Pokud použijete tuto metodu, chcete-li vypnout výpisu paměti k úniku, neobdržíte sestavy nevracení paměti platné ve vaší aplikaci. Tato metoda byste měli používat jenom Pokud jste si jisti, že sestava nevracení paměti obsahuje nevracení paměti false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxenablememorytracking"></a>  Afxenablememorytracking –  
 Sledování diagnostiky paměti je obvykle ve ladicí verze knihovny MFC povolené.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Parametry  
 *bTrack*  
 Nastavení této hodnoty na **TRUE** zapne sledování; paměti **FALSE** ji vypne.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí nastavení příznak pro povolení sledování.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete zakázat sledování na části kódu, víte, že jsou správně přidělení bloků.  
  
 Další informace o `AfxEnableMemoryTracking`, najdete v části [ladění aplikace MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Tato funkce funguje pouze v ladicí verze knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxismemoryblock"></a>  Afxismemoryblock –  
 Testuje adresu paměti a ujistěte se, reprezentuje blok aktuálně aktivní paměti, který byl přidělen diagnostiky verze **nové**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Odkazuje na blok paměti má být testována.  
  
 `nBytes`  
 Obsahuje délka bloku paměti v bajtech.  
  
 `plRequestNumber`  
 Odkazuje na **dlouho** celé číslo, které bude vyplněna bloku paměti přidělení pořadové číslo nebo nula, pokud nepředstavuje blok aktuálně aktivní paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuálně přidělenou paměť bloku a délka je správná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Také zkontroluje, zadaná velikost proti původní přidělená velikost. Pokud funkce vrátí nenulovou hodnotu, vrátí se pořadové číslo přidělení v `plRequestNumber`. Toto číslo představuje pořadí, ve kterém byl přidělen bloku všechny vzájemného **nové** přidělení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxisvalidaddress"></a>  Afxisvalidaddress –  
 Testy libovolná adresa paměti zajistit, že ho je celý vešel do jednoho místa paměti programu.  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Bodů na adresu paměti má být testována.  
  
 `nBytes`  
 Obsahuje počet bajtů paměti, která má být testována.  
  
 *bReadWrite*  
 Určuje, zda je paměť pro čtení i zápis ( **TRUE**) nebo jen pro čtení ( **FALSE**).  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění nenulové hodnoty, pokud zadaná paměťová blokovat je celý vešel do jednoho místa paměti programu; jinak 0.  
  
 V sestavení pro bez ladění nenulové hodnoty v případě `lp` není NULL; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Adresa není omezen na bloky přidělené **nové**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxisvalidstring"></a>  Afxisvalidstring –  
 Pomocí této funkce můžete určit, zda je ukazatel na řetězec platný.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Má ukazatel na test.  
  
 `nLength`  
 Určuje řetězec, který má být testována, v bajtech. Hodnota -1 označuje, že bude řetězec ukončené hodnotou null.  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění, nenulové hodnoty, pokud je zadaný ukazatel odkazuje na řetězec po zadanou velikost; jinak 0.  
  
 V sestavení pro bez ladění nenulové hodnoty v případě `lpsz` není NULL; jinak hodnota 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxsetallochook"></a>  Afxsetallochook –  
 Nastaví háku, která umožňuje volání zadaná funkce předtím, než je přidělená každého bloku paměti.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Parametry  
 *pfnAllocHook*  
 Určuje název funkce volání. V části poznámky pro prototyp funkce přidělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud chcete povolit přidělení; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přidělení paměti ladění Microsoft Foundation Class Library můžete volat funkce háku uživatelem definované uživatelům ke sledování přidělování paměti a k řízení, zda jsou povoleny přidělení. Funkce háku přidělení jsou deklaraci následujícím způsobem:  
  
 **BOOL AFXAPI AllocHook (size_t –** `nSize` **, BOOL** `bObject` **dlouhý** `lRequestNumber` **);**  
  
 `nSize`  
 Velikost přidělení navrhované paměti.  
  
 `bObject`  
 **Hodnota TRUE,** Pokud přidělení pro `CObject`-odvozené objektu; v opačném případě **FALSE**.  
  
 `lRequestNumber`  
 Přidělení paměti pořadové číslo.  
  
 Všimněte si, že **AFXAPI** konvence volání znamená, že volaného musí odebrat parametry v zásobníku.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses –  
 Volá funkci zadaný iterace pro všechny serializovatelný `CObject`-odvozených tříd v paměti aplikace.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parametry  
 `pfn`  
 Body do iterace funkce k volání pro každou třídu. Argumenty funkce jsou odkazy `CRuntimeClass` objekt a void ukazatel na doplňková data, která poskytuje volající funkce.  
  
 `pContext`  
 Odkazuje na volitelné data, která má volající může poskytovat funkce iterací. Může být tento ukazatel **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Serializovatelné `CObject`-jsou odvozené třídy odvozené pomocí `DECLARE_SERIAL` makro. Ukazatele, který je předán `AfxDoForAllClasses` v `pContext` předaný funkci zadaný iterace pokaždé, když je volána.  
  
> [!NOTE]
>  Tato funkce funguje pouze v ladicí verze knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxdoforallobjects"></a>  Afxdoforallobjects –  
 Spustí zadaný iterace funkce pro všechny objekty odvozené od `CObject` , byl přidělen s **nové**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parametry  
 `pfn`  
 Body do funkce iterace provést pro každý objekt. Argumenty funkce jsou odkazy `CObject` a void ukazatel na doplňková data, která poskytuje volající funkce.  
  
 `pContext`  
 Odkazuje na volitelné data, která má volající může poskytovat funkce iterací. Může být tento ukazatel **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Zásobník, globální, nebo vložené objekty nejsou uvedené. Předaný ukazatele `AfxDoForAllObjects` v `pContext` předaný funkci zadaný iterace pokaždé, když je volána.  
  
> [!NOTE]
>  Tato funkce funguje pouze v ladicí verze knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)