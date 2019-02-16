---
title: Soubory pokynů
ms.date: 11/04/2016
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
ms.openlocfilehash: 44566408a3afcfee7a15299a5845b5af385aeef8
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320689"
---
# <a name="hint-files"></a>Soubory pokynů

A *informačního souboru* pomáhá sadě Visual Studio identifikátory Visual C++, jako jsou názvy funkcemi a makry interpretovat integrované vývojové prostředí (IDE). Při otevření projektu jazyka Visual C++, integrovaném vývojovém prostředí od *systém analýzy* analyzuje kód v každý zdrojový soubor v projektu a shromažďuje informace o každém identifikátoru. Rozhraní IDE použije tyto informace pro podporu funkcí, jako **zobrazení tříd** prohlížeče a **navigační panel**.

Systém analýzy, která se používá v sadě Visual C++ 2010, rozumí syntaxe jazyka C/C++, ale můžete interpretuje výraz, který obsahuje makra. Příkaz může dojít k nesprávné interpretaci Pokud makro způsobí, že zdrojový kód není syntakticky správný, jak je uvedená. Příkaz se může stát syntakticky správný při kompilaci zdrojového kódu a nahradí preprocesor [identifikátor – makro](../preprocessor/hash-define-directive-c-cpp.md) s jeho definicí. Parsování systém funguje bez nutnosti sestavte projekt, protože používá soubory pokynů k interpretaci makra. Proto se procházení funkcí, jako **zobrazení tříd** je ihned k dispozici.

Obsahuje uživatelsky přizpůsobitelnými informačního souboru *pomocné parametry*, které mají stejnou syntaxi jako definice maker jazyka C/C++. Visual C++ obsahuje integrovanou informačního souboru, který stačí pro většinu projektů, ale můžete vytvořit vlastní soubory pokynů k vylepšení způsobu, jakým Visual Studio zpracovává identifikátory.

> [!IMPORTANT]
> Pokud změníte nebo přidáte informačního souboru, je nutné odstranit soubor SDF nebo VC.db souborů v řešení, aby se změny projevily.

## <a name="scenario"></a>Scénář

Předpokládejme, že následující kód je ve zdrojovém souboru, která zkoumáte **zobrazení tříd** prohlížeče. `STDMETHOD` – Makro deklaruje metodu s názvem `myMethod` , která přijímá jeden parametr a vrátí ukazatel **HRESULT**.

```cpp
// Source code file.
STDMETHOD(myMethod)(int parameter1);
```

Následující definice makra jsou v samostatných hlavičkovém souboru.

```cpp
// Header file.
#define STDMETHOD(method) HRESULT (STDMETHODCALLTYPE * method)
#define STDMETHODCALLTYPE __stdcall
#define HRESULT void*
```

Systém analýzy nemůže interpretovat zdrojového kódu, protože funkce s názvem `STDMETHOD` se zdá být deklarována, a že je syntakticky nesprávný prohlášení, protože má dva seznamy parametrů. Systém analýzy neotevře hlavičkový soubor definice pro zjišťování `STDMETHOD`, `STDMETHODCALLTYPE`, a `HRESULT` makra. Protože nelze interpretovat systém analýzy `STDMETHOD` – makro, ignoruje celý výraz a potom pokračuje v analýze.

Parsování systém nepoužívá soubory hlaviček, protože váš projekt může záviset na jeden nebo více důležitých souborů hlaviček. Pokud změn v souboru hlaviček, systém analýzy pravděpodobně nutné prozkoumat všechny soubory hlaviček v projektu, který může zpomalit výkon rozhraní IDE. Místo toho využívá analýzy systém pokyny, které určují způsob zpracování `STDMETHOD`, `STDMETHODCALLTYPE`, a `HRESULT` makra.

