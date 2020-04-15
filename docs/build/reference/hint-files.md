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
ms.openlocfilehash: 8037cb8025cc85a8479528490e1512531cbcc035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322316"
---
# <a name="hint-files"></a>Soubory pokynů

*Soubor nápovědy* obsahuje makra, která by jinak způsobila přeskoče oblastí kódu analyzátorem databáze procházení jazyka C++. Při otevření projektu Visual Studio C++ analyzátor analyzuje kód v každém zdrojovém souboru v projektu a vytvoří databázi s informacemi o každém identifikátoru. IDE používá tyto informace pro podporu funkce procházení kódu, jako je například prohlížeč **zobrazení tříd a** navigační **panel**.

Analyzátor databáze procházení C++ je přibližný analyzátor, který může analyzovat velké množství kódu v krátkém čase. Jedním z důvodů, proč je to rychlé, je to, že přeskočí obsah bloků. Například zaznamenává pouze umístění a parametry funkce a ignoruje její obsah. Některá makra mohou způsobit problémy s heuristiky, které se používají k určení začátku a konce bloku. Tyto problémy způsobit oblasti kódu, které mají být zaznamenány nesprávně.

Tyto přeskočené oblasti se mohou projevit několika způsoby:

- Chybějící typy a funkce v **zobrazení tříd ,** **přejít na** a navigační **panel**

- Nesprávné obory na **navigačním panelu**

- Návrhy na **vytvoření deklarace/definice** pro funkce, které jsou již definovány

Soubor nápovědy obsahuje uživatelem přizpůsobitelné rady, které mají stejnou syntaxi jako definice maker C/C++. Visual C++ obsahuje předdefinovaný soubor nápovědy, který je dostačující pro většinu projektů. Můžete však vytvořit vlastní soubory nápovědy pro zlepšení analyzátoru speciálně pro váš projekt.

> [!IMPORTANT]
> Pokud změníte nebo přidáte soubor nápovědy, budete muset provést další kroky, aby se změny projevily:
>
> - Ve verzích před Visual Studio 2017 verze 15.6: Odstraňte soubor .sdf a/nebo VC.db soubor v řešení pro všechny změny.
> - Ve Visual Studiu 2017 verze 15.6 a novější: Zavřete a znovu otevřete řešení po přidání nových souborů nápovědy.

## <a name="scenario"></a>Scénář

```cpp
#define NOEXCEPT noexcept
void Function() NOEXCEPT
{
}
```

Bez souboru `Function` nápovědy se nezobrazuje v **zobrazení tříd ,** **přejděte na** nebo navigačním **panelu**. Po přidání souboru nápovědy s touto definicí makra `NOEXCEPT` analyzátor nyní rozumí a nahrazuje makro, což mu umožňuje správně analyzovat funkci:

```cpp.hint
#define NOEXCEPT
```

## <a name="disruptive-macros"></a>Rušivá makra

Analyzátor narušuje dvěma kategoriemi maker:

- Makra, která zapouzdřují klíčová slova, která zdobí funkci

   ```cpp
   #define NOEXCEPT noexcept
   #define STDMETHODCALLTYPE __stdcall
   ```

   U těchto typů maker je v souboru nápovědy vyžadován pouze název makra:

   ```cpp.hint
   #define NOEXCEPT
   #define STDMETHODCALLTYPE
   ```

- Makra obsahující nevyvážené závorky

   ```cpp
   #define BEGIN {
   ```

   Pro tyto typy maker je v souboru nápovědy vyžadován název makra i jeho obsah:

   ```cpp.hint
   #define BEGIN {
   ```

## <a name="editor-support"></a>Podpora editoru

Počínaje visual studio 2017 verze 15.8 existuje několik funkcí pro identifikaci rušivých maker:

- Makra, která jsou uvnitř oblastí přeskočených analyzátorem, jsou zvýrazněna.

- K dispozici je rychlá akce pro vytvoření souboru nápovědy, který obsahuje zvýrazněné makro, nebo pokud existuje existující soubor nápovědy, pro přidání makra do souboru nápovědy.

![Zvýrazněné makro.](media/hint-squiggle-and-actions.png "Vlnitost nápovědy a rychlé akce")

Po provedení některé z rychlých akcí analyzátor provede změny souborů ovlivněných souborem nápovědy.

Ve výchozím nastavení je makro problému zvýrazněno jako návrh. Zvýraznění lze změnit na něco výraznějšího, například červenou nebo zelenou vlnovku. Použijte možnost **Makra ve přeskočené oblasti procházení** v části **Kód squiggles** v části **Nástroje** > **Možnosti** > **textového editoru** > **C/C++** > **Zobrazení**.

![Makra v možnosti Přeskočené oblasti procházení.](media/skipped-regions-squiggle-option.png "Možnost překlápěcí oblasti squiggle.")

