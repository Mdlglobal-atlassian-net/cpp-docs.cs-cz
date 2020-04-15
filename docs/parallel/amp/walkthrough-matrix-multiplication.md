---
title: 'Návod: Násobení matic'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: f30f8dc235bf0e76c342bea26a35bcbb36cfa237
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366802"
---
# <a name="walkthrough-matrix-multiplication"></a>Návod: Násobení matic

Tento podrobný návod ukazuje, jak pomocí C++ AMP urychlit provádění násobení matice. Dva algoritmy jsou prezentovány, jeden bez obkladů a jeden s obklady.

## <a name="prerequisites"></a>Požadavky

Než začnete, potřebujete:

- Přečtěte si [přehled C++ AMP](../../parallel/amp/cpp-amp-overview.md).

- Přečtěte si [pomocí dlaždic](../../parallel/amp/using-tiles.md).

- Zkontrolujte, zda používáte alespoň systém Windows 7 nebo Windows Server 2008 R2.

### <a name="to-create-the-project"></a>Vytvoření projektu

Pokyny pro vytvoření nového projektu se liší v závislosti na verzi sady Visual Studio, kterou jste nainstalovali. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Vytvoření projektu v sadě Visual Studio 2019

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Systém Windows**a **typ projektu** na **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Prázdný projekt** a pak zvolte **Další**. Na další stránce zadejte *MatrixMultiply* do pole **Název,** abyste určili název projektu a v případě potřeby zadejte umístění projektu.

   ![Nová konzolová aplikace](../../build/media/mathclient-project-name-2019.png "Nová konzolová aplikace")

1. Zvolte tlačítko **Vytvořit** pro vytvoření klientského projektu.

1. V **Průzkumníku řešení**otevřete místní nabídku **pro zdrojové soubory**a pak zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**, do pole **Název** zadejte *MatrixMultiply.cpp* a pak zvolte tlačítko **Přidat.**

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Vytvoření projektu v sadě Visual Studio 2017 nebo 2015

1. Na řádku nabídek v sadě Visual Studio zvolte **Soubor** > **nového** > **projektu**.

1. V části **Nainstalované** v podokně předloh vyberte **Visual C++**.

1. Vyberte **Prázdný projekt**, do pole **Název** zadejte *MatrixMultiply* a pak zvolte tlačítko **OK.**

1. Zvolte tlačítko **Další.**

1. V **Průzkumníku řešení**otevřete místní nabídku **pro zdrojové soubory**a pak zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte **soubor C++ (.cpp)**, do pole **Název** zadejte *MatrixMultiply.cpp* a pak zvolte tlačítko **Přidat.**

::: moniker-end

## <a name="multiplication-without-tiling"></a>Násobení bez dlaždic

V tomto oddíle zvažte násobení dvou matic A a B, které jsou definovány takto:

![3&#45;&#45;2 matice A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;&#45;2 matice A")

![2&#45;&#45;3 matice B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;&#45;3 matice B")

A je matice 3-by-2 a B je matice 2-by-3. Součin násobení A b je následující matice 3 po 3. Produkt se vypočítá vynásobením řádků A sloupci prvku B po elementu.

![3&#45;&#45;produktovou matricí](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;&#45;produktovou matricí")

### <a name="to-multiply-without-using-c-amp"></a>Množení bez použití C++ AMP

1. Otevřete soubor MatrixMultiply.cpp a použijte následující kód k nahrazení existujícího kódu.

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

   Algoritmus je přímočará implementace definice násobení matice. Nepoužívá žádné paralelní nebo zřetězené algoritmy ke zkrácení výpočetní doby.

1. Na řádku nabídek zvolte **Soubor** > **Uložit vše**.

1. Zvolte klávesovou zkratku **F5,** chcete-li spustit ladění a ověřit správnost výstupu.

1. Chcete-li aplikaci ukončit, zvolte **Enter.**

### <a name="to-multiply-by-using-c-amp"></a>Vynásobení pomocí C++ AMP

1. V Souboru MatrixMultiply.cpp přidejte `main` před metodu následující kód.

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

   Kód AMP se podobá kódu bez AMP. Volání spustí `parallel_for_each` jedno vlákno pro `product.extent`každý prvek v `for` , a nahradí smyčky pro řádek a sloupec. Hodnota buňky na řádku a sloupci `idx`je k dispozici v . K prvkům objektu `array_view` můžete přistupovat `[]` pomocí operátoru a `()` proměnné indexu nebo operátoru a proměnných řádků a sloupců. Příklad ukazuje obě metody. Metoda `array_view::synchronize` zkopíruje hodnoty `product` proměnné zpět `productMatrix` do proměnné.

1. Přidejte `include` následující `using` a příkazy v horní části MatrixMultiply.cpp.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. Upravte `main` metodu `MultiplyWithAMP` pro volání metody.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. Stisknutím klávesové zkratky **Ctrl**+**F5** spusťte ladění a ověřte, zda je výstup správný.

1. Stisknutím **mezerníku** aplikaci ukončete.

## <a name="multiplication-with-tiling"></a>Násobení s obklady

Skládání je technika, ve které rozdělíte data do podmnožiny stejné velikosti, které jsou označovány jako dlaždice. Tři věci se mění, když používáte obklady.

- Můžete vytvářet `tile_static` proměnné. Přístup k `tile_static` datům v prostoru může být mnohokrát rychlejší než přístup k datům v globálním prostoru. Instance `tile_static` proměnné je vytvořena pro každou dlaždici a všechna vlákna v dlaždici mají přístup k proměnné. Hlavní výhodou dlaždic je zvýšení výkonu `tile_static` díky přístupu.

- Můžete volat [tile_barrier::wait](reference/tile-barrier-class.md#wait) metoda zastavit všechny podprocesy v jedné dlaždici na zadaný řádek kódu. Nelze zaručit pořadí, ve kterých budou vlákna spuštěna, pouze to, že všechna `tile_barrier::wait` vlákna v jedné dlaždici se zastaví při volání před pokračováním v provádění.

- Máte přístup k indexu podprocesu vzhledem k celému `array_view` objektu a indexu vzhledem k dlaždici. Pomocí místníindex, můžete usnadnit čtení kódu a ladění.

Chcete-li využít dlaždicv násobení matice, algoritmus musí rozdělit matice do `tile_static` dlaždic a pak zkopírovat data dlaždice do proměnných pro rychlejší přístup. V tomto příkladu je matice rozdělena na dílčí matice stejné velikosti. Produkt se nachází vynásobením submatrice. Dvě matice a jejich produkt v tomto příkladu jsou:

![4&#45;&#45;4 matice A](../../parallel/amp/media/campmatrixatiled.png "4&#45;&#45;4 matice A")

![4&#45;&#45;4 matice B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;&#45;4 matice B")

![4&#45;podle&#45;4 produktové matice](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;podle&#45;4 produktové matice")

Matice jsou rozděleny do čtyř matic 2x2, které jsou definovány takto:

![4&#45;&#45;4 matice A rozdělena na 2&#45;&#45;2 dílčí mimatice&#45;](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;&#45;4 matice A rozdělena na 2&#45;&#45;2 dílčí mimatice&#45;")

![4&#45;&#45;4 matice B rozdělena na 2&#45;&#45;2 dílčí&#45;matice](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;&#45;4 matice B rozdělena na 2&#45;&#45;2 dílčí&#45;matice")

Součin A a B lze nyní zapsat a vypočítat takto:

![4&#45;&#45;4 matice A B rozdělena na 2&#45;&#45;2 pod&#45;matice](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;&#45;4 matice A B rozdělena na 2&#45;&#45;2 pod&#45;matice")

Vzhledem k `a` tomu, matice přes `h` jsou 2x2 matice, všechny produkty a součty z nich jsou také 2x2 matice. Z toho také vyplývá, že součin A a B je matice 4x4, jak se očekávalo. Chcete-li rychle zkontrolovat algoritmus, vypočítejte hodnotu prvku v prvním řádku, první sloupec v produktu. V příkladu by to byla hodnota prvku v prvním řádku `ae + bg`a prvním sloupci . Stačí vypočítat první sloupec, první `ae` řádek `bg` a pro každý termín. Tato hodnota `ae` `(1 * 1) + (2 * 5) = 11`pro je . Hodnota pro `bg` `(3 * 1) + (4 * 5) = 23`je . Konečná hodnota `11 + 23 = 34`je , která je správná.

Chcete-li implementovat tento algoritmus, kód:

- Používá `tiled_extent` objekt namísto `extent` objektu `parallel_for_each` ve volání.

- Používá `tiled_index` objekt namísto `index` objektu `parallel_for_each` ve volání.

- Vytvoří `tile_static` proměnné pro uložení submatrice.

- Používá `tile_barrier::wait` metodu k zastavení podprocesů pro výpočet produktů dílčích matic.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Vynásobení pomocí AMP a dlaždic

1. V Souboru MatrixMultiply.cpp přidejte `main` před metodu následující kód.

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
   1. Zkopírujte prvky dlaždice[0,0] `locA`do `a` . Zkopírujte prvky dlaždice[0,0] `locB`do `b` . Všimněte `product` si, že `a` `b`je kachlová, ne a . Proto použijete globální indexy `a, b`pro `product`přístup a . Volání je `tile_barrier::wait` nezbytné. Zastaví všechny vlákna v dlaždici, `locA` `locB` dokud oba a jsou vyplněny.

   1. Vynásobte `locA` `locB` a `product`vložte výsledky do .

   1. Zkopírujte prvky dlaždice[0,1] do `a` . `locA` Zkopírujte prvky dlaždice [1,0] do `b` `locB`.

   1. Násobí `locA` a `locB` přidá je k `product`výsledkům, které jsou již v .

   1. Násobení dlaždice[0,0] je dokončeno.

   1. Opakujte pro další čtyři dlaždice. Neexistuje žádný indexování speciálně pro dlaždice a vlákna lze spustit v libovolném pořadí. Při spuštění každého vlákna jsou `tile_static` proměnné vytvořeny pro každou dlaždici odpovídajícím způsobem a volání k `tile_barrier::wait` řízení toku programu.

   1. Při bližším zkoumání algoritmu si všimněte, že `tile_static` každá submatice je načtena do paměti dvakrát. Přenos dat nějakou dobu trvá. Jakmile jsou však `tile_static` data v paměti, přístup k datům je mnohem rychlejší. Vzhledem k tomu, že výpočet produktů vyžaduje opakovaný přístup k hodnotám v dílčích maticích, dochází k celkovému zvýšení výkonu. Pro každý algoritmus je nutné experimentovat najít optimální algoritmus a velikost dlaždice.

   V příkladech mimo AMP a bez dlaždic je každý prvek A a B přístupný čtyřikrát z globální paměti pro výpočet produktu. V příkladu dlaždice každý prvek je přístupný dvakrát z globální `tile_static` paměti a čtyřikrát z paměti. To není významný nárůst výkonu. Pokud by však matice A a B byly 1024x1024 a velikost dlaždice byla 16, došlo by k významnému zvýšení výkonu. V takovém případě by každý prvek `tile_static` zkopírovat do paměti pouze `tile_static` 16 krát a přistupovat z paměti 1024 krát.

1. Upravte hlavní metodu `MultiplyWithTiling` volání metody, jak je znázorněno.

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

## <a name="see-also"></a>Viz také

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