Jak víte, že potřebujete nápovědu? A pokud potřebujete nápovědu, jaký typ by měl vytvořit? Jeden podpis, že je potřeba Nápověda je-li zobrazit identifikátor v **zobrazení tříd** není konzistentní s zobrazení v **Editor**. Například **zobrazení tříd** mohou zobrazovat existuje člen třídy, o kterém víte, nebo je nesprávný název člena. Další informace o typech pokynů, které řeší běžné problémy najdete v části co makra vyžadují A pomocný parametr? části dále v tomto tématu.

## <a name="architecture"></a>Architektura

Soubory pokynů se vztahují na fyzické adresáře, ne logických adresářů použité v **Průzkumníka řešení**. Není nutné přidat do projektu soubor pokynů mají nějaký efekt. Soubory pokynů využívá systém analýzy pouze v případě, že analyzuje zdrojové soubory.

Každý soubor pomocný parametr je pojmenován **cpp.hint**. Proto může obsahovat informačního souboru, ale pouze jeden pomocný parametr souboru může dojít v určitém adresáři.

Váš projekt může být ovlivněna nula nebo více soubory pokynů. Pokud nejsou žádné soubory nápovědy, systém analýzy využívá i metody chyba obnovení ignorovat nečitelné zdrojového kódu. V opačném případě analýzy systému používá k hledání a získání pokynů následující strategii.

### <a name="search-order"></a>Pořadí hledání

Systém analýzy prohledání adresářů pro soubory pokynů v tomto pořadí.

- Adresář, který obsahuje instalační balíček pro Visual C++ (**vcpackages**). Tento adresář obsahuje integrovanou nápovědu soubor, který popisuje symboly v často používané systémové soubory, jako například **windows.h**. V důsledku toho projekt automaticky zdědí většina z těchto pomocných parametrů, které potřebuje.

- Cesta z kořenového adresáře zdrojového souboru do adresáře, který obsahuje zdrojový soubor samotný. V obvyklou pro projekty Visual C++ kořenový adresář obsahuje soubor řešení nebo projektu.

   Výjimkou z tohoto pravidla je-li *stop soubor* v cestě ke zdrojovému souboru. Stop soubor poskytuje větší kontrolu nad pořadí hledání a je libovolný soubor s názvem **cpp.stop**. Namísto spuštění z kořenového adresáře, prohledá systém analýzy z adresáře, který obsahuje stop soubor do adresáře, který obsahuje zdrojový soubor. V obvyklou pro projekty není nutné stop soubor.

### <a name="hint-gathering"></a>Pomocný parametr shromažďování

Informačního souboru obsahuje nulu nebo více *pomocné parametry*. Nápověda je definován nebo odstraněno stejně jako makra jazyka C/C++. To znamená `#define` direktivy preprocesoru vytvoří nebo předefinuje pomocného parametru a `#undef` pokyn odstraní.

Systém analýzy každý soubor pokynů se otevře v pořadí hledání je popsáno výše, shromáždí pokyny v každém souboru do sady *efektivní pokyny*a potom použije efektivní pokyny k interpretaci identifikátory v kódu.

Parsování systém používá následující pravidla shromažďování pomocné parametry.

- Pokud nový pomocný parametr určuje název, který již není definován, přidá nový pokyn název efektivní pokyny.

- Pokud nový pomocný parametr určuje název, který je již definován, nový pokyn předefinuje existující pomocný parametr.

- Pokud je nový pokyn `#undef` direktiv, který určuje existující efektivní pokyn, nový pokyn odstraní existující pomocný parametr.

První pravidlo znamená, že jsou efektivní pokyny dědí z dříve otevřených souborů pokynů. Poslední dvě pravidla znamenají, že pomocné parametry, které generují později v pořadí hledání můžete přepsat pomocných parametrů, ke kterým došlo dříve. Například můžete přepsat předchozí pomocných vytváření informačního souboru do adresáře, který obsahuje zdrojový soubor.

Popis shromažďování pomocných parametrů najdete v článku `Example` později v tomto tématu.

### <a name="syntax"></a>Syntaxe

