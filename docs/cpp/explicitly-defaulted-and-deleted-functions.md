---
title: Explicitně přednastavené a odstraněné funkce
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: bd13b5fef3a9dfc13d72f1ee34d7ced902735e15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360908"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Explicitně přednastavené a odstraněné funkce

V jazyce C++ 11 výchozí a odstraněné funkce poskytují explicitní kontrolu nad tím, zda jsou automaticky generovány speciální členské funkce. Odstraněné funkce také poskytují jednoduchý jazyk, který zabraňuje výskytu problematických povýšení typu v argumentech na funkce všech typů – speciální členské funkce, stejně jako normální členské funkce a nečlenské funkce – které by jinak způsobily nežádoucí volání funkce.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Výhody explicitně nesplácených a odstraněných funkcí

V jazyce C++ kompilátor automaticky generuje výchozí konstruktor, copy konstruktor, operátor přiřazení kopírování a destruktor pro typ, pokud nedeklaruje svůj vlastní. Tyto funkce jsou označovány jako *speciální členské funkce*a jsou to, co dělají jednoduché uživatelem definované typy v jazyce C++ se chovají jako struktury v jazyce C. To znamená, že je můžete vytvářet, kopírovat a ničit bez dalšího úsilí o kódování. C ++ 11 přináší přesunout sémantiku do jazyka a přidá přesunout konstruktor a přesunout operátor přiřazení do seznamu speciálních členských funkcí, které kompilátor může automaticky generovat.

To je vhodné pro jednoduché typy, ale složité typy často definují jednu nebo více speciálních členských funkcí sami, a to může zabránit automatickému generování dalších speciálních členských funkcí. V praxi:

- Pokud je explicitně deklarován některý konstruktor, není automaticky generován žádný výchozí konstruktor.

- Pokud je virtuální destruktor explicitně deklarován, nebude automaticky generován žádný výchozí destruktor.

- Pokud je explicitně deklarován konstruktor move nebo operátor přiřazení přesunutí, pak:

  - Není automaticky generován žádný konstruktor kopírování.

  - Není automaticky generován žádný operátor přiřazení kopie.

- Pokud je explicitně deklarován konstruktor kopírování, operátor přiřazení kopie, konstruktor přesunutí, operátor přiřazení přesunutí nebo destruktor, pak:

  - Není automaticky generován žádný konstruktor move.

  - Není automaticky generován žádný operátor přiřazení přesunutí.

> [!NOTE]
> Standard C++11 navíc určuje následující další pravidla:
>
> - Pokud je explicitně deklarován konstruktor nebo destruktor kopie, je automatické generování operátoru přiřazení kopie zastaralé.
> - Pokud je explicitně deklarován operátor přiřazení kopie nebo destruktor, je automatické generování konstruktoru kopie zastaralé.
>
> V obou případech Visual Studio nadále automaticky generovat potřebné funkce implicitně a nevydává upozornění.

Důsledky těchto pravidel může také úniku do hierarchií objektů. Například pokud z nějakého důvodu základní třída neobsahuje výchozí konstruktor, který je volatelný z odvozené třídy – to **znamená,** že veřejný nebo **chráněný** konstruktor, který nepřijímá žádné parametry – pak třída, která je z ní odvozena, nemůže automaticky generovat vlastní výchozí konstruktor.

Tato pravidla mohou zkomplikovat implementaci co by mělo být přímočaré, uživatelem definované typy a společné c++ idiomy – například vytvoření uživatelem definovaného typu nekopírovatelné deklarováním konstruktoru kopie a operátoru přiřazení kopírování soukromě a jejich nedefinováním.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Před C++ 11 byl tento fragment kódu idiomatickou formou nekopírovatelných typů. Má však několik problémů:

- Kopie konstruktoru musí být deklarována soukromě skrýt, ale protože je deklarována vůbec, automatické generování výchozí konstruktor je zabráněno. Musíte explicitně definovat výchozí konstruktor, pokud chcete, i když to nedělá nic.

- I v případě, že explicitně definovaný výchozí konstruktor neprovede žádné, je kompilátorem považován za netriviální. Je méně efektivní než automaticky generovaný výchozí `noncopyable` konstruktor a zabraňuje tomu, aby byl skutečným typem POD.

