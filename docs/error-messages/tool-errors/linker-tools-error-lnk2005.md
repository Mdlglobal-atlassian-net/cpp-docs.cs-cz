---
title: Chyba linkerů LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 8b4f75b90254c702ecb2afb65108278a59df69ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667282"
---
# <a name="linker-tools-error-lnk2005"></a>Chyba linkerů LNK2005

> *symbol* již definována v objektu

Symbol *symbol* byl definován více než jednou.

Tato chyba je následována závažná chyba [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).

### <a name="possible-causes-and-solutions"></a>Možné příčiny a řešení

Obecně platí, tato chyba znamená mají poškozen *jednu definici pravidla*, což umožňuje jenom jednu definici pro použité šablony, funkce, typ nebo objekt v souboru daný objekt a jenom jednu definici napříč celou spustitelný soubor pro externě viditelný objekty nebo funkce.

Tady jsou některé běžné příčiny této chyby.

- Této chybě může dojít, když soubor hlaviček definuje proměnnou. Například pokud zahrnete více než jednom zdrojovém souboru tento soubor hlaviček v projektu, vrátí chybu:

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   Možná řešení patří:

   - Deklarujte proměnnou `extern` v souboru hlaviček: `extern int global_int;`, pak je definujte a volitelně inicializovat v jednom a pouze jeden zdrojový soubor: `int global_int = 17;`. Tato proměnná je globální, můžete použít v libovolného zdrojového souboru deklarováním `extern`, například zahrnutím souboru hlaviček. Doporučujeme, abyste toto řešení pro proměnné, které musí být globální, ale vhodné softwarového inženýrství postup minimalizuje globální proměnné.

   - Deklarujte proměnnou [statické](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`. Omezuje rozsah definici pro aktuální soubor objektu a umožňuje více souborů objekt má své vlastní kopii proměnné. Nedoporučujeme definovat statické proměnné v souborech hlaviček z důvodu předešli nedorozuměním s globálními proměnnými. Raději k přesunutí definice statických proměnných do zdrojové soubory, které je používají.

   - Deklarujte proměnnou [selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`. Toto dá linkeru pokyn, vyberte jednu definici pro použití podle všechny externí odkazy a zrušit zbývající. Toto řešení je někdy užitečné při kombinování knihovny importu. V opačném případě nedoporučujeme ji tak, aby nedocházelo k chybám linkeru.

- Této chybě může dojít, když soubor hlaviček definuje funkci, která není `inline`. Pokud zahrnete více než jednom zdrojovém souboru tento soubor hlavičky, získáte více definicí funkce ve spustitelném souboru.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Možná řešení patří:

   - Přidat `inline` klíčové funkce:

        ```h
        // LNK2005_func_inline.h
        inline int sample_function(int k) { return 42 * (k % 167); }
        ```

   - Odeberte tělo funkce ze souboru hlaviček a ponechat jenom deklarace a pak implementovat funkci v jeden a pouze jeden zdrojový soubor:

        ```h
        // LNK2005_func_decl.h
        int sample_function(int);
        ```

        ```cpp
        // LNK2005_func_impl.cpp
        int sample_function(int k) { return 42 * (k % 167); }
        ```

- Této chybě může dojít také při definování členské funkce mimo deklaraci třídy v souboru hlaviček:

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   Chcete-li opravit tento problém, přesuňte definice členské funkce uvnitř třídy. Členské funkce definované uvnitř deklarace třídy jsou implicitně vložená.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- Této chybě může dojít, pokud připojíte více než jedna verze standardní knihovny nebo CRT. Například pokud budete chtít propojit jak maloobchodní a knihovny ladění CRT nebo statické a dynamické verze knihovny nebo dvě různé verze knihovny standard spustitelný soubor, tato chyba může být nahlášeno v mnoha případech. Chcete-li vyřešit tento problém, odeberte všechny kopie krom jedné každou knihovnu z příkazu link. Nedoporučujeme kombinovat maloobchodního prodeje a ladění knihoven nebo různými verzemi knihovny ve stejném spustitelném souboru.

   Sdělí linkeru, aby používat knihovny jiné než výchozí hodnoty, na příkazovém řádku zadejte knihoven, které chcete použít a použít [: / NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) možnost zakázat výchozí knihovny. V integrovaném vývojovém prostředí, přidejte odkazy do projektu k určení knihovny, které chcete použít a pak otevřete **stránky vlastností** dialogové okno pro váš projekt a **Linkeru**, **vstup** vlastnost Nastavte buď **ignorovat všechny výchozí knihovny**, nebo **ignorovat konkrétní výchozí knihovny** vlastnosti, které chcete zakázat výchozí knihovny.

- K této chybě může dojít, pokud je kombinovat používání statické a dynamické knihovny, při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnost. Této chybě může dojít například při vytváření knihovny DLL pro použití v spustitelný soubor, který odkazuje ve statické CRT. Chcete tento problém vyřešit, použijte pouze statické knihovny nebo pouze dynamické knihovny pro celý spustitelný soubor a všechny knihovny, kterou můžete používat ve spustitelném souboru.

- K této chybě může dojít, pokud symbol je zabalenou funkcí (vytvořené kompilací s [/Gy](../../build/reference/gy-enable-function-level-linking.md)) a je zahrnutý v více než jeden soubor, ale byl změněn mezi kompilacemi. Chcete-li vyřešit tento problém, znovu zkompilujte všechny soubory, které zahrnují zabalené funkce.

- Této chybě může dojít, pokud symbol je definována odlišně v dva členské objekty v jiných knihovnách a obě členské objekty se používají. Jedním ze způsobů chcete opravit tento problém, když jsou staticky propojené knihovny je použijte členského objektu z jediného knihovny a zahrňte tuto knihovnu nejprve do příkazového řádku linkeru. Pokud chcete použít obě symboly, musíte vytvořit způsob, jak odlišit. Pokud vytváříte knihovnu ze zdroje, můžete zabalit každou knihovnu v jedinečný obor názvů. Alternativně můžete vytvořit novou knihovnu obálky, který používá k zabalení odkazy na jednu z původní knihovny, odkaz nové knihovny původní knihovny, a potom odkaz spustitelný soubor do nové knihovny namísto původní knihovna jedinečné názvy.

- K této chybě může dojít, pokud `extern const` proměnná je definována dvakrát a má jinou hodnotu v každé definici. Chcete-li vyřešit tento problém, definovat konstantní pouze jednou, nebo použití oborů názvů nebo `enum class` definice k rozlišení konstanty.

- K této chybě může dojít, pokud použijete uuid.lib v kombinaci s jinými soubory LIB, které definují GUID (například oledb.lib a adsiid.lib). Příklad:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   Chcete-li tento problém vyřešit, přidejte [/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) možnosti příkazového řádku linkeru a ujistěte se, že je tento uuid.lib první knihovna odkazuje.
