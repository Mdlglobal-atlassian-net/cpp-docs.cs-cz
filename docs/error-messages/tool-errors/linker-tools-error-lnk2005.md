---
title: Chyba linkerů LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353237"
---
# <a name="linker-tools-error-lnk2005"></a>Chyba linkerů LNK2005

> *symbol* již definovaný v objektu

*Symbol* symbolu byl definován více než jednou.

Po této chybě následuje závažná chyba [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

Obecně tato chyba znamená, že jste porušili *jedno pravidlo definice*, které umožňuje pouze jednu definici pro libovolnou šablonu, funkci, typ nebo objekt v daném souboru objektu a pouze jednu definici v celém spustitelném souboru pro externě viditelné objekty nebo funkce.

Zde jsou některé běžné příčiny této chyby.

- K této chybě může dojít, když soubor záhlaví definuje proměnnou. Pokud například tento soubor záhlaví zahrnete do více než jednoho zdrojového souboru v projektu, dojde k chybě:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Mezi možná řešení patří:

  - Deklarujte proměnnou `extern` `extern int global_int;`v souboru záhlaví: , pak ji definujte a `int global_int = 17;`volitelně inicializujte v jednom a pouze jednom zdrojovém souboru: . Tato proměnná je nyní globální, které můžete použít `extern`v libovolném zdrojovém souboru deklarováním , například zahrnutím souboru záhlaví. Doporučujeme toto řešení pro proměnné, které musí být globální, ale osvědčené softwarové inženýrství praxe minimalizuje globální proměnné.

  - Deklarujte `static int static_int = 17;` [proměnnou static :](../../cpp/storage-classes-cpp.md#static). To omezuje rozsah definice na aktuální soubor objektu a umožňuje více souborů objektů mít vlastní kopii proměnné. Nedoporučujeme definovat statické proměnné v souborech hlaviček z důvodu možného záměny s globálními proměnnými. Raději přesuňte statické definice proměnných do zdrojových souborů, které je používají.

  - Deklarujte proměnnou [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. To říká propojovacího systému vybrat jednu definici pro použití všechny externí odkazy a zahodit zbytek. Toto řešení je někdy užitečné při kombinování knihoven importu. V opačném případě nedoporučujeme jako způsob, jak se vyhnout chybám propojovacího linku.

- K této chybě může dojít, když soubor záhlaví `inline`definuje funkci, která není . Pokud tento soubor záhlaví zahrnete do více než jednoho zdrojového souboru, získáte ve spustitelném souboru více definic funkce.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Mezi možná řešení patří:

  - Přidejte `inline` klíčové slovo do funkce:

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - Odeberte tělo funkce ze souboru záhlaví a ponechte pouze deklaraci a poté implementujte funkci v jednom a pouze jednom zdrojovém souboru:

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- K této chybě může dojít také v případě, že definujete členské funkce mimo deklaraci třídy v souboru záhlaví:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Chcete-li tento problém vyřešit, přesuňte definice členské funkce uvnitř třídy. Členské funkce definované uvnitř deklarace třídy jsou implicitně vloženy.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- K této chybě může dojít, pokud propojíte více než jednu verzi standardní knihovny nebo CRT. Pokud se například pokusíte propojit maloobchodní a ladicí knihovny CRT nebo statické i dynamické verze knihovny nebo dvě různé verze standardní knihovny se spustitelným souborem, může být tato chyba hlášena mnohokrát. Chcete-li tento problém vyřešit, odeberte všechny kromě jedné kopie každé knihovny z příkazu odkaz. Nedoporučujeme kombinovat maloobchodní a ladicí knihovny nebo různé verze knihovny ve stejném spustitelném souboru.

   Chcete-li propojovacímu systému sdělit, aby používal jiné knihovny než výchozí hodnoty, zadejte na příkazovém řádku knihovny, které chcete použít, a pomocí možnosti [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) zakažte výchozí knihovny. V rozhraní IDE přidejte odkazy do projektu, abyste určili knihovny, které chcete použít, a pak otevřete dialogové okno **Stránky vlastností** pro váš projekt a na stránce **Vlastnosti Linker**, **Vstup** nastavte buď **Ignorovat všechny výchozí knihovny**, nebo **Ignorovat vlastnosti konkrétních výchozích knihoven,** chcete-li zakázat výchozí knihovny.

- K této chybě může dojít, pokud smícháte použití statických a dynamických knihoven při použití možnosti [/clr.](../../build/reference/clr-common-language-runtime-compilation.md) K této chybě může například dojít, pokud vytvoříte dll pro použití ve spustitelném souboru, který odkazuje ve statickém CRT. Chcete-li tento problém vyřešit, používejte pouze statické knihovny nebo pouze dynamické knihovny pro celý spustitelný soubor a pro všechny knihovny, které vytvoříte, aby je používaly ve spustitelném souboru.

- K této chybě může dojít, pokud je symbol zabalenou funkcí (vytvořenou kompilací s [/Gy)](../../build/reference/gy-enable-function-level-linking.md)a byl zahrnut do více než jednoho souboru, ale byl změněn mezi kompilacemi. Chcete-li tento problém vyřešit, překompilujte všechny soubory, které obsahují zabalenou funkci.

- K této chybě může dojít, pokud je symbol definován odlišně ve dvou členských objektech v různých knihovnách a používají se oba členské objekty. Jedním ze způsobů, jak tento problém vyřešit, když jsou knihovny staticky propojeny, je použití členského objektu pouze z jedné knihovny a zahrnutí této knihovny nejprve do příkazového řádku linkeru. Chcete-li použít oba symboly, musíte vytvořit způsob, jak je odlišit. Pokud například můžete vytvářet knihovny ze zdroje, můžete každou knihovnu zabalit do jedinečného oboru názvů. Případně můžete vytvořit novou knihovnu obálky, která používá jedinečné názvy k zabalení odkazů na jednu z původních knihoven, propojení nové knihovny s původní knihovnou a propojování spustitelného souboru s novou knihovnou namísto původní knihovny.

- K této chybě `extern const` může dojít, pokud je proměnná definována dvakrát a má v každé definici jinou hodnotu. Chcete-li tento problém vyřešit, definujte konstantu pouze jednou nebo použijte obory názvů nebo `enum class` definice k rozlišení konstant.

- K této chybě může dojít, pokud používáte uuid.lib v kombinaci s jinými soubory LIB, které definují identifikátory GUID (například oledb.lib a adsiid.lib). Příklad:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Chcete-li tento problém vyřešit, přidejte [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) do možnosti příkazového řádku linkeru a ujistěte se, že uuid.lib je první odkazovaná knihovna.
