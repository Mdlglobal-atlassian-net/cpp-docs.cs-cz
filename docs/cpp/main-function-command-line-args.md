---
title: Hlavní funkce a argumenty příkazového řádku (C++)
description: Hlavní funkce je vstupním bodem pro C++ program.
ms.date: 12/10/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
ms.openlocfilehash: 95e774700c63dc815f6d814bfda84a38a38d4e6e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302396"
---
# <a name="main-function-and-command-line-arguments"></a>Hlavní funkce a argumenty příkazového řádku

Všechny C++ programy musí mít funkci `main`. Pokud se pokusíte zkompilovat C++ projekt *. exe* bez funkce main, kompilátor vyvolá chybu. (Knihovny Dynamic-Link a statické knihovny nemají funkci `main`.) Funkce `main` je tam, kde začíná provádění zdrojového kódu, ale před tím, než program zadá funkci `main`, jsou všechny členy statické třídy bez explicitních inicializátorů nastaveny na nulu. V Microsoft C++jsou globální statické objekty také inicializovány před vstupem do `main`. U funkce `main`, která neplatí pro žádné jiné C++ funkce, platí několik omezení. Funkce `main`:

- Nemůže být přetížen (viz [přetížení funkce](function-overloading.md)).
- Nelze deklarovat jako **inline**.
- Nelze deklarovat jako **static**.
- Nelze zabrat její adresu.
- Nelze ji volat.

Syntaxe deklarace pro `main` je následující:

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Specifické pro společnost Microsoft**

Pokud vaše zdrojové soubory používají znaky Unicode, můžete použít `wmain`, což je verze `main`s velkým znakem. Syntaxe deklarace pro `wmain` je následující:

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

Můžete také použít `_tmain`, která je definována v Tchar. h. `_tmain` překládá na `main`, pokud není definována _UNICODE. V takovém případě `_tmain` přeloží na `wmain`.

Pokud není zadána žádná návratová hodnota, kompilátor poskytne návratovou hodnotu nula. Alternativně lze funkce `main` a `wmain` deklarovat jako vracející **typ void** (žádná návratová hodnota). Pokud deklarujete `main` nebo `wmain` jako vrácení **void**, nemůžete vrátit ukončovací kód do nadřazeného procesu nebo operačního systému pomocí příkazu [return](../cpp/return-statement-in-program-termination-cpp.md) . Chcete-li vrátit ukončovací kód, pokud je `main` nebo `wmain` deklarován jako **void**, je nutné použít funkci [Exit](../cpp/exit-function.md) .

**Specifické pro konec Microsoftu**

## <a name="command-line-arguments"></a>Argumenty příkazového řádku

Argumenty pro `main` nebo `wmain` umožňují pohodlné analýze argumentů příkazového řádku a volitelně také přístup k proměnným prostředí. Typy pro `argc` a `argv` jsou definovány jazykem. Názvy `argc`, `argv`a `envp` jsou tradiční, ale můžete je libovolně pojmenovat.

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

Definice argumentů jsou následující:

*argc*<br/>
Celé číslo, které obsahuje počet argumentů, které následují v *argv*. Parametr *argc* je vždycky větší nebo roven 1.

*argv*<br/>
Pole řetězců zakončených znakem null představující argumenty příkazového řádku zadané uživatelem programu. Podle konvence `argv[0]` je příkaz, se kterým se program vyvolá, `argv[1]` je první argument příkazového řádku a tak dále, dokud `argv[argc]`, což je vždycky NULL. Informace o potlačení zpracování příkazového řádku naleznete v tématu [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) .

První argument příkazového řádku je vždycky `argv[1]` a poslední z nich je `argv[argc - 1]`.

> [!NOTE]
> Podle konvence `argv[0]` je příkaz, se kterým se program vyvolá. Je ale možné vytvořit proces pomocí funkce [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) a pokud použijete první i druhý argument (*lpApplicationName* a *lpCommandLine*) `argv[0]`, nesmí být název spustitelného souboru. pomocí [GetModuleFileName –](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) načtěte název spustitelného souboru a jeho plně kvalifikovanou cestu.

**Specifické pro společnost Microsoft**

*envp*<br/>
Pole *envp* , což je společné rozšíření v mnoha systémech UNIX, se používá v Microsoftu C++. Je to pole řetězců, které představují proměnné nastavené v uživatelském prostředí. Toto pole je ukončeno prvkem NULL. Dá se deklarovat jako pole ukazatelů na **char** (`char *envp[]`) nebo jako ukazatel na ukazatele na **char** (`char **envp`). Pokud program používá `wmain` místo `main`, použijte **wchar_t** datový typ místo **char**. Blok prostředí předaný `main` a `wmain` je "zmrazená" kopie aktuálního prostředí. Pokud následně změníte prostředí prostřednictvím volání `putenv` nebo `_wputenv`, bude se změnit aktuální prostředí (vrácené `getenv` nebo `_wgetenv` a proměnná `_environ` nebo `_wenviron`), ale blok, na který envp odkazuje, se nezmění. Informace o potlačení zpracování prostředí naleznete v tématu [přizpůsobení zpracování příkazového řádku](../cpp/customizing-cpp-command-line-processing.md) . Tento argument je kompatibilní se standardem ANSI v jazyce C, ale ne v jazyce C++.

