---
title: Používání bloků
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: 6c935134e033d12fc140c8d377ef59d0b47265fc
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518254"
---
# <a name="using-tiles"></a>Používání bloků

K maximalizaci akcelerace aplikace můžete použít dlaždici. Dělení rozdělí vlákna na stejné pravoúhlé podmnožiny nebo *dlaždice*. Použijete-li odpovídající velikost a dlaždicový algoritmus, můžete získat ještě více zrychlení z kódu C++ amp. Základní komponenty dlaždic:

- proměnné `tile_static`. Hlavní výhodou dělení na dlaždice je zvýšení výkonu z `tile_static` přístupu. Přístup k datům v `tile_static` paměti může být výrazně rychlejší než přístup k datům v globálním prostoru (`array` nebo `array_view` objektů). Instance `tile_static` proměnné je vytvořena pro každou dlaždici a všechna vlákna v dlaždici mají přístup k proměnné. V typických algoritmech, které jsou v typickém režimu, se data zkopírují do `tile_static` paměti jednou z globální paměti a pak se v `tile_static` paměti několikrát přistupovalo.

- [tile_barrier:: wait – metoda](reference/tile-barrier-class.md#wait) Volání `tile_barrier::wait` pozastaví provádění aktuálního vlákna, dokud všechna vlákna ve stejné dlaždici dosáhnou volání `tile_barrier::wait`. Pořadí, v jakém se vlákna budou spouštět, nemůžete zaručit, že se za voláním `tile_barrier::wait` nespustí žádná vlákna na dlaždici, dokud všechna vlákna nedosáhnou volání. To znamená, že pomocí metody `tile_barrier::wait` můžete provádět úlohy na dlaždici, a ne na bázi vláken. Typický algoritmus dláždění má kód pro inicializaci `tile_static` paměti pro celou dlaždici následovanou voláním `tile_barrer::wait`. Kód, který následuje `tile_barrier::wait` obsahuje výpočty, které vyžadují přístup ke všem hodnotám `tile_static`.

- Místní a globální indexování. Máte přístup k indexu vlákna relativně k celému `array_view` nebo `array`mu objektu a indexu relativně k dlaždici. Použití místního indexu může usnadnit čtení a ladění kódu. Obvykle používáte místní indexování pro přístup k proměnným `tile_static` a globální indexování pro přístup k proměnným `array` a `array_view`.

- Třída [tiled_extent](../../parallel/amp/reference/tiled-extent-class.md) a [tiled_index](../../parallel/amp/reference/tiled-index-class.md). Místo objektu `extent` ve volání `parallel_for_each` se použije objekt `tiled_extent`. Místo objektu `index` ve volání `parallel_for_each` se použije objekt `tiled_index`.

Aby bylo možné využít dlaždici, musí váš algoritmus rozdělit výpočetní doménu na dlaždice a pak zkopírovat data dlaždice do `tile_static` proměnných pro rychlejší přístup.

## <a name="example-of-global-tile-and-local-indices"></a>Příklad globálních, dlaždicových a místních indexů

Následující diagram představuje matrici velikosti 8x9 dat, která je uspořádaná na dlaždicích 2x3.

![8&#45;–&#45;9 matice dělená na&#45;2&#45;o 3 dlaždice](../../parallel/amp/media/usingtilesmatrix.png "8&#45;–&#45;9 matice dělená na&#45;2&#45;o 3 dlaždice")

Následující příklad zobrazuje globální, dlaždici a místní indexy této dlaždicové matice. Objekt `array_view` je vytvořen pomocí prvků typu `Description`. `Description` obsahuje globální, dlaždici a místní indexy prvku v matici. Kód v volání `parallel_for_each` nastaví hodnoty globálních, dlaždicových a místních indexů každého prvku. Výstup zobrazí hodnoty ve strukturách `Description`.

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

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

Hlavní práce v příkladu je v definici objektu `array_view` a volání `parallel_for_each`.

1. Vektor `Description` struktur je zkopírován do objektu velikosti 8x9 `array_view`.

2. Metoda `parallel_for_each` je volána s objektem `tiled_extent` jako výpočetní doménou. Objekt `tiled_extent` je vytvořen voláním metody `extent::tile()` proměnné `descriptions`. Parametry typu volání `extent::tile()`, `<2,3>`, určují, že jsou vytvořeny dlaždice 2x3. Proto matice velikosti 8x9 je vedle 12 dlaždic, čtyři řádky a tři sloupce.

3. Metoda `parallel_for_each` je volána jako index pomocí objektu `tiled_index<2,3>` (`t_idx`). Parametry typu indexu (`t_idx`) musí odpovídat parametrům typu výpočetní domény (`descriptions.extent.tile< 2, 3>()`).

4. Po spuštění každého vlákna index `t_idx` vrátí informace o tom, která dlaždice je ve vlákně (vlastnost`tiled_index::tile`) a umístění vlákna v dlaždici (`tiled_index::local` vlastnost).

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>Synchronizace dlaždic – tile_static a tile_barrier:: wait

Předchozí příklad znázorňuje rozložení a indexy dlaždice, ale není samo o sobě velmi užitečný.  Dlaždice se hodí, když jsou dlaždice integrální pro algoritmus a zneužije proměnné `tile_static`. Vzhledem k tomu, že všechna vlákna v dlaždici mají přístup k proměnným `tile_static`, jsou pro synchronizaci přístupu k proměnným `tile_static` použita volání `tile_barrier::wait`. I když všechna vlákna v dlaždici mají přístup k proměnným `tile_static`, neexistuje žádné zaručené pořadí spouštění vláken na dlaždici. Následující příklad ukazuje, jak použít proměnné `tile_static` a metodu `tile_barrier::wait` k výpočtu průměrné hodnoty každé dlaždice. Tady jsou klíče pro porozumění příkladu:

1. RawData je uložený v matrici 8x8.

2. Velikost dlaždice je 2x2. Tím se vytvoří 4x4 mřížka dlaždic a průměry se dají uložit do matice 4x4 pomocí objektu `array`. Ve funkci s omezením AMP můžete zachytit jenom omezený počet typů, které můžete zachytit odkazem. Třída `array` je jednou z nich.

3. Velikost matice a velikost vzorku jsou definovány pomocí příkazů `#define`, protože parametry typu pro `array`, `array_view`, `extent`a `tiled_index` musí být konstantní hodnoty. Můžete také použít deklarace `const int static`. Jako další výhodou je triviální Změna velikosti vzorku pro výpočet průměru v 4x4 dlaždicích.

4. Pro každou dlaždici je deklarováno pole `tile_static` 2x2 hodnot typu float. I když je deklarace v cestě kódu pro každé vlákno, je pro každou dlaždici v matici vytvořeno pouze jedno pole.

5. K dispozici je řádek kódu ke zkopírování hodnot v každé dlaždici do pole `tile_static`. Pro každé vlákno, po zkopírování hodnoty do pole, spuštění vlákna zastaví v důsledku volání `tile_barrier::wait`.

6. V případě, že všechna vlákna v dlaždici dosáhla bariéry, lze vypočítat průměr. Vzhledem k tomu, že se kód spustí pro každé vlákno, je k dispozici příkaz `if`, který vypočítá pouze průměr jednoho vlákna. Průměr je uložený v proměnné averages. Bariéra je v podstatě konstrukce, která řídí výpočty podle dlaždic, podobně, jako byste mohli použít smyčku `for`.

7. Data v proměnné `averages`, protože se jedná o `array` objekt, musí být zkopírována zpět na hostitele. V tomto příkladu se používá operátor převodu vektoru.

8. V úplném příkladu můžete změnit SAMPLESIZE na 4 a kód se spustí správně bez jakýchkoli dalších změn.

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

Může se zvážit vytvoření `tile_static` proměnné s názvem `total` a přírůstku této proměnné pro každé vlákno, jako je:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Prvním problémem s tímto přístupem je, že proměnné `tile_static` nemohou mít Inicializátory. Druhý problém je, že při přiřazování `total`existuje konflikt časování, protože všechna vlákna v dlaždici mají přístup k proměnné bez konkrétního pořadí. Mohli byste programovat algoritmus, který umožňuje přístup k celkovému počtu všech bariér v jednom vlákně, jak je uvedeno dále. Toto řešení však není rozšiřitelné.

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

## <a name="memory-fences"></a>Ploty paměti

Existují dva typy přístupů do paměti, které je třeba synchronizovat – globální přístup k paměti a přístup k `tile_static` paměti. Objekt `concurrency::array` přiděluje pouze globální paměť. `concurrency::array_view` může odkazovat na globální paměť, `tile_static` paměti nebo obojí v závislosti na tom, jak byla vytvořena.  Existují dva druhy paměti, které je třeba synchronizovat:

- globální paměť

- `tile_static`

*Velikost* paměti zajišťuje, aby přístup k paměti byl k dispozici ostatním vláknům na dlaždici vlákna a aby byly přístupy k paměti spouštěny podle pořadí programu. Pro zajištění toho, kompilátory a procesory nemění pořadí čtení a zápisu napříč plotem. V C++ amp je velikost paměti vytvořena voláním jedné z těchto metod:

- [tile_barrier:: wait – metoda](reference/tile-barrier-class.md#wait): vytvoří plot kolem globální i `tile_static` paměti.

- [tile_barrier:: Wait_with_all_memory_fence metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): vytvoří ohrazení kolem globální i `tile_static`ové paměti.

- [tile_barrier:: Wait_with_global_memory_fence metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): vytvoří plot pouze kolem globální paměti.

- [tile_barrier:: Wait_with_tile_static_memory_fence metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): vytvoří plot pouze kolem `tile_static` paměti.

Volání konkrétní ochranné části, kterou požadujete, může zlepšit výkon aplikace. Typ bariéry má vliv na to, jak kompilátor a příkazy pro změnu pořadí hardwaru. Pokud například použijete globální ochrannou paměť, vztahuje se pouze na globální přístup k paměti, kompilátor a hardware mohou změnit pořadí čtení a zápisu pro `tile_static` proměnné na obou stranách plotu.

V následujícím příkladu bariéra synchronizuje zápisy do `tileValues`, `tile_static` proměnnou. V tomto příkladu je místo `tile_barrier::wait`volána `tile_barrier::wait_with_tile_static_memory_fence`.

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
