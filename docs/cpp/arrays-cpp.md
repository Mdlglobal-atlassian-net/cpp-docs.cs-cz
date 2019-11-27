---
title: Pole (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188992"
---
# <a name="arrays-c"></a>Pole (C++)

Pole je posloupnost objektů stejného typu, které zaujímají souvislou oblast paměti. Tradiční pole ve stylu jazyka C jsou zdrojem mnoha chyb, ale jsou stále běžné, zejména v případě starších základů kódu. V moderní C++, důrazně doporučujeme použít [std:: Vector](../standard-library/vector-class.md) nebo [std:: Array](../standard-library/array-class-stl.md) namísto polí ve stylu jazyka C popsaných v této části. Oba tyto standardní typy knihoven ukládají své prvky jako souvislý blok paměti, ale poskytují mnohem větší bezpečnost typů spolu s iterátory, které mají zaručit, aby odkazovaly na platné umístění v rámci sekvence. Další informace najdete v tématu [kontejnery (moderní C++)](containers-modern-cpp.md).

## <a name="stack-declarations"></a>Deklarace zásobníku

V deklaraci C++ pole je velikost pole zadána za názvem proměnné, nikoli za názvem typu jako v některých jiných jazycích. Následující příklad deklaruje pole 1000 dvojitých hodnot, které mají být přiděleny v zásobníku. Počet elementů musí být dodán jako celočíselný literál nebo jinak jako konstantní výraz, protože kompilátor musí zjistit, kolik místa v zásobníku se má přidělit. nemůže použít hodnotu počítanou v době běhu. Každému elementu v poli je přiřazena výchozí hodnota 0. Pokud nepřiřazujete výchozí hodnotu, každý element zpočátku bude obsahovat jakékoli náhodné hodnoty, které budou v daném umístění.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

První prvek v poli je element 0th a poslední prvek je element (*n*-1), kde *n* je počet prvků, které pole může obsahovat. Počet elementů v deklaraci musí být integrálního typu a musí být větší než 0. Je vaší zodpovědností zajistit, že program nikdy nepředává hodnotu operátoru dolního indexu, který je větší než `(size - 1)`.

Pole s nulovou velikostí je platné pouze v případě, že je pole posledním polem **struktury** nebo **sjednocení** a když jsou povoleny rozšíření Microsoft Extensions (/ze).

Pole založené na zásobníku jsou rychlejší pro přidělení a přístup než pole založená na haldě, ale počet prvků nemůže být tak velký, aby používal příliš mnoho paměti zásobníku. Velikost je příliš velká, záleží na programu. Pomocí nástrojů pro profilaci můžete zjistit, jestli je pole moc velké.

## <a name="heap-declarations"></a>Deklarace haldy

Pokud požadujete, aby bylo pole, které je příliš velké pro přidělení v zásobníku, nebo jehož velikost nelze znát v době kompilace, můžete jej přidělit na haldu pomocí [nového\[výrazu \]](new-operator-cpp.md) . Operátor vrací ukazatel na první prvek. Operátor dolního indexu můžete použít s proměnnou ukazatele stejně jako s polem založeném na zásobníku. Můžete také použít [aritmetický ukazatel](../c-language/pointer-arithmetic.md) k přesunutí ukazatele na libovolný prvek v poli. Vaše zodpovědnost za zajištění těchto akcí:

- Vždycky uchováváte kopii původní adresy ukazatele, abyste ji mohli odstranit, pokud už pole nepotřebujete.
- nebudete zvyšovat ani snižovat adresu ukazatele za hranicemi pole.

Následující příklad ukazuje, jak definovat pole v haldě v době běhu a jak přistupovat k prvkům pole pomocí operátoru dolního indexu nebo pomocí aritmetického ukazatele:

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>Inicializace polí

Můžete inicializovat pole ve smyčce, jednom prvku v čase nebo v jednom příkazu. Obsah následujících dvou polí je stejný:

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>Předávání polí do funkcí

Když je pole předáno funkci, je předáno jako ukazatel na první prvek. To platí pro pole založená na zásobníku i na haldě. Ukazatel neobsahuje žádné další informace o velikosti ani typu. Toto chování se nazývá *ukazatel Decay*. Při předání pole do funkce je nutné vždy zadat počet prvků v samostatném parametru. Toto chování také znamená, že prvky pole nejsou zkopírovány, když je pole předáno funkci. Chcete-li zabránit funkci v úpravách prvků, zadejte parametr jako ukazatel na elementy **const** .

Následující příklad ukazuje funkci, která přijímá pole a délku. Ukazatel ukazuje na původní pole, nikoli na kopii. Vzhledem k tomu, že parametr není **const**, může funkce upravit prvky pole.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Deklarujte pole jako const, aby ho bylo možné jen pro čtení v rámci bloku funkce:

```cpp
void process(const double p*, const size_t len);
```

Stejnou funkci lze také deklarovat v těchto způsobech bez změny chování. Pole je stále předáno jako ukazatel na první prvek:

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>Multidimenzionální pole

Pole vytvořená z jiných polí jsou multidimenzionální pole. Tato multidimenzionální pole jsou určena umístěním více závorek konstantních výrazů v sekvenci. Zvažte například tuto deklaraci:

```cpp
int i2[5][7];
```

Určuje pole typu **int**, koncepčně uspořádané do dvojrozměrné matice na pěti řádcích a sedm sloupců, jak je znázorněno na následujícím obrázku:

![Koncepční rozložení vícerozměrného&#45;pole](../cpp/media/vc38rc1.gif "Koncepční rozložení vícerozměrného&#45;pole") <br/>
Koncepční rozložení multidimenzionálního pole

V deklaracích polí s více dimenzemi, které mají seznam inicializátorů (jak je popsáno v [inicializátorech](../cpp/initializers.md)), konstantní výraz, který určuje hranice pro první dimenzi, lze vynechat. Příklad:

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

Předchozí deklarace definuje pole, které má tři řádky se čtyřmi sloupci. Řádky reprezentují továrny a sloupce reprezentují trhy, na které se továrny dodávají. Hodnoty jsou náklady na dopravu z továrny na trhy. První dimenze pole je ponechána, ale kompilátor ji vyplní prozkoumáním inicializátoru.

Použití operátoru dereference (*) u n-dimenzionálního typu pole vrací jednorozměrné pole n-1. Pokud je n rovno 1, je vrácena skalární hodnota (nebo prvek pole).

Pole jazyka C++ jsou uložena podle pořadí hlavního řádku. Pořadím hlavního řádku se rozumí, že se nejrychlejší dolní index liší od posledního.

## <a name="example"></a>Příklad

Postup vynechání specifikace vazeb pro první dimenzi multidimenzionálního pole lze také použít v deklaracích funkce následujícím způsobem:

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

Funkce `FindMinToMkt` je zapsána tak, aby přidávání nových továren nevyžadovalo změny kódu, pouze opětovnou kompilaci.

## <a name="initializing-arrays"></a>Inicializace polí

Má-li třída konstruktor, pole této třídy jsou inicializována konstruktorem. Je-li v seznamu inicializátorů méně položek než prvků pole, je pro zbývající prvky použit výchozí konstruktor. Není-li pro třídu definován výchozí konstruktor, musí být seznam inicializátorů úplný – pro každý prvek pole tedy musí existovat jeden inicializátor.

Vezměte v úvahu třídu `Point` definující dva konstruktory:

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

První prvek pole `aPoint` je vytvořen pomocí konstruktoru `Point( int, int )`. Zbývající dva prvky jsou vytvořeny výchozím konstruktorem.

Statická pole členů (zda **const** nebo not) mohou být inicializována ve svých definicích (mimo deklaraci třídy). Příklad:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>Přístup k prvkům pole

K jednotlivým prvkům pole můžete přistupovat pomocí operátoru dolního indexu pole (`[ ]`). Pokud je jednorozměrné pole použito ve výrazu, který nemá žádný dolní index, název pole se vyhodnotí jako ukazatel na první prvek v poli.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Při použití multidimenzionálních polí můžete použít různé kombinace ve výrazech.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

V předchozím kódu je `multi` trojrozměrné pole typu **Double**. Ukazatel `p2multi` odkazuje na pole typu **Double** o velikosti tři. V tomto příkladu je pole použito s jedním, dvěma a třemi dolními indexy. I když je obvyklejší zadat všechny dolní indexy, jako v příkazu `cout`, je někdy užitečné vybrat konkrétní podmnožinu prvků pole, jak je znázorněno v příkazech, které následují `cout`.

## <a name="overloading-subscript-operator"></a>Přetížení operátoru dolního indexu

Stejně jako ostatní operátory může být operátor dolního indexu (`[]`) předefinován uživatelem. Výchozí chování operátoru indexu, pokud není přetížen, je kombinování názvu pole a indexu pomocí následující metody:

`*((array_name) + (subscript))`

Stejně jako všechna sčítání, která zahrnují typy ukazatelů, se změna velikosti provádí automaticky pro úpravu velikosti typu. Proto výsledná hodnota není *n* bajtů od počátku pole-Name; místo toho je to *n*-tou prvek pole. Další informace o tomto převodu naleznete v tématu [operátory sčítání](additive-operators-plus-and.md).

Pro vícerozměrná pole je adresa odvozena podobně následujícím způsobem:

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>Pole ve výrazech

Když je identifikátor typu pole zobrazen ve výrazu jiném než `sizeof`, adresa (`&`) nebo inicializace odkazu, je převeden na ukazatel na první prvek pole. Příklad:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Ukazatel `psz` odkazuje na první prvek pole `szError1`. Pole, na rozdíl od ukazatelů, nejsou upravitelná l-hodnota. Proto je následující přiřazení neplatné:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Viz také:

[std:: Array](../standard-library/array-class-stl.md)
