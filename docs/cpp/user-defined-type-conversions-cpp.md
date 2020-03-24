---
title: Převody uživatelem definovaných typů (C++)
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
ms.openlocfilehash: 055b5bd5c82e4f0be449d548de25267eabef47bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187931"
---
# <a name="user-defined-type-conversions-c"></a>Převody uživatelem definovaných typů (C++)

*Převod* vytváří novou hodnotu určitého typu z hodnoty jiného typu. *Standardní převody* jsou integrovány do C++ jazyka a podporují integrované typy a můžete vytvořit *uživatelsky definované převody* k provádění převodů na, z nebo mezi uživatelsky definovanými typy.

Standardní převody provádějí převody mezi vestavěnými typy, mezi ukazateli nebo odkazy na typy související dědičností, na a z ukazatelů void a na ukazatel s hodnotou null. Další informace najdete v tématu [standardní převody](../cpp/standard-conversions.md). Uživatelsky definované převody provádějí převody mezi uživatelsky definovanými typy nebo mezi uživatelsky definovanými typy a vestavěnými typy. Můžete je implementovat jako [konstruktory převodu](#ConvCTOR) nebo jako [funkce pro převod](#ConvFunc).

Převody mohou být buď explicitní – Pokud programátor volá jeden typ, který se má převést na jiný typ, jako v přetypování nebo přímé inicializaci – nebo implicitní – při volání jazyka nebo programu na jiný typ než ten, který je dán programátorem.

Implicitní převody se pokoušejí v těchto případech:

- Argument dodaný funkci nemá stejný typ jako shodný parametr.

- Hodnota vrácená funkcí není stejného typu jako návratový typ funkce.

- Inicializátorový výraz nemá stejný typ jako objekt, který inicializuje.

- Výraz, který ovládá podmíněný příkaz, konstruktor smyčky nebo přepínač, nemá typ výsledku, který je požadován pro jeho řízení.

- Operand dodaný operátorovi nemá stejný typ jako shodný parametr operandu. Pro předdefinované operátory musí mít oba operandy stejný typ a jsou převedeny na společný typ, který může představovat obojí. Další informace najdete v tématu [standardní převody](standard-conversions.md). Pro operátory definované uživatelem musí mít každý operand stejný typ jako shodný parametr operandu.

Pokud jeden standardní převod nemůže dokončit implicitní převod, kompilátor může použít uživatelem definovaný převod, za nímž následuje volitelně dodatečný standardní převod, k jeho dokončení.

V případě, že dva nebo více uživatelsky definovaných převodů, které provádějí stejný převod, jsou k dispozici v rámci konverze webu, převod je označován jako nejednoznačný. Takové nejednoznačnosti představují chybu, protože kompilátor nemůže určit, který z dostupných převodů by měl zvolit. Nejedná se však o chybu pouze k definování více způsobů provádění stejného převodu, protože sada dostupných převodů může být odlišná na různých umístěních ve zdrojovém kódu – například v závislosti na tom, které hlavičkové soubory jsou obsaženy ve zdrojovém souboru. Pokud je v lokalitě pro převod k dispozici pouze jeden převod, nedochází k nejednoznačnosti. Existuje několik způsobů, jak mohou nastat dvojznačné převody, ale nejběžnější jsou:

- Vícenásobná dědičnost. Převod je definován ve více než jedné základní třídě.

- Nejednoznačné volání funkce Převod je definován jako převodní konstruktor cílového typu a jako převodní funkce typu zdroje. Další informace najdete v tématu [funkce pro převod](#ConvFunc).

Nejednoznačnost můžete obvykle vyřešit tak, že název daného typu zadáte mnohem více nebo pomocí explicitního přetypování k objasnění svého záměru.

Konstruktory převodu i převodní funkce dodržují pravidla řízení přístupu členů, ale přístupnost převodů je považována pouze za if a v případě, že lze určit jednoznačnou konverzi. To znamená, že převod může být nejednoznačný i v případě, že úroveň přístupu konkurenčního převodu by zabránila použití. Další informace o přístupnost členů naleznete v tématu [member Access Control](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Explicitní klíčové slovo a problémy s implicitním převodem

Ve výchozím nastavení, když vytvoříte uživatelem definovaný převod, ho kompilátor může použít k provádění implicitních převodů. V některých případech se jedná o to, co chcete, ale v některých případech jednoduchá pravidla, která jsou vodítkem kompilátoru při vytváření implicitních převodů, mohou vést k tomu, aby mohl přijímat kód, který nechcete.

Jeden dobře známý příklad implicitního převodu, který může způsobit problémy, je převod na **bool**. Existuje mnoho důvodů, proč je vhodné vytvořit typ třídy, který lze použít v logickém kontextu, například, aby jej bylo možné použít k řízení příkazu **if** nebo smyčky, ale pokud kompilátor provede uživatelem definovaný převod na předdefinovaný typ, kompilátor může následně použít další standardní převod. Účelem tohoto dalšího standardního převodu je povolit pro věci, jako je povýšení z **krátkých** na **int**, ale také otevře dvířka pro méně zřejmé převody – například z **bool** na **int**, což umožňuje, aby byl typ třídy použit v celočíselných kontextech, které nikdy nezamýšlelte. Tento konkrétní problém se označuje jako *bezpečný problém bool*. Tento druh problému je tam, kde může klíčové slovo **Explicit** pomáhat.

Klíčové slovo **Explicit** instruuje kompilátor, že zadaný převod nelze použít k provádění implicitních převodů. Pokud jste chtěli syntaktickou pohodlí implicitních převodů před zavedením **explicitního** klíčového slova, museli byste přijmout nezamýšlené důsledky, které implicitní převod někdy vytvoří, nebo použít méně pohodlné a pojmenované převodní funkce jako alternativní řešení. Teď můžete pomocí klíčového slova **Explicit** vytvořit pohodlný převod, který se dá použít jenom k provedení explicitního přetypování nebo přímé inicializace, a to nevede k druhům problémů exemplified pomocí bezpečného problému bool.

**Explicitní** klíčové slovo lze použít na konstruktory převodu od c++ 98 a k funkcím pro převod od c++ 11. Následující části obsahují další informace o použití klíčového slova **Explicit** .

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>Konstruktory převodu

Konstruktory převodu definují převody z uživatelsky definovaných nebo předdefinovaných typů na uživatelsky definovaný typ. Následující příklad ukazuje konstruktor převodu, který je převeden z vestavěného typu **Double** na uživatelsky definovaný typ `Money`.

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

Všimněte si, že první volání funkce `display_balance`, které přebírá argument typu `Money`, nevyžaduje převod, protože jeho argument je správného typu. Při druhém volání `display_balance`však je nutný převod, protože typ argumentu, **Double** s hodnotou `49.95`, není to, co funkce očekává. Funkce nemůže tuto hodnotu použít přímo, ale vzhledem k tomu, že existuje převod z typu argumentu –**Double**– na typ odpovídajícího parametru –`Money`– dočasná hodnota typu `Money` je vytvořená z argumentu a používá se k dokončení volání funkce. Ve třetím volání `display_balance`si všimněte, že argument není **Double**, ale je místo typu **float** s hodnotou `9.99`– a přesto může být volání funkce dokončeno, protože kompilátor může provést standardní převod – v tomto případě z **float** na **Double**– a poté provést převod definovaný uživatelem z **Double** na `Money` k dokončení nezbytné konverze.

### <a name="declaring-conversion-constructors"></a>Deklarace konstruktorů převodu

Následující pravidla platí pro deklaraci konstruktoru převodu:

- Cílový typ převodu je uživatelsky definovaný typ, který je sestaven.

- Konstruktory převodu obvykle přebírají přesně jeden argument, který je typu zdroje. Konstruktor převodu však může určit další parametry, pokud má každý další parametr výchozí hodnotu. Typ zdroje zůstává typ prvního parametru.

- Konstruktory převodu, jako jsou všechny konstruktory, nespecifikují návratový typ. Zadání návratového typu v deklaraci je chyba.

- Konstruktory převodu můžou být explicitní.

### <a name="explicit-conversion-constructors"></a>Explicitní konstruktory převodu

Deklarací konstruktoru převodu, který má být **explicitní**, lze použít pouze k provedení přímé inicializace objektu nebo k provedení explicitního přetypování. Tím zabráníte funkcím, které přijímají argument typu třídy z zároveň implicitně přijímá argumenty typu zdroje převodu a brání v kopírování typu třídy z hodnoty zdrojového typu. Následující příklad ukazuje, jak definovat explicitní konstruktor převodu a vliv na to, jaký kód je ve správném formátu.

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

V tomto příkladu si všimněte, že stále můžete použít explicitní konstruktor převodu k provedení přímé inicializace `payable`. Pokud místo toho jste chtěli kopírovat-inicializovat `Money payable = 79.99;`, bude to chyba. První volání `display_balance` není ovlivněno, protože argument je správného typu. Druhé volání `display_balance` je chyba, protože konstruktor převodu nelze použít k provádění implicitních převodů. Třetí volání `display_balance` je platné z důvodu explicitního přetypování na `Money`, ale Všimněte si, že kompilátor stále pomáhá dokončit přetypování vložením implicitního přetypování z **float** na **Double**.

I když pohodlí při povolování implicitních převodů může proniknout, může to vést k obtížně nalezeným chybám. Pravidlem pro palec je vytvořit všechny konstruktory převodu s výjimkou případů, kdy jste si jisti, že chcete, aby konkrétní konverze probíhala implicitně.

##  <a name="conversion-functions"></a><a name="ConvFunc"></a>Převodní funkce

Převodní funkce definují převody z uživatelsky definovaného typu na jiné typy. Tyto funkce jsou někdy označovány jako "operátory přetypování", protože jsou společně s konstruktory převodu volány, když je hodnota převedena na jiný typ. Následující příklad ukazuje funkci převodu, která je převedena z uživatelsky definovaného typu, `Money`na předdefinovaný typ **Double**:

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

Všimněte si, že členská proměnná `amount` je soukromá a že funkce veřejné konverze pro typ **Double** je zavedená pouze k vrácení hodnoty `amount`. Ve `display_balance`funkce se implicitní převod vyskytne v případě, že je hodnota `balance` streamovaná na standardní výstup pomocí `<<`operátoru vložení datového proudu. Vzhledem k tomu, že pro uživatelsky definovaný typ `Money`není definován žádný operátor vkládání datových proudů, ale existuje jeden pro vestavěný typ **Double**, kompilátor může použít funkci převodu z `Money` ke **zdvojnásobení** pro splnění operátoru vkládání datových proudů.

Převodní funkce jsou zděděny odvozenými třídami. Funkce převodu v odvozené třídě přepíší zděděnou funkci převodu pouze při převodu na naprosto stejný typ. Například uživatelsky definovaná převodní funkce **operátoru** odvozené třídy int nepřepisuje nebo ani neovlivňuje – uživatelsky definovaná převodní funkce **operátoru**základní třídy, i když standardní převody definují vztah konverze mezi **int** a **short**.

### <a name="declaring-conversion-functions"></a>Deklarace funkcí převodu

Následující pravidla platí pro deklaraci funkce pro převod:

- Cílový typ převodu musí být deklarován před deklarací funkce pro převod. Třídy, struktury, výčty a definice typedef nelze deklarovat v rámci deklarace funkce pro převod.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Funkce převodu nepřijímají argumenty. Zadání jakýchkoli parametrů v deklaraci je chyba.

- Funkce pro převod mají návratový typ, který je určen názvem funkce pro převod, což je také název cílového typu převodu. Zadání návratového typu v deklaraci je chyba.

- Převodní funkce můžou být virtuální.

- Převodní funkce můžou být explicitní.

### <a name="explicit-conversion-functions"></a>Funkce explicitního převodu

Je-li funkce převodu deklarována jako explicitní, může být použita pouze k provedení explicitního přetypování. To brání funkcím, které přijímají argument cílového typu funkce převodu, a zároveň implicitně přijímá argumenty typu třídy a zabraňuje kopírování instancí cílového typu z hodnoty typu třídy. Následující příklad ukazuje, jak definovat explicitní funkci převodu a vliv na to, jaký kód je ve správném formátu.

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

V tomto příkladu byla explicitně provedena **dvojice operátora** funkce převodu a ve funkci `display_balance` k provedení převodu byla zavedena explicitní přetypování na typ **Double** . Pokud bylo toto přetypování vynecháno, kompilátor nebude schopen najít vhodný operátor vložení datového proudu `<<` pro typ `Money` a dojde k chybě.