Pomocné parametry se vytvoří a odstraní se stejnou syntaxí, jako direktivy preprocesoru, které vytvoříte a odstraníte makra. Systém pro analýzy ve skutečnosti používá preprocesoru C/C++ k vyhodnocení pomocné parametry. Další informace o direktivách preprocesoru, naleznete v tématu [#define – direktiva (C/C++)](../preprocessor/hash-define-directive-c-cpp.md) a [#undef – direktiva (C++)](../preprocessor/hash-undef-directive-c-cpp.md).

Prvky pouze neobvyklé syntaxe jsou `@<`, `@=`, a `@>` řetězců pro nahrazení. Toto jsou informačního souboru konkrétní nahrazení řetězce, které se používají pouze s *mapy* makra. Mapování je sada makra, které se vztahují data, funkce nebo událostí do jiných dat, funkce nebo obslužné rutiny událostí. Například `MFC` používá k vytvoření mapy [zprávy maps](../mfc/reference/message-maps-mfc.md), a `ATL` používá k vytvoření mapy [objekt map](../atl/reference/object-map-macros.md). Konkrétní náhradní řetězce informačního souboru označuje počáteční, středně pokročilé i koncové prvky objektu map. Pouze název makra mapy je důležité. Každý řetězec nahrazení proto skryje záměrně implementace tohoto makra.

Pomocné parametry použijte následující syntaxi.

|Syntaxe|Význam|
|------------|-------------|
|`#define` *pomocný parametr name* *řetězci pro nahrazení*<br /><br /> `#define` *pomocný parametr name* `(` *parametr*,... `)` *řetězci pro nahrazení*|Direktivy preprocesoru, který definuje pomocného parametru nové nebo existující pokyn předefinuje. Po direktivě preprocesoru nahradí všechny výskyty *pomocný parametr name* ve zdrojovém kódu se *řetězci pro nahrazení*.<br /><br /> Druhá forma syntaxe definuje funkci podobnou nápovědu. Pokud dojde k pomocného parametru funkce jako ve zdrojovém kódu, preprocesor nejprve nahradí všechny výskyty *parametr* v *řetězci pro nahrazení* se ve zdrojovém kódu a nahradí odpovídající argument *pomocný parametr name* s *řetězci pro nahrazení*.|
|`@<`|Konkrétní soubor pokynů *řetězci pro nahrazení* , který označuje začátek sadu elementů mapy.|
|`@=`|Konkrétní soubor pokynů *řetězci pro nahrazení* , který určuje vložený prvek mapy. Mapa může mít více elementů mapy.|
|`@>`|Konkrétní soubor pokynů *řetězci pro nahrazení* , který označuje konec sady prvků mapy.|
|`#undef` *pomocný parametr name*|Direktivy preprocesoru odstraní existující pomocný parametr. Název v pomocném parametru poskytuje *pomocný parametr name* identifikátor.|
|`//` *Komentář*|Jednořádkový komentář.|
|`/*` *Komentář* `*/`|Víceřádkové komentáře.|

## <a name="what-macros-require-a-hint"></a>Co makra vyžadují nápovědu?

Určité typy maker může narušovat systém analýzy. Tato část popisuje typy makra, které mohou způsobovat problémy a typ pokynů, že lze vytvořit pro vyřešení tohoto problému.

### <a name="disruptive-macros"></a>Ničivé makra

Některé makra způsobit analýzy systém interpretuje zdrojového kódu, ale mohou být ignorovány, aniž by zhoršení možnosti procházení. Například jazyk anotace zdrojového kódu ([SAL](../c-runtime-library/sal-annotations.md)) vyřešit makra C++ atributy, které vám pomůžou najít programovací chyby. Pokud chcete ignorovat poznámky SAL procházení kódu, můžete chtít vytvořit informačního souboru, která skrývá anotace.

V následující zdrojový kód, zadejte parametr `FormatWindowClassName()` funkce je `PXSTR`, a název parametru je `szBuffer`. Ale analýzy chyby systému `_Pre_notnull_` a `_Post_z_` poznámky SAL pro typ parametru nebo název parametru.

**Zdrojový kód:**

```cpp
static void FormatWindowClassName(_Pre_notnull__Post_z_ PXSTR szBuffer)
```

**Strategie:** Definice null

Strategie v této situaci se zachází poznámky SAL, jako kdyby neexistovala. K tomuto účelu zadejte pokyn, jejichž náhradní řetězec má hodnotu null. V důsledku toho systém analýzy ignoruje poznámky a **zobrazení tříd** prohlížeče je nezobrazí. (Visual C++ obsahuje integrovanou informačního souboru, který skryje poznámky SAL.)

**Soubor pokynů:**

```cpp.hint
#define _Pre_notnull_
```

### <a name="concealed-cc-language-elements"></a>Elementy jazyka C/C++ skryté

Typický případ, že systém analýzy špatně interpretuje zdrojový kód je makro, které skryje C/C++ [interpunkci](../cpp/punctuators-cpp.md) nebo [– klíčové slovo](../cpp/keywords-cpp.md) token. Tj makru může obsahovat polovinu dvojice interpunkční znaky, jako `<>`, `[]`, `{}`, a `()`.

V následující zdrojový kód `START_NAMESPACE` – makro skryje levou složenou závorku (`{`).

**Zdrojový kód:**

```cpp
#define START_NAMESPACE namespace MyProject {
```

**Strategie:** Kopírování s přímým přístupem

Pokud sémantiku makra jsou důležité pro uživatele z procházení, vytvoření pomocného parametru, který je stejný jako makra. Systém analýzy přeloží makra na definice v souboru nápovědy.

Všimněte si, že obsahuje-li makra ve zdrojovém souboru dalších maker, tato makra jsou interpretovány pouze v případě, že jsou již v sadě efektivní pokyny.

**Soubor pokynů:**

```cpp.hint
#define START_NAMESPACE namespace MyProject {
```

### <a name="maps"></a>Mapy

Mapování se skládá z maker, která určí počáteční element koncový element a nula nebo více zprostředkujícího prvků. Systém analýzy špatně interpretuje mapy, protože každý makra mapy skryje elementy jazyka C/C++ a syntaxe úplný příkaz jazyka C/C++ se distribuuje do mnoha samostatných maker.

Definuje následující zdrojový kód `BEGIN_CATEGORY_MAP`, `IMPLEMENTED_CATEGORY`, a `END_CATEGORY_MAP` makra.

**Zdrojový kód:**

```cpp
#define BEGIN_CATEGORY_MAP(x)\
static const struct ATL::_ATL_CATMAP_ENTRY* GetCategoryMap() throw() {\
static const struct ATL::_ATL_CATMAP_ENTRY pMap[] = {
#define IMPLEMENTED_CATEGORY( catid ) { _ATL_CATMAP_ENTRY_IMPLEMENTED, &catid },
#define END_CATEGORY_MAP()\
   { _ATL_CATMAP_ENTRY_END, NULL } };\
   return( pMap ); }
```

**Strategie:** Identifikace prvků mapy

Zadejte pomocné parametry pro spuštění, střední (pokud existuje) a ukončení prvky objektu map. Použít náhradní řetězce speciální mapy, `@<`, `@=`, a `@>`. Další informace najdete v tématu `Syntax` v tomto tématu.

**Soubor pokynů:**

```cpp.hint
// Start of the map.
#define BEGIN_CATEGORY_MAP(x) @<
// Intermediate map element.
#define IMPLEMENTED_CATEGORY( catid ) @=
// Intermediate map element.
#define REQUIRED_CATEGORY( catid ) @=
// End of the map.
#define END_CATEGORY_MAP() @>
```

### <a name="composite-macros"></a>Složené makra

Složené makra obsahují jeden nebo více typů – makro, které matou systém analýzy.

Obsahuje následující zdrojový kód `START_NAMESPACE` makro, které určuje začátek rozsahu oboru názvů, a `BEGIN_CATEGORY_MAP` – makro, které určuje začátek objektu map.

**Zdrojový kód:**

```cpp
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```

**Strategie:** Kopírování s přímým přístupem

Pokyny pro vytvoření `START_NAMESPACE` a `BEGIN_CATEGORY_MAP` makra a pak vytvořte nápovědu pro `NSandMAP` makro, které je stejný, jak je uvedeno výše pro zdrojový kód. Můžete také složené – makro se skládá pouze rušivé makra a prázdné znaky, můžete definovat pokyn, jejichž řetězci pro nahrazení je definice null.

V tomto příkladu se předpokládá `START_NAMESPACE` už má pomocného parametru, jak je popsáno v tomto tématu v `Concealed C/C++ Language Elements` podnadpisu. A předpokládá `BEGIN_CATEGORY_MAP` má pomocného parametru, jak je popsáno výše u `Maps`.

**Soubor pokynů:**

```cpp.hint
#define NSandMAP START_NAMESPACE BEGIN_CATEGORY_MAP
```

### <a name="inconvenient-macros"></a>Nevyhovující makra

Některé makra lze interpretovat analýzy systému, ale zdrojový kód je obtížné číst, protože makra je dlouhý nebo složitý. Pro účely čitelnosti může poskytnout nápovědu, která zjednodušuje zobrazení makra.

**Zdrojový kód:**

```cpp
#define STDMETHOD(methodName) HRESULT (STDMETHODCALLTYPE * methodName)
```

**Strategie:** Zjednodušení

Vytvoření pomocného parametru, který zobrazuje jednodušší definici makra.

**Soubor pokynů:**

```cpp.hint
#define STDMETHOD(methodName) void* methodName
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak jsou pomocné parametry shromážděna z soubory pokynů. Stop soubory nejsou použity v tomto příkladu.

Následující obrázek znázorňuje některé z fyzického adresáře projektu v jazyce Visual C++. Soubory nápovědy jsou ve `vcpackages`, `Debug`, `A1`, a `A2` adresáře.

### <a name="hint-file-directories"></a>Pomocný parametr souborové adresáře

![Běžné a projekt&#45;konkrétní pomocný parametr souborové adresáře. ](../ide/media/hintfile.png "HintFile")

### <a name="directories-and-hint-file-contents"></a>Adresáře a obsah souboru nápovědy

Následující seznam obsahuje adresáře v tomto projektu, které obsahují soubory pokynů a obsah těchto souborů pokynů. Jenom některé z mnoha pomocné parametry v `vcpackages` directory informačního souboru jsou uvedené.

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

### <a name="effective-hints"></a>Efektivní pokyny

V následující tabulce jsou uvedeny efektivní pokyny pro zdrojové soubory v tomto projektu.

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

Následující poznámky platí pro v předchozím seznamu.

- Způsobují efektivní pokyny `vcpackages`, `Debug`, `A1`, a `A2` adresáře.

- **#Undef** direktivu `Debug` informačního souboru odebrat `#define _In_` pomocného parametru v `vcpackages` directory informačního souboru.

- Soubor pokynů v `A1` předefinuje `START_NAMESPACE`.

- `#undef` Pomocného parametru v `A2` directory odebrat pomocné parametry pro `OBRACE` a `CBRACE` v `Debug` directory informačního souboru.

## <a name="see-also"></a>Viz také

[Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[#define – direktiva (C++)](../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef – direktiva (C++)](../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Poznámky SAL](../c-runtime-library/sal-annotations.md)<br>
[Mapy zpráv](../mfc/reference/message-maps-mfc.md)<br>
[Makra Map zpráv](../atl/reference/message-map-macros-atl.md)<br>
[Makra map objektů](../atl/reference/object-map-macros.md)
