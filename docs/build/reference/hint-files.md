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
ms.openlocfilehash: af28dac17c57c8c0699950cc1fdb542642c01722
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707116"
---
# <a name="hint-files"></a>Soubory pokynů

A *informačního souboru* obsahuje makra, které by mohly jinak způsobit oblasti kódu přeskočení analyzátor databáze prohlížení jazyka C++. Při otevření sady Visual Studio C++ projektu, analyzátor kódu v každý zdrojový soubor v projektu analyzuje a vytvoří databázi s informacemi o každém identifikátoru. Integrované vývojové prostředí používá informace pomáhající při procházení kódu funkce, jako **zobrazení tříd** prohlížeče a **navigační panel**.

Analyzátor databáze prohlížení jazyka C++ je analyzátor přibližných shod, které mohou analyzovat velké množství kódu v krátkém čase. Jeden z důvodů, proč je rychlá totiž přeskočí obsah bloky. Například pouze zaznamenává umístění a parametry funkce a ignoruje jeho obsah. Určité makra může způsobovat problémy s heuristiky používá k určení začátku a konce bloku. Takové problémy způsobují oblasti kódu, aby se zaznamenávaly nesprávně.

Tyto oblasti přeskočené můžete manifest několika různými způsoby:

- Chybějící typy a funkce v **zobrazení tříd**, **přejít na** a **navigační panel**

- Nesprávný obory v **navigační panel**

- Návrhy **vytvořit deklaraci/definici** pro funkce, které jsou již definovány

Pomocný parametr soubor obsahuje uživatelsky přizpůsobitelnými pomocné parametry, které mají stejnou syntaxi jako definice maker jazyka C/C++. Visual C++ obsahuje integrovanou informačního souboru, který stačí pro většinu projektů. Můžete však vytvořit vlastní soubory pokynů ke zlepšení analyzátor určený k projektu.

> [!IMPORTANT]
> Pokud změníte nebo přidáte informačního souboru, je třeba provést další kroky, aby se změny projevily:
> - Ve verzích před Visual Studio 2017 verze 15.6: Odstraňte soubor SDF nebo VC.db soubor v řešení pro všechny změny.
> - V sadě Visual Studio 2017 verze 15.6 prostřednictvím 15.9: Zavřete a znovu otevřete řešení po přidání nových souborů nápovědy.

## <a name="scenario"></a>Scénář

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Bez informačního souboru `Function` nezobrazuje v **zobrazení tříd**, **přejít na** nebo **navigační panel**. Po přidání informačního souboru s touto definicí maker, analyzátor teď rozumí a nahradí `NOEXCEPT` – makro, což umožňuje správně analyzovat funkce:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Ničivé makra

Existují dvě kategorie makra, které narušují analyzátor:

- Makra, které provádí zapouzdření klíčová slova, která doplnění funkce

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   Pro tyto typy makra se vyžaduje jenom název – makro do informačního souboru:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makra, které obsahují nevyváženou hranaté závorky

   ```cpp
   #define BEGIN {
   ```

   Pro tyto typy makra se vyžaduje název makra a jeho obsah v souboru nápovědy:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Podpora editoru

Spouští se v sadě Visual Studio 2017 verze 15.8, že existuje několik funkcí k identifikaci rušivé makra:

- Makra, které jsou uvnitř oblastí na základě analyzátor přeskočila jsou zvýrazněné.

- Rychlé akce vytvoření informačního souboru, který zahrnuje zvýrazněné – makro, nebo pokud je existující soubor pokynů k přidá dané makro do informačního souboru.

![Zvýrazněné – makro. ](media/hint-squiggle-and-actions.png "Pomocného parametru vlnovku a rychlé akce")

Po provedení buď rychlé akce, analyzátor reparses soubory ovlivněné informačního souboru.

Ve výchozím nastavení je zvýrazněn – makro problému jako návrh. Zvýraznění lze změnit na něco zřetelnější, jako je například červenou nebo zelenou vlnovku. Použití **makra v oblastech přeskočeno procházení** možnost **podtržení vlnovkou kód** části **nástroje** > **možnosti**  >  **Textový Editor** > **C/C++** > **zobrazení**.

![Makra v přeskočené možnost procházení oblastech. ](media/skipped-regions-squiggle-option.png "Přeskočeno možnost vlnovku oblastech.")

## <a name="display-browsing-database-errors"></a>Zobrazení chyby databáze procházení