**Specifické pro konec Microsoftu**

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít argumenty *argc*, *argv*a *envp* k `main`:

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>Analýza C++ argumentů příkazového řádku

**Specifické pro společnost Microsoft**

Při interpretaciC++ argumentů uvedených na příkazovém řádku operačního systému používá Microsoft C/Startup kód následující pravidla:

- Argumenty jsou odděleny prázdným znakem, což je mezera nebo karta.

- Znak stříšky (^) není rozpoznán jako řídicí znak nebo oddělovač. Tento znak je před předáním do pole `argv` v programu zcela zpracován analyzátorem příkazového řádku v operačním systému.

- Řetězec obklopený dvojitými uvozovkami ("*String*") je interpretován jako jeden argument, bez ohledu na prázdné místo obsažené v. V argumentu může být vložen řetězec v uvozovkách.

- Dvojitá uvozovka před znakem zpětného lomítka (\\) je interpretována jako literální znak dvojité uvozovky (").

- Zpětná lomítka jsou interpretována doslova, pokud bezprostředně nepředchází uvozovky.

- Je-li sudý počet zpětných lomítek následován znakem dvojitých uvozovek, je jedno zpětné lomítko umístěno v poli `argv` pro každou dvojici zpětných lomítek a dvojité uvozovky jsou interpretovány jako oddělovač řetězců.

- Je-li lichý počet zpětných lomítek následovaný dvojitou uvozovkou, jedno zpětné lomítko je umístěno v poli `argv` pro každý pár zpětných lomítek a dvojité uvozovky je "Escape" zbývajícím zpětným lomítkem, což způsobuje, že je znak dvojité uvozovky (") umístěn v `argv`.

### <a name="example"></a>Příklad

Následující program ukazuje, jak jsou předány argumenty příkazového řádku:

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

Následující tabulka ukazuje příklad vstupu a očekávaného výstupu, který demonstruje pravidla v předchozím seznamu.

### <a name="results-of-parsing-command-lines"></a>Výsledky analýzy příkazových řádků

|Vstup z příkazového řádku|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**Specifické pro konec Microsoftu**

## <a name="wildcard-expansion"></a>Rozšíření zástupného znaku

**Specifické pro společnost Microsoft**

K zadávání argumentů názvů souborů a cest v příkazovém řádku lze používat zástupné znaky – otazník (?) a hvězdičku (*).

Argumenty příkazového řádku jsou zpracovávány rutinou s názvem `_setargv` (nebo `_wsetargv` v prostředí s velkým znakem), které ve výchozím nastavení nerozšiřují zástupné znaky na samostatné řetězce v poli `argv` řetězců. Další informace o povolení rozšíření zástupných znaků najdete v tématu [rozšiřování argumentů zástupného znaku](../c-language/expanding-wildcard-arguments.md).

**Specifické pro konec Microsoftu**

## <a name="customizing-c-command-line-processing"></a>Přizpůsobení zpracování příkazového řádku jazyka C++

**Specifické pro společnost Microsoft**

Pokud aplikace nepřijímá argumenty příkazového řádku, je možné ušetřit malé množství místa potlačením použití rutiny knihovny, která vykonává zpracování příkazového řádku. Tato rutina se nazývá `_setargv` a je popsána v tématu [rozšíření zástupných znaků](../cpp/wildcard-expansion.md). Chcete-li potlačit jeho použití, definujte rutinu, která neprovede nic v souboru obsahujícím funkci `main` a pojmenujte ji `_setargv`. Volání `_setargv` je pak vyhovující vaší definicí `_setargv`a verze knihovny není načtena.

Podobně pokud nikdy nepřistupujete k tabulce prostředí pomocí argumentu `envp`, můžete poskytnout vlastní prázdnou rutinu, která bude použita místo `_setenvp`, rutiny zpracování prostředí. Stejně jako u funkce `_setargv` musí být `_setenvp` deklarované jako **extern "C"** .

Váš program může volat do `spawn` nebo `exec` rodinu rutin v knihovně run-time jazyka C. Jde-li o tento případ, neměla by být rutina zpracování prostředí potlačena, protože slouží k předání prostředí z nadřazeného procesu podřízenému procesu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Základní koncepty](../cpp/basic-concepts-cpp.md)