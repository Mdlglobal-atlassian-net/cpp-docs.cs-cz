---
title: 'Návod: Násobení matic | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0c61bff6251d5ae833611161ef7b1bb06e6f39a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-matrix-multiplication"></a>Návod: Násobení matic
Tento podrobný návod ukazuje, jak používat C++ AMP k urychlení provádění násobení matic. Dva algoritmy uvádíme jednu bez dlaždic a jednu s vedle sebe.  
  
## <a name="prerequisites"></a>Požadavky  
 Než začnete:  
  
-   Čtení [přehled produktu C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Čtení [pomocí dlaždice](../../parallel/amp/using-tiles.md).  
  
-   Ujistěte se, že [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)], nebo [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] je v počítači nainstalována.  
  
### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  V řádku nabídek v sadě Visual Studio, vyberte **soubor**, **nový**, **projektu**.  
  
2.  V části **nainstalovaná** v podokně šablon vyberte **Visual C++**.  
  
3.  Vyberte **prázdný projekt**, zadejte `MatrixMultiply` v **název** pole a potom vyberte **OK** tlačítko.  
  
4.  Vyberte **Další** tlačítko.  
  
5.  V **Průzkumníku řešení**, otevřete místní nabídku pro **zdrojové soubory**a potom zvolte **přidat**, **novou položku**.  
  
6.  V **přidat novou položku** dialogové okno, vyberte **soubor C++ ()**, zadejte `MatrixMultiply.cpp` v **název** pole a potom vyberte **přidat** tlačítko.  
  