**Projektu** > **zobrazit chyby databáze procházení** příkaz nabídky zobrazí všechny oblasti, které se nepodařilo parsovat v **seznam chyb**. Tento příkaz slouží k zjednodušení vytváření počáteční informačního souboru. Analyzátor však nelze zjistit, pokud byl příčinu chyby rušivé – makro, proto je nutné vyhodnotit všechny chyby. Spustit **zobrazit chyby databáze procházení** příkazů a přejít k každé chybě načtení ovlivněných souboru v editoru. Po načtení souboru uvnitř oblasti jsou makra, se zvýrazněným. Rychlé akce pro přidání do informačního souboru můžete vyvolat. Po aktualizaci souboru pomocný parametr se automaticky aktualizuje seznam chyb. Případně, pokud upravujete soubor pokynů ručně můžete použít **znovu prohledat řešení** příkazu aktivovat aktualizaci.

## <a name="architecture"></a>Architektura

Soubory pokynů se vztahují na fyzické adresáře, není logický adresáře, které jsou zobrazené v **Průzkumníka řešení**. Není nutné pro přidání informačního souboru do projektu soubor pokynů mají nějaký efekt. Soubory pokynů využívá systém analýzy pouze v případě, že analyzuje zdrojové soubory.

Každý soubor pomocný parametr je pojmenován **cpp.hint**. Může obsahovat informačního souboru, ale pouze jeden pomocný parametr souboru může dojít v určitém adresáři.

Váš projekt může být ovlivněna nula nebo více soubory pokynů. Pokud nejsou žádné soubory nápovědy, systém analýzy využívá i metody chyba obnovení ignorovat nečitelné zdrojového kódu. V opačném případě analýzy systému používá k hledání a získání pokynů následující strategii.

### <a name="search-order"></a>Pořadí hledání

Systém analýzy prohledání adresářů pro soubory pokynů v tomto pořadí.

- Adresář, který obsahuje instalační balíček pro Visual C++ (**vcpackages**). Tento adresář obsahuje integrovanou nápovědu soubor, který popisuje symboly v často používané systémové soubory, jako například **windows.h**. V důsledku toho projekt automaticky zdědí většina z těchto pomocných parametrů, které potřebuje.

- Cesta z kořenového adresáře zdrojového souboru do adresáře, který obsahuje zdrojový soubor samotný. V typické aplikaci Visual Studio C++ projektu, kořenový adresář obsahuje soubor řešení nebo projektu.

   Výjimkou z tohoto pravidla je-li *stop soubor* v cestě ke zdrojovému souboru. Stop soubor je libovolný soubor s názvem **cpp.stop**. Stop soubor nabízí větší kontrolu nad pořadí hledání. Namísto spuštění z kořenového adresáře, prohledá systém analýzy z adresáře, který obsahuje stop soubor do adresáře, který obsahuje zdrojový soubor. V obvyklou pro projekty není nutné stop soubor.

### <a name="hint-gathering"></a>Pomocný parametr shromažďování

Informačního souboru obsahuje nulu nebo více *pomocné parametry*. Nápověda je definován nebo odstraněno stejně jako makra jazyka C/C++. To znamená `#define` direktivy preprocesoru vytvoří nebo předefinuje pomocného parametru a `#undef` pokyn odstraní.

Parsování systém otevře každý soubor pokynů v pořadí hledání popsané výše. Shromáždí pokyny v každém souboru do sady *efektivní pokyny*a potom použije efektivní pokyny k interpretaci identifikátory v kódu.

Systém analýzy používá k shromažďování pomocné parametry tato pravidla:

- Pokud nový pomocný parametr určuje název, který již není definován, přidá nový pokyn název efektivní pokyny.

- Pokud nový pomocný parametr určuje název, který je již definován, nový pokyn předefinuje existující pomocný parametr.

- Pokud je nový pokyn `#undef` direktiv, který určuje existující efektivní pokyn, nový pokyn odstraní existující pomocný parametr.

První pravidlo znamená, že jsou efektivní pokyny dědí z dříve otevřených souborů pokynů. Poslední dvě pravidla znamenají, že pomocné parametry později v pořadí hledání můžete přepsat dřívější pomocné parametry. Například můžete přepsat předchozí pomocných vytváření informačního souboru do adresáře, který obsahuje zdrojový soubor.

