---
title: 'Návod: Násobení matic'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: 341800e258f89db340d206ebe04bc20d4763ad1a
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518488"
---
# <a name="walkthrough-matrix-multiplication"></a>Návod: Násobení matic

V tomto podrobném návodu se dozvíte, jak pomocí C++ amp zrychlit provádění násobení matic. K dispozici jsou dva algoritmy, a to bez dlaždic a jednoho s dlaždicí.

## <a name="prerequisites"></a>Požadavky

Než začnete:

- Přečtěte si [ C++ přehled amp](../../parallel/amp/cpp-amp-overview.md).

- Přečtěte si [použití dlaždic](../../parallel/amp/using-tiles.md).

- Ujistěte se, že používáte minimálně Windows 7 nebo Windows Server 2008 R2.

### <a name="to-create-the-project"></a>Vytvoření projektu

Pokyny pro vytvoření nového projektu se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Ujistěte se, že máte selektor verzí v levém horním rohu nastavený na správnou verzi.

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Vytvoření projektu v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**. 

1. Z filtrovaného seznamu typů projektů zvolte možnost **prázdný projekt** a pak zvolte možnost **Další**. Na další stránce zadejte do pole **název** *MatrixMultiply* a zadejte název projektu a v případě potřeby určete umístění projektu.

   ![Nová aplikace konzoly](../../build/media/mathclient-project-name-2019.png "Nová aplikace konzoly")

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

1. V **Průzkumník řešení**otevřete místní nabídku pro **zdrojové soubory**a zvolte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte  **C++ soubor (. cpp)** , do pole **název** zadejte *MatrixMultiply. cpp* a poté klikněte na tlačítko **Přidat** .

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Vytvoření projektu v aplikaci Visual Studio 2017 nebo 2015

1. Na panelu nabídek v aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**.

1. V části **nainstalováno** v podokně šablony vyberte **možnost C++Visual** .

1. Vyberte **prázdný projekt**, do pole **název** zadejte *MatrixMultiply* a pak klikněte na tlačítko **OK** .

1. Zvolte **Další** tlačítko.

1. V **Průzkumník řešení**otevřete místní nabídku pro **zdrojové soubory**a zvolte možnost **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte  **C++ soubor (. cpp)** , do pole **název** zadejte *MatrixMultiply. cpp* a poté klikněte na tlačítko **Přidat** .

::: moniker-end

## <a name="multiplication-without-tiling"></a>Násobení bez dláždění

V této části zvažte násobení dvou matric, a a B, které jsou definovány takto:

