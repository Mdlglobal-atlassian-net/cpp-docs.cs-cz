---
title: Převody typů definovaných uživatelem (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
ms.openlocfilehash: e74d5b3a748a9aab22a6a9d83c4d6c4bd3379df4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374678"
---
# <a name="user-defined-type-conversions-c"></a>Převody typů definovaných uživatelem (C++)

Převod *conversion* vytvoří novou hodnotu nějakého typu z hodnoty jiného typu. *Standardní převody* jsou integrovány do jazyka C++ a podporují jeho předdefinované typy a můžete vytvořit *uživatelem definované převody* k provádění převodů do, z nebo mezi typy definovanými uživatelem.

Standardní převody provádět převody mezi předdefinované typy, mezi odkazy nebo odkazy na typy související dědičnosti, do a z void ukazatele a na ukazatel null. Další informace naleznete v tématu [Standardní převody](../cpp/standard-conversions.md). Uživatelem definované převody provádějí převody mezi typy definovanými uživatelem nebo mezi typy definovanými uživatelem a předdefinovanými typy. Můžete je implementovat jako [konstruktory převodu](#ConvCTOR) nebo jako [funkce převodu](#ConvFunc).

Převody mohou být explicitní – když programátor volá jeden typ, který má být převeden na jiný, jako v přetypování nebo přímé inicializace – nebo implicitní – když jazyk nebo program vyžaduje jiný typ, než je daný programátorem.

O implicitní převody se pokusíte v:Implicitní conversions are attemptd when:

- Argument zadaný funkci nemá stejný typ jako odpovídající parametr.

- Hodnota vrácená z funkce nemá stejný typ jako návratový typ funkce.

- Výraz inicializátoru nemá stejný typ jako objekt, který inicializuje.

- Výraz, který řídí podmíněný příkaz, opakování konstrukce nebo přepínač nemá typ výsledku, který je nutný k jeho řízení.

- Operand dodaný operátoru nemá stejný typ jako odpovídající operand-parametr. Pro předdefinované operátory musí mít oba operandy stejný typ a jsou převedeny na běžný typ, který může představovat obojí. Další informace naleznete v tématu [Standardní převody](standard-conversions.md). Pro uživatelem definované operátory musí mít každý operand stejný typ jako odpovídající parametr operand.

Pokud jeden standardní převod nemůže dokončit implicitní převod, kompilátor může k jeho dokončení použít uživatelem definovaný převod následovaný volitelně dalším standardním převodem.

Pokud jsou na konverzním webu k dispozici dva nebo více uživatelem definovaných konverzí, které provádějí stejný převod, převod je považován za nejednoznačný. Takové nejasnosti jsou chyba, protože kompilátor nemůže určit, který z dostupných převodů by měl zvolit. Není však chybou pouze definovat více způsobů provedení stejného převodu, protože sada dostupných konverzí se může lišit na různých místech ve zdrojovém kódu – například v závislosti na tom, které soubory hlaviček jsou zahrnuty do zdrojového souboru. Dokud je na konverzním webu k dispozici pouze jedna konverze, neexistuje žádná nejednoznačnost. Existuje několik způsobů, jak mohou vzniknout nejednoznačné převody, ale nejběžnější jsou:

- Vícenásobná dědičnost. Převod je definován ve více než jedné základní třídě.

- Nejednoznačné volání funkce. Převod je definován jako konstruktor převodu cílového typu a jako funkce převodu typu zdroje. Další informace naleznete v [tématu Funkce převodu](#ConvFunc).

Nejednoznačnost můžete obvykle vyřešit pouze tím, že kvalifikuje název zúčastněného typu úplněji nebo provedením explicitní hodování k objasnění vašeho záměru.

Konstruktory převodu i funkce převodu dodržují pravidla řízení přístupu členů, ale přístupka převodů se zvažuje pouze tehdy, pokud a kdy lze určit jednoznačný převod. To znamená, že převod může být nejednoznačný i v případě, že úroveň přístupu konkurenčního převodu by zabránila jeho použití. Další informace o usnadnění přístupu členů naleznete [v tématu Řízení přístupu členů](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Explicitní klíčové slovo a problémy s implicitní převod

Ve výchozím nastavení při vytváření uživatelem definovaného převodu jej kompilátor může použít k provádění implicitních převodů. Někdy je to, co chcete, ale jindy jednoduchá pravidla, která řídí kompilátor při vytváření implicitních převodů, může vést k přijetí kódu, který nechcete.

Jeden dobře známý příklad implicitní převod, který může způsobit problémy, je převod **bool**. Existuje mnoho důvodů, proč můžete chtít vytvořit typ třídy, který lze použít v booleovském kontextu – například tak, aby jej bylo možné použít k řízení **příkazu nebo** smyčky if – ale když kompilátor provede uživatelem definovaný převod na předdefinovaný typ, kompilátor může později použít další standardní převod. Záměrem této další standardní konverze je umožnit věci, jako je propagace z **krátké** **na int**, ale také otevírá dveře pro méně zřejmé konverze – například z **bool** na **int**, který umožňuje typ třídy, které mají být použity v celočíselné kontexty jste nikdy nezamýšleli. Tento konkrétní problém se označuje jako *problém bezpečného bool*. Tento druh problému je místo, kde **explicitní** klíčové slovo může pomoci.

Explicitní **explicit** klíčové slovo říká kompilátoru, že zadaný převod nelze použít k provedení implicitní převody. Pokud jste chtěli syntaktické pohodlí implicitních převodů před explicitní **klíčové** slovo bylo zavedeno, museli jste buď přijmout nezamýšlené důsledky, které implicitní převod někdy vytvořil, nebo použít méně pohodlné funkce s názvem převodu jako řešení. Nyní pomocí **explicitního** klíčového slova můžete vytvořit pohodlné konverze, které lze použít pouze k explicitnímu přetypování nebo přímé inicializaci, a které nevedou k problémům, které ilustruje problém safe bool.

Explicitní **explicit** klíčové slovo lze použít pro konstruktory převodu od C ++ 98 a na funkce převodu od C ++ 11. Následující části obsahují další informace o použití **explicitního** klíčového slova.

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>Konstruktory převodu

Konstruktory převodu definují převody z uživatelem definovaných nebo předdefinovaných typů na typ definovaný uživatelem. Následující příklad ukazuje konstruktor převodu, který převádí z předdefinovaného typu **double** na uživatelem definovaný typ `Money`.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };

    display_balance(payable);
    display_balance(49.95);
    display_balance(9.99f);

    return 0;
}
```

Všimněte si, že `display_balance`první volání funkce , `Money`která přebírá argument typu , nevyžaduje převod, protože jeho argument je správný typ. Však při druhém `display_balance`volání , převod je potřeba, protože typ argumentu, `49.95` **double** s hodnotou , není co funkce očekává. Funkce nelze použít tuto hodnotu přímo, ale protože je převod z typu argumentu –**double**–na typ odpovídající parametr–`Money`– dočasná hodnota typu `Money` je vytvořena z argumentu a slouží k dokončení volání funkce. Ve třetí volání `display_balance`na , všimněte si, že argument není **double** `9.99`, ale je **float** s hodnotou – a přesto volání funkce lze stále dokončit, protože kompilátor může provést `Money` standardní převod – v tomto případě z **float** na **double**– a potom provést uživatelem definovaný převod z **double** k dokončení potřebného převodu.

### <a name="declaring-conversion-constructors"></a>Deklarování konstruktorů převodu

Následující pravidla platí pro deklarování konstruktoru převodu:

- Cílový typ převodu je uživatelem definovaný typ, který je vytvářen.

- Převod ní konstruktory obvykle trvat přesně jeden argument, který je typu zdroje. Konstruktor převodu však může zadat další parametry, pokud má každý další parametr výchozí hodnotu. Typ zdroje zůstává typem prvního parametru.

- Převodní konstruktory, stejně jako všechny konstruktory, neurčují návratový typ. Zadání návratového typu v deklaraci je chyba.

- Převodníky mohou být explicitní.

### <a name="explicit-conversion-constructors"></a>Konstruktory explicitní převodu

Deklarováním konstruktoru převodu jako **explicitního**lze jej použít pouze k provedení přímé inicializace objektu nebo k explicitnímu přetypování. Tím zabráníte, aby funkce, které přijímají argument typu třídy, také implicitně přijímaly argumenty zdrojového typu konstruktoru převodu a zabránily kopírování typu třídy z hodnoty typu zdroje. Následující příklad ukazuje, jak definovat konstruktor explicitní převod a vliv, který má na jaký kód je ve správném formátu.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    explicit Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.

    display_balance(payable);      // Legal: no conversion required
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.
    display_balance((Money)9.99f); // Legal: explicit cast to Money

    return 0;
}
```

V tomto příkladu všimněte si, že stále můžete použít `payable`konstruktor explicitní převod provést přímou inicializaci . Pokud byste místo toho měli `Money payable = 79.99;`zkopírovat-inicializovat , bylo by chyba. První volání `display_balance` není ovlivněna, protože argument je správný typ. Druhé volání `display_balance` je chyba, protože konstruktor převodu nelze použít k provedení implicitní převody. Třetí volání `display_balance` je legální z důvodu `Money`explicitní přetypování do , ale všimněte si, že kompilátor stále pomohl dokončit přetypování vložením implicitního přetypování z **float** na **double**.

Přestože pohodlí povolení implicitní převody může být lákavé, přitom může zavést těžko najít chyby. Pravidlem je, aby všechny konstruktory převodu explicitní, s výjimkou případů, kdy jste si jisti, že chcete, aby konkrétní převod dojít implicitně.

## <a name="conversion-functions"></a><a name="ConvFunc"></a>Funkce převodu

Funkce převodu definují převody z uživatelem definovaného typu na jiné typy. Tyto funkce jsou někdy označovány jako "operátory přetypovacího vysílání", protože spolu s konstruktory převodu jsou volány při přetypováno hodnota na jiný typ. Následující příklad ukazuje funkci převodu, `Money`která se převádí z uživatelem definovaného typu , na předdefinovaný typ **double**:

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance << std::endl;
}
```

Všimněte si, `amount` že členská proměnná je soukromá a že je zavedena funkce veřejného převodu typu **double** pouze pro vrácení hodnoty `amount`. Ve funkci `display_balance`dojde k implicitnímu převodu, když `balance` je hodnota streamována na `<<`standardní výstup pomocí operátoru vložení datového proudu . Vzhledem k tomu, že pro uživatelem definovaný `Money`typ není definován žádný operátor vkládání datového proudu , ale `Money` je k dispozici jeden pro předdefinovaný typ **double**, může kompilátor použít funkci převodu z **double** ke splnění operátoru vkládání datového proudu.

Funkce převodu jsou zděděny odvozenými třídami. Funkce převodu v odvozené třídě pouze přepsat zděděné funkce převodu při jejich převodu na přesně stejný typ. Například uživatelem definovaná funkce převodu operátoru odvozené třídy **int** nepřepíše nebo ani neovlivní uživatelem definovanou funkci převodu **operátoru**základní třídy , která je krátká , i když standardní převody definují vztah převodu mezi **int** a **short**.

### <a name="declaring-conversion-functions"></a>Deklarování funkcí převodu

Pro deklarování funkce převodu platí následující pravidla:

- Cílový typ převodu musí být deklarován před deklarací funkce převodu. Třídy, struktury, výčty a typedefs nelze deklarovat v rámci deklarace funkce převodu.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Funkce převodu nepřijímají argumenty. Zadání všech parametrů v deklaraci je chyba.

- Funkce převodu mají návratový typ, který je určen názvem funkce převodu, což je také název cílového typu převodu. Zadání návratového typu v deklaraci je chyba.

- Funkce převodu mohou být virtuální.

- Funkce převodu může být explicitní.

### <a name="explicit-conversion-functions"></a>Explicitní funkce převodu

Pokud je funkce převodu prohlášena za explicitní, lze ji použít pouze k provedení explicitního přetypování. Tím zabráníte, aby funkce, které přijímají argument cílového typu funkce převodu, také implicitně přijímaly argumenty typu třídy a zabránily tomu, aby instance cílového typu byly inicializovány z hodnoty typu třídy. Následující příklad ukazuje, jak definovat explicitní funkce převodu a vliv, který má na jaký kód je ve správném formátu.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    explicit operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << (double)balance << std::endl;
}
```

Zde byl operátor funkce převodu **double** explicitní a ve funkci `display_balance` pro provedení převodu bylo zavedeno explicitní přetypování typu **double.** Pokud toto přetypování byly vynechány, kompilátor by nelze `<<` najít `Money` vhodný operátor vložení datového proudu pro typ a došlo by k chybě.