- I když je konstruktor kopie a operátor přiřazení kopírování skryty `noncopyable` před vnějším kódem, členské funkce a přátelé aplikace je stále mohou zobrazit a volat. Pokud jsou deklarovány, ale nejsou definovány, jejich volání způsobí chybu propojovacího propojení.

- I když se jedná o běžně přijímaný idiom, záměr není jasný, pokud nerozumíte všem pravidlům pro automatické generování speciálních členských funkcí.

V jazyce C++ 11 lze nekopírovatelný idiom implementovat způsobem, který je přímočařejší.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Všimněte si, jak jsou vyřešeny problémy s idiomem před C++11:

- Generování výchozí konstruktor je stále zabráněno deklarováním konstruktoru kopie, ale můžete jej přivést zpět explicitně výchozí.

- Explicitně výchozí speciální členské funkce jsou stále považovány za `noncopyable` triviální, takže neexistuje žádná penalizace výkonu a není zabráněno být true POD typu.

- Konstruktor kopie a operátor přiřazení kopírování jsou veřejné, ale odstraněny. Je chyba kompilace definovat nebo volat odstraněné funkce.

- Záměr je jasný každému, `=default` kdo `=delete`rozumí a . Nemusíte rozumět pravidlům pro automatické generování speciálních členských funkcí.

Podobné idiomy existují pro vytváření uživatelem definovaných typů, které jsou nemovité, které lze pouze dynamicky přidělit nebo které nelze dynamicky přidělit. Každý z těchto idiomy mají pre-C++ 11 implementace, které trpí podobnými problémy a které jsou podobně vyřešeny v Jazyce C ++ 11 jejich implementací z hlediska výchozí a odstraněné speciální členské funkce.

## <a name="explicitly-defaulted-functions"></a>Explicitně výchozí funkce

Můžete výchozí výchozí některé zvláštní členské funkce – explicitně uvést, že zvláštní členské funkce používá výchozí implementaci, definovat zvláštní členské funkce s kvalifikátorem neveřejnépřístup nebo obnovit zvláštní členské funkce, jejichž automatické generování bylo zabráněno jinými okolnostmi.

Výchozí speciální členské funkce deklarováním jako v tomto příkladu:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Všimněte si, že můžete výchozí speciální členské funkce mimo tělo třídy tak dlouho, dokud je inlinable.

Z důvodu výhod výkonu triviální speciální členské funkce, doporučujeme, abyste raději automaticky generované speciální členské funkce před prázdná těla funkce, pokud chcete výchozí chování. Můžete to provést buď explicitní výchozí zvláštní členské funkce, nebo tím, že deklaruje (a také není deklarování jiné zvláštní členské funkce, které by zabránily jeho automatické generování.)

## <a name="deleted-functions"></a>Odstraněné funkce

Můžete odstranit speciální členské funkce, stejně jako normální členské funkce a nečlenské funkce, abyste zabránili jejich definování nebo volání. Odstranění speciálních členských funkcí poskytuje čistší způsob, jak zabránit kompilátoru ve generování speciálních členských funkcí, které nechcete. Funkce musí být odstraněna, jak je deklarována; nelze jej později odstranit způsobem, jakým lze deklarovat funkci a později výchozí hodnotu.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Odstranění normální členské funkce nebo nečlenských funkcí zabraňuje tomu, aby problematické povýšení typu způsobovalo volání nechtěné funkce. To funguje, protože odstraněné funkce stále účastní rozlišení přetížení a poskytují lepší shodu než funkce, která by mohla být volána po povýšení typů. Volání funkce překládá na konkrétnější – ale odstraněné – funkce a způsobí chybu kompilátoru.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Všimněte si v předchozí `call_with_true_double_only` ukázce, že volání pomocí **argumentu float** způsobí chybu kompilátoru, ale volání `call_with_true_double_only` pomocí argumentu **int** by ne; v případě **int** argument bude povýšen z **int** **double** a úspěšně volat **dvojitou** verzi funkce, i když to nemusí být to, co je zamýšleno. Chcete-li zajistit, že jakékoli volání této funkce pomocí non-double argument způsobí chybu kompilátoru, můžete deklarovat verzi šablony funkce, která je odstraněna.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
