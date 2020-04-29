---
title: Přehled produktu C++ AMP
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: f0b46065371b8cb70802cfc38b7365fd2db14bf5
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538637"
---
# <a name="c-amp-overview"></a>Přehled produktu C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) zrychlí provádění kódu jazyka C++ využitím hardwaru, jako je například grafický procesor (GPU) na samostatné grafické kartě. Pomocí C++ AMP můžete kódovat multidimenzionální datové algoritmy, aby bylo možné spuštění zrychlit pomocí paralelismu na heterogenním hardwaru. C++ AMP programovací model zahrnuje multidimenzionální pole, indexování, přenos paměti, dělení a knihovnu matematické funkce. Pomocí C++ AMP jazykové rozšíření můžete řídit, jak se data přesunou z procesoru do GPU a zpět, abyste mohli zvýšit výkon.

## <a name="system-requirements"></a>Systémové požadavky

- Windows 7 nebo novější

- Windows Server 2008 R2 nebo novější

- DirectX 11 – úroveň funkcí 11,0 nebo novější hardware

- Pro ladění v emulátoru softwaru se vyžaduje Windows 8 nebo Windows Server 2012. Pro ladění na hardwaru je nutné nainstalovat ovladače pro grafickou kartu. Další informace najdete v tématu [ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code).

- Poznámka: v ARM64 se v tuto chvíli nepodporuje AMP.

## <a name="introduction"></a>Úvod

Následující dva příklady ilustrují primární součásti C++ AMP. Předpokládejme, že chcete přidat odpovídající prvky 2 1 polí. Například můžete chtít přidat `{1, 2, 3, 4, 5}` a `{6, 7, 8, 9, 10}` získat. `{7, 9, 11, 13, 15}` Bez použití C++ AMP může napsat následující kód pro přidání čísel a zobrazení výsledků.

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

Důležité části kódu jsou následující:

- Data: data se skládají ze tří polí. Všechny mají stejný rozměr (jedna) a length (pět).

- Iterace: první `for` smyčka poskytuje mechanismus pro iteraci prvků v polích. Kód, který chcete spustit pro výpočet součtu, je obsažen v prvním `for` bloku.

- Index: `idx` proměnná přistupuje k jednotlivým prvkům polí.

Pomocí C++ AMP můžete místo toho napsat následující kód.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

Jsou k dispozici stejné základní prvky, ale C++ AMP konstrukce jsou použity:

- Data: k vytvoření tří objektů C++ AMP [Array_view](../../parallel/amp/reference/array-view-class.md) lze použít pole jazyka C++. Zadáte čtyři hodnoty pro vytvoření `array_view` objektu: hodnoty dat, pořadí, typ prvku a délku `array_view` objektu v každé dimenzi. Pořadí a typ jsou předány jako parametry typu. Data a délka jsou předány jako parametry konstruktoru. V tomto příkladu je pole C++, které je předáno konstruktoru, jednorozměrné. Pořadí a délka slouží k vytvoření obdélníkového tvaru dat v `array_view` objektu a hodnoty dat slouží k vyplnění pole. Běhová knihovna také obsahuje [třídu Array](../../parallel/amp/reference/array-class.md), která má rozhraní, které se podobá `array_view` třídě a je popsána dále v tomto článku.

- Iterace: [funkce parallel_for_each (C++ amp)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) poskytuje mechanismus pro iteraci v datových prvcích nebo *výpočetní doméně*. V tomto příkladu je výpočetní doména určena pomocí `sum.extent`. Kód, který chcete spustit, je obsažen ve výrazu lambda nebo ve *funkci jádra*. `restrict(amp)` Určuje, že se používá pouze podmnožina jazyka C++, kterou C++ amp může zrychlit.

- Index: proměnná [třídy indexu](../../parallel/amp/reference/index-class.md) , `idx`, je deklarována s rozměrem jednoho, aby odpovídala rozměru `array_view` objektu. Pomocí indexu můžete přistupovat k jednotlivým prvkům `array_view` objektů.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Tvarování a indexování dat: index a rozsah