## <a name="multiplication-without-tiling"></a>Násobení bez dlaždic  
 V této části vezměte v úvahu násobení matic dva, A a B, které jsou definovány takto:  
  
 ![3&#45;podle&#45;2 matice](../../parallel/amp/media/campmatrixanontiled.png "campmatrixanontiled")  
  
 ![2&#45;podle&#45;3 matice](../../parallel/amp/media/campmatrixbnontiled.png "campmatrixbnontiled")  
  
 Matice 3 2 je A a B 2 3 matice. Produkt součin hodnot a b se následující matice 3 x 3. Produkt je vypočtena vynásobením řádků A sloupců b elementu pomocí elementu.  
  
 ![3&#45;podle&#45;3 matice](../../parallel/amp/media/campmatrixproductnontiled.png "campmatrixproductnontiled")  
  
### <a name="to-multiply-without-using-c-amp"></a>Mají vynásobit bez použití C++ AMP  
  
1.  Otevřete MatrixMultiply.cpp a použít následující kód k nahrazení existujícího kódu.  
  
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
  
    The algorithm is a straightforward implementation of the definition of matrix multiplication. It does not use any parallel or threaded algorithms to reduce the computation time.  
  
2.  Na řádku nabídek zvolte **soubor**, **Uložit vše**.  
  
3.  Zvolte klávesovou zkratku F5 spusťte ladění a ověřte, zda je správný výstup.  
  
4.  Zvolte Enter aplikaci ukončíte.  
  
### <a name="to-multiply-by-using-c-amp"></a>Chcete-li vynásobit používání modelu C++ AMP  
  
1.  V MatrixMultiply.cpp, přidejte následující kód, než `main` metoda.  
  
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
  
    The AMP code resembles the non-AMP code. The call to `parallel_for_each` starts one thread for each element in `product.extent`, and replaces the `for` loops for row and column. The value of the cell at the row and column is available in `idx`. You can access the elements of an `array_view` object by using either the `[]` operator and an index variable, or the `()` operator and the row and column variables. The example demonstrates both methods. The `array_view::synchronize` method copies the values of the `product` variable back to the `productMatrix` variable.  
  
2.  Přidejte následující `include` a `using` příkazy v horní části MatrixMultiply.cpp.  
  
```cpp  
#include <amp.h>  
using namespace concurrency;  
```  
  
3.  Změnit `main` metoda k volání `MultiplyWithAMP` metoda.  
  
```cpp  
void main() {  
    MultiplyWithOutAMP();  
    MultiplyWithAMP();  
    getchar();  
}  
```  
  
4.  Zvolte klávesovou zkratku Ctrl + F5 spusťte ladění a ověřte, zda je správný výstup.  
  
5.  Zvolte MEZERNÍK ukončete aplikaci.  
  
## <a name="multiplication-with-tiling"></a>Násobení s vedle sebe  
 Dlaždice je technika, ve kterém rozdělení dat do rovná velikosti podmnožiny, které jsou známé jako dlaždice. Tři věci změnit, pokud používáte vedle sebe.  
  
-   Můžete vytvořit `tile_static` proměnné. Přístup k datům v `tile_static` prostor může být mnohem rychlejší než přístup k datům v globálním prostoru. Instance `tile_static` proměnné se vytvoří pro každou dlaždici, a všechna vlákna v dlaždici mají přístup k proměnné. Hlavní výhodou dlaždice je zvýšení výkonu z důvodu `tile_static` přístup.  
  
-   Můžete volat [tile_barrier::wait –](reference/tile-barrier-class.md#wait) metoda zastavení všech vláken v jedné dlaždici na zadaný řádek kódu. Pořadí, ve kterém vláken se spustí pouze v, nebudete moct zaručit, že všechny podprocesy v jedné dlaždici se zastaví na volání `tile_barrier::wait` předtím, než budou pokračovat v provádění.  

  
-   Máte přístup k index vlákno relativně k celý `array_view` objekt a index relativně k dlaždici. Pomocí místní index lze usnadnit kódu ke čtení a ladění.  
  
 Pokud chcete využít výhod dlaždice v násobení matic, použije algoritmus oddílu matice do dlaždice a potom zkopírovat data dlaždice do `tile_static` proměnných pro rychlejší přístup. V tomto příkladu je matice rozděleny do submatrices rovna velikosti. Produkt je nalezen vynásobením submatrices. Jsou dvě matic a jejich produktu v tomto příkladu:  
  
 ![4&#45;podle&#45;4 matice](../../parallel/amp/media/campmatrixatiled.png "campmatrixatiled")  
  
 ![4&#45;podle&#45;4 matice](../../parallel/amp/media/campmatrixbtiled.png "campmatrixbtiled")  
  
 ![4&#45;podle&#45;4 matice](../../parallel/amp/media/campmatrixproducttiled.png "campmatrixproducttiled")  
  
 Matice jsou rozděleny do čtyř 2 x 2 matice, které jsou definovány takto:  
  
 ![4&#45;podle&#45;4 matice rozdělena na oddíly do 2&#45;podle&#45;2 dílčí&#45;matice](../../parallel/amp/media/campmatrixapartitioned.png "campmatrixapartitioned")  
  
 ![4&#45;podle&#45;4 matice rozdělena na oddíly do 2&#45;podle&#45;2 dílčí&#45;matice](../../parallel/amp/media/campmatrixbpartitioned.png "campmatrixbpartitioned")  
  
 Produkt A a B nyní může zapisovat a vypočítávány následujícím způsobem:  
  
 ![4&#45;podle&#45;4 matice rozdělena na oddíly do 2&#45;podle&#45;2 dílčí&#45;matice](../../parallel/amp/media/campmatrixproductpartitioned.png "campmatrixproductpartitioned")  
  
 Protože matice `a` prostřednictvím `h` jsou matice 2 x 2, všechny produkty a součtů z nich jsou také matice 2 x 2. Také vyplývá, že A * B je matice 4 x 4, podle očekávání. Pokud chcete rychle zkontrolovat algoritmus, vypočítejte hodnotu elementu v prvním řádku, první sloupec v rámci produktu. V příkladu, který bude hodnota elementu v prvním řádku a první sloupec `ae + bg`. Budete muset vypočítat první sloupec, první řádek `ae` a `bg` ke každému termínu. Tuto hodnotu pro `ae` je `1*1 + 2*5 = 11`. Hodnota `bg` je `3*1 + 4*5 = 23`. Konečná hodnota je `11 + 23 = 34`, který je správný.  
  
 K implementaci tento algoritmus kód:  
  
-   Používá `tiled_extent` objektu místo `extent` objekt v `parallel_for_each` volání.  
  
-   Používá `tiled_index` objektu místo `index` objekt v `parallel_for_each` volání.  
  
-   Vytvoří `tile_static` proměnné, do kterých submatrices.  
  
-   Používá `tile_barrier::wait` metoda zastavit vláken pro výpočet produktů submatrices.  
  
### <a name="to-multiply-by-using-amp-and-tiling"></a>Mají vynásobit pomocí AMP a vedle sebe  
  
1.  V MatrixMultiply.cpp, přidejte následující kód, než `main` metoda.  
  
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
  
    1.  Kopírování prvků dlaždici [0,0] `a` do `locA`. Kopírování prvků dlaždici [0,0] `b` do `locB`. Všimněte si, že `product` rozložen formou dlaždic, není `a` a `b`. Proto globální indexy, které používáte pro přístup k `a, b`, a `product`. Volání `tile_barrier::wait` je nezbytné. Dokud všechny podprocesy v dlaždici zastaví `locA` a `locB` jsou vyplněny.  
  
    2.  Vynásobit `locA` a `locB` a umístí výsledky `product`.  
  
    3.  Kopírování prvků dlaždici [0,1] `a` do `locA`. Kopírování prvků dlaždici [1,0] `b` do `locB`.  
  
    4.  Vynásobit `locA` a `locB` a přidat je do výsledky, které jsou již v `product`.  
  
    5.  Násobení dlaždice [0,0] byla dokončena.  
  
    6.  Opakujte pro čtyři dlaždice. Neexistuje žádné indexování speciálně pro dlaždice a vláken může spustit v libovolném pořadí. Protože každé vlákno provede, `tile_static` proměnné se vytvoří pro každou dlaždici správně a volání k `tile_barrier::wait` řídí tok programu.  
  
    7.  Jak byste pečlivě zkontrolovat algoritmus, Všimněte si, že každý submatrix je načten do `tile_static` paměti dvakrát. Přenos dat dobu trvat. Nicméně jakmile jsou data v `tile_static` paměti, přístup k datům je mnohem rychlejší. Protože výpočet produkty vyžaduje opakované přístup k hodnotám v submatrices, je získat celkový výkon. U jednotlivých algoritmů se vyžaduje experimentování a najít optimální algoritmus dlaždici velikost.  
  
         V příkladech bez AMP a bez dlaždice každý prvek A a B přistupuje čtyřikrát z globální paměť pro výpočet produktu. V příkladu dlaždice každý prvek přistupuje dvakrát z globální paměť a čtyřikrát `tile_static` paměti. To není značné zvýšení výkonu. Ale pokud 1024 x 1 024 A a B matic a velikost dlaždice měla 16, by značné zvýšení výkonu. V takovém případě by každý prvek zkopírují do `tile_static` paměť pouze 16 krát a k němu přistupovat z `tile_static` paměti 1024 časy.  
  
2.  Upravit hlavní metoda k volání `MultiplyWithTiling` metoda, jak je vidět.  
  
```cpp  
void main() {  
    MultiplyWithOutAMP();  
    MultiplyWithAMP();  
    MultiplyWithTiling();  
    getchar();  
}  
```  
  
3.  Zvolte klávesovou zkratku Ctrl + F5 spusťte ladění a ověřte, zda je správný výstup.  
  
4.  Vyberte na panelu místa pro ukončení aplikace.  
  
## <a name="see-also"></a>Viz také  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)

