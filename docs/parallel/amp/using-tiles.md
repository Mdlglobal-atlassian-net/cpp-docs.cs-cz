---
title: Používání bloků
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: ede62c80a83b5f5fc1d691bf52dde67140e68246
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176091"
---
# <a name="using-tiles"></a>Používání bloků

Maximalizace rychlosti aplikace můžete použít dělení do bloků. Dělení do bloků rozděluje vlákna do rovnoměrných obdélníkových podmnožin nebo *dlaždice*. Pokud používáte vhodné velikosti bloku a algoritmu využívajícím bloky, můžete získat ještě větší zrychlení v kódu C++ AMP. Základní komponenty dělení do bloků jsou:

- `tile_static` proměnné. Hlavní výhodou dělení do bloků je výkonový zisk plynoucí z `tile_static` přístup. Přístup k datům v `tile_static` paměti může být výrazně rychlejší než přístup k datům v globálním prostoru (`array` nebo `array_view` objekty). Instance `tile_static` proměnné je vytvořena pro každou dlaždici a všechna vlákna v dlaždici mají k této proměnné přístup. V typickém algoritmu využívajícím bloky, se data zkopírovala do `tile_static` paměti jednou z globální paměti a pak k nim mnohokrát přistupováno z `tile_static` paměti.

- [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait). Volání `tile_barrier::wait` pozastaví provádění aktuálního vlákna, dokud všechna vlákna ve stejném bloku nedosáhnou volání `tile_barrier::wait`. Nelze zaručit pořadí spuštění vlákna, pouze že žádná vlákna v bloku nebude provádět příkazy po volání `tile_barrier::wait` dokud všechna vlákna nedosáhnout tohoto volání. To znamená, že pomocí `tile_barrier::wait` metodu, můžete provádět úkoly na základě dlaždice dlaždice spíše než vlákno po vlákně. Dělení do bloků typický algoritmus využívající dlaždice má kód `tile_static` paměti pro celou dlaždici následovanou voláním do `tile_barrer::wait`. Kód, který následuje `tile_barrier::wait` obsahuje výpočty, které vyžadují přístup ke všem `tile_static` hodnoty.

- Místní a globální indexování. Máte přístup k indexu vlákna relativnímu k celým `array_view` nebo `array` objektu a indexu relativnímu k dlaždici. Použití místního indexu může usnadnit kódu ke čtení a ladění. Obvykle použijete místní indexování pro přístup k `tile_static` proměnné a globální indexování pro přístup k `array` a `array_view` proměnné.

- [tiled_extent – třída](../../parallel/amp/reference/tiled-extent-class.md) a [tiled_index – třída](../../parallel/amp/reference/tiled-index-class.md). Použijete `tiled_extent` místo objektu `extent` objekt `parallel_for_each` volání. Použijete `tiled_index` místo objektu `index` objekt `parallel_for_each` volání.

Pro využití dělení do bloku musí algoritmus rozdělit výpočetní doménu do bloků a potom zkopírujte data dlaždice do `tile_static` proměnné pro rychlejší přístup.

## <a name="example-of-global-tile-and-local-indices"></a>Příklad globálních, blokových a místní indexy

Následující diagram reprezentuje matici 8 x 9 data, která jsou uspořádána v dlaždicích 2 x 3.

