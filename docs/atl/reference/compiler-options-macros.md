---
title: "Možnosti kompilátoru makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c224eb0c17a779c7ebda6f606713fe2219abba06
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-options-macros"></a>Možnosti kompilátoru makra
Tyto makra řízení kompilátoru konkrétní funkce.  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, který umožňuje chyby v projektech převést z předchozích verzí ATL.|  
|[_ATL_APARTMENT_THREADED –](#_atl_apartment_threaded)|Určete, zda jeden nebo více objektů použít dělení objektu apartment.|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Díky určité `CString` konstruktory explicitní, brání všechny neúmyslnému převody.|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Chcete-li použít C++ standardní kompatibilní syntaxi, která generuje chyba kompilátoru C4867 v případě jiných standardní syntaxi slouží k inicializaci ukazatel na členské funkce definujte toto makro.|  
|[_ATL_FREE_THREADED –](#_atl_free_threaded)|Zadejte, pokud jeden nebo více objektům používat volné nebo neutrální dělení na vlákna.|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol, který označuje, projekt bude mít objekty, které jsou označeny jako obě volné nebo neutrální. Makro [_atl_free_threaded –](#_atl_free_threaded) by měl být místo toho použít.|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, který brání použití výchozí obor názvů jako ATL.|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, který brání související COM kód kompilován s projektem.|  
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, který zabrání ukazatel vtable inicializaci v konstruktoru a destruktoru třídy.|  
|[ATL_NOINLINE](#atl_noinline)|Symbol, který označuje funkce by neměl být vložená.|  
|[_ATL_SINGLE_THREADED –](#_atl_single_threaded)|Určete, zda všechny vaše objektů, které používají jeden model vláken.|  
  
##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS  
 Symbol, který umožňuje chyby v projektech převést z předchozích verzí ATL.  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>Poznámky  
 Před Visual C++ .NET 2002 ATL zakázané spoustu upozornění a je zakázaná, aby se nikdy vám ukázal, v uživatelském kódu zanechali. Konkrétně:  
  
-   Podmíněným výrazem C4127 je konstant  
  
-   C4786 identifikátor: identifikátor byl zkrácen na znaky "číslo" v informace o ladění  
  
-   Nestandardní rozšíření C4201 používané: nameless struktura/sjednocení  
  
-   C4103 filename: #pragma pack lze změnit zarovnání  
  
-   C4291 deklarace: žádný odpovídající delete – operátor nalezen; Pokud se inicializace vyvolá výjimku, nebude uvolnit paměť  
  
-   C4268 "identifikátor": 'const' statické nebo globálních dat inicializován s kompilátoru generované výchozí konstruktor doplní objekt s nulami  
  
-   C4702 nedostupný kódu  
  
 V projektech převést z předchozích verzí jsou tato upozornění stále zakázal hlavičky knihoven.  
  
 Toto chování lze změnit přidáním následující řádek do souboru stdafx.h před zahrnutím hlavičky knihoven.  
  
 [!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 Pokud `#define` se přidá, ATL hlavičky jsou pozor, pokud chcete zachovat stav tato upozornění tak, že nejsou zakázané globálně (nebo uživatel explicitně zakáže jednotlivých upozornění nepovolíte je).  
  
 Nové projekty nainstalován tento `#define` ve výchozím nastavení v stdafx.h.  
  
##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED –  
 Určete, zda jeden nebo více objektů použít dělení objektu apartment.  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>Poznámky  
 Určuje dělení objektu apartment. V tématu [nastavení modelu vláken pro projekt](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro ostatní vlákna možnosti, a [možnosti, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) popis dělení na vlákna modely k dispozici pro objekt knihovny ATL.  
  
##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 Díky určité `CString` konstruktory explicitní, brání všechny neúmyslnému převody.  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je to definované, jsou všechny CString konstruktory, které přebírají jeden parametr kompilovat s explicitní klíčové slovo, které brání implicitní převody vstupní argumenty. To znamená, například, že když _UNICODE je definována, pokud se pokusíte použít char * řetězec jako argument konstruktoru CString, dojde k chybě kompilátoru. Použití tohoto makra v situacích, kdy potřebujete zabránit implicitní převody mezi řetězci úzké a široké typy.  
  
 Pomocí _T – makro všechny řetězcové argumenty konstruktoru, můžete definovat _ATL_CSTRING_EXPLICIT_CONSTRUCTORS a vyhnout se chybám kompilace bez ohledu na to, jestli je definován _UNICODE.  
  
##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING  
 Chcete-li vynutit použití syntaxe kompatibilní se standardem standard ANSI C++ pro ukazatel na členské funkce definujte toto makro. Pomocí této makro způsobí, že chyba kompilátoru C4867 má být vygenerován při nestandardní syntaxe slouží k inicializaci ukazatel na funkci člen.  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>Poznámky  
 Knihovny ATL a MFC změnilo tak, aby odpovídaly – kompilátor Visual C++ vylepšené standardní C++ dodržování předpisů. Podle standardu ANSI C++, musí mít syntaxe ukazatele na funkce člena třídy `&CMyClass::MyFunc`.  
  
 Když [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) není definován (výchozí případ), ATL a MFC zakáže C4867 chyby ve službě maps – makro (mapy zejména zpráv), aby kód, který byl vytvořen v dřívějších verzích můžete nadále sestavení jako předtím. Pokud definujete **_ATL_ENABLE_PTM_WARNING**, váš kód by měl být standard C++ kompatibilní.  
  
 Však nestandardní formuláře se již nepoužívá, takže potřebujete přesunout existujícího kódu C++ standardní kompatibilní syntaxi. Například následující:  
  
 [!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 By mělo být změněno na:  
  
 [!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 Všimněte si, že pro makra mapy, které přidávají znak 'a', můžete nesmí ji znovu přidejte v kódu.  
  
##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED –  
 Zadejte, pokud jeden nebo více objektům používat volné nebo neutrální dělení na vlákna.  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>Poznámky  
 Určuje, volných vláken. Volných vláken je ekvivalentní k modelu objektu apartment s více vlákny. V tématu [nastavení modelu vláken pro projekt](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro ostatní vlákna možnosti, a [možnosti, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) popis dělení na vlákna modely k dispozici pro objekt knihovny ATL.  
  
##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED  
 Symbol, který označuje, projekt bude mít objekty, které jsou označeny jako obě volné nebo neutrální.  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je definována tento symbol, ATL načte v kódu, který bude synchronizovat správně přístup ke globálním datům. Nový kód by měl použít ekvivalentní makro [_atl_free_threaded –](#_atl_free_threaded) místo.  
  
##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE  
 Symbol, který brání použití výchozí obor názvů jako ATL.  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud není definován tento symbol, včetně atlbase.h provede **pomocí oboru názvů ATL** ve výchozím nastavení, což může způsobit konflikty pojmenování. Chcete-li tomu zabránit, definujte tento symbol.  
  
##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT  
 Symbol, který brání související COM kód kompilován s projektem.  
  
```
_ATL_NO_COM_SUPPORT```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE inline
    myfunction
 { ... }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED –
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../../atl/specifying-the-threading-model-for-a-project-atl.md) for other threading options, and [Options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../../atl/reference/atl-macros.md)
