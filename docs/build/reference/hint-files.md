---
title: Soubory pokynů
ms.date: 02/26/2019
f1_keywords:
- cpp.hint
- vc.hint.file
helpviewer_keywords:
- stop file
- cpp.hint
- hint file
- cpp.stop
- Class View, hint file
ms.assetid: 17194f66-cf62-4523-abec-77db0675ab65
ms.openlocfilehash: ca111fcb8b0fc511fda3bbb3a4769ebc9fdd28bc
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189010"
---
# <a name="hint-files"></a>Soubory pokynů

*Soubor s nápovědou* obsahuje makra, která by jinak způsobila, že oblasti kódu budou přeskočeny analyzátorem databáze C++ procházení. Když otevřete projekt sady Visual Studio C++ , analyzátor analyzuje kód v každém zdrojovém souboru v projektu a vytvoří databázi s informacemi o každém identifikátoru. Rozhraní IDE používá tyto informace k podpoře funkcí pro procházení kódu, jako je **zobrazení tříd** prohlížeč a **navigační panel**.

Analyzátor C++ databáze procházení je přibližný analyzátor, který může v krátké době analyzovat velké objemy kódu. Jedním z důvodů je, že to je rychlé, protože přeskočí obsah bloků. Například zaznamenává pouze umístění a parametry funkce a ignoruje její obsah. Určitá makra mohou způsobit problémy s heuristickými metodami, které slouží k určení začátku a konce bloku. Tyto problémy způsobují nesprávné zaznamenávání oblastí kódu.

Tyto vynechané oblasti mohou být v manifestu vícenásobným způsobem:

- Chybějící typy a funkce v **zobrazení tříd**, **Přejít na** a **navigační panel**

- Nesprávné obory v **navigačním panelu**

- Návrhy na **vytvoření deklarace/definice** pro funkce, které jsou již definovány

Soubor s nápovědou obsahuje uživatelsky přizpůsobitelné Rady, které mají stejnou syntaxi jako definiceC++ C/makra. Vizuál C++ obsahuje integrovaný soubor pokynů, který je pro většinu projektů dostačující. Můžete však vytvořit vlastní soubory pokynů pro zlepšení analyzátoru konkrétně pro váš projekt.

> [!IMPORTANT]
> Pokud upravíte nebo přidáte soubor pokynů, je nutné provést další kroky, aby se změny projevily:
> - Ve verzích před Visual Studio 2017 verze 15,6: Odstraňte soubor. sdf nebo soubor VC. DB v řešení pro všechny změny.
> - V aplikaci Visual Studio 2017 verze 15,6 a novější: po přidání nových souborů pokynů toto řešení zavřete a znovu otevřete.

## <a name="scenario"></a>Scénář

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Bez souboru nápovědy se `Function` nezobrazuje v **zobrazení tříd**, **Přejít na** nebo **navigační panel**. Po přidání souboru s nápovědou v této definici makra analyzátor nyní rozumí a nahrazuje makro `NOEXCEPT`, které umožňuje správně analyzovat funkci:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Rušivá makra

Existují dvě kategorie maker, které mají rušivý dopad na analyzátor:

- Makra, která odpouzdřují klíčová slova, která naformátují funkci

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   U těchto typů maker se v souboru nápovědy vyžaduje jenom název makra:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makra, která obsahují nevyvážené závorky

   ```cpp
   #define BEGIN {
   ```

   U těchto typů maker se v souboru nápovědy vyžaduje název makra i jeho obsah:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Podpora editoru

Od verze Visual Studio 2017 verze 15,8 existuje několik funkcí, které identifikují rušivá makra:

- Jsou zvýrazněna makra, která jsou v oblastech, které byly přeskočeny analyzátorem.

- K dispozici je rychlá akce pro vytvoření souboru nápovědy, který obsahuje zvýrazněné makro, nebo pokud existuje existující soubor pokynů pro přidání makra do souboru pokynů.

![Zvýrazněné makro](media/hint-squiggle-and-actions.png "Vlnovka s nápovědou a rychlé akce")

Po provedení některé z rychlých akcí analyzátor znovu analyzuje soubory ovlivněné souborem nápovědy.