![8&#45;podle&#45;9 matice dělí 2&#45;podle&#45;3 dlaždice](../../parallel/amp/media/usingtilesmatrix.png "8&#45;podle&#45;9 matice dělí 2&#45;podle&#45;3 dlaždice")

Následující příklad ukazuje globální, blokové a místní indexy této blokové matice. `array_view` Za použití prvků typu je vytvořen objekt `Description`. `Description` Udržuje globální, dlaždice a místní indexy prvků matice. Kód ve volání `parallel_for_each` nastaví hodnotu globálního, blokového a místního indexu každého prvku. Výstup zobrazuje hodnoty `Description` struktury.

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

void main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

Hlavní práce ukázky spočívá v definici sady `array_view` objektu a volání `parallel_for_each`.

1. Vektor `Description` struktury je zkopírována do 8 x 9 `array_view` objektu.

2. `parallel_for_each` Metoda je volána `tiled_extent` objektu jako výpočetní doménou. `tiled_extent` Objekt je vytvořen zavoláním `extent::tile()` metodu `descriptions` proměnné. Typové parametry volání `extent::tile()`, `<2,3>`, určete, zda budou vytvořeny bloky velikosti 2 x 3. Proto matice 8 x 9 je rozložen formou dlaždic do 12 bloků, čtyři řádky a tři sloupce.

3. `parallel_for_each` Metoda je volána za použití `tiled_index<2,3>` objektu (`t_idx`) jako index. Typové parametry indexu (`t_idx`) musí odpovídat typovým parametrům výpočetní domény (`descriptions.extent.tile< 2, 3>()`).

4. Při spuštění každého vlákna index `t_idx` vrátí informace o dlaždice vlákno je v (`tiled_index::tile` vlastnost) a umístění vlákna v dlaždici (`tiled_index::local` vlastnost).

## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Synchronizace – tile_static a tile_barrier::wait

Předchozí příklad ilustruje rozložení bloků a indexů, ale není sám o sobě velmi užitečné.  Dělení do bloků se stává užitečným, jsou nedílnou součástí algoritmu a využívají `tile_static` proměnné. Vzhledem k tomu, že všechna vlákna bloku mají přístup k `tile_static` proměnné, volání `tile_barrier::wait` se používají k synchronizaci přístupu k `tile_static` proměnné. Ačkoli všechna vlákna bloku mají přístup k `tile_static` proměnné, není zaručeno pořadí provádění vlákna v dlaždici. Následující příklad ukazuje, jak používat `tile_static` proměnné a `tile_barrier::wait` metodu pro výpočet průměrné hodnoty každého bloku. Zde jsou klíčové údaje pro pochopení tohoto příkladu:

1. Objekt rawData je uložen v matici 8 x 8.

2. Velikost bloku je 2 x 2. Tím se vytvoří dlaždic mřížky 4 x 4 a průměry mohou být uloženy do matice 4 x 4 pomocí `array` objektu. Existuje pouze omezený počet typů, které lze zachytit odkazem ve funkci s omezením AMP. `array` Třída je jeden z nich.

3. Velikost matice a velikost vzorku jsou definovány pomocí `#define` příkazy, protože typové parametry `array`, `array_view`, `extent`, a `tiled_index` musí být konstantní hodnoty. Můžete také použít `const int static` deklarace. Další výhodou je je jednoduché změnit velikost vzorku pro výpočet průměrné dlaždice více než 4 x 4.

4. A `tile_static` 2 x 2 pole hodnot s plovoucí desetinnou čárkou je deklarován pro každou dlaždici. Ačkoli je deklarace v kódové cestě pro každé vlákno, se vytvoří pouze jedno pole pro každý blok v matici.

5. Je jeden řádek kódu a zkopírujte hodnoty v každém bloku do `tile_static` pole. Pro každé vlákno po zkopírování hodnoty do pole je spuštění vlákna pozastaveno kvůli volání `tile_barrier::wait`.

6. Pokud všechna vlákna bloku dosáhnou této bariéry, lze vypočítat průměr. Jelikož se kód spouští pro každé vlákno, je `if` příkaz pouze výpočet průměru v jednom vlákně. Průměr je uložen v proměnné averages. Odbourejte překážky bránící je v podstatě konstrukci, která řídí výpočty po, podobně jako můžete použít `for` smyčky.

7. Data v `averages` proměnné, protože se jedná `array` objektu, musí být zkopírována zpět k hostiteli. Tento příklad používá operátor převodu vektoru.

8. V úplném příkladu lze změnit hodnotu SAMPLESIZE na 4 a kód se provede správně bez jakýchkoliv jiných změn.

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESSIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>Konflikty časování

Může být lákavé vytvořit `tile_static` proměnnou s názvem `total` a zvyšovat ji pro každé vlákno následujícím způsobem:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Prvním problémem tohoto přístupu je, že `tile_static` proměnné nemůžou mít inicializátory. Druhý problém je, že je u přiřazování k časování `total`, protože všechna vlákna v dlaždici mají k této proměnné přístup bez určitého pořadí. Lze naprogramovat algoritmus tak povolit pouze jednomu vláknu přistupovat k hodnotě celkem u každé bariéry, jak je ukázáno dále. Toto řešení však není rozšiřitelné.

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>Ohrazení paměti

Existují dva typy přístupů k paměti, které musí být synchronizovány – přístup ke globální paměti a `tile_static` přístup do paměti. A `concurrency::array` objekt alokuje pouze globální paměť. A `concurrency::array_view` globální paměti, můžete odkazovat na `tile_static` nebo do obou v závislosti na způsobu jeho vytvoření.  Existují dva druhy paměti, která musí být synchronizovány:

- globální paměť

- `tile_static`

A *ohrazení paměti* zajišťuje, že jsou k dispozici pro ostatní vlákna v dlaždici vlákna přístupy k paměti a že paměti jsou provedeny podle pořadí programu. Aby toto bylo zajištěno, kompilátory a procesory nemění pořadí čtení a zápisu napříč ohrazením. V jazyce C++ AMP je ohrazení paměti vytvořen voláním jedné z těchto metod:

- [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait): vytvoří ohrazení kolem i globální a `tile_static` paměti.

- [tile_barrier::wait_with_all_memory_fence – metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): vytvoří ohrazení kolem i globální a `tile_static` paměti.

- [tile_barrier::wait_with_global_memory_fence – metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): vytvoří ohrazení pouze kolem globální paměti.

- [tile_barrier::wait_with_tile_static_memory_fence – metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): vytvoří ohrazení pouze kolem `tile_static` paměti.

Volání konkrétní požadovaného ohrazení může zvýšit výkon vaší aplikace. Typ bariéry ovlivňuje, jak kompilátor a hardware mění pořadí příkazů. Například pokud používáte ohrazení globální paměti, použije přístupy do globální paměti a proto se mohou změnit pořadí kompilátor a hardware čte a zapisuje do `tile_static` proměnné na obou stranách ohrazení.

V následujícím příkladu bariéra synchronizuje zápisy do `tileValues`, `tile_static` proměnné. V tomto příkladu `tile_barrier::wait_with_tile_static_memory_fence` se nazývá místo `tile_barrier::wait`.

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>Viz také:

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static Keyword](../../cpp/tile-static-keyword.md)
