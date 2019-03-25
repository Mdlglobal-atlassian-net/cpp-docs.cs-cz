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
ms.openlocfilehash: 258266768d3f456fb761a9d5a403a92c502dbe32
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356241"
---
# <a name="c-amp-overview"></a>Přehled produktu C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) urychluje provádění kódu jazyka C++ využitím hardwaru paralelizovaného pro data, jako jsou grafický procesor (GPU) na samostatné grafické kartě. S použitím jazyka C++ AMP, vám umožní kódování algoritmy vícerozměrnými daty tak, aby provádění bude urychleno pomocí paralelismu na heterogenním hardwaru. Model programování C++ AMP zahrnuje vícerozměrná pole, indexování, přenos paměti, rozložení a knihovnu matematických funkcí. Rozšíření jazyka C++ AMP můžete řídit, jak jsou data přenášena z procesoru do GPU a zpět, takže můžete zlepšit výkon.

## <a name="system-requirements"></a>Požadavky na systém

- Windows 7 nebo novější

- Windows Server 2008 R2 nebo novější

- Rozhraní DirectX 11 úroveň funkce 11.0 nebo novější hardware

- Pro ladění v softwarovém emulátoru se vyžaduje systém Windows 8 nebo Windows Server 2012. Pro ladění na hardwaru, je nutné nainstalovat ovladače pro grafickou kartu. Další informace najdete v tématu [ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code).

- Poznámka: AMP není aktuálně podporována u ARM64.

## <a name="introduction"></a>Úvod

Následující dva příklady ilustrují primární součásti knihovny C++ AMP. Předpokládejme, že chcete přidat odpovídající prvky dvou jednorozměrných polí. Například můžete chtít přidat `{1, 2, 3, 4, 5}` a `{6, 7, 8, 9, 10}` získat `{7, 9, 11, 13, 15}`. Bez používání modelu C++ AMP, můžete například napsat následující kód pro přidání čísel a zobrazení výsledků.

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

- Data: Data obsahují tři pole. Všechny mají stejný počet rozměrů (jeden) a délku (pět).

- Iterace: První `for` smyčky poskytuje mechanismus pro procházení prvků v polích. Kód, který chcete spustit pro výpočet součtu je obsažen v prvním `for` bloku.

- Index: `idx` Proměnnou přistupuje k jednotlivým prvkům polí.

Používání modelu C++ AMP, můžete například napsat následující kód místo.

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

Stejné základní prvky jsou k dispozici, ale jsou použity konstrukce knihovny C++ AMP:

- Data: Pole jazyka C++ lze použít k sestavení tři C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) objekty. Zadat čtyři hodnoty k vytvoření `array_view` objektu: hodnoty dat, počet rozměrů, typ elementu a délku `array_view` objektu v každém rozměru. Počet rozměrů a typ jsou předány jako parametry typu. Data a délka jsou předány jako parametry konstruktoru. V tomto příkladu je jednorozměrné pole jazyka C++, která je předána do konstruktoru. Počet rozměrů a délka se používají k tvorbě obdélníkového tvaru dat `array_view` objektu a datové hodnoty jsou použity k vyplnění pole. Běhová knihovna také zahrnuje [array – třída](../../parallel/amp/reference/array-class.md), která má podobné rozhraní `array_view` třídy a je popsána dále v tomto článku.

