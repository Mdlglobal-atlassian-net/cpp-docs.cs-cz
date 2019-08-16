---
title: EXPORTY
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 8338f27d35d3779a55b83b70c7a3eef285a91f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492887"
---
# <a name="exports"></a>EXPORTY

Zavádí část jedné nebo více definicí exportu, které určují exportované názvy nebo pořadí funkcí nebo dat. Každá definice musí být na samostatném řádku.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Poznámky

První *definice* může být na stejném řádku jako `EXPORTS` klíčové slovo nebo na dalším řádku. Okně. DEF soubor může obsahovat jeden nebo více `EXPORTS` příkazů.

Syntaxe pro *definici* exportu je:

> *entryname*\[ __=__ *internal_name*|*other_module.exported_name*] \[ **\@** _ordinal_ \[**NONAME**] ] \[ \[**PRIVATE**] | \[**DATA**] ]

*Název_položky* je funkce nebo název proměnné, který chcete exportovat. To je povinné. Pokud se název, který exportujete, liší od názvu v knihovně DLL, zadejte název exportu v knihovně DLL pomocí *internal_name*. Například pokud vaše knihovna DLL exportuje funkci `func1` a chcete, aby ji volající používali jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=func1
```

Pokud je název, který exportujete z nějakého jiného modulu, zadejte název exportu v knihovně DLL pomocí *other_module. exported_name*. Například pokud vaše knihovna DLL exportuje funkci `other_module.func1` a chcete, aby ji volající používali jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=other_module.func1
```

Pokud název, který exportujete, pochází z jiného modulu, který exportuje podle pořadového čísla, zadejte pořadí exportu v knihovně DLL pomocí *other_module*. __#__ *ordinální číslo* Například pokud vaše knihovna DLL exportuje funkci z jiného modulu, kde je pořadovým číslem 42 a chcete, aby ji volající používali jako `func2`, zadali byste:

```DEF
EXPORTS
   func2=other_module.#42
```

Vzhledem k tomu, že kompilátor MSVC používá C++ pro funkce dekorace názvů, musíte buď použít dekorované jméno *internal_name* , nebo definovat exportované funkce `extern "C"` pomocí ve zdrojovém kódu. Kompilátor také upraví funkce jazyka C, které používají konvenci volání [__stdcall](../../cpp/stdcall.md) s podtržítkem (\_) a příponu složenou z znaku ' Sign (\@) následovaný počtem bajtů (v desítkové soustavě) v seznamu argumentů.

Chcete-li najít dekorované názvy vytvářené kompilátorem, použijte nástroj [DUMPBIN](dumpbin-reference.md) nebo parametr linker [/map](map-generate-mapfile.md) . Dekorované názvy jsou specifické pro kompilátor. Pokud exportujete dekorované názvy do. DEF soubor, spustitelné soubory, které odkazují na knihovnu DLL, musí být také sestaveny pomocí stejné verze kompilátoru. Tím se zajistí, že dekorované názvy v volajícím odpovídají exportovaným názvům v. Soubor DEF.

Můžete použít \@ *pořadové* číslo, které určuje, že číslo, a nikoli název funkce, přejde do tabulky exportu knihovny DLL. Mnoho souborů DLL systému Windows má za účelem podpory staršího kódu exportovat ordinální čísla. Bylo běžné použít anglické řadové číslovky v 16bitovém kódu Windows, protože může přispět k minimalizaci velikosti knihovny DLL. Nedoporučujeme exportovat funkce podle pořadových čísel, pokud je klienti knihovny DLL nepotřebují pro podporu starší verze. Protože. Soubor LIB bude obsahovat mapování mezi pořadovým číslem a funkcí, můžete použít název funkce stejně jako obvykle v projektech, které používají knihovnu DLL.

Pomocí volitelného klíčového slova **NONAME** můžete exportovat jenom podle pořadového čísla a zmenšit velikost tabulky exportu ve výsledné knihovně DLL. Pokud však chcete použít [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) na knihovně DLL, je nutné znát pořadové číslo, protože název nebude platný.

Volitelné klíčové slovo **Private** brání *vstupu* v knihovně import generovaný odkazem. Nemá vliv na export v imagi, který je vygenerovaný ODKAZem.

Volitelná **data** klíčová slova určují, že export je data, nikoli kód. Tento příklad ukazuje, jak můžete exportovat datovou proměnnou s `exported_global`názvem:

```DEF
EXPORTS
   exported_global DATA
```

Existují čtyři způsoby, jak definici exportovat, v seznamu Doporučené pořadí:

1. Klíčové slovo [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu

1. `EXPORTS` Příkaz v. DEF soubor

1. Specifikace [/Export](export-exports-a-function.md) v příkazu Link

1. Direktiva [Komentáře](../../preprocessor/comment-c-cpp.md) ve zdrojovém kódu formuláře `#pragma comment(linker, "/export: definition ")`. Následující příklad ukazuje direktivu #pragma komentáře před deklarací funkce, kde `PlainFuncName` je nedekorovaný název a `_PlainFuncName@4` je dekorovaným názvem funkce:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

Direktiva #pragma je užitečná v případě, že potřebujete exportovat nedekorovaný název funkce a mít různé exporty v závislosti na konfiguraci sestavení (například v 32ch nebo 64 sestaveních).

Všechny čtyři metody lze použít ve stejném programu. Když propojení vytvoří program, který obsahuje export, vytvoří také knihovnu importu, pokud není. Soubor EXP se používá v sestavení.

Tady je příklad oddílu EXPORTs:

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Při exportu proměnné z knihovny DLL pomocí. DEF soubor, není nutné zadávat `__declspec(dllexport)` proměnnou. V jakémkoli souboru, který používá knihovnu DLL, je však stále nutné použít `__declspec(dllimport)` na deklaraci dat.

## <a name="see-also"></a>Viz také:

[Pravidla pro příkazy definice modulu](rules-for-module-definition-statements.md)
