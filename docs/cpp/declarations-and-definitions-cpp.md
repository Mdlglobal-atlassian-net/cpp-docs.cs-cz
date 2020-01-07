---
title: Deklarace a definice (C++)
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: d52294b635e05f42a4c48620214a90cad609f575
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301545"
---
# <a name="declarations-and-definitions-c"></a>Deklarace a definice (C++)

C++ Program se skládá z různých entit, jako jsou proměnné, funkce, typy a obory názvů. Každá z těchto entit musí být *deklarována* dříve, než bude možné ji použít. Deklarace určuje jedinečný název entity společně s informacemi o jejím typu a dalších vlastnostech. V C++ bodě, kde je název deklarován, je bod, ve kterém se bude viditelný pro kompilátor. Nelze odkazovat na funkci nebo třídu, která je deklarována v pozdějším okamžiku v kompilační jednotce. Proměnné by měly být deklarovány co nejblíže před bodem, ve kterém jsou použity.

Následující příklad ukazuje některé deklarace:

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

Na řádku 5 je deklarována funkce `main`. Na řádku 7 je proměnná **const** s názvem `pi` deklarovaná a *inicializovaná*. Na řádku 8 je celočíselná `i` deklarovaná a inicializovaná s hodnotou vytvořenou `f`funkcí. Název `f` je viditelný pro kompilátor z důvodu *dopředné deklarace* na řádku 3. 

V řádku 9 je deklarována proměnná s názvem `obj` typu `C`. Tato deklarace však vyvolá chybu, protože `C` není deklarována až později v programu a není deklarována s dopředně. Chcete-li chybu opravit, můžete buď přesunout celou *definici* `C` před `main` nebo jinak přidat k ní deklaraci dopředné deklarace. Toto chování se liší od jiných jazyků C#, jako je například, ve kterém lze funkce a třídy použít před jejich bodem deklarace ve zdrojovém souboru. 

V řádku 10 je deklarována proměnná s názvem `str` typu `std::string`. Název `std::string` je viditelný, protože je představen v [souboru hlaviček](header-files-cpp.md) `string`, který je sloučen do zdrojového souboru na řádku 1. `std` je obor názvů, ve kterém je deklarována `string` třída.

Na řádku 11 je vyvolána chyba, protože název `j` nebyl deklarován. Deklarace musí poskytovat typ na rozdíl od jiných jazyků, jako je například javaScript. V řádku 12 je použita klíčová slova `auto`, která instruuje kompilátor, aby odvodit typ `k` na základě hodnoty, se kterou je inicializován. Kompilátor v tomto případě zvolí `int` pro daný typ.  

## <a name="declaration-scope"></a>Rozsah deklarace

Název, který je zavedený deklarací, je platný v *oboru* , ve kterém se nachází deklarace. V předchozím příkladu proměnné, které jsou deklarovány uvnitř funkce `main`, jsou *lokální proměnné*. Můžete deklarovat další proměnnou s názvem `i` mimo hlavní, v *globálním oboru*a by to byla zcela samostatná entita. Takové duplikace názvů ale mohou vést k nejasnostem a chybám programátora a je třeba se jim vyhnout. V řádku 21 je třída `C` deklarována v oboru oboru názvů `N`. Použití oborů názvů pomáhá zabránit *kolizím názvů*. Většina C++ názvů standardních knihoven je deklarována v rámci oboru názvů `std`. Další informace o tom, jak pravidla oboru pracují s deklaracemi, najdete v tématu [Scope](../cpp/scope-visual-cpp.md).

## <a name="definitions"></a>Definice

Některé entity, včetně funkcí, tříd, výčtů a konstantních proměnných, musí být definovány kromě deklarovaného. *Definice* poskytuje kompilátoru všechny informace, které potřebuje k vygenerování kódu počítače při pozdějším použití entity v programu. V předchozím příkladu řádek 3 obsahuje deklaraci funkce `f` ale *definice* funkce je k dispozici na řádcích 15 až 18. Na řádku 21 je třída `C` deklarována i definována (i když definování třídy nedělá žádnou hodnotu). Je nutné definovat konstantní proměnnou, jinými slovy, která je přiřazena hodnota, ve stejném příkazu, v němž je deklarována. Deklarace předdefinovaného typu, jako je například `int`, je automaticky definice, protože kompilátor ví, kolik místa je pro něj přiděleno.

Následující příklad ukazuje deklarace, které jsou také definice:

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

Tady je několik deklarací, které nejsou definicemi:

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Definice typedef a using – příkazy

Ve starších verzích C++nástroje klíčové slovo [typedef](aliases-and-typedefs-cpp.md) slouží k deklaraci nového názvu, který je *aliasem* pro jiný název. Například typ `std::string` je jiný název pro `std::basic_string<char>`. Mělo by být zřejmé, proč programátoři používají název typedef a nikoli skutečný název. V moderním C++se klíčové slovo [using](aliases-and-typedefs-cpp.md) upřednostňuje přes typedef, ale nápad je stejný: nový název je deklarovaný pro entitu, která už je deklarovaná a definovaná.

## <a name="static-class-members"></a>Statické členy třídy

Vzhledem k tomu, že jsou datové členy statické třídy diskrétní proměnné sdílené všemi objekty třídy, musí být definovány a inicializovány mimo definici třídy. (Další informace naleznete v tématu [třídy](../cpp/classes-and-structs-cpp.md).)

## <a name="extern-declarations"></a>Externí deklarace

C++ Program může obsahovat více než jednu [jednotku kompilace](header-files-cpp.md). Chcete-li deklarovat entitu, která je definována v samostatné kompilační jednotce, použijte klíčové slovo [extern](extern-cpp.md) . Informace v deklaraci jsou pro kompilátor dostačující, ale pokud definici entity nelze najít v kroku propojení, pak linker vyvolá chybu.

## <a name="in-this-section"></a>V tomto oddílu

[Třídy úložiště](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[Inicializátory](initializers.md)<br/>
[Aliasy a definice Typedef](aliases-and-typedefs-cpp.md)<br/>
[deklarace using](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[Atributy vC++](attributes.md)<br/>

## <a name="see-also"></a>Viz také:

[Základní koncepty](../cpp/basic-concepts-cpp.md)<br/>