Ve výchozím nastavení je makro problému zvýrazněno jako návrh. Zvýraznění lze změnit na něco, co je patrné, například červená nebo zelená vlnovka. V části **nástroje** > **Možnosti** > **textový editor** > **C++ C/**  > **zobrazení**použijte možnost **makra v seznamu vynechané oblasti procházení** v části **vlnovky kódu** .

![Makra v případě vynechané možnosti oblastí procházení](media/skipped-regions-squiggle-option.png "Byla vynechána možnost vlnovku pro vynechané oblasti.")

## <a name="display-browsing-database-errors"></a>Zobrazit chyby databáze procházení

Příkaz nabídky **Zobrazit chyby databáze** v **projektu** > zobrazení procházení zobrazí všechny oblasti, které se nepodařilo analyzovat v **Seznam chyb**. Příkaz slouží k zjednodušení sestavení počátečního souboru s nápovědou. Analyzátor ale nemůže sdělit, zda příčinou chyby bylo rušivé makro, takže je nutné vyhodnotit každou chybu. Spusťte příkaz **Zobrazit chyby databáze procházení** a přejděte k jednotlivým chybám, abyste načetli ovlivněný soubor v editoru. Když je soubor načtený, pokud jsou nějaká makra uvnitř oblasti, zvýrazní se. Můžete vyvolat rychlé akce, které je třeba přidat do souboru nápovědy. Po aktualizaci souboru nápovědy se seznam chyb aktualizuje automaticky. Případně, pokud upravujete soubor pokynů ručně, můžete použít příkaz pro **opětovné prohledání řešení** a aktivovat aktualizaci.

## <a name="architecture"></a>Architektura

Soubory pokynů se týkají fyzických adresářů, nikoli logických adresářů zobrazených v **Průzkumník řešení**. Nemusíte přidávat soubor pokynů do projektu, aby měl soubor pokynů efekt. Systém analýzy používá soubory pokynů pouze v případě, že analyzuje zdrojové soubory.

Každý soubor s nápovědou má název **cpp. Hint**. Mnoho adresářů může obsahovat soubor s nápovědou, ale v konkrétním adresáři může dojít pouze k jednomu souboru s nápovědou.

Projekt může mít vliv na žádný nebo více souborů s nápovědou. Pokud nejsou k dispozici žádné soubory pokynů, analytický systém používá techniky obnovení chyb pro ignorování nečitelného zdrojového kódu. V opačném případě analytický systém používá následující strategii k hledání a shromažďování pomocných postupů.

### <a name="search-order"></a>Pořadí hledání

Systém analýzy hledá v adresářích soubory pokynů v následujícím pořadí.

- Adresář, který obsahuje instalační balíček pro Visual C++ (**vcpackages**). Tento adresář obsahuje vestavěný soubor pokynů, který popisuje symboly v často používaných systémových souborech, jako je například **Windows. h**. V důsledku toho projekt automaticky zdědí většinu tipů, které potřebuje.

- Cesta z kořenového adresáře zdrojového souboru do adresáře, který obsahuje samotný zdrojový soubor. V typickém projektu sady C++ Visual Studio obsahuje kořenový adresář soubor řešení nebo projektu.

   Výjimkou z tohoto pravidla je, pokud je *soubor stop* v cestě ke zdrojovému souboru. Soubor stop je libovolný soubor s názvem **cpp. stop**. Soubor stop poskytuje další kontrolu nad pořadím vyhledávání. Místo spuštění z kořenového adresáře prohledává systém analýzy z adresáře, který obsahuje soubor stop, do adresáře, který obsahuje zdrojový soubor. V typickém projektu nepotřebujete soubor stop.

### <a name="hint-gathering"></a>Shromažďování pokynů

Soubor s nápovědou obsahuje nula nebo více *tipů*. Pomocný parametr je definován nebo odstraněn stejně jako makro C neboC++ . To znamená, že direktiva preprocesoru `#define` vytvoří nebo předefinuje pomocný parametr a direktiva `#undef` odstraní pomocný parametr.

Systém analýzy otevře všechny soubory pokynů v pořadí hledání, které bylo popsáno dříve. Sestaví porady jednotlivých souborů do sady *efektivních pomocných*parametrů a pak pomocí efektivních pomocných parametrů interpretuje identifikátory ve vašem kódu.

Systém analýzy používá tato pravidla ke shromáždění tipů:

- Pokud nová Nápověda Určuje název, který ještě není definovaný, přidá nový pokyn název k efektivním pomocným parametrům.

- Pokud nový parametr určí název, který je již definován, Nový pomocný parametr znovu definuje existující nápovědu.

- Pokud je nový pomocný parametr `#undef` direktivou, která určuje existující efektivní pomocný parametr, nový pokyn odstraní existující nápovědu.

První pravidlo znamená, že účinné pomocné parametry jsou zděděné z dříve otevřených souborů pokynů. Poslední dvě pravidla znamenají, že pomocný parametr pozdější v pořadí hledání může přepsat předchozí nápovědu. Můžete například přepsat všechny předchozí pomocné parametry, pokud vytvoříte soubor pokynů v adresáři, který obsahuje zdrojový soubor.

Informace o tom, jak se shromažďují pomocné údaje, najdete v části [příklad](#example) .

### <a name="syntax"></a>Syntaxe

Pomocné parametry můžete vytvořit a odstranit pomocí stejné syntaxe jako direktivy preprocesoru pro vytváření a odstraňování maker. Ve skutečnosti systém analýzy používá k vyhodnocení pokynů C/C++ preprocesor. Další informace o direktivách preprocesoru naleznete v tématu direktiva [#define (c/C++)](../../preprocessor/hash-define-directive-c-cpp.md) a [Direktiva #undef (cC++/)](../../preprocessor/hash-undef-directive-c-cpp.md).

Jedinými neobvyklými syntaktickými prvky jsou `@<`, `@=`a `@>` nahrazující řetězce. Tyto nahrazující řetězce specifické pro soubor s nápovědou jsou používány pouze v makrech *map* . Mapa je sada maker, která se vztahují na data, funkce nebo události do jiných dat, funkcí nebo obslužných rutin událostí. `MFC` například používá mapy k vytváření [map zpráv](../../mfc/reference/message-maps-mfc.md)a `ATL` používá mapy k vytváření [map objektů](../../atl/reference/object-map-macros.md). Nahrazující řetězce specifické pro soubor s nápovědou označují počáteční, mezilehlé a koncové prvky mapy. Pouze název mapového makra je podstatný. Proto každý nahrazující řetězec záměrně skrývá implementaci makra.

Pomocné parametry používají tuto syntaxi:

|Syntaxe|Význam|
|------------|-------------|
|*pomocný parametr `#define` –* *nahrazování názvů – řetězec*<br /><br /> `#define` parametr *-name* `(` *parametr*,...`)`*náhradní řetězec*|Direktiva preprocesoru, která definuje nový pomocný parametr nebo předefinuje existující nápovědu. Po direktivě nahradí preprocesor všechny výskyty *názvu pomocného parametru* ve zdrojovém kódu pomocí *řetězce nahrazení*.<br /><br /> Druhá forma syntaxe definuje pomocný parametr podobný funkci. Pokud se ve zdrojovém kódu vyskytne pomocný parametr, preprocesor nejprve nahradí každý výskyt *parametru* v *řetězci pro nahrazení* odpovídajícím argumentem ve zdrojovém kódu a pak nahradí *pomocný parametr názvem* s *náhradním řetězcem*.|
|`@<`|*Řetězec nahrazení* specifický pro soubor s nápovědou, který označuje začátek sady prvků mapy.|
|`@=`|*Řetězec nahrazení* specifický pro soubor s nápovědou, který označuje pomocný element mapy. Mapa může mít více elementů mapy.|
|`@>`|*Řetězec nahrazení* specifický pro soubor s nápovědou, který označuje konec sady prvků mapy.|
|*pomocný parametr `#undef` – název*|Direktiva preprocesoru, která odstraní existující pomocný parametr. Název pomocného parametru je uveden pomocí identifikátoru *názvu pomocného parametru* .|
|*komentář* `//`|Jednořádkový komentář.|
|`/*` *komentář* `*/`|Víceřádkový komentář.|

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak se z souborů pokynů shromažďují pomocné parametry. V tomto příkladu nejsou používány soubory stop.

Ilustrace znázorňuje některé fyzické adresáře v projektu sady Visual Studio C++ . Existují soubory pokynů v adresářích `vcpackages`, `Debug`, `A1`a `A2`.

### <a name="hint-file-directories"></a>Adresáře souborů pokynů

![Společné a specifické&#45;adresáře souborů nápovědy pro konkrétní projekt](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Adresáře a obsah souboru pokynů

Tento seznam obsahuje adresáře v tomto projektu, které obsahují soubory pokynů, a obsah těchto souborů s nápovědou. V seznamu pomocného adresáře `vcpackages` se uvádí jenom některé z mnoha pomocných parametrů:

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Ladit

    ```cpp.hint
    // Debug
    #undef _In_
    #define OBRACE {
    #define CBRACE }
    #define RAISE_EXCEPTION(x) throw (x)
    #define START_NAMESPACE namespace MyProject {
    #define END_NAMESPACE }
    ```

- A1

    ```cpp.hint
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    ```

- A2

    ```cpp.hint
    // A2
    #undef OBRACE
    #undef CBRACE
    ```

### <a name="effective-hints"></a>Efektivní Nápověda

Tato tabulka uvádí efektivní nápovědu pro zdrojové soubory v tomto projektu:

- Zdrojový soubor: A1_A2_B. cpp

- Efektivní Nápověda:

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    // Debug...
    #define RAISE_EXCEPTION(x) throw (x)
    // A1
    #define START_NAMESPACE namespace A1Namespace {
    // ...Debug
    #define END_NAMESPACE }
    ```

Tyto poznámky se vztahují na předchozí seznam:

- Efektivní pomocné parametry se nacházejí v adresářích `vcpackages`, `Debug`, `A1`a `A2`.

- Direktiva **#undef** v souboru s nápovědou `Debug` odebrala v souboru pokynů adresáře `vcpackages` nápovědu `#define _In_`.

- Soubor pokynů v adresáři `A1` znovu definuje `START_NAMESPACE`.

- Pomocný parametr `#undef` v adresáři `A2` odebral pomocný parametr pro `OBRACE` a `CBRACE` v souboru pokynů pro `Debug` adresář.

## <a name="see-also"></a>Viz také:

[Typy souborů vytvořených pro projekty sady C++ Visual Studio](file-types-created-for-visual-cpp-projects.md)<br>
[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef – direktiva (C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Poznámky SAL](../../c-runtime-library/sal-annotations.md)<br>