Než budete moci spustit kód jádra, je nutné definovat hodnoty dat a deklarovat tvar dat. Všechna data jsou definovaná jako pole (pravoúhlá) a můžete definovat, že pole bude mít libovolné pořadí (počet dimenzí). Data mohou mít libovolnou velikost v libovolné z dimenzí.

### <a name="index-class"></a>index – třída

[Třída index](../../parallel/amp/reference/index-class.md) určuje umístění v objektu `array` nebo `array_view` zapouzdřením posunu od počátku v každé dimenzi do jednoho objektu. Při přístupu k umístění v poli předáte `index` objektu operátoru `[]`indexování místo seznamu indexů celých čísel. K prvkům v jednotlivých dimenzích můžete přistupovat pomocí [operátoru Array:: operator ()](reference/array-class.md#operator_call) nebo [operátoru array_view:: operator ()](reference/array-view-class.md#operator_call).

Následující příklad vytvoří jednorozměrné index, který určuje třetí prvek v jednorozměrném `array_view` objektu. Index se používá k vytištění třetího prvku v `array_view` objektu. Výstup má hodnotu 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

Následující příklad vytvoří dvourozměrný index, který určuje prvek, kde řádek = 1 a sloupec = 2 v dvojrozměrném `array_view` objektu. Prvním parametrem v `index` konstruktoru je komponenta řádku a druhý parametr je komponenta sloupce. Výstup je 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

Následující příklad vytvoří prostorový index, který určuje prvek, kde hloubka = 0, řádek = 1 a sloupec = 3 v trojrozměrném `array_view` objektu. Všimněte si, že první parametr je hloubka komponenty, druhým parametrem je komponenta řádku a třetí parametr je komponenta sloupce. Výstup je 8.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent – třída

[Třída rozsahu](../../parallel/amp/reference/extent-class.md) určuje délku dat v každém rozměru objektu `array` or. `array_view` Můžete vytvořit rozsah a použít ho k vytvoření objektu `array` nebo. `array_view` Můžete také načíst rozsah existujícího `array` objektu nebo. `array_view` Následující příklad vytiskne délku rozsahu v každém rozměru `array_view` objektu.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

Následující příklad vytvoří `array_view` objekt, který má stejné rozměry jako objekt v předchozím příkladu, ale v tomto příkladu se místo použití explicitních `extent` parametrů v `array_view` konstruktoru používá objekt.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>Přesun dat do akcelerátoru: pole a array_view

Dva datové kontejnery, které slouží k přesunu dat do akcelerátoru, jsou definovány v knihovně modulu runtime. Jsou to [Třída Array](../../parallel/amp/reference/array-class.md) a [třída array_view](../../parallel/amp/reference/array-view-class.md). `array` Třída je třída kontejneru, která vytvoří hloubkovou kopii dat, když je objekt vytvořen. `array_view` Třída je Obálková třída, která kopíruje data v případě, že funkce jádra přistupuje k datům. Když jsou na zdrojovém zařízení potřebná data, data se zkopírují zpátky.

### <a name="array-class"></a>array – třída

Pokud je `array` vytvořen objekt, je vytvořena hluboká kopie dat v akcelerátoru, pokud použijete konstruktor, který obsahuje ukazatel na datovou sadu. Funkce jádra upraví kopii v akcelerátoru. Po dokončení spuštění funkce jádra je nutné zkopírovat data zpět do struktury zdrojových dat. Následující příklad vynásobí každý prvek ve vektoru hodnotou 10. Po dokončení `vector conversion operator` funkce jádra se použije ke zkopírování dat zpět do objektu Vector.

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="array_view-class"></a>array_view – třída

`array_view` Má skoro stejné členy jako `array` třída, ale základní chování není stejné. Data předaná `array_view` konstruktoru nejsou replikována na GPU, protože se jedná o `array` konstruktor. Místo toho se data zkopírují do akcelerátoru, když se spustí funkce jádra. Proto pokud vytvoříte dva `array_view` objekty, které používají stejná data, oba `array_view` objekty budou odkazovat na stejný paměťový prostor. Když to uděláte, musíte synchronizovat jakýkoli vícevláknový přístup. Hlavní výhodou použití `array_view` třídy je, že data se přesunou pouze v případě, že je to nezbytné.

### <a name="comparison-of-array-and-array_view"></a>Porovnání pole a array_view

Následující tabulka shrnuje podobnosti a rozdíly mezi třídami `array` a. `array_view`

|Popis|array – třída|array_view – třída|
|-----------------|-----------------|-----------------------|
|Při určení pořadí|V době kompilace.|V době kompilace.|
|Když se určí rozsah|V době běhu.|V době běhu.|
|Obrazec|–.|–.|
|Úložiště dat|Je datový kontejner.|Je obálka dat.|
|Kopírovat|Explicitní a hluboká kopie v definici|Implicitní kopírování, je-li k němu přistupovaná funkce jádra.|
|Načítání dat|Zkopírováním dat pole zpět do objektu ve vlákně procesoru.|Přímým přístupem k `array_view` objektu nebo voláním [metody array_view:: Synchronize](reference/array-view-class.md#synchronize) pro pokračování přístupu k datům v původním kontejneru.|

### <a name="shared-memory-with-array-and-array_view"></a>Sdílená paměť s polem a array_view

Sdílená paměť je paměť, ke které je možné použít procesor i akcelerátor. Použití sdílené paměti eliminuje nebo významně snižuje nároky na kopírování dat mezi CPU a akcelerátorem. I když je paměť sdílená, nelze k ní současně přistupovat pomocí procesoru i akcelerátoru, což způsobí nedefinované chování.

`array`objekty lze použít k určení jemně odstupňované kontroly nad použitím sdílené paměti, pokud je příslušný akcelerátor podporuje. Zda akcelerátor podporuje sdílenou paměť, je určena vlastností [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) akcelerátoru, která vrací **hodnotu true** , pokud je sdílená paměť podporována. Pokud je podporovaná sdílená paměť, [vyčíslení výchozího Access_type výčtu](reference/concurrency-namespace-enums-amp.md#access_type) pro přidělení paměti v akcelerátoru `default_cpu_access_type` je určené vlastností. Ve výchozím nastavení `array` objekty `array_view` a převezmou `access_type` objekty, které jsou přidruženy k `accelerator`primárnímu objektu.

Nastavením vlastnosti [pole datového členu Array:: cpu_access_type](reference/array-class.md#cpu_access_type) `array` explicitně můžete vykonat jemně odstupňovanou kontrolu nad tím, jak se používá sdílená paměť, takže můžete optimalizovat aplikaci pro výkonnostní charakteristiky hardwaru, a to na základě vzorců přístupu k paměti pro výpočetní jádra. `array_view` Odpovídá stejnému `cpu_access_type` jako k `array` , ke kterému je přidružen; nebo pokud je array_view vytvořená bez zdroje dat, `access_type` odráží prostředí, které nejdřív způsobí, že mu přidělí úložiště. To znamená, že pokud je poprvé k němu přistupující hostitel (CPU), chová se, jako by byl vytvořen přes zdroj dat procesoru, a sdílí `access_type` objekt `accelerator_view` přidružený pomocí zachycení. Pokud je však poprvé k `accelerator_view`dispozici, bude se chovat, jako by byl vytvořen pomocí `array` vytvořeného objektu `accelerator_view` a sdílí. `array` `access_type`

Následující příklad kódu ukazuje, jak určit, zda výchozí akcelerátor podporuje sdílenou paměť, a poté vytvoří několik polí, které mají různé konfigurace cpu_access_type.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallel_for_each"></a>Spouští se kód pro data: parallel_for_each

Funkce [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) definuje kód, který chcete spustit v akcelerátoru proti datům v objektu `array` nebo. `array_view` Vezměte v úvahu následující kód z úvodu tohoto tématu.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

`parallel_for_each` Metoda přijímá dva argumenty, výpočetní doménu a výraz lambda.

*Výpočetní doména* je `extent` objekt nebo `tiled_extent` objekt, který definuje sadu vláken, která se má vytvořit pro paralelní spuštění. Jedno vlákno je vygenerováno pro každý prvek ve výpočetní doméně. V tomto případě je `extent` objekt jednorozměrné a má pět prvků. Proto se spustí pět vláken.

*Výraz lambda* definuje kód, který se má spustit v každém vlákně. Klauzule `[=]`Capture, určuje, že tělo výrazu lambda přistupuje ke všem zachyceným proměnným podle hodnoty, což v tomto případě `a`jsou, `b`a. `sum` V tomto příkladu seznam parametrů vytvoří jednorozměrné `index` proměnné s názvem. `idx` Hodnota `idx[0]` je 0 v prvním vlákně a v každém dalším vlákně se zvyšuje o jednu. `restrict(amp)` Určuje, že se používá pouze podmnožina jazyka C++, kterou C++ amp může zrychlit.  Omezení funkcí, které mají modifikátor omezení, jsou popsána v tématu [restrict (C++ amp)](../../cpp/restrict-cpp-amp.md). Další informace naleznete v tématu, [syntaxe výrazu lambda](../../cpp/lambda-expression-syntax.md).

Výraz lambda může zahrnovat kód, který se má provést, nebo může volat samostatnou funkci jádra. Funkce jádra musí zahrnovat `restrict(amp)` modifikátor. Následující příklad je ekvivalentní k předchozímu příkladu, ale volá samostatnou funkci jádra.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>Zrychlení kódu: dlaždice a bariéry

Další akceleraci můžete získat pomocí dělení na sebe. Dělení rozdělí vlákna na stejné pravoúhlé podmnožiny nebo *dlaždice*. Určíte velikost příslušné dlaždice na základě vaší sady dat a algoritmu, který kódujete. Pro každé vlákno máte přístup k *globálnímu* umístění datového prvku relativně k celému `array` nebo `array_view` a přístup k *místnímu* umístění vzhledem k dlaždici. Použití hodnoty místního indexu zjednodušuje váš kód, protože nemusíte psát kód pro převod hodnot indexu z globálních na místní. Chcete-li použít dělení na více objektů, zavolejte [metodu rozsah:: Tile](reference/extent-class.md#tile) ve výpočetní doméně `parallel_for_each` v metodě a použijte objekt [tiled_index](../../parallel/amp/reference/tiled-index-class.md) ve výrazu lambda.

V typických aplikacích se prvky v dlaždici vztahují nějakým způsobem a kód musí mít přístup a sledovat hodnoty napříč dlaždicí. K tomuto účelu použijte klíčové slovo [tile_static](../../cpp/tile-static-keyword.md) a [metodu tile_barrier:: wait](reference/tile-barrier-class.md#wait) . Proměnná, která má klíčové slovo **tile_static** má obor v celé dlaždici a instance proměnné je vytvořena pro každou dlaždici. Je nutné zpracovat synchronizaci přístupu vlákna dlaždice k proměnné. [Metoda tile_barrier:: wait](reference/tile-barrier-class.md#wait) zastaví provádění aktuálního vlákna, dokud všechna vlákna v dlaždici nedosáhnou volání `tile_barrier::wait`. Takže můžete nashromáždit hodnoty přes dlaždici pomocí **tile_static** proměnných. Pak můžete dokončit jakékoli výpočty, které vyžadují přístup ke všem hodnotám.

Následující diagram představuje dvojrozměrné pole dat vzorkování, která jsou uspořádána do dlaždic.

![Indexovat hodnoty v dlaždicovém rozsahu](../../parallel/amp/media/camptiledgridexample.png "Indexovat hodnoty v dlaždicovém rozsahu")

Následující příklad kódu používá data vzorkování z předchozího diagramu. Kód nahradí každou hodnotu v dlaždici průměrem hodnot v dlaždici.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>Matematické knihovny

C++ AMP obsahuje dvě matematické knihovny. Knihovna s dvojitou přesností v [oboru názvů Concurrency::p recise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) poskytuje podporu pro funkce s dvojitou přesností. Poskytuje taky podporu pro funkce s jednoduchou přesností, i když je u hardwaru pořád povinná podpora s dvojitou přesností. Je v souladu se [specifikací C99 (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887). Akcelerátor musí podporovat celou dvojitou přesnost. Můžete určit, zda se jedná, kontrolou hodnoty [datového členu akcelerátor:: supports_double_precision](reference/accelerator-class.md#supports_double_precision). Rychlá knihovna matematického [zpracování v oboru názvů Concurrency:: fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md)obsahuje další sadu matematických funkcí. Tyto funkce, které podporují jenom `float` operandy, se spouštějí rychleji, ale nejsou tak přesné jako ty v matematické knihovně s dvojitou přesností. Funkce jsou obsaženy v souboru hlaviček \<> amp_math. h a všechny jsou deklarovány pomocí `restrict(amp)`. Funkce v souboru hlaviček \<> cmath jsou importovány do obou oborů názvů `fast_math` a `precise_math` . Klíčové slovo **restrict** slouží k odlišení \<cmath verze> a C++ amp verzi. Následující kód vypočítá logaritmus o základu 10 pomocí rychlé metody každé hodnoty, která je ve výpočetní doméně.

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>Knihovna grafiky

C++ AMP obsahuje knihovnu grafiky, která je navržena pro urychlené programování grafiky. Tato knihovna se používá jenom na zařízeních, která podporují nativní grafické funkce. Metody jsou v [oboru názvů Concurrency:: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) a jsou obsaženy v souboru hlaviček \<> amp_graphics. h. Klíčové komponenty knihovny grafiky jsou:

- [Texture – třída](../../parallel/amp/reference/texture-class.md): lze použít třídu textury k vytváření textur z paměti nebo ze souboru. Textury připomínají pole, protože obsahují data a připomínají se kontejnery ve standardní knihovně C++ s ohledem na přiřazení a konstrukci kopírování. Další informace najdete v tématu [kontejnery knihovny Standard C++](../../standard-library/stl-containers.md). Parametry šablony pro `texture` třídu jsou typ prvku a pořadí. Pořadí může být 1, 2 nebo 3. Typ prvku může být jeden z typů krátkých vektorů, které jsou popsány dále v tomto článku.

- [Writeonly_texture_view třída](../../parallel/amp/reference/writeonly-texture-view-class.md): poskytuje přístup jen pro zápis k libovolné textuře.

- Krátká vektorová knihovna: definuje sadu krátkých vektorových typů délky 2, 3 a 4, které jsou založené na **int**, `uint`, **float**, **Double**, [normě](../../parallel/amp/reference/norm-class.md)nebo [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Aplikace Univerzální platforma Windows (UWP)

Stejně jako jiné knihovny jazyka C++ můžete ve svých aplikacích pro UWP použít C++ AMP. Tyto články popisují, jak zahrnout kód C++ AMP v aplikacích, které jsou vytvořeny pomocí jazyků C++, C#, Visual Basic nebo JavaScript:

- [Používání C++ AMP v aplikacích pro UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Návod: Vytvoření základní komponenty prostředí Windows Runtime v jazyce C++ a její volání z JavaScriptu](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Optimalizátor cest mapy Bingu, aplikace pro Windows Store v JavaScriptu a C++](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [Použití C++ AMP z jazyka C# pomocí prostředí Windows Runtime](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [Použití C++ AMP z jazyka C #](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [Volání nativních funkcí ze spravovaného kódu](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP a Vizualizér souběžnosti

Vizualizátor souběžnosti zahrnuje podporu pro analýzu výkonu C++ AMPho kódu. Tyto články popisují tyto funkce:

- [Graf aktivity GPU](/visualstudio/profiling/gpu-activity-graph)

- [Aktivita GPU (stránkování)](/visualstudio/profiling/gpu-activity-paging)

- [Aktivita GPU (tento proces)](/visualstudio/profiling/gpu-activity-this-process)

- [Aktivita GPU (jiné procesy)](/visualstudio/profiling/gpu-activity-other-processes)

- [Kanály (Zobrazení vláken)](/visualstudio/profiling/channels-threads-view)

- [Analýza kódu C++ AMP pomocí Vizualizátor souběžnosti](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>Doporučení k výkonu

Modulo a dělení celých čísel bez znaménka mají výrazně lepší výkon než modul a dělení celých čísel se znaménkem. Pokud je to možné, doporučujeme použít celá čísla bez znaménka.

## <a name="see-also"></a>Viz také

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe výrazu lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Paralelní programování v blogu nativního kódu](https://go.microsoft.com/fwlink/p/?linkid=238472)
