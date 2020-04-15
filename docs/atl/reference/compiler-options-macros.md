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
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331622"
---
# <a name="compiler-options-macros"></a>Makra možností kompilátoru

Tato makra řídí specifické funkce kompilátoru.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, který umožňuje chyby v projektech převedených z předchozích verzí knihovny ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Definujte, jestli jeden nebo více objektů používá apartment threading.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Provede `CString` explicitní některé konstruktory, brání jakékoli neúmyslné převody.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Definujte toto makro, aby bylo možné použít standardní syntaxi standardu C++, která generuje chybu kompilátoru C4867, když se nestandardní syntaxe používá k inicializaci ukazatele na člennou funkci.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Definujte, jestli jeden nebo více objektů používá volné nebo neutrální zřetězení.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol, který označuje projekt bude mít objekty, které jsou označeny jako Oba, Free nebo Neutrální. Místo toho by měl ymamové [_ATL_FREE_THREADED](#_atl_free_threaded) použít.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, který zabraňuje výchozímu použití oboru názvů jako knihovny ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, který zabraňuje com související kód z kompilovány s projektem.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, který zabraňuje vtable ukazatel inicializován v konstruktoru třídy a destruktoru.|
|[ATL_NOINLINE](#atl_noinline)|Symbol, který označuje funkci by neměla být vložena.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Definujte, jestli všechny objekty používají model jednoho zřetězení.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Symbol, který umožňuje chyby v projektech převedených z předchozích verzí knihovny ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Poznámky

Před Visual C++ .NET 2002 atl zakázáno mnoho upozornění a ponechal je zakázáno tak, aby se nikdy neobjevil v uživatelském kódu. Konkrétně:

- Podmíněný výraz C4127 je konstantní.

- C4786 'identifier' : identifikátor byl zkrácen na znaky "číslo" v informacích o ladění

- C4201 nestandardní rozšíření použité : bezejmenná struktura / unie

- C4103 'název souboru' : používá #pragma balení pro změnu zarovnání

- C4291 'declaration' : nebyl nalezen žádný odpovídající operátor; paměť nebude uvolněna, pokud inicializace vyvolá výjimku

- C4268 'identifier' : 'const' statická/globální data inicializovaná s kompilátorem generovaným výchozím konstruktorem vyplní objekt nulami

- Nedostupný kód C4702

V projektech převedených z předchozích verzí jsou tato upozornění stále zakázána záhlavími knihoven.

Přidáním následujícího řádku do souboru *pch.h* *(stdafx.h* v sadě Visual Studio 2017 a starší) před zahrnutím záhlaví knihoven lze toto chování změnit.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Pokud `#define` je přidána, hlavičky seznamu atl jsou opatrní zachovat stav těchto upozornění tak, aby nebyly zakázány globálně (nebo pokud uživatel explicitně zakáže jednotlivá upozornění, není povolit).

Nové projekty `#define` mají tuto sadu v *pch.h* *(stdafx.h* v Sadě Visual Studio 2017 a starší) ve výchozím nastavení.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Definujte, jestli jeden nebo více objektů používá apartment threading.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje apartment threading. Popis modelů [zřetězení](../../atl/specifying-the-threading-model-for-a-project-atl.md) dostupných pro objekt KNIHOVNY ATL naleznete v tématu Určení modelu vláken projektu pro další možnosti zřetězení a [Options, ATL Simple Object Wizard.](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Provede `CString` explicitní některé konstruktory, brání jakékoli neúmyslné převody.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Poznámky

Když je definován tento konstruktor, všechny cstring konstruktory, které berou jeden parametr jsou kompilovány s explicit klíčové slovo, které zabraňuje implicitní převody vstupní argumenty. To například znamená, že když je definována _UNICODE, pokud se pokusíte použít řetězec char* jako argument konstruktoru CString, dojde k chybě kompilátoru. Toto makro použijte v situacích, kdy je třeba zabránit implicitním převodům mezi úzkými a širokými typy řetězců.

Pomocí _T makra na všechny argumenty řetězce konstruktoru můžete definovat _ATL_CSTRING_EXPLICIT_CONSTRUCTORS a vyhnout se chybám kompilace bez ohledu na to, zda je definován _UNICODE.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Definujte toto makro, aby bylo možné vynutit použití standardní syntaxe ANSI C++ pro ukazatel na členské funkce. Použití tohoto makra způsobí, že chyba kompilátoru C4867 bude generována při použití nestandardní syntaxe k inicializaci ukazatele na člennou funkci.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Poznámky

Knihovny KNIHOVNY ATL a Knihovny MFC byly změněny tak, aby odpovídaly vylepšenému standardnímu standardu c++ kompilátoru Microsoft C++. Podle standardu ANSI C++ by měla být `&CMyClass::MyFunc`syntaxe ukazatele na členovou funkci třídy .

Pokud [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) není definován (výchozí případ), KNIHOVNA ATL/MFC zakáže chybu C4867 v mapách maker (zejména mapy zpráv), aby kód, který byl vytvořen v dřívějších verzích, mohl pokračovat v sestavení jako dříve. Pokud definujete **_ATL_ENABLE_PTM_WARNING**, váš kód by měl být kompatibilní se standardem Jazyka C++.

Nestandardní formulář byl však zastaral. Je třeba přesunout existující kód do standardní syntaxe c++. Například následující kód:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

je potřeba změnit na:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Pro makra mapy přidejte znak ampersand '&'. Znak byste neměli přidávat znovu do kódu.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Definujte, jestli jeden nebo více objektů používá volné nebo neutrální zřetězení.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje volné zřetězení. Volné podprocesy je ekvivalentní modelu apartment s více vlákny. Popis modelů [zřetězení](../../atl/specifying-the-threading-model-for-a-project-atl.md) dostupných pro objekt KNIHOVNY ATL naleznete v tématu Určení modelu vláken projektu pro další možnosti zřetězení a [Options, ATL Simple Object Wizard.](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Symbol, který označuje projekt bude mít objekty, které jsou označeny jako Oba, Free nebo Neutrální.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Poznámky

Pokud je definován tento symbol, atl bude vyžádat kód, který bude správně synchronizovat přístup ke globálním datům. Nový kód by měl místo toho používat ekvivalentní [makro _ATL_FREE_THREADED.](#_atl_free_threaded)

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Symbol, který zabraňuje výchozímu použití oboru názvů jako knihovny ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Poznámky

Pokud tento symbol není definován, včetně atlbase.h bude provádět **pomocí oboru názvů ATL** ve výchozím nastavení, což může vést ke konfliktům názvů. Chcete-li tomu zabránit, definujte tento symbol.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Symbol, který zabraňuje com související kód z kompilovány s projektem.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

Symbol, který zabraňuje vtable ukazatel inicializován v konstruktoru třídy a destruktoru.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Poznámky

Pokud je zabráněno vtable ukazatel je zabráněno inicializována v konstruktoru třídy a destruktoru, propojovací zařízení můžete eliminovat vtable a všechny funkce, na které odkazuje. Rozbalí se na **__declspec(novtable)**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

Symbol, který označuje funkci by neměla být vložena.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parametry

*moje funkce*<br/>
Funkce, která by neměla být vložena.

### <a name="remarks"></a>Poznámky

Tento symbol použijte, pokud chcete zajistit, aby se funkce neinklarovala kompilátorem, i když musí být deklarována jako válčí, aby ji bylo možné umístit do souboru záhlaví. Rozbalí se na **__declspec(noinline)**.

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Definujte, zda všechny objekty používají model jednoho zřetězení

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Poznámky

Určuje, že objekt vždy běží v primárním vlákně COM. Popis modelů [zřetězení](../../atl/specifying-the-threading-model-for-a-project-atl.md) dostupných pro objekt KNIHOVNY ATL naleznete v tématu Určení modelu vláken projektu pro další možnosti zřetězení a [Options, ATL Simple Object Wizard.](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
