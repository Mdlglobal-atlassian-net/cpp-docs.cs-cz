---
title: Diagnostické služby | Dokumentace Microsoftu
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
ms.openlocfilehash: 14c231edc5395515836ccbbe9adea87e0f31b33d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068401"
---
# <a name="diagnostic-services"></a>Diagnostické služby
Knihovny Microsoft Foundation Class poskytuje mnoho diagnostické služby, které usnadňují ladění svých programů jednodušší. Tyto diagnostické služby zahrnují makra a globální funkce, které umožňují sledovat paměti pro vaše programy přidělení, Vypsat obsah objektů za běhu a Tisk zprávy ladění za běhu. Makra a globální funkce pro diagnostické služby jsou seskupené do následujících kategorií:  
  
-   Obecná diagnostická makra  
  
-   Obecné diagnostické funkce a proměnné  
  
-   Diagnostické funkce objektů  
  
 Tato makra a funkce jsou k dispozici, pro všechny třídy odvozené z `CObject` v ladění a vydání verze knihovny MFC. Nicméně všechny s výjimkou DEBUG_NEW a ověřte, zda nedělat nic ve vydané verzi.  
  
 V knihovně ladění, jsou všechny bloky paměti přidělené uváděn s řadou "guard bajtů." Pokud tyto bajty jsou narušen zápis vyvolání chybové paměti, diagnostických rutin můžete nahlásit problém. Pokud zahrnete řádku:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 v souboru implementace veškerá volání **nové** uloží název souboru a číslo řádku kde přidělení paměti byla provedena. Funkce [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) zobrazí tyto dodatečné informace umožňující identifikaci nevracení paměti. Také odkazovat na třídu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) Další informace o diagnostický výstup.  
  
 Kromě toho knihovny run-time jazyka C podporuje také sadu diagnostické funkce, které lze použít k ladění aplikací. Další informace najdete v tématu [ladit rutiny](../../c-runtime-library/debug-routines.md) v referenční dokumentace knihoven Run-Time.  
  
### <a name="mfc-general-diagnostic-macros"></a>MFC – obecné diagnostické makra  
  