![3&#45;podle&#45;2 matice A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;podle&#45;2 matice A")

![2&#45;podle&#45;3 matice B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;podle&#45;3 matice B")

A je matice 3 – 2 a B je matice 2-po 3. Součin vynásobení hodnotou B je následující matice 3 po 3. Produkt je vypočítán vynásobením řádků A sloupci elementu B elementem.

![matice&#45;3&#45;podle 3 produktu](../../parallel/amp/media/campmatrixproductnontiled.png "matice&#45;3&#45;podle 3 produktu")

### <a name="to-multiply-without-using-c-amp"></a>Vynásobení bez C++ použití amp

1. Otevřete MatrixMultiply. cpp a pomocí následujícího kódu nahraďte stávající kód.

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

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   Algoritmus je jednoduchá implementace definice násobení matice. Nevyužívá žádné paralelní ani zřetězené algoritmy ke snížení doby výpočtu.

1. Na panelu nabídek vyberte možnost **soubor** > **Uložit vše**.

1. Kliknutím na klávesovou zkratku **F5** spusťte ladění a ověřte, zda je výstup správný.

1. Pokud chcete aplikaci ukončit, klikněte na tlačítko **ENTER** .

### <a name="to-multiply-by-using-c-amp"></a>Vynásobení pomocí C++ amp

1. V MatrixMultiply. cpp přidejte následující kód před metodu `main`.

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

   Kód AMP se podobá kódu, který není AMP. Volání `parallel_for_each` spustí jedno vlákno pro každý prvek v `product.extent`a nahradí `for` smyčky pro řádek a sloupec. Hodnota buňky na řádku a ve sloupci je k dispozici v `idx`. K prvkům objektu `array_view` můžete přistupovat pomocí operátoru `[]` a proměnné indexu nebo operátoru `()` a proměnných řádku a sloupce. Příklad ukazuje obě metody. Metoda `array_view::synchronize` zkopíruje hodnoty `product` proměnné zpět do proměnné `productMatrix`.

1. Přidejte následující příkazy `include` a `using` v horní části MatrixMultiply. cpp.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. Upravte metodu `main` pro volání metody `MultiplyWithAMP`.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. Stisknutím klávesové zkratky **Ctrl**+**F5** spusťte ladění a ověřte, zda je výstup správný.

1. Stisknutím **mezerníku** aplikaci ukončete.

## <a name="multiplication-with-tiling"></a>Násobení s dlážděním

Dláždění je technika, ve které můžete rozdělit data na stejné podmnožiny, které jsou označovány jako dlaždice. Při použití dlaždic se mění tři věci.

- Můžete vytvořit `tile_static` proměnných. Přístup k datům v `tile_static`m prostoru může být mnohokrát rychlejší než přístup k datům v globálním prostoru. Instance `tile_static` proměnné je vytvořena pro každou dlaždici a všechna vlákna v dlaždici mají přístup k proměnné. Hlavní výhodou dělení na dlaždice je zvýšení výkonu z důvodu `tile_static`ho přístupu.

- Můžete zavolat metodu [tile_barrier:: wait](reference/tile-barrier-class.md#wait) pro zastavení všech vláken v jedné dlaždici na zadaném řádku kódu. Pořadí, ve kterém budou vlákna spuštěná, nemůžete zaručit, jenom když všechna vlákna v jedné dlaždici skončí při volání `tile_barrier::wait` před pokračováním v provádění.

- Máte přístup k indexu vlákna vzhledem k celému objektu `array_view` a indexu relativně k dlaždici. Pomocí místního indexu můžete usnadnit čtení a ladění kódu.

Aby bylo možné využít výhod dělení do násobení, musí algoritmus rozdělit matici na dlaždice a následně zkopírovat data dlaždice do `tile_static` proměnných pro rychlejší přístup. V tomto příkladu je matice rozdělena do podmatic stejné velikosti. Produkt se najde vynásobením dílčích matric. V tomto příkladu jsou dvě matice a jejich produkt:

![4&#45;–&#45;4 matice A](../../parallel/amp/media/campmatrixatiled.png "4&#45;–&#45;4 matice A")

![4&#45;–&#45;4 matice B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;–&#45;4 matice B")

![4&#45;.&#45;4 matice produktů](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;.&#45;4 matice produktů")

Matice jsou rozdělené do čtyř matic 2x2, které jsou definovány takto:

![4&#45;–&#45;4 matice dělené do 2&#45;podle&#45;2 dílčích&#45;matric](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;–&#45;4 matice dělené do 2&#45;podle&#45;2 dílčích&#45;matric")

![4&#45;–&#45;4 matice B rozdělené do 2&#45;podle&#45;2 dílčích&#45;matric](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;–&#45;4 matice B rozdělené do 2&#45;podle&#45;2 dílčích&#45;matric")

Produkt a a B lze nyní zapsat a vypočítat následujícím způsobem:

![4&#45;o&#45;4 matice A B dělené 2&#45;podle&#45;2 dílčích&#45;matric](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;o&#45;4 matice A B dělené 2&#45;podle&#45;2 dílčích&#45;matric")

Vzhledem k tomu, že matice `a` přes `h` jsou matice 2x2, všechny produkty a jejich součty se také řadí do těchto matric. Sleduje také, že produkt a a B je 4x4 matice, jak je očekáváno. Chcete-li rychle ověřit algoritmus, Vypočítejte hodnotu prvku v prvním řádku, první sloupec v produktu. V příkladu, který by byl hodnotou prvku v prvním řádku a prvním sloupcem `ae + bg`. Pro každý termín musíte vypočítat jenom první sloupec, první řádek `ae` a `bg`. Tato hodnota pro `ae` je `(1 * 1) + (2 * 5) = 11`. Hodnota pro `bg` je `(3 * 1) + (4 * 5) = 23`. Konečná hodnota je `11 + 23 = 34`, což je správné.

Pro implementaci tohoto algoritmu kód:

- Používá `tiled_extent` objekt namísto `extent` objektu ve volání `parallel_for_each`.

- Používá `tiled_index` objekt namísto `index` objektu ve volání `parallel_for_each`.

- Vytvoří proměnné `tile_static` pro uložení podmatic.

- Používá metodu `tile_barrier::wait` k zastavení vláken pro výpočet produktů podmatric.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Vynásobení pomocí AMP a dlaždic

1. V MatrixMultiply. cpp přidejte následující kód před metodu `main`.

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

   Tento příklad se výrazně liší od příkladu bez dlaždic. Kód používá tyto koncepční kroky:
   1. Zkopírujte prvky dlaždice [0, 0] `a` do `locA`. Zkopírujte prvky dlaždice [0, 0] `b` do `locB`. Všimněte si, že `product` je dlážděn, není `a` a `b`. Proto pomocí globálních indexů získáte přístup k `a, b`a `product`. Volání `tile_barrier::wait` je nezbytné. Zastaví všechna vlákna v dlaždici, dokud nejsou vyplněny `locA` i `locB`.

   1. Vynásobení `locA` a `locB` a vložení výsledků do `product`.

   1. Zkopírujte prvky dlaždice [0, 1] `a` do `locA`. Zkopírování prvků dlaždice [1, 0] z `b` do `locB`.

   1. Vynásobte `locA` a `locB` a přidejte je do výsledků, které jsou již v `product`.

   1. Násobení dlaždice [0, 0] je dokončeno.

   1. Opakujte pro ostatní čtyři dlaždice. Pro dlaždice není k dispozici žádné indexování a vlákna lze spustit v libovolném pořadí. Při každém spuštění vlákna se `tile_static` proměnné pro každou dlaždici vytvoří správně a volání `tile_barrier::wait` řídí tok programu.

   1. Při prohlédnutí algoritmu pečlivě si všimněte, že každá podmatice je načtena do `tile_static` paměti dvakrát. Tento přenos dat trvá čas. Jakmile se ale data nacházejí v `tile_static` paměti, je přístup k datům mnohem rychlejší. Vzhledem k tomu, že výpočet produktů vyžaduje opakovaný přístup k hodnotám v podmatricích, dojde k celkovému nárůstu výkonu. Pro každý algoritmus je nutné experimenty najít optimální algoritmus a velikost dlaždice.

   V příkladech, které nejsou AMP a non-dlaždice, jsou každý prvek a a B dostupné čtyřikrát z globální paměti pro výpočet produktu. V příkladu dlaždice je každý element k dispozici dvakrát z globální paměti a čtyřikrát z `tile_static` paměti. Nejedná se o významný nárůst výkonu. Pokud by však byly a a B 1024x1024 matice a velikost dlaždice byla 16, došlo k výraznému nárůstu výkonu. V takovém případě by každý prvek byl zkopírován do `tile_static` paměti pouze 16 časů a byl k němu přihlédnuto z `tile_static` paměti 1024.

1. Upravte metodu Main pro volání metody `MultiplyWithTiling`, jak je znázorněno na obrázku.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. Stisknutím klávesové zkratky **Ctrl**+**F5** spusťte ladění a ověřte, zda je výstup správný.

1. Stisknutím **mezerníku** aplikaci ukončete.

## <a name="see-also"></a>Viz také:

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
