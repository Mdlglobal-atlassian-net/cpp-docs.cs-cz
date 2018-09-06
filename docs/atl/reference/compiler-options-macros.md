---
title: Makra možností kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 087e03ea44388249817d6ffd70659a30e8bdabe0
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758619"
---
# <a name="compiler-options-macros"></a>Makra možností kompilátoru

Tato makra řízení kompilátoru specifické funkce.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, který umožňuje chyby v projektech, které jsou převedené z předchozích verzí knihovny ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Určete, zda jeden nebo více objektů použít podprocesový model apartment.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Díky určité `CString` konstruktory explicitní, brání všechny neúmyslnému převody.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Chcete-li použít standardní kompatibilní syntaxi C++, který vygeneruje chybu kompilátoru C4867, pokud není standardní syntaxe je použita k inicializaci ukazatele na členskou funkci definujte toto makro.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Určete, zda jeden nebo více objektů pomocí bezplatné nebo neutrální dělení na vlákna.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol, který označuje, projekt bude mít objekty, které jsou označeny jako obojí zdarma nebo neutrální. Makro [_ATL_FREE_THREADED](#_atl_free_threaded) by místo toho používat.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, který brání použití výchozí obor názvů jako knihovnu ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, který zabraňuje modelu COM související kód kompilován s projektem.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, který zabrání ukazatel vtable inicializaci konstruktor a destruktor třídy.|
|[ATL_NOINLINE](#atl_noinline)|Symbol, který označuje funkce by neměl být vložená.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Určete, zda všechny objekty používat jeden model vláken.|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

Symbol, který umožňuje chyby v projektech, které jsou převedené z předchozích verzí knihovny ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Poznámky

Před Visual C++ .NET 2002 ATL zakázané spoustu upozornění a doleva je zakázat, aby se nikdy zobrazila v uživatelském kódu. Konkrétně:

- C4127 podmíněný výraz je konstantní.

- C4786 'identifier': identifikátor se zkrátil na znaků 'number' v informacích o ladění

- C4201 používá se nestandardní rozšíření: struktura/sjednocení nameless

- C4103 filename: použít #pragma pack ke změně zarovnání

- C4291 "deklarace": byl nalezen žádný odpovídající operátor delete paměť se neuvolní, pokud při inicializaci dojde k výjimce

- C4268 'identifier': 'const' statická/globální data inicializovaná s konstruktorem default generovaným kompilátorem vyplní objekt nulami

- Nedosažitelný kód C4702

V projektech převedené z předchozích verzí tato upozornění stále zakázal hlavičky knihovny.

Toto chování lze změnit přidáním následující řádek do souboru stdafx.h před zahrnutím hlavičky knihovny.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Pokud tento `#define` se přidá, hlavičkách ATL. je pozor zachovat stav těchto upozornění tak, aby se globálně zakázané (nebo pokud uživatel explicitně zakáže jednotlivých upozornění, ne, aby se mohly).

Máte nové projekty `#define` ve výchozím nastavení v souboru stdafx.h.

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

Určete, zda jeden nebo více objektů použít podprocesový model apartment.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje podprocesový model apartment. V tématu [určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro ostatní vlákna možnosti, a [možnosti, Průvodce jednoduchý objekt knihovny ATL](../../atl/reference/options-atl-simple-object-wizard.md) popis práce s vlákny modely k dispozici pro objekt knihovny ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Díky určité `CString` konstruktory explicitní, brání všechny neúmyslnému převody.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Poznámky

Když je definována, všechny konstruktory CString, které vyžadovat jeden parametr se kompilují pomocí explicitní klíčové slovo, které brání implicitních převodů vstupní argumenty. To znamená například, že když je definována _UNICODE, při pokusu o použití char * řetězec jako argument konstruktoru CString a způsobí chybu kompilátoru. Použijte toto makro v situacích, kdy potřebujete zabránit implicitní převody mezi typy úzké a široké řetězce.

Pomocí makra _T na všechny řetězcové argumenty konstruktoru, můžete definovat _ATL_CSTRING_EXPLICIT_CONSTRUCTORS a vyhněte se chyby při kompilaci bez ohledu na to, zda je definován _UNICODE.

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

Pokud chcete vynutit použití syntaxe vyhovující standardu ANSI C++ pro ukazatele na členské funkce definujte toto makro. Pomocí tohoto makra způsobí chybu kompilátoru C4867 vygenerování při nestandardní syntaxe je použita k inicializaci ukazatele na členskou funkci.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Poznámky

Knihovny ATL a MFC se změnily tak, aby odpovídaly kompilátor Visual C++ vylepšené standard C++ dodržování předpisů. Podle standardu ANSI C++ by měl být syntaxe ukazatel na členskou funkci třídy `&CMyClass::MyFunc`.

Když [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) není definována (výchozí případ), ATL/MFC zakáže C4867 chyby v rámci služby maps – makro (zejména zprávy maps) tak, aby kód, který byl vytvořen ve starších verzích pokračovat v sestavení jako předtím. Pokud definujete **_ATL_ENABLE_PTM_WARNING**, váš kód by měl být kompatibilní s standard jazyka C++.

Ale nestandardní formuláře je zastaralá, tak budete potřebovat přesunout existující kód C++ standardní kompatibilní syntaxi. Například následující:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

By měl být změněn na:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Všimněte si, že pro mapu makra, které aplikacím dodávají znak '&', neměli byste přidávat ho znovu ve vašem kódu.

##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED

Určete, zda jeden nebo více objektů pomocí bezplatné nebo neutrální dělení na vlákna.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje, volných vláken. Volných vláken je ekvivalentní s více vlákny typu apartment modelu. V tématu [určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro ostatní vlákna možnosti, a [možnosti, Průvodce jednoduchý objekt knihovny ATL](../../atl/reference/options-atl-simple-object-wizard.md) popis práce s vlákny modely k dispozici pro objekt knihovny ATL.

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

Symbol, který označuje, projekt bude mít objekty, které jsou označeny jako obojí zdarma nebo neutrální.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Poznámky

Pokud tento symbol není definován, bude ATL o přijetí změn v kódu, který budou synchronizovat správně přístup ke globálním datům. Nový kód by měl použít makra ekvivalentní [_ATL_FREE_THREADED](#_atl_free_threaded) místo.

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

Symbol, který brání použití výchozí obor názvů jako knihovnu ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Poznámky

Pokud tento symbol není definován, včetně atlbase.h provede **s použitím oboru názvů ATL** ve výchozím nastavení, což může způsobit konflikty pojmenování. Chcete-li tomu zabránit, definujte tento symbol.

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

Symbol, který zabraňuje modelu COM související kód kompilován s projektem.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

Symbol, který zabrání ukazatel vtable inicializaci konstruktor a destruktor třídy.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Poznámky

Pokud ukazatel vtable se zabrání během inicializace v konstruktoru třídy a destruktor, linker vyloučit tabulku vtable a všechny funkce, na které odkazuje. Rozšíří **__declspec(novtable)**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

Symbol, který označuje funkce by neměl být vložená.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parametry

*MáFunkce*  
Funkce, která by neměla být vložená.

### <a name="remarks"></a>Poznámky

Pokud chcete zajistit, aby že funkce nezíská vložené kompilátorem, přestože musí být deklarován jako vložený, takže může být umístěn v záhlaví souboru, použijte tento symbol. Rozšíří **__declspec(noinline)**.

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

Určete, zda všechny objekty používat jeden model vláken

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje, že objekt vždy běží v primárním vláknu COM. V tématu [určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro ostatní vlákna možnosti, a [možnosti, Průvodce jednoduchý objekt knihovny ATL](../../atl/reference/options-atl-simple-object-wizard.md) popis práce s vlákny modely k dispozici pro objekt knihovny ATL.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