|||  
|-|-|  
|[KONTROLNÍ VÝRAZ](#assert)|Vytiskne zprávu a pak program přeruší se, pokud zadaný výraz nevyhodnotí jako FALSE. ladicí verze knihovny.|  
|[ASSERT_KINDOF](#assert_kindof)|Testy, které je objekt objekt z dané třídy nebo třídy odvozené z dané třídy.|  
|[ASSERT_VALID](#assert_valid)|Ověřuje platnost vnitřního objektu voláním jeho `AssertValid` členské funkce; obvykle přepsané z `CObject`.|
|[DEBUG_NEW](#debug_new)|Poskytuje název souboru a číslo řádku pro všechna přidělení objektu v režimu ladění usnadňují vyhledání nevrácené paměti.|  
|[DEBUG_ONLY](#debug_only)|Podobně jako kontrolní VÝRAZ, ale nikoliv testovací hodnota výrazu; užitečné pro kód, který by se měl spustit pouze v režimu ladění.|  
|[Ujistěte se, že a ENSURE_VALID](#ensure)|Slouží k ověření správnosti dat.|
|[THIS_FILE](#this_file)|Rozšíří na název souboru, který je kompilován.|
|[TRASOVÁNÍ](#trace)|Poskytuje `printf`-ni v ladicí verzi knihovny.|  
|[OVĚŘENÍ](#verify)|Podobně jako kontrolní VÝRAZ ale vyhodnotí výraz ve vydané verzi knihovny stejně jako v ladicí verzi.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC obecné diagnostické proměnné a funkce  
  
|||  
|-|-|  
|[afxDump](#afxdump)|Globální proměnné, která odesílá [CDumpContext](../../mfc/reference/cdumpcontext-class.md) informace v okně výstupu ladicího programu, nebo do terminálu ladění.|  
|[afxmemdf –](#afxmemdf)|Globální proměnné, které ovládá chování ladění přidělení paměti.|  
|[Afxcheckerror –](#afxcheckerror)|Globální proměnné, které se použily k testování předaný SCODE zobrazíte, pokud se jedná se o chybu a pokud ano, zobrazí odpovídající chybu.|  
|[Afxcheckmemory –](#afxcheckmemory)|Ověří že integritu všechny aktuálně přidělené paměti.|  
|[Afxdebugbreak –](#afxdebugbreak)|Způsobí přerušení provádění.|
|[afxDump](#cdumpcontext_in_mfc)|Pokud je volána v ladicím programu, vypíše stav objektu během ladění.|  
|[afxDump](#afxdump)|Vnitřní funkce, která Vypíše stav objektu během ladění.|
|[Afxdumpstack –](#afxdumpstack)|Vygenerujte snímek aktuálního zásobníku. Tato funkce je vždy propojovat staticky.|  
|[Afxenablememoryleakdump –](#afxenablememoryleakdump)|Umožňuje výpis paměti.|  
|[Afxenablememorytracking –](#afxenablememorytracking)|Zapne sledování zapnutí a vypnutí paměti.|  
|[Afxismemoryblock –](#afxismemoryblock)|Ověřuje, že byl správně přidělen blok paměti.|  
|[Afxisvalidaddress –](#afxisvalidaddress)|Ověří, zda rozsah adres paměti v rámci programu hranice.|  
|[Afxisvalidstring –](#afxisvalidstring)|Určuje, zda je platný ukazatel na řetězec.|  
|[Afxsetallochook –](#afxsetallochook)|Umožňuje volání funkce na každý přidělení paměti.|  
  
### <a name="mfc-object-diagnostic-functions"></a>Diagnostické funkce objektů MFC  
  
|||  
|-|-|  
|[AfxDoForAllClasses –](#afxdoforallclasses)|Provede zadanou funkci na všech `CObject`-odvozené třídy, které podporují, kontrolu typu za běhu.|  
|[Afxdoforallobjects –](#afxdoforallobjects)|Provede zadanou funkci na všech `CObject`-odvozené objekty, které byly přiděleny s **nové**.|  

### <a name="mfc-compilation-macros"></a>MFC – makra kompilace
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Potlačí upozornění kompilátoru pro použití zastaralé funkce knihovny MFC.|  


## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS
Potlačí upozornění kompilátoru pro použití zastaralé funkce knihovny MFC.  
   
### <a name="syntax"></a>Syntaxe   
```  
_AFX_SECURE_NO_WARNINGS  
```     
### <a name="example"></a>Příklad  
 Tento vzorový kód způsobí upozornění kompilátoru, pokud _AFX_SECURE_NO_WARNINGS nebyly definovány.  
  
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
Voláním této funkce způsobí přerušení (v místě volání `AfxDebugBreak`) při provádění ladicí verze aplikace knihovny MFC.  

### <a name="syntax"></a>Syntaxe    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>Poznámky  
 `AfxDebugBreak` nemá žádný vliv ve vydaných verzích aplikace knihovny MFC a měly by se odebrat. Tato funkce by měla sloužit pouze v aplikacích MFC. Použijte verzi rozhraní API systému Win32 `DebugBreak`, způsobit přerušení v aplikacích non-MFC.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxver_.h   

##  <a name="assert"></a>  KONTROLNÍ VÝRAZ
 Vyhodnotí jako svůj argument.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Parametry  
 *booleanExpression*  
 Určuje výraz (včetně hodnot ukazatel), který se vyhodnotí na nenulovou hodnotu nebo 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je výsledek 0, makro vytiskne diagnostickou zprávu a zruší program. Pokud je podmínka nenulová, nemá žádný účinek.  
  
 Diagnostická zpráva má tvar  
  
 `assertion failed in file <name> in line <num>`  
  
 kde *název* je název zdrojového souboru a *num* je číslo řádku výrazu, který se ve zdrojovém souboru se nezdařilo.  
  
 Ve vydané verzi knihovny MFC kontrolní VÝRAZ není vyhodnocen výraz a tím nepřeruší program. Pokud výraz musí být vyhodnocen bez ohledu na prostředí, použijte makro OVĚŘTE místo ASSERT.  
  
> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="assert_kindof"></a>  ASSERT_KINDOF  
 Toto makro vyhodnotí, že objekt, na které je objekt z dané třídy, nebo je objekt třídy odvozené z dané třídy.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název `CObject`-odvozené třídy.  
  
 *odstraněný objekt*  
 Ukazatel na objekt třídy.  
  
### <a name="remarks"></a>Poznámky  
 *Odstraněný objekt* parametr by měl být ukazatel na objekt a může být **const**. Objekt, na který a musí podporovat třídu `CObject` run-time třída informace. Například, chcete-li zajistit `pDocument` je ukazatel na objekt `CMyDoc` třída nebo některý z jeho vy, může kód:  
  
 [!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 Použití `ASSERT_KINDOF` – makro je přesně stejné jako kódování:  
  
 [!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Tato funkce funguje pouze pro třídy deklarované s [DECLARE_DYNAMIC] (spustit – čas objekt model-services.md #declare_dynamic nebo [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) – makro.  
  
> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="assert_valid"></a>  ASSERT_VALID  
 Použijte k otestování předpokladů o platnost vnitřní stav objektu.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Parametry  
 *odstraněný objekt*  
 Určuje objekt třídy odvozené z `CObject` , který má přepsání verze `AssertValid` členskou funkci.  
  
### <a name="remarks"></a>Poznámky  
 ASSERT_VALID volání `AssertValid` členské funkce objektu předána jako argument.  
  
 ASSERT_VALID ve vydané verzi knihovny MFC, nemá žádný účinek. V ladicí verzi ověří ukazatel, kontroluje s hodnotou NULL a volá objektu vlastní `AssertValid` členské funkce. Pokud některé z těchto testů selže, zobrazí se upozornění stejným způsobem jako [ASSERT](#assert).  
  
> [!NOTE]
>  Tato funkce je k dispozici pouze v ladicí verzi knihovny MFC.  
  
 Další informace a příklady najdete v tématu [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW  
 Pomáhá při hledání nevrácené paměti.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Poznámky  
 DEBUG_NEW můžete použít kdekoli v programu, která by obvykle použijete **nové** operátor přidělení haldy úložiště.  
  
 V režimu ladění (když **_DEBUG** je definován symbol), název souboru a číslo řádku pro každý objekt, který přiděluje uchovává informace o DEBUG_NEW. Poté, kdy použít [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) členská funkce, každý objekt, kterým je přiřazen výraz DEBUG_NEW je zobrazen název souboru a číslo řádku kde byl přidělen.  
  
 Použití DEBUG_NEW, vložte následující direktiva do zdrojových souborů:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Po vložení této direktivy preprocesoru vloží DEBUG_NEW bez ohledu na to používáte **nové**, a udělá zbytek knihovny MFC. Při kompilaci verze programu DEBUG_NEW přeloží na jednoduchý **nové** se negenerují operace a název souboru a informace čísla řádku.  
  
> [!NOTE]
>  V předchozích verzí knihovny MFC (4.1 a starší) je potřeba umístit `#define` příkazem za všechny příkazy, které volaly IMPLEMENT_DYNCREATE nebo IMPLEMENT_SERIAL makra. To již není nezbytné.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY  
 V režimu ladění (když **_DEBUG** je definován symbol), DEBUG_ONLY vyhodnotí jako svůj argument.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro vydání DEBUG_ONLY nevyhodnocuje svého argumentu. To je užitečné, když máte kód, který má být spuštěn pouze v sestaveních ladění.  
  
 DEBUG_ONLY – makro odpovídá okolní *výraz* s `#ifdef _DEBUG` a `#endif`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

 ### <a name="ensure"></a>  Ujistěte se, že a ENSURE_VALID
Slouží k ověření správnosti dat.  
   
### <a name="syntax"></a>Syntaxe    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>Parametry  
 *booleanExpression*  
 Určuje logický výraz, který má být testována.  
   
### <a name="remarks"></a>Poznámky  
 Účelem těchto maker je zlepšit ověření parametrů. Makra brání dalšímu zpracování nesprávné parametry ve vašem kódu. Na rozdíl od makra ASSERT Ujistěte se, že makra vyvolat výjimku kromě generování kontrolní výraz.  
  
 Makra chovat podle konfigurace projektu dvěma způsoby. Makra ASSERT volání a potom vyvolána výjimka, pokud výraz se nezdaří. Proto v konfiguraci ladění (to znamená, pokud je definována _DEBUG) makra vytvořit kontrolní výraz a výjimka při v konfiguraci vydání produktu makra pouze výjimky (kontrolní VÝRAZ není vyhodnocen výraz v konfiguraci vydání).  
  
 Makro ENSURE_ARG funguje jako Ujistěte se, že makra.  
  
 ENSURE_VALID volá ASSERT_VALID – makro (který má vliv pouze v sestaveních ladění). Kromě toho ENSURE_VALID vyvolá výjimku, pokud ukazatel na hodnotu NULL. NULL test se provádí v konfigurace Debug a Release.  
  
 Pokud selže některý z těchto testů, se zobrazí upozornění stejným způsobem jako kontrolní VÝRAZ. Makro vyvolá výjimku neplatný argument v případě potřeby.  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [OVĚŘENÍ](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE
Rozšíří na název souboru, který je kompilován.  
   
### <a name="syntax"></a>Syntaxe    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>Poznámky  
 Makra ASSERT a ověřte, zda je používán informace. Průvodci Průvodce aplikace a kód umístit makro souborů se zdrojovým kódem, který vytvoří.  
   
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
 [KONTROLNÍ VÝRAZ](#assert)   
 [OVĚŘENÍ](#verify)


##  <a name="trace"></a>  TRASOVÁNÍ  
 Ladicí program aktuální aplikace odešle zadaného řetězce.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) popis trasování. TRASOVÁNÍ a ATLTRACE2 mají stejné chování.  
  
 Toto makro v ladicí verzi knihovny MFC, odešle zadaný řetězec ladicí program aktuální aplikace. V sestavení pro vydání toto makro zkompiluje Nothing (není vygenerovaný žádný kód vůbec).  
  
 Další informace najdete v tématu [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="verify"></a>  OVĚŘENÍ  
 V ladicí verzi knihovny MFC vyhodnotí jako svůj argument.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Parametry  
 *booleanExpression*  
 Určuje výraz (včetně hodnot ukazatel), který se vyhodnotí na nenulovou hodnotu nebo 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je výsledek 0, makro vytiskne diagnostickou zprávu a ukončí program. Pokud je podmínka nenulová, nemá žádný účinek.  
  
 Diagnostická zpráva má tvar  
  
 `assertion failed in file <name> in line <num>`  
  
 kde *název* je název zdrojového souboru a *num* je číslo řádku výrazu, který se ve zdrojovém souboru se nezdařilo.  
  
 Ve vydané verzi knihovny MFC ověřte, zda vyhodnotí výraz, ale nepodporuje vytisknout ani přerušit program. Například pokud má výraz hodnotu volání funkce, budou volání provedeno.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (CDumpContext v prostředí MFC)  
 Poskytuje základní funkce výpis objektu ve vaší aplikaci.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Poznámky  
 `afxDump` je i předdefinovanou [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objekt, který umožňuje odeslat `CDumpContext` informace v okně výstupu ladicího programu nebo na terminálu ladění. Obvykle je zadat `afxDump` jako parametr `CObject::Dump`.  
  
 V části Windows NT a všechny verze systému Windows `afxDump` výstup je odeslán do okna výstup ladění jazyka Visual C++ při ladění aplikace.  
  
 Tato proměnná je definováno pouze v ladicí verzi knihovny MFC. Další informace o `afxDump`, naleznete v tématu [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h


## <a name="afxdump"></a> AfxDump (interní)
Vnitřní funkce, která knihovna MFC používá pro výpis stavu objektu během ladění.  

### <a name="syntax"></a>Syntaxe    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>Parametry  
 *Poštovní přihrádka*  
 Ukazatel na objekt třídy odvozené z `CObject`.  
   
### <a name="remarks"></a>Poznámky  
 `AfxDump` volání objektu `Dump` členské funkce a odesílá informace do umístění určeného `afxDump` proměnné. `AfxDump` je k dispozici pouze v ladicí verzi knihovny MFC.  
  
 Váš program kód by neměl volat `AfxDump`, ale místo toho by měly volat `Dump` členskou funkci na příslušný objekt.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
   
### <a name="see-also"></a>Viz také  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>  afxmemdf –  
 Tato proměnná je přístupný z ladicího programu nebo aplikace a umožňuje ladit přidělování diagnostiky.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Poznámky  
 `afxMemDF` může mít následující hodnoty uvedené ve výčtu `afxMemDF`:  
  
- `allocMemDF` Zapne ladicí alokátoru (výchozí nastavení do ladicí knihovny).  
  
- `delayFreeMemDF` Zpoždění uvolnění paměti. Když váš program uvolňuje blok paměti, nevrátí alokátoru, tato paměť pro příslušný operační systém. To umístí zátěže maximální velikost paměti v programu.  
  
- `checkAlwaysMemDF` Volání `AfxCheckMemory` pokaždé, když je paměť přidělena nebo uvolněna. Tím se výrazně snížit přidělení paměti a navrácení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="afxcheckerror"></a>  Afxcheckerror –  
 Tato funkce testuje předaný SCODE zobrazíte, pokud se jedná se o chybu.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud se jedná se o chybu, funkce vyvolá výjimku. Pokud je předaná SCODE E_OUTOFMEMORY, funkce vyvolá [cmemoryexception –](../../mfc/reference/cmemoryexception-class.md) voláním [afxthrowmemoryexception –](exception-processing.md#afxthrowmemoryexception). V opačném případě vyvolá funkce [coleexception –](../../mfc/reference/coleexception-class.md) voláním [afxthrowoleexception –](exception-processing.md#afxthrowoleexception).  
  
 Tato funkce je možné zkontrolovat vrácené hodnoty volání funkce OLE ve vaší aplikaci. Při testování návratovou hodnotu pomocí této funkce ve vaší aplikaci, můžete správně reagovat na chybové stavy s minimální množství kódu.  
  
> [!NOTE]
>  Tato funkce má stejný účinek ladění a sestavení bez ladění.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h

##  <a name="afxcheckmemory"></a>  Afxcheckmemory –  
 Tato funkce ověří volné paměti fondu a vytiskne chybové zprávy podle potřeby.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud žádné chyby paměti; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud funkci zjistí žádné poškození paměti, vytiskne hodnotu nothing.  
  
 Jsou kontrolovány všechny bloky paměti aktuálně přidělený k haldě, včetně těch, které přidělaná **nové** , ale ne těch, které jsou přidělené přímá volání základní paměti alokátory, jako například **malloc** funkce nebo `GlobalAlloc` funkce Windows. Pokud jakýkoli blok je poškozen, je zpráva vytištěna do výstupu ladicího programu.  
  
 Zadáte-li na řádku  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 v programu modulu, pak následných volání `AfxCheckMemory` zobrazit název souboru a číslo řádku, kde byla přidělena paměť.  
  
> [!NOTE]
>  Pokud modul obsahuje jeden nebo více implementací serializovatelné třídy, pak je nutné umístit `#define` řádek po posledním volání IMPLEMENT_SERIAL – makro.  
  
 Tato funkce funguje pouze v ladicí verzi knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
 
##  <a name="afxdump"></a>  AfxDump (MFC)  
 Voláním této funkce v ladicím programu pro výpis stavu objektu během ladění.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Parametry  
 *Poštovní přihrádka*  
 Ukazatel na objekt třídy odvozené z `CObject`.  
  
### <a name="remarks"></a>Poznámky  
 `AfxDump` volání objektu `Dump` členské funkce a odesílá informace do umístění určeného `afxDump` proměnné. `AfxDump` je k dispozici pouze v ladicí verzi knihovny MFC.  
  
 Váš program kód by neměl volat `AfxDump`, ale místo toho by měly volat `Dump` členskou funkci na příslušný objekt.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  

### <a name="see-also"></a>Viz také  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>  Afxdumpstack –  
 Tato globální funkce slouží ke generování obrázku aktuálního zásobníku.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Parametry  
 *dwTarget*  
 Určuje cíl výstupu s výpisem paměti. Možné hodnoty, které lze spojovat pomocí bitového operátoru OR ( **&#124;**) – operátor, jsou následující:  
  
- Odešle AFX_STACK_DUMP_TARGET_TRACE výstup prostřednictvím [trasování](#trace) – makro. TRACE – makro generuje výstup v sestaveních ladění. generuje žádný výstup v sestaveních pro vydání. Navíc trasování je možné přesměrovat do jiné cíle kromě ladicího programu.  
  
- Odešle AFX_STACK_DUMP_TARGET_DEFAULT výstup výpisu stavu systému do výchozí cíl. Pro sestavení pro ladění výstup přejde na TRACE – makro. V sestavení pro vydání výstup přejde do schránky.  
  
- AFX_STACK_DUMP_TARGET_CLIPBOARD odesílá výstup pouze do schránky. Data se umístí do schránky jako prostý text ve formátu schránky CF_TEXT.  
  
- AFX_STACK_DUMP_TARGET_BOTH odesílá výstup do schránky a na TRACE – makro současně.  
  
- Odešle AFX_STACK_DUMP_TARGET_ODS výstup přímo do ladicího programu pomocí funkce Win32 `OutputDebugString()`. Tato možnost bude generovat výstupem ladicího programu v obou ladění a verze sestavení, když je připojen ladicí program k procesu. AFX_STACK_DUMP_TARGET_ODS vždy dosáhne ladicího programu (Pokud je připojena) a nelze přesměrovat.  
  
### <a name="remarks"></a>Poznámky  
 Následující příklad zobrazuje jeden řádek výstupu generovaného z volání `AfxDumpStack` z rutiny tlačítko v aplikaci MFC dialogového okna:  
  
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
  
 Každý řádek na výše uvedeném výstupu označuje adresu poslední volání funkce, úplný název cesty modulu, který obsahuje volání funkce a prototyp funkce volána. Pokud volání funkce v zásobníku se neodehrává na přesnou adresu funkce, zobrazí se posunu bajtů.  
  
 Například následující tabulka popisuje první řádek výše výstupu:  
  
|Výstup|Popis|  
|------------|-----------------|  
|`00427D55:`|Zpáteční adresa poslední volání funkce.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|Úplná cesta název modulu, který obsahuje volání funkce.|  
|`void AfxDumpStack(unsigned long)`|Prototyp funkce volána.|  
|`+ 181 bytes`|Posun v bajtech od adresy prototypu funkce (v tomto případě `void AfxDumpStack(unsigned long)`) na návratovou adresu (v tomto případě `00427D55`).|  
  
 `AfxDumpStack` je k dispozici v ladění a nondebug verze knihovny MFC; Nicméně funkce je vždy propojovat staticky, i v případě, že spustitelný soubor používá knihovnu MFC ve sdílené knihovně DLL. V implementacích sdílené knihovny se funkce nachází ve MFCS42. Knihovny LIB (a jeho variant).  
  
 Chcete-li úspěšně používat tuto funkci:  
  
-   Soubor IMAGEHLP. Knihovna DLL musí být na vaší cestě. Pokud tuto knihovnu DLL, funkce se zobrazí chybová zpráva. Zobrazit [knihovna obrázků pomáhají](/windows/desktop/Debug/image-help-library) informace o sadě funkce poskytované IMAGEHLP.  
  
-   Moduly, které mají rámce v zásobníku musí obsahovat informace o ladění. Pokud neobsahují informace o ladění, funkce stále generuje trasování zásobníku, ale méně podrobný trasování.  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxenablememoryleakdump"></a>  Afxenablememoryleakdump –  
 Povolí nebo zakáže výpis paměti v destruktoru AFX_DEBUG_STATE.  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>Parametry  
*bDump*<br/>
[in] Hodnota TRUE označuje, že výpis paměti je povolená; Hodnota FALSE označuje, že výpis paměti je zakázaná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnota pro tento příznak.  
  
### <a name="remarks"></a>Poznámky  
 Pokud aplikace uvolní knihovnu MFC, knihovny MFC zkontroluje nevracení paměti. V tuto chvíli jsou všechny nevracení paměti hlášeny uživateli prostřednictvím **ladění** okno sady Visual Studio.  
  
 Pokud se vaše aplikace načte jiné knihovny než knihovnu MFC, budou některé přidělení paměti v této knihovně správně hlášené jako nevracení paměti. Nevracení paměti False může způsobit, že aplikace zavřete pomalu jako knihovna MFC ohlásí je. V takovém případě použijte `AfxEnableMemoryLeakDump` zakázat výpis paměti.  
  
> [!NOTE]
>  Pokud použijete tuto metodu k vypnutí možnosti výpis paměti, neobdržíte žádné sestavy nevracení paměti platné ve vaší aplikaci. Tato metoda byste měli používat, jenom Pokud jste si jisti, že sestavy nevracení paměti obsahuje nevracení paměti hodnotu false.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxenablememorytracking"></a>  Afxenablememorytracking –  
 Sledování diagnostiky paměti je obvykle povolené v ladicí verzi knihovny MFC.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Parametry  
 *bTrack*  
 Tuto hodnotu nastavíte na hodnotu TRUE zapne sledování; paměti FALSE vypne.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí nastavení příznak sledování povolit.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci použijte k zakázání sledování na části kódu, o kterém víte, že jsou správně přidělení bloků.  
  
 Další informace o `AfxEnableMemoryTracking`, naleznete v tématu [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Tato funkce funguje pouze v ladicí verzi knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxismemoryblock"></a>  Afxismemoryblock –  
 Testuje adresu paměti, abyste měli jistotu, představuje bloku paměti aktuálně aktivní, která byla přidělena diagnostických verzí **nové**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Odkazuje na blok paměti má být testována.  
  
 *nBytes*  
 Obsahuje délky bloku paměti v bajtech.  
  
 *plRequestNumber*  
 Odkazuje **dlouhé** celé číslo, které se vyplní číslo pořadí přidělení bloku paměti nebo nula, pokud nepředstavuje blok paměti aktuálně aktivní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud blok paměti v tuto chvíli přidělená a délka je správná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Také zkontroluje zadané velikosti oproti původní přidělená velikost. Pokud funkce vrátí nenulovou hodnotu, vrátí se číslo pořadí přidělení v *plRequestNumber*. Toto číslo představuje pořadí, ve kterém byl přidělen blok vzhledem k všechny ostatní **nové** přidělení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxisvalidaddress"></a>  Afxisvalidaddress –  
 Testuje libovolnou adresu paměti k zajištění, že je obsažen zcela v rámci programu paměťový prostor.  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>Parametry  
 *LP*  
 Odkazuje na adresu paměti má být testována.  
  
 *nBytes*  
 Obsahuje počet bajtů paměti, která má být testována.  
  
 *bReadWrite*  
 Určuje, zda je paměť pro čtení a zápis (pravda) nebo pouze pro čtení (FALSE).  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení ladění je zcela v rámci programu paměťový prostor; obsažené nenulovou hodnotu, pokud zadaná paměťová blokovat jinak 0.  
  
 V sestaveních bez ladění nenulovou hodnotu, pokud *lp* není NULL; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Adresa není omezen na bloky přidělaná **nové**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxisvalidstring"></a>  Afxisvalidstring –  
 Tuto funkci použijte k určení, zda je platný ukazatel na řetězec.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 *lpsz*  
 Ukazatel na test.  
  
 *nLength*  
 Určuje řetězec, který má být testována, v bajtech. Hodnota -1 znamená, že bude řetězec zakončený hodnotou null.  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení ladění, nenulovou hodnotu, pokud zadaný ukazatel odkazuje na řetězec zadané velikosti; jinak 0.  
  
 V sestaveních bez ladění nenulovou hodnotu, pokud *lpsz* není NULL; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxsetallochook"></a>  Afxsetallochook –  
 Nastaví hák, která umožňuje voláním zadanou funkci před každý blok paměti je přidělen.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Parametry  
 *pfnAllocHook*  
 Určuje název funkce volání. Viz poznámky pro prototyp funkce přidělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud chcete povolit přidělování; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přidělení paměti ladění knihovny Microsoft Foundation Class můžete volat funkci uživatelem definované připojení umožňuje uživateli sledování přidělování paměti a řídit, jestli je povolené přidělení. Funkce háku přidělení jsou prototypem následujícím způsobem:  
  
 **BOOL AFXAPI AllocHook (size_t** `nSize` **, BOOL** `bObject` **dlouhý** `lRequestNumber` **);**  
  
 *nSize*  
 Velikost přidělení navrhovaných paměti.  
  
 *bObject*  
 Hodnota TRUE, pokud je přidělení `CObject`-odvozeného objektu; jinak hodnota FALSE.  
  
 *lRequestNumber*  
 Číslo pořadí přidělení paměti.  
  
 Všimněte si, že AFXAPI konvence volání znamená, že volaný musí odebrat parametry ze zásobníku.  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses –  
 Volá funkci zadané iteraci pro všechny serializovatelný `CObject`-odvozené třídy v paměti aplikace.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parametry  
 *pfn*  
 Body iterace funkci volat pro každou třídu. Argumenty funkce mají ukazatel na `CRuntimeClass` objekt a ukazatel void doplňková data, která poskytuje volající funkci.  
  
 *pContext*  
 Odkazuje na volitelnými daty, která můžete zadat volající funkci iterace. Tento ukazatel může mít hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Serializovatelné `CObject`-odvozené třídy jsou třídy odvozeny pomocí DECLARE_SERIAL – makro. Ukazatel, který je předán `AfxDoForAllClasses` v *pContext* je předán do funkce zadané iteraci pokaždé, když je volána.  
  
> [!NOTE]
>  Tato funkce funguje pouze v ladicí verzi knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h 

##  <a name="afxdoforallobjects"></a>  Afxdoforallobjects –  
 Spustí funkci zadané iteraci pro všechny objekty odvozené z `CObject` , který byl přidělen s **nové**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parametry  
 *pfn*  
 Body iterace funkci pro každý objekt. Argumenty funkce mají ukazatel na `CObject` a ukazatel void doplňková data, která poskytuje volající funkci.  
  
 *pContext*  
 Odkazuje na volitelnými daty, která můžete zadat volající funkci iterace. Tento ukazatel může mít hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Zásobník, globální, nebo vložené objekty nejsou uvedené. Ukazatel předaný `AfxDoForAllObjects` v *pContext* je předán do funkce zadané iteraci pokaždé, když je volána.  
  
> [!NOTE]
>  Tato funkce funguje pouze v ladicí verzi knihovny MFC.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)