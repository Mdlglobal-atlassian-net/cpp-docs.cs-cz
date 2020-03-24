---
title: Explicitně přednastavené a odstraněné funkce
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: b43588aac1d246c83f5281456625eeb0ff36b94d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179975"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Explicitně přednastavené a odstraněné funkce

Ve výchozích a odstraněných funkcích jazyka C++ 11 získáte explicitní kontrolu nad tím, zda jsou automaticky generovány zvláštní členské funkce. Odstraněné funkce také poskytují jednoduchý jazyk, aby nedocházelo k problematickým propagačním událostem typu v argumentech pro funkce všech typů – speciální členské funkce a běžné členské funkce a nečlenské funkce, které by jinak způsobily volání nechtěné funkce.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Výhody explicitně nastavených a odstraněných funkcí

V C++nástroji kompilátor automaticky generuje výchozí konstruktor, kopírovací konstruktor, operátor přiřazení kopie a destruktor pro typ, pokud nedeklaruje svou vlastní hodnotu. Tyto funkce jsou známé jako *speciální členské funkce*a jsou to, jak se mají jednoduché uživatelsky definované typy C++ chovat jako struktury v C. To znamená, že je můžete vytvářet, kopírovat a zničit bez dalšího kódovacího úsilí. C++ 11 přináší možnost přesunout sémantiku do jazyka a přidá do seznamu speciálních členských funkcí, které kompilátor může automaticky generovat, operátor přesunutí a operátor přiřazení přesunutí.

To je vhodné pro jednoduché typy, ale komplexní typy často definují jednu nebo více speciálních členských funkcí samotných a to může zabránit automatickému generování jiných speciálních členských funkcí. V praxi:

- Pokud je jakýkoli konstruktor explicitně deklarovaný, pak není automaticky vygenerován žádný výchozí konstruktor.

- Pokud je virtuální destruktor explicitně deklarovaný, pak není automaticky vygenerován žádný výchozí destruktor.

- Pokud je explicitně deklarován konstruktor přesunu nebo operátor přiřazení přesunutí, pak:

   - Žádný kopírovací konstruktor není automaticky vygenerován.

   - Negeneruje se automaticky žádný operátor přiřazení kopie.

- Pokud je kopírovací konstruktor, operátor přiřazení kopírování, konstruktor přesunutí, operátor přiřazení přesunutí nebo destruktor explicitně deklarován, pak:

   - Žádný konstruktor přesunu není automaticky vygenerován.

   - Žádný operátor přiřazení přesunu není automaticky vygenerován.

> [!NOTE]
> Standard jazyka C++ 11 navíc určuje následující další pravidla:
>
> - Je-li kopírovací konstruktor nebo destruktor explicitně deklarován, pak je automatické generování operátoru přiřazení kopírování zastaralé.
> - Pokud je explicitně deklarován operátor přiřazení kopie nebo destruktor, je automatické generování kopírovacího konstruktoru zastaralé.
>
> V obou případech Visual Studio nadále automaticky generuje nezbytné funkce implicitně a negeneruje upozornění.

Důsledky těchto pravidel může také proniknout do hierarchií objektů. Například pokud z jakéhokoli důvodu nemůže základní třída mít výchozí konstruktor, který je možné volat z odvozené třídy – to znamená **veřejný** nebo **chráněný** konstruktor, který nepřijímá žádné parametry – potom třída, která je odvozena z, nemůže automaticky generovat svůj vlastní výchozí konstruktor.

Tato pravidla mohou zkomplikovat implementaci toho, co by mělo být přímo předávané, uživatelsky definované typy a běžné C++ idiomy – například vytvoření uživatelsky definovaného typu, který není možné kopírovat, deklarováním konstruktoru kopírování a operátoru přiřazení kopie soukromě a bez jejich definování.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Před C++ 11 byl tento fragment kódu idiomatickou formou nekopírovacích typů. Má ale několik problémů:

- Kopírovací konstruktor musí být deklarován soukromě, aby jej bylo možné skrýt, ale vzhledem k tomu, že je deklarována vůbec, je zabráněno automatické generaci výchozího konstruktoru. Musíte explicitně definovat výchozí konstruktor, pokud chcete, a to i v případě, že neprovádí žádnou akci.

- I v případě, že explicitně definovaný výchozí konstruktor neprovede žádnou akci, je kompilátor považován za netriviální. Je méně efektivní než automaticky generovaný výchozí konstruktor a znemožňuje `noncopyable`, aby byly typu true POD.

