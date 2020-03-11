---
title: Makra možností kompilátoru
ms.date: 08/19/2019
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
ms.openlocfilehash: 84083c696ee7bdcbb9538bf587c4aaded7a3932e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857168"
---
# <a name="compiler-options-macros"></a>Makra možností kompilátoru

Tato makra řídí konkrétní funkce kompilátoru.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, který umožňuje chyby v projektech převedených z předchozích verzí knihovny ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Definujte, zda jeden nebo více objektů používá dělení na vlákna.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Zpřístupňuje některé konstruktory `CString` explicitní a brání jakýmkoli neúmyslným převodům.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definujte toto makro, aby se použila C++ standardní syntaxe vyhovující standardu, která generuje chybu kompilátoru C4867, když se k inicializaci ukazatele na členskou funkci používá nestandardní syntaxe.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Definujte, jestli jeden nebo víc vašich objektů používá Volná nebo neutrální vlákna.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol, který označuje, že projekt bude mít objekty, které jsou označeny jako, Free nebo neutral. Místo toho by se mělo použít [_ATL_FREE_THREADED](#_atl_free_threaded) makra.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, který brání výchozímu použití oboru názvů jako ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, který brání kompilování kódu souvisejícího s COM s vaším projektem.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, který znemožňuje inicializaci ukazatele vtable v konstruktoru a destruktoru třídy.|
|[ATL_NOINLINE](#atl_noinline)|Symbol označující, že funkce by neměla být vložená.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Definujte, jestli všechny vaše objekty používají model jediného dělení na vlákna.|

##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Symbol, který umožňuje chyby v projektech převedených z předchozích verzí knihovny ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Poznámky

Před rozhraním Visual C++ .NET 2002 knihovna ATL zakázala mnoho upozornění a ponechána zakázaná, aby nikdy nezobrazovala v uživatelském kódu. Konkrétně:

- Podmíněný výraz C4127 je konstanta.

- C4786 ' identifier ': identifikátor byl zkrácen na ' Number ' znaků v ladicích informacích

- Používá se nestandardní rozšíření C4201: Nameless struct/Union

- C4103 ' filename ': pro změnu zarovnání se používá #pragma pack

- C4291 ' Declaration ': nenašel se žádný shodný operátor delete; paměť nebude uvolněna, pokud inicializace vyvolá výjimku.

- C4268 ' identifier ': statická/globální data ' const ' se inicializují s výchozím konstruktorem generovaným kompilátorem, který vyplní objekt nulami

- C4702 nedosažitelný kód

V projektech převedených z předchozích verzí jsou tato upozornění stále zakázána pomocí hlaviček knihoven.

Přidáním následujícího řádku do souboru *PCH. h* (*stdafx. h* v rámci sady Visual Studio 2017 a starší) před zahrnutím hlaviček knihoven můžete toto chování změnit.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Pokud je přidán tento `#define`, hlavičky ATL budou opatrní, aby zachovaly stav těchto upozornění, takže nejsou globálně zakázané (nebo pokud uživatel explicitně zakáže jednotlivá upozornění, nikoli jim povolit).

Ve výchozím nastavení mají nové projekty tento `#define` nastavené v souboru *PCH. h* (*stdafx. h* v sadě Visual Studio 2017 a starší).

##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Definujte, zda jeden nebo více objektů používá dělení na vlákna.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje zřetězení Apartment. Viz [Určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro jiné možnosti vlákna a [Možnosti, Průvodce jednoduchým objektem ATL](../../atl/reference/options-atl-simple-object-wizard.md) pro popis modelů vláken dostupných pro objekt ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Zpřístupňuje některé konstruktory `CString` explicitní a brání jakýmkoli neúmyslným převodům.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Poznámky

Při definování tohoto konstruktoru všechny konstruktory CString, které přijímají jeden parametr, jsou kompilovány pomocí klíčového slova Explicit, které brání implicitním převodům vstupních argumentů. To znamená, že pokud je definována _UNICODE například, pokud se pokusíte použít řetězcový znak * jako argument konstruktoru CString, výsledkem bude chyba kompilátoru. Toto makro použijte v situacích, kdy potřebujete zabránit implicitním převodům mezi úzkými a širšími typy řetězců.

Pomocí makra _T u všech řetězcových argumentů konstruktoru můžete definovat _ATL_CSTRING_EXPLICIT_CONSTRUCTORS a vyhnout se chybám kompilace bez ohledu na to, zda je definována _UNICODE.

##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Definujte toto makro, aby se vynutilo použití syntaxe C++ standardu ANSI pro ukazatel na členské funkce. Použití tohoto makra způsobí vygenerování chyby kompilátoru C4867, pokud se k inicializaci ukazatele na členskou funkci nepoužívá nestandardní syntaxe.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Poznámky

Knihovny ATL a MFC se změnily tak, aby odpovídaly C++ standardnímu C++ dodržování předpisů kompilátoru Microsoftu. Podle standardu ANSI C++ by měla být `&CMyClass::MyFunc`syntaxe ukazatele na členskou funkci třídy.

Pokud není definován [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) (výchozí případ), knihovna ATL/MFC zakáže chybu C4867 v mapách maker (zejména v mapách zpráv), aby kód, který byl vytvořen v dřívějších verzích, mohl pokračovat v sestavení jako dříve. Pokud definujete **_ATL_ENABLE_PTM_WARNING**, váš kód by měl C++ splňovat standardní předpisy.

Nestandardní forma je však zastaralá. Je nutné přesunout existující kód do C++ syntaxe standardu vyhovující standardu. Například následující kód:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

je potřeba změnit na:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Pro makra map přidejte znak ampersand ' & '. Neměli byste znak znovu přidat do kódu.

##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Definujte, jestli jeden nebo víc vašich objektů používá Volná nebo neutrální vlákna.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje volné zřetězení. Bezplatné dělení na vlákna je ekvivalentní modelu apartment s více vlákny. Viz [Určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro jiné možnosti vlákna a [Možnosti, Průvodce jednoduchým objektem ATL](../../atl/reference/options-atl-simple-object-wizard.md) pro popis modelů vláken dostupných pro objekt ATL.

##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Symbol, který označuje, že projekt bude mít objekty, které jsou označeny jako, Free nebo neutral.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Poznámky

Pokud je tento symbol definován, knihovna ATL si vyžádá kód, který bude správně synchronizovat přístup k globálním datům. Nový kód by měl místo toho používat ekvivalentní [_ATL_FREE_THREADED](#_atl_free_threaded) makra.

##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Symbol, který brání výchozímu použití oboru názvů jako ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Poznámky

Pokud tento symbol není definován, včetně atlbase. h, bude ve výchozím nastavení provedeno **pomocí oboru názvů ATL** , což může vést ke konfliktům pojmenování. Tomu zabráníte tak, že definujete tento symbol.

##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Symbol, který brání kompilování kódu souvisejícího s COM s vaším projektem.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>ATL_NO_VTABLE

Symbol, který znemožňuje inicializaci ukazatele vtable v konstruktoru a destruktoru třídy.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Poznámky

Pokud je zakázán ukazatel vtable v konstruktoru a destruktoru třídy, linker může eliminovat vtable a všechny funkce, na které odkazuje. Rozbalí se na **__declspec (vtable)** .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>ATL_NOINLINE

Symbol označující funkci by neměl být vložen.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parametry

*funkci*<br/>
Funkce, která by neměla být vložena.

### <a name="remarks"></a>Poznámky

Použijte tento symbol, pokud chcete zajistit, aby kompilátor neodkazoval, i když musí být deklarován jako inline, aby mohl být umístěn v hlavičkovém souboru. Rozbalí se na **__declspec (vloženo)** .

##  <a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Definujte, jestli všechny vaše objekty používají model s jedním vláknem.

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje, že se objekt vždy spouští v primárním vlákně COM. Viz [Určení modelu vláken projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) pro jiné možnosti vlákna a [Možnosti, Průvodce jednoduchým objektem ATL](../../atl/reference/options-atl-simple-object-wizard.md) pro popis modelů vláken dostupných pro objekt ATL.

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)
