---
title: EXPORTY
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 33b70c680bfc3db24f5326a2027fa9ec4740e3f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271343"
---
# <a name="exports"></a>EXPORTY

Představuje oddíl jednu nebo víc definic exportu určujících exportovaným názvům nebo řadové číslovky funkce nebo data. Každá definice musí být na samostatném řádku.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Poznámky

První *definice* může být na stejném řádku jako `EXPORTS` – klíčové slovo nebo na následujícím řádku. Na. Soubor DEF mohou obsahovat jednu nebo více `EXPORTS` příkazy.

Syntaxe pro export *definice* je:

> *entryname*\[__=__*internal_name*|*other_module.exported_name*] \[**\@**_ordinal_ \[**NONAME**] ] \[ \[**PRIVATE**] | \[**DATA**] ]

*název_položky* je název funkce nebo proměnná, která chcete exportovat. Toto je povinné. Pokud se název, který exportujete liší od názvu v knihovně DLL, zadejte název pro export v knihovně DLL pomocí *internal_name*. Například, pokud vaše knihovna DLL exportuje funkce `func1` a chcete, aby volající použít ho jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=func1
```

Pokud se název, který můžete exportovat z některých modulu, zadejte název pro export v knihovně DLL pomocí *other_module.exported_name*. Například, pokud vaše knihovna DLL exportuje funkce `other_module.func1` a chcete, aby volající použít ho jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=other_module.func1
```

Pokud se název, který můžete exportovat z jiného modulu, který exportuje podle pořadových čísel, určení export uživatele pořadovém místě v knihovně DLL pomocí *other_module*.__#__ *ordinální*. Například, pokud vaše knihovna DLL exportuje funkce z modulu, a to je 42 pořadovém místě, kde chcete, aby volající použít ho jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=other_module.#42
```

Protože kompilátor MSVC používá dekorování názvů pro C++ funkce, je nutné použít upravený název *internal_name* nebo definovat exportovaných funkcí s použitím `extern "C"` ve zdrojovém kódu. Kompilátor také upraví funkcí jazyka C, které používají [__stdcall](../../cpp/stdcall.md) podtržítkem konvence volání (\_) předponu a příponu tvořený zavináč (\@) následovaný počtem bajtů (v desítkové soustavě) v Seznam argumentů.

Pokud chcete zjistit dekorované názvy produkované kompilátorem, použijte [DUMPBIN](dumpbin-reference.md) nástroje nebo linker [/MAP](map-generate-mapfile.md) možnost. Dekorované názvy jsou specifické pro kompilátor. Pokud exportujete dekorované názvy ve. Soubor DEF spustitelné soubory, které na knihovnu DLL musí být sestaveny také pomocí stejné verze kompilátoru. Tím se zajistí, že dekorované názvy volajícího odpovídaly exportovaným názvům v. Soubor DEF.

Můžete použít \@ *ordinální* k určení, že číslo a ne název funkce, přejde do tabulky exportu knihovny DLL. Mnoho knihoven DLL Windows exportovat řadové číslovky důvodu podpory původního kódu. Bylo běžné použití řadové číslovky v 16bitového kódu Windows, protože může pomoct minimalizovat velikost knihovny DLL. Nedoporučujeme export funkcí podle pořadových čísel, pokud ho vaše knihovna DLL klienti potřebovat pro stále podporuje starší verze. Vzhledem k tomu,. LIB soubor bude obsahovat mapování mezi řadová číslovka a funkci, můžete použít název funkce, jako byste normálně v projektech, které používají knihovnu DLL.

Pomocí volitelného **NONAME** – klíčové slovo, můžete exportovat na základě pořadí pouze a snížit velikost tabulky exportu v výslednou knihovnu DLL. Nicméně pokud chcete použít [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) na knihovnu DLL, musíte znát řadová číslovka, protože nebude platný název.

Optional – klíčové slovo **PRIVÁTNÍ** brání *Název_položky* nebudou zahrnuty do knihovna importů generovaná odkaz. Export obrázku také generovány podle propojení nemá vliv.

Optional – klíčové slovo **DATA** Určuje, že export dat, není kód. Tento příklad ukazuje, jak jste mohli exportovat data proměnnou s názvem `exported_global`:

```DEF
EXPORTS
   exported_global DATA
```

Existují čtyři způsoby, jak exportovat definici uvedené v doporučené pořadí:

1. [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) – klíčové slovo ve zdrojovém kódu

1. `EXPORTS` Výroky. Soubor DEF

1. [/EXPORT](export-exports-a-function.md) specifikace v příkazu LINK

1. A [komentář](../../preprocessor/comment-c-cpp.md) směrnice ve zdrojovém kódu formuláře `#pragma comment(linker, "/export: definition ")`. Následující příklad ukazuje Direktiva #pragma komentář před deklarací funkce, kde `PlainFuncName` je nedekorovaný název a `_PlainFuncName@4` je upravený název funkce:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

Direktiva #pragma je užitečné, pokud je potřeba exportovat názvu nedekorovaných funkce a mají různé exporty v závislosti na konfiguraci sestavení (například v 32bitové nebo 64bitové sestavení).

Všechny čtyři metody je možné ve stejném programu. Při propojení buildů program, který obsahuje exporty, také vytvoří knihovnu importu, není-li. EXP soubor se používá v sestavení.

Tady je příklad oddílu EXPORTŮ:

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Při exportu proměnné z knihovny DLL pomocí. Soubor DEF, není nutné zadat `__declspec(dllexport)` na proměnnou. Ale v žádném souboru, který používá knihovnu DLL, musí stále používáte `__declspec(dllimport)` u deklarace data.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)