Popis shromažďování pomocných parametrů najdete v článku [příklad](#example) oddílu.

### <a name="syntax"></a>Syntaxe

Vytvářet a odstraňovat pomocných parametrů pomocí stejné syntaxe jako direktivy preprocesoru, vytvářet a odstraňovat makra. Systém pro analýzy ve skutečnosti používá preprocesoru C/C++ k vyhodnocení pomocné parametry. Další informace o direktivách preprocesoru, naleznete v tématu [#define – direktiva (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) a [#undef – direktiva (C++)](../../preprocessor/hash-undef-directive-c-cpp.md).

Prvky pouze neobvyklé syntaxe jsou `@<`, `@=`, a `@>` řetězců pro nahrazení. Tyto řetězce konkrétní náhrada informačního souboru se používají v *mapy* makra. Mapování je sada makra, které se vztahují data, funkce nebo událostí do jiných dat, funkce nebo obslužné rutiny událostí. Například `MFC` používá k vytvoření mapy [zprávy maps](../../mfc/reference/message-maps-mfc.md), a `ATL` používá k vytvoření mapy [objekt map](../../atl/reference/object-map-macros.md). Konkrétní náhradní řetězce informačního souboru označení počáteční, středně pokročilé i koncové prvky objektu map. Pouze název makra mapy je důležité. Každý řetězec nahrazení proto skryje záměrně implementace tohoto makra.

Pomocné parametry použijte následující syntaxi:

|Syntaxe|Význam|
|------------|-------------|
|`#define` *pomocný parametr name* *řetězci pro nahrazení*<br /><br /> `#define` *pomocný parametr name* `(` *parametr*,... `)` *řetězci pro nahrazení*|Direktivy preprocesoru, který definuje pomocného parametru nové nebo existující pokyn předefinuje. Po direktivě preprocesoru nahradí všechny výskyty *pomocný parametr name* ve zdrojovém kódu se *řetězci pro nahrazení*.<br /><br /> Druhá forma syntaxe definuje funkci podobnou nápovědu. Pokud dojde k pomocného parametru funkce jako ve zdrojovém kódu, preprocesor nejprve nahradí všechny výskyty *parametr* v *řetězci pro nahrazení* se ve zdrojovém kódu a nahradí odpovídající argument *pomocný parametr name* s *řetězci pro nahrazení*.|
|`@<`|Konkrétní soubor pokynů *řetězci pro nahrazení* , který označuje začátek sadu elementů mapy.|
|`@=`|Konkrétní soubor pokynů *řetězci pro nahrazení* , který určuje vložený prvek mapy. Mapa může mít více elementů mapy.|
|`@>`|Konkrétní soubor pokynů *řetězci pro nahrazení* , který označuje konec sady prvků mapy.|
|`#undef` *pomocný parametr name*|Direktivy preprocesoru odstraní existující pomocný parametr. Název v pomocném parametru poskytuje *pomocný parametr name* identifikátor.|
|`//` *Komentář*|Jednořádkový komentář.|
|`/*` *Komentář* `*/`|Víceřádkové komentáře.|

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak jsou pomocné parametry shromážděna z soubory pokynů. Stop soubory nejsou použity v tomto příkladu.

Na obrázku ukazuje některé z fyzického adresáře v sadě Visual Studio C++ projektu. Existují soubory pokynů v `vcpackages`, `Debug`, `A1`, a `A2` adresáře.

### <a name="hint-file-directories"></a>Pomocný parametr souborové adresáře

![Běžné a projekt&#45;konkrétní pomocný parametr souborové adresáře. ](media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Adresáře a obsah souboru nápovědy

Tento seznam obsahuje adresáře v tomto projektu, které obsahují soubory pokynů a obsah těchto souborů pokynů. Jenom některé z mnoha pomocné parametry v `vcpackages` directory informačního souboru patří:

- vcpackages

    ```cpp.hint
    // vcpackages (partial list)
    #define _In_
    #define _In_opt_
    #define _In_z_
    #define _In_opt_z_
    #define _In_count_(size)
    ```

- Ladění

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

### <a name="effective-hints"></a>Efektivní pokyny

Tato tabulka shrnuje efektivní pokyny pro zdrojové soubory v tomto projektu:

- Zdrojový soubor: A1_A2_B.cpp

- Efektivní pokyny:

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

Tyto poznámky platí pro v předchozím seznamu:

- Způsobují efektivní pokyny `vcpackages`, `Debug`, `A1`, a `A2` adresáře.

- **#Undef** direktivu `Debug` informačního souboru odebrat `#define _In_` pomocného parametru v `vcpackages` directory informačního souboru.

- Soubor pokynů v `A1` předefinuje `START_NAMESPACE`.

- `#undef` Pomocného parametru v `A2` directory odebrat pomocné parametry pro `OBRACE` a `CBRACE` v `Debug` directory informačního souboru.

## <a name="see-also"></a>Viz také:

[Soubor typy vytvořené pro sadu Visual Studio C++ projekty](file-types-created-for-visual-cpp-projects.md)<br>
[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef – direktiva (C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Poznámky SAL](../../c-runtime-library/sal-annotations.md)<br>

