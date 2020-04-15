---
title: EXPORTY
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328247"
---
# <a name="exports"></a>EXPORTY

Zavádí část jedné nebo více definic exportu, které určují exportované názvy nebo řadové názvy funkcí nebo dat. Každá definice musí být na samostatném řádku.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Poznámky

První *definice* může být na stejném `EXPORTS` řádku jako klíčové slovo nebo na následujícím řádku. Tá. Soubor DEF může obsahovat jeden nebo více `EXPORTS` příkazů.

Syntaxe *definice* exportu je:

> *název*\[__=__*internal_name*internal_name|*other_module.exported_name* \[ **\@**] _ojmenný_ \[název **NONAME**] ] \[ \[ **SOUKROMÉ**] | \[ **ÚDAJE**] ]

*entryname* je název funkce nebo proměnné, který chcete exportovat. To je nutné. Pokud se exportovaný název liší od názvu v dll, zadejte název exportu v dll pomocí *internal_name*. Pokud například dll exportuje funkci `func1` a chcete, `func2`aby ji volající používali jako , zadali byste:

```DEF
EXPORTS
   func2=func1
```

Pokud je exportovaný název z jiného modulu, zadejte název exportu v dll pomocí *other_module.exported_name*. Pokud například dll exportuje funkci `other_module.func1` a chcete, `func2`aby ji volající používali jako , zadali byste:

```DEF
EXPORTS
   func2=other_module.func1
```

Pokud název, který exportujete, pochází z jiného modulu, který exportuje podle ordinalu, zadejte vyřazovací pole exportu v dll pomocí *other_module*. __#__ *vysvěcené*. Například pokud vaše DLL exportuje funkci z jiného modulu, kde je řadové číslo `func2`42 a chcete, aby volající použít jako , byste zadat:

```DEF
EXPORTS
   func2=other_module.#42
```

Vzhledem k tomu, že kompilátor MSVC používá pro funkce *internal_name* jazyka C++název, `extern "C"` musíte použít upravený název internal_name nebo definovat exportované funkce pomocí ve zdrojovém kódu. Kompilátor také zdobí c funkce, které používají [__stdcall](../../cpp/stdcall.md) konvence volání s podtržítkem\_(\@) předponu a příponou složenou z znaku at ( ) následovanépočtem bajtů (v desítkovém čísle) v seznamu argumentů.

Chcete-li najít dekorované názvy vytvořené kompilátorem, použijte nástroj [DUMPBIN](dumpbin-reference.md) nebo propojovací ho [/MAP](map-generate-mapfile.md) možnost. Dekorované názvy jsou specifické pro kompilátor. Pokud exportujete dekorované názvy v . DEF, spustitelné soubory, které odkazují na dll musí být také vytvořeny pomocí stejné verze kompilátoru. Tím je zajištěno, že dekorované názvy volajícího odpovídají exportovaným názvům v . DEF.

Řadové \@ *ordinal* číslo můžete použít k určení, že číslo, a nikoli název funkce, přejde do exportní tabulky dll. Mnoho knihoven DLL systému Windows exportuje řadové číslovky pro podporu staršího kódu. Bylo běžné používat řadové číslovky v 16bitovém kódu systému Windows, protože může pomoci minimalizovat velikost dll. Nedoporučujeme exportovat funkce podle ordinal, pokud klienti vaší dll potřebují pro starší podporu. Vzhledem k tomu, . LIB soubor bude obsahovat mapování mezi řadovým a funkcí, můžete použít název funkce jako obvykle v projektech, které používají dll.

Pomocí volitelného klíčového slova **NONAME** můžete exportovat pouze podle pravidla a zmenšit velikost exportní tabulky ve výsledné dll. Pokud však chcete použít [getprocaddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) na dll, musíte znát ordinal, protože název nebude platný.

Volitelné klíčové slovo **PRIVATE** zabrání zahrnutí *názvu entry* do knihovny importu generované linkem. Nemá vliv na export v obraze také generované LINK.

Volitelné klíčové slovo **DATA** určuje, že export je data, nikoli kód. Tento příklad ukazuje, jak můžete `exported_global`exportovat datovou proměnnou s názvem :

```DEF
EXPORTS
   exported_global DATA
```

Existují čtyři způsoby exportu definice uvedené v doporučeném pořadí:

1. Klíčové slovo [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu

1. Prohlášení `EXPORTS` v . SOUBOR DEF

1. Specifikace [/EXPORT](export-exports-a-function.md) v příkazu LINK

1. [Direktiva komentáře](../../preprocessor/comment-c-cpp.md) ve zdrojovém kódu formuláře `#pragma comment(linker, "/export: definition ")`. Následující příklad ukazuje #pragma direktivu `PlainFuncName` komentáře před deklarací `_PlainFuncName@4` funkce, kde je upravený název a je upravený název funkce:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

#pragma direktiva je užitečná, pokud potřebujete exportovat název neupravené funkce a mít různé exporty v závislosti na konfiguraci sestavení (například v 32bitových nebo 64bitových sestaveních).

Všechny čtyři metody lze použít ve stejném programu. Když link vytvoří program, který obsahuje exporty, vytvoří také knihovnu importu, pokud . Exp soubor se používá v sestavení.

Tady je příklad oddílu EXPORTS:

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Při exportu proměnné z dll pomocí . DEF, není nutné zadat `__declspec(dllexport)` na proměnné. Však v každém souboru, který používá `__declspec(dllimport)` DLL, musíte stále používat na prohlášení dat.

## <a name="see-also"></a>Viz také

[Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)