## <a name="display-browsing-database-errors"></a>Zobrazit chyby databáze procházení

Příkaz Příkaz**Chyby procházení aplikace** **Project** > Display Browsing Database Zobrazuje všechny oblasti, které se v **seznamu chyb**nepodařilo analyzovat . Příkaz je určen pro zjednodušení vytváření počátečního souboru nápovědy. Analyzátor však nemůže zjistit, zda příčinou chyby bylo rušivé makro, takže je nutné vyhodnotit každou chybu. Spusťte příkaz **Chyby procházení zobrazení** a přejděte na každou chybu, chcete-li načíst ohrožený soubor v editoru. Jakmile je soubor načten, pokud jsou v oblasti nějaká makra, jsou zvýrazněna. Můžete vyvolat rychlé akce a přidat je do souboru nápovědy. Po aktualizaci souboru nápovědy se seznam chyb automaticky aktualizuje. Případně, pokud upravujete soubor nápovědy ručně, můžete použít příkaz **Znovu prohledávat řešení** k aktivaci aktualizace.

## <a name="architecture"></a>Architektura

Soubory nápovědy se vztahují k fyzickým adresářům, nikoli k logickým adresářům zobrazených v **Průzkumníku řešení**. Není třeba přidávat soubor nápovědy do projektu pro soubor nápovědy mít vliv. Systém analýzy používá soubory nápovědy pouze v případě, že analyzuje zdrojové soubory.

Každý soubor nápovědy se nazývá **cpp.hint**. Mnoho adresářů může obsahovat soubor nápovědy, ale v určitém adresáři může nastat pouze jeden soubor nápovědy.

Projekt může být ovlivněn nulou nebo více soubory nápovědy. Pokud neexistují žádné soubory nápovědy, systém analýzy používá techniky obnovení chyb k ignorování nerozluštitelného zdrojového kódu. V opačném případě systém analýzy používá následující strategii k vyhledání a shromáždění nápovědy.

### <a name="search-order"></a>Pořadí hledání

Systém analýzy vyhledává v adresářích soubory nápovědy v následujícím pořadí.

- Adresář, který obsahuje instalační balíček pro Visual C++ (**vcpackages**). Tento adresář obsahuje vestavěný soubor nápovědy, který popisuje symboly v často používaných systémových souborech, například **windows.h**. V důsledku toho projekt automaticky zdědí většinu nápovědy, které potřebuje.

- Cesta z kořenového adresáře zdrojového souboru do adresáře, který obsahuje samotný zdrojový soubor. V typickém projektu Visual Studio C++ obsahuje kořenový adresář soubor řešení nebo projektu.

   Výjimkou z tohoto pravidla je, pokud je *soubor stop* v cestě ke zdrojovému souboru. Soubor stop je libovolný soubor s názvem **cpp.stop**. Soubor stop poskytuje další kontrolu nad pořadím hledání. Namísto spuštění z kořenového adresáře prohledává systém analýzy z adresáře, který obsahuje soubor stop, do adresáře, který obsahuje zdrojový soubor. V typickém projektu nepotřebujete soubor stop.

### <a name="hint-gathering"></a>Shromažďování tipů

Soubor nápovědy obsahuje *nulu*nebo více rad . Nápověda je definována nebo odstraněna stejně jako makro C/C++. To znamená, `#define` že preprocesorsměrnice vytvoří nebo předefinuje `#undef` nápovědu a směrnice odstraní nápovědu.

Systém analýzy otevře každý soubor nápovědy v pořadí hledání popsaném výše. Akumuluje rady každého souboru do sady *efektivních rad*a pak použije efektivní rady k interpretaci identifikátorů v kódu.

Systém analýzy používá tato pravidla k akumulaci nápovědy:

- Pokud nová nápověda určuje název, který ještě není definován, nová nápověda přidá název k efektivním přijím.

- Pokud nová nápověda určuje název, který je již definován, nová nápověda předefinuje existující nápovědu.

- Pokud nová nápověda `#undef` je směrnice, která určuje existující efektivní nápovědu, nový nápověda odstraní existující nápovědu.

První pravidlo znamená, že efektivní rady jsou zděděny z dříve otevřených souborů nápovědy. Poslední dvě pravidla znamenají, že rady později v pořadí hledání mohou přepsat dřívější rady. Pokud například vytvoříte soubor nápovědy v adresáři, který obsahuje zdrojový soubor, můžete přepsat všechny předchozí rady.

