---
title: 'Návod: Násobení matic'
ms.date: 11/19/2018
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: ae86ff5a111348404616c8bb4fecd3bf22afc90c
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176156"
---
# <a name="walkthrough-matrix-multiplication"></a>Návod: Násobení matic

Tento podrobný návod ukazuje, jak použít C++ AMP zrychlí provádění násobení matic. Jsou uvedeny dva algoritmy, jeden bez dlaždic a druhý s dělení do bloků.

## <a name="prerequisites"></a>Požadavky

Než začnete:

- Čtení [přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md).

- Čtení [pomocí dlaždice](../../parallel/amp/using-tiles.md).

- Ujistěte se, že tento Windows 7, Windows 8, Windows Server 2008 R2 nebo Windows Server 2012 je nainstalovaný ve vašem počítači.

### <a name="to-create-the-project"></a>Vytvoření projektu

1. V panelu nabídek v sadě Visual Studio zvolte **souboru** > **nový** > **projektu**.

1. V části **nainstalováno** v podokně šablony vyberte **Visual C++**.

1. Vyberte **prázdný projekt**, zadejte *MatrixMultiply* v **název** pole a klikněte na tlačítko **OK** tlačítko.

1. Zvolte **Další** tlačítko.

1. V **Průzkumníka řešení**, otevřete místní nabídku pro **zdrojové soubory**a klikněte na tlačítko **přidat** > **nová položka**.

1. V **přidat novou položku** dialogu **soubor C++ (.cpp)**, zadejte *MatrixMultiply.cpp* v **název** pole a klikněte na tlačítko  **Přidat** tlačítko.

## <a name="multiplication-without-tiling"></a>Násobení bez dělení do bloků

V této části vezměte v úvahu Násobení dvou matice A a B, které jsou definovány takto:

![3&#45;podle&#45;2 matice](../../parallel/amp/media/campmatrixanontiled.png "3&#45;podle&#45;2 matice")

![2&#45;podle&#45;3 matice B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;podle&#45;3 matice B")

Matice 3 2 je A a B je 2 x 3 matice. Součin hodnot a b je následující matice 3 číslem 3. Produkt se počítá vynásobením řádků A sloupců B prvek po prvku.

![3&#45;podle&#45;3 produktu matice](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;podle&#45;3 produktu matice")

### <a name="to-multiply-without-using-c-amp"></a>Pokud chcete vynásobit bez používání modelu C++ AMP

1. Otevřete MatrixMultiply.cpp a pomocí následujícího kódu nahraďte stávající kód.

```cpp
#include <iostream>

void MultiplyWithOutAMP() {
    int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};
    int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};
    int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};

    for (int row = 0; row < 3; row++) {
        for (int col = 0; col < 3; col++) {
            // Multiply the row of A by the column of B to get the row, column of product.
            for (int inner = 0; inner < 2; inner++) {
                product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];
            }
            std::cout << product[row][col] << "  ";
        }
        std::cout << "\n";
    }
}

void main() {
    MultiplyWithOutAMP();
    getchar();
}
```

   Algoritmus je jednoduchá implementace definice násobení matic. Zkrátit čas výpočtu nepoužívá žádné algoritmy paralelní nebo vláken.

1. V panelu nabídky zvolte **souboru** > **Uložit vše**.

1. Zvolte **F5** klávesovou zkratku pro spuštění ladění a ověřte, zda výstup je správná.

1. Zvolte **Enter** ukončíte aplikaci.

### <a name="to-multiply-by-using-c-amp"></a>Pro násobení pomocí jazyka C++ AMP

1. V MatrixMultiply.cpp, přidejte následující kód před `main` metody.

```cpp
void MultiplyWithAMP() {
    int aMatrix[] = { 1, 4, 2, 5, 3, 6 };
    int bMatrix[] = { 7, 8, 9, 10, 11, 12 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    array_view<int, 2> a(3, 2, aMatrix);

    array_view<int, 2> b(2, 3, bMatrix);

    array_view<int, 2> product(3, 3, productMatrix);

    parallel_for_each(product.extent,
        [=] (index<2> idx) restrict(amp) {
            int row = idx[0];
            int col = idx[1];
            for (int inner = 0; inner <2; inner++) {
                product[idx] += a(row, inner)* b(inner, col);
            }
        });

    product.synchronize();

    for (int row = 0; row <3; row++) {
        for (int col = 0; col <3; col++) {
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

   Kód AMP se podobá kódu bez AMP. Volání `parallel_for_each` spouští jedno vlákno pro každý prvek v `product.extent`a nahradí `for` smyčky pro řádků a sloupců. Hodnota buňky v řádku a sloupce je k dispozici v `idx`. Dostanete prvky `array_view` s použitím buď `[]` operátor a indexovaná proměnná, nebo `()` řádků a sloupců proměnných a operátor. Tento příklad ukazuje obě metody. `array_view::synchronize` Metoda zkopíruje hodnoty `product` proměnné zpět `productMatrix` proměnné.

1. Přidejte následující `include` a `using` příkazů v horní části MatrixMultiply.cpp.

```cpp
#include <amp.h>
using namespace concurrency;
```

1. Upravit `main` metoda se má volat `MultiplyWithAMP` metody.

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    getchar();
}
```

1. Zvolte **Ctrl**+**F5** klávesovou zkratku pro spuštění ladění a ověřte, zda výstup je správná.

1. Zvolte **MEZERNÍK** ukončíte aplikaci.

## <a name="multiplication-with-tiling"></a>Násobení s dělení do bloků

Dělení do bloků je technika, ve kterém můžete dělit data do stejné velikosti podmnožiny, které jsou známé jako dlaždice. Tři věci změnit při použití dělení do bloků.

- Můžete vytvořit `tile_static` proměnné. Přístup k datům v `tile_static` prostor může být mnohem rychlejší než přístup k datům v globálním prostoru. Instance `tile_static` proměnné je vytvořena pro každou dlaždici a všechna vlákna v dlaždici mají k této proměnné přístup. Hlavní výhodou dělení do bloků je výkonový zisk plynoucí z důvodu `tile_static` přístup.

- Můžete volat [tile_barrier::wait](reference/tile-barrier-class.md#wait) metoda zastavení všech vláken v jednu dlaždici na určený řádek kódu. Nelze zaručit pořadí, ve kterém budou vlákna spuštěna, pouze že všechna vlákna v dlaždici jeden zastaví volání `tile_barrier::wait` před jejich pokračování v provádění.

- Máte přístup k indexu vlákna relativnímu k celým `array_view` objektu a indexu relativnímu k dlaždici. Pomocí místního indexu lze usnadnit kódu ke čtení a ladění.

Pro využití dělení do bloku v násobení matic musí algoritmus rozdělit matici na dlaždice a potom zkopírujte data dlaždice do `tile_static` proměnné pro rychlejší přístup. V tomto příkladu je rozdělená matici na submatrices stejnou velikost. Produkt je tak, submatrices nalezen. Jsou dva matice a jejich produktů v tomto příkladu:

![4&#45;podle&#45;matice 4](../../parallel/amp/media/campmatrixatiled.png "4&#45;podle&#45;matice 4")

![4&#45;podle&#45;4 matice B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;podle&#45;4 matice B")

![4&#45;podle&#45;matice 4 produktu](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;podle&#45;matice 4 produktu")

Matricí jsou rozdělené do matice čtyři 2 x 2, které jsou definovány takto:

![4&#45;podle&#45;4 matice A rozdělené do 2&#45;podle&#45;2 sub&#45;matice](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;podle&#45;4 matice A rozdělené do 2&#45;podle&#45;2 sub&#45;matice")

![4&#45;podle&#45;4 matice B rozdělená na 2&#45;podle&#45;2 sub&#45;matice](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;podle&#45;4 matice B rozdělená na 2&#45;podle&#45;2 sub&#45;matice")

Produkt A a B teď může zapisovat a vypočítávány následujícím způsobem:

![4&#45;podle&#45;4 matice A B rozdělená na 2&#45;podle&#45;2 sub&#45;matice](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;podle&#45;4 matice A B rozdělená na 2&#45;podle&#45;2 sub&#45;matice")

Protože matice `a` prostřednictvím `h` jsou maticích 2 x 2, všechny produkty a součtů z nich jsou také maticích 2 x 2. Také vyplývá, že produkt A a B je matice 4 x 4, podle očekávání. Můžete rychle zjistit, že algoritmus, vypočítá hodnotu elementu v prvním řádku, první sloupec v rámci produktu. V příkladu, bylo by hodnota elementu v prvním řádku a první sloupec `ae + bg`. Stačí vypočítat prvního sloupce, první řádek `ae` a `bg` ke každému termínu. Tuto hodnotu pro `ae` je `(1 * 1) + (2 * 5) = 11`. Hodnota pro `bg` je `(3 * 1) + (4 * 5) = 23`. Konečná hodnota je `11 + 23 = 34`, která je správná.

K implementaci tento algoritmus, kód:

- Používá `tiled_extent` místo objektu `extent` objekt `parallel_for_each` volání.

- Používá `tiled_index` místo objektu `index` objekt `parallel_for_each` volání.

- Vytvoří `tile_static` proměnné pro uložení submatrices.

- Používá `tile_barrier::wait` metoda vláken pro výpočet produkty submatrices zastavit.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Pro násobení pomocí AMP a dělení do bloků

1. V MatrixMultiply.cpp, přidejte následující kód před `main` metody.

```cpp
void MultiplyWithTiling() {
    // The tile size is 2.
    static const int TS = 2;

    // The raw data.
    int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    // Create the array_view objects.
    array_view<int, 2> a(4, 4, aMatrix);
    array_view<int, 2> b(4, 4, bMatrix);
    array_view<int, 2> product(4, 4, productMatrix);

    // Call parallel_for_each by using 2x2 tiles.
    parallel_for_each(product.extent.tile<TS, TS>(),
        [=] (tiled_index<TS, TS> t_idx) restrict(amp)
        {
            // Get the location of the thread relative to the tile (row, col)
            // and the entire array_view (rowGlobal, colGlobal).
            int row = t_idx.local[0];
            int col = t_idx.local[1];
            int rowGlobal = t_idx.global[0];
            int colGlobal = t_idx.global[1];
            int sum = 0;

            // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.
            // For the first tile and the first loop, it copies a into locA and e into locB.
            // For the first tile and the second loop, it copies b into locA and g into locB.
            for (int i = 0; i < 4; i += TS) {
                tile_static int locA[TS][TS];
                tile_static int locB[TS][TS];
                locA[row][col] = a(rowGlobal, col + i);
                locB[row][col] = b(row + i, colGlobal);
                // The threads in the tile all wait here until locA and locB are filled.
                t_idx.barrier.wait();

                // Return the product for the thread. The sum is retained across
                // both iterations of the loop, in effect adding the two products
                // together, for example, a*e.
                for (int k = 0; k < TS; k++) {
                    sum += locA[row][k] * locB[k][col];
                }

                // All threads must wait until the sums are calculated. If any threads
                // moved ahead, the values in locA and locB would change.
                t_idx.barrier.wait();
                // Now go on to the next iteration of the loop.
            }

            // After both iterations of the loop, copy the sum to the product variable by using the global location.
            product[t_idx.global] = sum;
        });

    // Copy the contents of product back to the productMatrix variable.
    product.synchronize();

    for (int row = 0; row <4; row++) {
        for (int col = 0; col <4; col++) {
            // The results are available from both the product and productMatrix variables.
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

    This example is significantly different than the example without tiling. The code uses these conceptual steps:

    1. Zkopírujte prvky dlaždici [0; 0] `a` do `locA`. Zkopírujte prvky dlaždici [0; 0] `b` do `locB`. Všimněte si, že `product` rozložen formou dlaždic, ne `a` a `b`. Proto použít globální indexy pro přístup k `a, b`, a `product`. Volání `tile_barrier::wait` je velmi důležité. Zastaví všechna vlákna v dlaždici do obou `locA` a `locB` jsou vyplněny.

    2. Vynásobit `locA` a `locB` a uložte výsledky do `product`.

    3. Zkopírujte prvky dlaždici [0,1] `a` do `locA`. Zkopírujte prvky dlaždici [1,0] `b` do `locB`.

    4. Vynásobit `locA` a `locB` a přidat je do výsledky, které se již nacházejí v `product`.

    5. Násobení dlaždice [0; 0] je dokončena.

    6. Opakujte pro další čtyři dlaždice. Neexistuje žádné indexování speciálně pro dlaždice a vlákna můžete spustit v libovolném pořadí. Jak spustí každé vlákno `tile_static` proměnné se vytvářejí odpovídajícím způsobem pro každou dlaždici a volání `tile_barrier::wait` řídí tok programu.

    7. Při prohlížení algoritmus úzce, Všimněte si, že každý submatrix je načten do `tile_static` paměti dvakrát. Přenos dat trvat dobu. Nicméně jakmile jsou data v `tile_static` paměti, je mnohem rychlejší přístup k datům. Protože výpočet produkty vyžaduje opakované přístup k hodnotám v submatrices, není zvýšení celkového výkonu. Pro každý algoritmus experimentování ve službě je potřeba najít optimálního algoritmu a velikost dlaždice.

         V příkladech bez AMP a mimo dlaždicí každý prvek A a B přistupuje čtyřikrát z globální paměti k výpočtu produktu. V příkladu dlaždice každý prvek přistupuje dvakrát z globální paměti a čtyřikrát `tile_static` paměti. To není důležité výkonnější. 1 024 x 1 024 šlo A a B matice a velikost dlaždice se 16, by bylo zvýšení výkonu. V takovém případě každý prvek má být zkopírováno do `tile_static` paměti pouze 16 a k němu přistupovat z `tile_static` paměti 1024 časy.

2. Změnit hlavní metoda k volání `MultiplyWithTiling` způsob, jak je znázorněno.

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    MultiplyWithTiling();
    getchar();
}
```

3. Zvolte **Ctrl**+**F5** klávesovou zkratku pro spuštění ladění a ověřte, zda výstup je správná.

4. Zvolte **místo** panelu ukončíte aplikaci.

## <a name="see-also"></a>Viz také

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)