- I když je kopírovací konstruktor a operátor přiřazení kopírování skryté z vnějšího kódu, členské funkce a přátelé `noncopyable` mohou stále zobrazit a volat je. Pokud jsou deklarovány, ale nejsou definovány, volání způsobí chybu linkeru.

- I když je to běžně přijatý idiom, záměr není jasný, pokud nerozumíte všem pravidlům pro automatické generování speciálních členských funkcí.

V jazyce C++ 11 lze idiom bez možnosti kopírování implementovat způsobem, který je jednodušší.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Všimněte si, jak jsou vyřešeny problémy s idiom před C + + 11:

- Generování výchozího konstruktoru je stále znemožněno deklarací kopírovacího konstruktoru, ale můžete jej přenést zpět explicitním výchozím nastavením.

- Explicitně používané speciální členské funkce jsou stále považovány za triviální, takže nedochází k žádnému snížení výkonu a `noncopyable` nebrání tomu, aby se staly hodnotou true POD.

- Kopírovací konstruktor a operátor přiřazení kopie jsou veřejné, ale odstraněné. Jedná se o chybu při kompilaci k definování nebo volání odstraněné funkce.

- Záměr je jasný všem, kdo rozumí `=default` a `=delete`. Nemusíte pochopit pravidla pro automatické generování speciálních členských funkcí.

Podobné idiomy existují pro vytváření uživatelem definovaných typů, které jsou nepohyblivé, které lze pouze dynamicky přidělit nebo které nelze dynamicky přidělit. Každá z těchto idiomy má implementace předběžných v jazyce C + + 11, které mají podobné problémy a jsou podobně vyřešeny v C++ 11 implementací z podmínek výchozích a odstraněných speciálních členských funkcí.

## <a name="explicitly-defaulted-functions"></a>Explicitně nastavené funkce

Můžete použít výchozí některou z speciálních členských funkcí – pro explicitní stav, že speciální členská funkce používá výchozí implementaci, k definování speciální členské funkce s kvalifikátorem neveřejného přístupu nebo k obnovení speciální členské funkce, jejíž Automatické generování bylo znemožněno jinými okolnostmi.

Pro speciální členskou funkci jste ve výchozím nastavení deklarováni jako v tomto příkladu:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Všimněte si, že můžete určit výchozí členskou funkci mimo tělo třídy, pokud je to vložitelné.

Z důvodu výkonu výhod triviálních speciálních členských funkcí doporučujeme, abyste raději automaticky vygenerovali speciální funkce členů nad prázdnými subjekty funkcí, pokud chcete výchozí chování. Můžete to provést buď explicitním výchozím nastavením speciální členské funkce, nebo tím, že ji nedeklarujete (a také nedeklarujete jiné zvláštní členské funkce, které by zabránily jejímu automatickému generování.)

## <a name="deleted-functions"></a>Odstraněné funkce

Můžete odstranit speciální členské funkce a také běžné členské funkce a nečlenské funkce, aby byly zabráněno jejich definování nebo volání. Odstranění speciálních členských funkcí poskytuje čisticí způsob, jak zabránit kompilátoru v generování speciálních členských funkcí, které nechcete. Funkce musí být odstraněna, protože je deklarována; nemůže být smazán následně způsobem, který může být funkce deklarována a poté později použita.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Odstranění normální členské funkce nebo nečlenské funkce zabraňuje problematickému typu propagačních akcí, které způsobují volání nezamýšlené funkce. To funguje, protože odstraněné funkce se pořád účastní řešení přetížení a poskytují lepší shodu než funkce, která by se dala volat po zvýšení úrovně typů. Volání funkce se přeloží na konkrétnější, ale Deleted – funkce a způsobí chybu kompilátoru.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Všimněte si, že v předchozím příkladu, který volá `call_with_true_double_only` pomocí argumentu **typu float** , by došlo k chybě kompilátoru, ale volání `call_with_true_double_only` pomocí argumentu **int** nepředstavuje. v případě typu **int** bude argument povýšen z **int** na **Double** a úspěšně volá **dvojitou** verzi funkce, i když to nemusí být zamýšlené. Chcete-li zajistit, aby jakékoli volání této funkce pomocí nedouble argumentu způsobilo chybu kompilátoru, můžete deklarovat verzi šablony funkce, která je odstraněna.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