Zobrazení způsobu shromáždění nápověd y naleznete v části [Příklad.](#example)

### <a name="syntax"></a>Syntaxe

Rady při psaní vytvoříte a odstraníte pomocí stejné syntaxe jako direktivy preprocesoru k vytvoření a odstranění maker. Ve skutečnosti systém analýzy používá preprocesor C/C++ k vyhodnocení rady. Další informace o direktivách preprocesoru naleznete [v tématu #define directive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md) a [#undef directive (C/C++).](../../preprocessor/hash-undef-directive-c-cpp.md)

Pouze neobvyklé prvky `@<`syntaxe jsou , `@=`a `@>` náhradní řetězce. Tyto řetězce specifické pro soubor nápovědy se používají pouze v *makra* mapy. Mapa je sada maker, která spojují data, funkce nebo události s jinými daty, funkcemi nebo obslužnými rutinami událostí. Pomocí map `MFC` například vytváří [mapy](../../mfc/reference/message-maps-mfc.md) `ATL` zpráv a mapy k vytváření [map objektů](../../atl/reference/object-map-macros.md). Náhradní řetězce specifické pro soubor nápovědy označují počáteční, střední a koncové prvky mapy. Významný je pouze název makra mapy. Proto každý náhradní řetězec záměrně skryje implementaci makra.

Rady používají tuto syntaxi:

|Syntaxe|Význam|
|------------|-------------|
|`#define`*řetězec nahrazení* názvu *nápovědy*<br /><br /> `#define`*parametr* *název nápovědy* `(` , ... `)` *náhradní řetězec*|Preprocesorová směrnice, která definuje novou nápovědu nebo předefinuje existující nápovědu. Po direktivě preprocesor nahradí každý výskyt *názvu nápovědy* ve zdrojovém kódu *náhradním řetězcem*.<br /><br /> Druhý formulář syntaxe definuje nápovědu jako funkce. Pokud se ve zdrojovém kódu vyskytne nápověda jako funkce, preprocesor nejprve nahradí každý výskyt *parametru* v *náhradním řetězci* odpovídajícím argumentem ve zdrojovém kódu a potom nahradí *název nápovědy* *náhradním řetězcem*.|
|`@<`|Řetězec *nahrazení* specifické ho souboru nápovědy, který označuje začátek sady prvků mapy.|
|`@=`|Náhradní *řetězec* specifické pro soubor nápovědy, který označuje zprostředkující prvek mapy. Mapa může mít více prvků mapy.|
|`@>`|Řetězec *nahrazení* specifické ho souboru nápovědy, který označuje konec sady prvků mapy.|
|`#undef`*název nápovědy*|Preprocesorsměrnice, která odstraní existující nápovědu. Název nápovědy je poskytnut identifikátorem *názvu nápovědy.*|
|`//`*komentář*|Jednořádkový komentář.|
|`/*`*komentář*`*/`|Víceřádkový komentář.|

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak se shromažďují rady ze souborů nápovědy. Stop soubory nejsou použity v tomto příkladu.

Obrázek znázorňuje některé fyzické adresáře v projektu Visual Studio C++. Soubory nápovědy jsou `vcpackages` `Debug`v `A1`adresářích , , a `A2` .

### <a name="hint-file-directories"></a>Adresáře souborů nápovědy

![Běžné a projektové&#45;konkrétní adresáře souborů nápovědy.](media/hintfile.png "Soubor nápovědy")

### <a name="directories-and-hint-file-contents"></a>Adresáře a obsah souboru nápovědy

Tento seznam zobrazuje adresáře v tomto projektu, které obsahují soubory nápovědy, a obsah těchto souborů nápovědy. Jsou uvedeny pouze některé `vcpackages` z mnoha rad v souboru nápovědy adresáře:

- vcbalíčky

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

### <a name="effective-hints"></a>Efektivní rady

V této tabulce jsou uvedeny účinné rady pro zdrojové soubory v tomto projektu:

- Zdrojový soubor: A1_A2_B.cpp

- Efektivní rady:

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

Tyto poznámky platí pro předchozí seznam:

- Efektivní rady jsou z `vcpackages` `Debug`, `A1`, `A2` a adresáře.

- Direktiva `Debug` **#undef** v `#define _In_` souboru `vcpackages` nápovědy odstranila nápovědu v souboru nápovědy adresáře.

- Soubor nápovědy `START_NAMESPACE` `A1` v adresáři předefinuje .

- `#undef` Nápověda v `A2` adresáři odstranila `OBRACE` `CBRACE` rady `Debug` pro a v souboru nápovědy adresáře.

## <a name="see-also"></a>Viz také

[Typy souborů vytvořené pro projekty jazyka Visual Studio C++](file-types-created-for-visual-cpp-projects.md)<br>
[#define – direktiva (C++)](../../preprocessor/hash-define-directive-c-cpp.md)<br>
[#undef – direktiva (C++)](../../preprocessor/hash-undef-directive-c-cpp.md)<br>
[Poznámky SAL](../../c-runtime-library/sal-annotations.md)<br>