- Iterace: [Parallel_for_each – funkce (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) poskytuje mechanismus pro procházení datových prvků, nebo *výpočetní domény*. V tomto příkladu je výpočetní domény určené `sum.extent`. Kód, který chcete spustit je obsažen ve výrazu lambda nebo *funkce jádra*. `restrict(amp)` Označuje, že je použita pouze podmnožina jazyka C++, kterou může knihovna C++ AMP urychlit.

- Index: [Index – třída](../../parallel/amp/reference/index-class.md) proměnnou, `idx`, je deklarována s rozměrem jedna, aby odpovídala pořadí `array_view` objektu. Pomocí indexu lze přistupovat k jednotlivým prvkům `array_view` objekty.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Tvarování a indexování dat: index a rozsah

Musíte definovat hodnoty dat a deklarovat tvar dat. před spuštěním kódu jádra. Všechna data je definován jako poli (obdélníkovém) a můžete definovat pole, které chcete mít jakékoliv řazení (počet rozměrů). Data mohou být libovolné velikosti v libovolný počet rozměrů.

### <a name="index-class"></a>index – třída

[Index – třída](../../parallel/amp/reference/index-class.md) Určuje umístění v `array` nebo `array_view` objekt zapouzdřením posunu od začátku v každém rozměru do jednoho objektu. Při přístupu k umístění, do pole, předáte `index` objekt indexujícímu operátoru `[]`, namísto seznamu celočíselných indexů. Pomocí můžete přístup k prvkům v každém rozměru [array:: operator() – operátor](reference/array-class.md#operator_call) nebo [array_view:: Operator() – operátor](reference/array-view-class.md#operator_call).

Následující příklad vytvoří jednorozměrný index, který určuje třetí prvek v jednorozměrném `array_view` objektu. Index je použit ke zobrazení třetího prvku `array_view` objektu. Výstup je 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

Následující příklad vytváří dvojrozměrný index, který určuje prvek kde na řádku 1 a ve sloupci = 2 v dvourozměrném `array_view` objektu. První parametr v `index` konstruktor je řádek a druhý parametr zase sloupec. Výstup je 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

Následující příklad vytvoří trojrozměrný index, který určuje prvek kde hloubka = 0, na řádku 1 a ve sloupci = 3 v trojrozměrném `array_view` objektu. Všimněte si, že první parametr je hloubka, druhý parametr je řádek a třetí parametr zase sloupec. Výstup je 8.

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

[Extent – třída](../../parallel/amp/reference/extent-class.md) určuje délku dat v každém rozměru objektu `array` nebo `array_view` objektu. Můžete vytvořit rozsah a použít ho k vytvoření `array` nebo `array_view` objektu. Můžete také získat rozsah existujícího `array` nebo `array_view` objektu. Následující příklad vytiskne délku rozsahu v každém rozměru objektu `array_view` objektu.

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

Následující příklad vytvoří `array_view` objekt, který má stejné rozměry jako objekt v předchozím příkladu, ale v tomto příkladu používá `extent` namísto použití explicitních parametrů v objektu `array_view` konstruktoru.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Přesun dat na akcelerátor: array a array_view

Dva datové kontejnery používají pro přesun dat do akcelerátoru jsou definovány v knihovně modulu runtime. Jsou [array – třída](../../parallel/amp/reference/array-class.md) a [array_view – třída](../../parallel/amp/reference/array-view-class.md). `array` Třída je třídou kontejneru, která při vytvoření objektu vytvoří hlubokou kopii dat. `array_view` Třída je třídou obálky, která zkopíruje data při funkce jádra přistupuje k datům. Při potřebě dat na zdrojovém zařízení jsou data zkopírována zpět.

### <a name="array-class"></a>array – třída

Když `array` objekt je vytvořen, hluboká kopie dat se vytvoří v akcelerátoru, pokud je použit konstruktor, který obsahuje ukazatel na datové sadě. Funkce jádra modifikuje kopii v akcelerátoru. Po dokončení spuštění funkce jádra musí zkopírovat data zpět do struktury zdrojových dat. Následující příklad vynásobí každý prvek vektoru 10. Po dokončení funkce jádra `vector conversion operator` se použije ke zkopírování dat zpět do objektu vektoru.

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

### <a name="arrayview-class"></a>array_view – třída

`array_view` Má téměř stejné členy jako `array` třídy, ale základní chování není totéž. Data předaná do `array_view` konstruktor není v GPU replikována tak jako u `array` konstruktoru. Místo toho data zkopírována do akcelerátoru při provádění funkce jádra. Proto pokud jsou vytvořeny dva `array_view` objekty, které používají stejná data, oba `array_view` objekty odkazují na stejném paměťovém prostoru. Když toto provedete, budete muset synchronizovat vícevláknový přístup. Hlavní výhodou používání `array_view` třída je, že data se přesunou pouze v případě potřeby.

### <a name="comparison-of-array-and-arrayview"></a>Porovnání třídy array a array_view

Následující tabulka shrnuje podobnosti a rozdíly mezi `array` a `array_view` třídy.

|Popis|array – třída|array_view – třída|
|-----------------|-----------------|-----------------------|
|Pokud je určen počet rozměrů|V době kompilace.|V době kompilace.|
|Kdy je stanoven rozsah|V době běhu.|V době běhu.|
|Obrazec|Obdélníkový.|Obdélníkový.|
|Úložiště dat|Je datový kontejner.|Je obálka dat.|
|Kopírovat|Explicitní a hluboká kopie při definici.|Implicitní kopie při přístupu funkce jádra.|
|Načítání dat|Kopírování dat pole zpět do objektu ve vlákně procesoru.|Pomocí přímého přístupu `array_view` objektu nebo pomocí volání metody [array_view::synchronize – metoda](reference/array-view-class.md#synchronize) nadále přístup k datům v původním kontejneru.|

### <a name="shared-memory-with-array-and-arrayview"></a>Sdílená paměť s objekty array a array_view

Sdílená paměť je paměť, která je přístupná pomocí procesoru a akcelerátoru. Využití sdílené paměti eliminuje nebo významně snižuje režijní náklady na kopírování dat mezi CPU a akcelerátorem. I když je paměť sdílená, se nedá přistupovat souběžně CPU a akcelerátorem a tím proto způsobí nedefinované chování.

`array` objekty lze použít k určení velice přesně kontrolovat využití sdílené paměti, pokud přidružený akcelerátor podporuje. Určuje, zda akcelerátor podporuje sdílenou paměť je určeno akcelerátoru [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) vlastnost, která vrací **true** při je podporována sdílená paměť. Pokud je podporována sdílená paměť, výchozí [access_type – výčet](reference/concurrency-namespace-enums-amp.md#access_type) paměti je určeno přidělení v akcelerátoru `default_cpu_access_type` vlastnost. Ve výchozím nastavení `array` a `array_view` objekty trvají na stejném `access_type` jako primárně spojený `accelerator`.

Tím, že nastavíte [Array::cpu_access_type data – datový člen](reference/array-class.md#cpu_access_type) vlastnost `array` explicitně, které můžete procvičit jemné doladění řízení nad tím, jak sdílené paměti se používají, aby mohli optimalizovat aplikace pro výkon hardwaru vlastnosti závislosti na vzorech přístupu paměti jádra jeho výpočtu těží. `array_view` Odráží stejné `cpu_access_type` jako `array` , který je spojen s; nebo, pokud objekt array_view konstruován beze zdroje dat, jeho `access_type` odráží prostředí, které nejprve vyvolá přidělení úložiště. To znamená, pokud je nejprve otevřen hostitelem (CPU), pak se chová jako by byl vytvořen ze zdrojů dat procesoru a sdílených složek `access_type` z `accelerator_view` spojeného při vzniku; nicméně, pokud je první přistupuje `accelerator_view`, pak se chová jako by šlo vytváří přes `array` vytvořeném u tohoto `accelerator_view` a sdílených složek `array`společnosti `access_type`.

Následující příklad kódu ukazuje, jak určit, zda výchozí akcelerátor podporuje sdílenou paměť a potom vytvoří několik polí, která mají různou konfiguraci cpu_access_type.

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

## <a name="executing-code-over-data-parallelforeach"></a>Provádění kódu nad daty: parallel_for_each

[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) funkce definuje kód, který chcete spustit na akcelerátoru nad daty v `array` nebo `array_view` objektu. Vezměte v úvahu následující kód z úvodu tohoto tématu.

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

`parallel_for_each` Metoda přebírá dva argumenty, výpočetní doménu a výraz lambda.

*Výpočetní domény* je `extent` objektu nebo `tiled_extent` objekt, který definuje sadu vláken pro vytvoření pro paralelní zpracování. Pro každý prvek ve výpočetní doméně je generováno jedno vlákno. V takovém případě `extent` objekt je jednorozměrný a má pět prvků. Proto je spuštěno pět vláken.

*Výraz lambda* definuje kód, který chcete spustit v každém vláknu. Klauzule zachycení `[=]`, určuje, že hlavní část výrazu lambda přistupuje všem zaznamenaným proměnným podle hodnoty, které jsou v tomto případě `a`, `b`, a `sum`. V tomto příkladu vytváří seznam parametrů jednorozměrnou `index` proměnnou s názvem `idx`. Hodnota `idx[0]` je 0 v prvním vlákně a zvýší o 1 v každém následném vlákně. `restrict(amp)` Označuje, že je použita pouze podmnožina jazyka C++, kterou může knihovna C++ AMP urychlit.  Omezení ve funkcích, které obsahují modifikátor restrict, jsou popsány v [omezení (C++ AMP)](../../cpp/restrict-cpp-amp.md). Další informace najdete v tématu, [Lambda Expression Syntax](../../cpp/lambda-expression-syntax.md).

Výraz lambda může obsahovat kód pro spuštění nebo může volat samostatnou funkci jádra. Funkce jádra musí zahrnovat `restrict(amp)` modifikátor. Následující příklad je ekvivalentní předchozí příklad, ale volá samostatnou funkci jádra.

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

## <a name="accelerating-code-tiles-and-barriers"></a>Urychlování kódu: Dlaždice a překážky

Další zrychlení lze získat pomocí rozložení. Dělení do bloků rozděluje vlákna do rovnoměrných obdélníkových podmnožin nebo *dlaždice*. Můžete určit velikost odpovídající dlaždice na základě sady dat a algoritmu, který píšete. Pro každé vlákno, máte přístup k *globální* umístění datového prvku, relativnímu k celému `array` nebo `array_view` a přístup k *místní* umístění, relativnímu k dlaždici. Používání hodnoty místního indexu zjednodušuje kód, protože není nutné napsat kód pro převod hodnot indexu z globálních na místní. Chcete-li použít dělení do bloků, zavolejte [Extent::Tile – metoda](reference/extent-class.md#tile) ve výpočetní doméně v `parallel_for_each` metoda a použití [tiled_index](../../parallel/amp/reference/tiled-index-class.md) objektu ve výrazu lambda.

V typických aplikacích prvky v dlaždici nějakým způsobem související a kód má přístup k a sledovat hodnoty napříč dlaždicí. Použití [tile_static – klíčové slovo](../../cpp/tile-static-keyword.md) – klíčové slovo a [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait) jak toho dosáhnout. Proměnná, která má **tile_static** – klíčové slovo má rozsah přes celou dlaždici a instance proměnné je vytvořena pro každou dlaždici. Je třeba ošetřit synchronizaci přístupu vláken dlaždic k proměnné. [Tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait) zastaví provádění aktuálního vlákna, dokud všechna vlákna v dlaždici nedosáhnou volání `tile_barrier::wait`. Takto lze nashromáždit hodnoty napříč dlaždicí pomocí **tile_static** proměnné. Poté mohou být dokončeny všechny výpočty, které vyžadují přístup ke všem hodnotám.

Následující diagram představuje dvojrozměrné pole dat vzorkování, která jsou uspořádána v dlaždicích.

![Index hodnoty v dlaždic](../../parallel/amp/media/camptiledgridexample.png "Index hodnoty v dlaždic")

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

C++ AMP obsahuje dvě matematické knihovny. Knihovna s dvojitou přesností v [Concurrency::precise_math Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md) poskytuje podporu pro funkce s dvojitou přesností. Také poskytuje podporu pro funkce s jednoduchou přesností, i když je nutné použít podporu dvojité přesnosti na hardwaru. Odpovídá [dle specifikace C99 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887). Akcelerátor musí podporovat plnou dvojitou přesnost. Můžete určit, zda ji provede pomocí kontroly hodnoty [Accelerator::supports_double_precision – datový člen](reference/accelerator-class.md#supports_double_precision). Rychlé matematické knihovny v [Concurrency::fast_math Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md), obsahuje jinou sadu matematických funkcí. Tyto funkce, které podporují pouze `float` operandy, prováděny rychleji, ale nejsou tak přesné jako ty v knihovně matematiku s dvojitou přesností. Funkce jsou obsaženy v \<amp_math.h > hlavičkový soubor a všechny jsou deklarovány pomocí `restrict(amp)`. Funkce \<cmath > soubor hlaviček jsou importovány do obou `fast_math` a `precise_math` obory názvů. **Omezit** – klíčové slovo se používá pro rozlišení \<cmath > verze a verze C++ AMP. Následující kód vypočítá logaritmus o základu 10, pomocí rychlé metody pro každou hodnotu, která je ve výpočetní doméně.

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

## <a name="graphics-library"></a>Grafické knihovny

C++ AMP obsahuje grafickou knihovnu, která je navržena pro urychlené programování grafiky. Tato knihovna se používá jenom na zařízeních, která podporují nativní grafické funkce. Metody jsou v [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md) a jsou obsaženy v \<amp_graphics.h > soubor hlaviček. Klíčové součásti grafické knihovny jsou:

- [Texture – třída](../../parallel/amp/reference/texture-class.md): Tuto třídu textur lze použít pro tvorbu textur z paměti nebo ze souboru. Textury se podobají polím, protože obsahují data a připomínají kontejnery ve standardní knihovně jazyka C++ s ohledem na přiřazení a konstrukci kopie. Další informace najdete v tématu [kontejnery standardní knihovny C++](../../standard-library/stl-containers.md). Parametry šablony `texture` třídy jsou typ prvku a počet rozměrů. Počet rozměrů může být 1, 2 nebo 3. Typ prvku může být jeden z typů krátkých vektorů, popsaných dále v tomto článku.

- [writeonly_texture_view – třída](../../parallel/amp/reference/writeonly-texture-view-class.md): Poskytuje přístup jen pro zápis pro všechny textury.

- Knihovna krátkých vektorů: Definuje sadu typů krátkých vektorů o délce 2, 3 a 4, které jsou založeny na **int**, `uint`, **float**, **double**, [norm](../../parallel/amp/reference/norm-class.md), nebo [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Aplikace Universal Windows Platform (UWP)

Stejně jako ostatní knihovny jazyka můžete použít C++ AMP v aplikacích pro UPW. Tyto články popisují, jak zahrnout kód jazyka C++ AMP v aplikacích, která je vytvořena pomocí C++, C#, Visual Basic nebo JavaScript:

- [Používání modelu C++ AMP v aplikacích pro UPW](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Návod: Vytvoření základní komponenty prostředí Windows Runtime v jazyce C++ a volání komponenty z jazyka JavaScript](http://go.microsoft.com/fwlink/p/?linkid=249077)

- [Optimalizátor cest, app Store okno v jazyce JavaScript a C++ map Bing](http://go.microsoft.com/fwlink/p/?linkid=249078)

- [Jak používat c ++ AMP z C# s použitím prostředí Windows Runtime](http://go.microsoft.com/fwlink/p/?linkid=249080)

- [Jak používat c ++ AMP z C#](http://go.microsoft.com/fwlink/p/?linkid=249081)

- [Volání nativních funkcí ze spravovaného kódu](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP a vizualizér souběžnosti

Vizualizátor souběžnosti zahrnuje podporu pro analýzu výkonu kódu jazyka C++ AMP. Tyto články popisují tyto funkce:

- [Graf aktivity GPU](/visualstudio/profiling/gpu-activity-graph)

- [Aktivita GPU (stránkování)](/visualstudio/profiling/gpu-activity-paging)

- [Aktivita GPU (tento proces)](/visualstudio/profiling/gpu-activity-this-process)

- [Aktivita GPU (jiné procesy)](/visualstudio/profiling/gpu-activity-other-processes)

- [Kanály (Zobrazení vláken)](/visualstudio/profiling/channels-threads-view)

- [Analýza kódu C++ AMP pomocí Vizualizéru souběžnosti](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>Doporučení k výkonu

Operace modulo a dělení celých čísel bez znaménka mají výrazně lepší výkon než operace modulo a dělení celých čísel se znaménkem. Doporučujeme používat celá čísla bez znaménka Pokud je to možné.

## <a name="see-also"></a>Viz také:

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe výrazů lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Paralelní programování v blogu nativního kódu](http://go.microsoft.com/fwlink/p/?linkid=238472)
