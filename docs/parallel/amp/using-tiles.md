---
title: "Pomocí dlaždice | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0cb598a5b0f87080a937218962037d849275d7bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-tiles"></a>Používání bloků
Dlaždice můžete maximalizovat akcelerace vaší aplikace. Dlaždice rozdělí vláken na stejné obdélníková podmnožiny nebo *dlaždice*. Pokud používáte příslušné dlaždice velikost a algoritmus vedle sebe, můžete získat i další akcelerace z vašeho kódu C++ AMP. Základní součásti dlaždice jsou:  
  
- `tile_static`proměnné. Hlavní výhodou dlaždice je výkonnější z `tile_static` přístup. Přístup k datům v `tile_static` paměti může být výrazně rychlejší než přístup k datům v globálním prostoru (`array` nebo `array_view` objektů). Instance `tile_static` proměnné se vytvoří pro každou dlaždici, a všechna vlákna v dlaždici mají přístup k proměnné. V typické vedle sebe algoritmu data zkopírována do `tile_static` paměti jednou z globální paměti a potom k němu přistupovat mnohokrát z `tile_static` paměti.  
  
- [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait). Volání `tile_barrier::wait` pozastaví spuštění aktuální vlákno, dokud všechny podprocesy v dlaždici stejné nezobrazí volání `tile_barrier::wait`. Nebudete moct zaručit pořadí, který se spustí vláken v, pouze to, že žádné vláken v dlaždici, budou spuštěny po volání `tile_barrier::wait` dokud všechny podprocesy dosáhli volání. To znamená, že pomocí `tile_barrier::wait` metodu, můžete provádět úlohy na základě dlaždice dlaždice než základ vlákno podprocesu. Typické dlaždice algoritmus má kód pro inicializaci `tile_static` paměti pro celou dlaždici následuje volání `tile_barrer::wait`. Kód, který následuje `tile_barrier::wait` obsahuje výpočty, které vyžadují přístup ke všem `tile_static` hodnoty.  

  
-   Místní a globální indexování. Máte přístup k index vlákno relativně k celý `array_view` nebo `array` objekt a index relativně k dlaždici. Pomocí místní indexu může usnadnit kódu ke čtení a ladění. Obvykle se používá pro přístup k místním indexování `tile_static` proměnné a globální indexování pro přístup k `array` a `array_view` proměnné.  
  
- [tiled_extent – třída](../../parallel/amp/reference/tiled-extent-class.md) a [tiled_index – třída](../../parallel/amp/reference/tiled-index-class.md). Můžete použít `tiled_extent` objektu místo `extent` objekt v `parallel_for_each` volání. Můžete použít `tiled_index` objektu místo `index` objekt v `parallel_for_each` volání.  
  
 Abyste mohli využívat rozložení vedle sebe, musí vaše algoritmus oddílu výpočetní doméně do dlaždice a poté zkopírujte data dlaždice do `tile_static` proměnných pro rychlejší přístup.  
  
## <a name="example-of-global-tile-and-local-indices"></a>Příklad globální, dlaždice a místní indexů  
 Následující diagram představuje matici 8 x 9 dat, která jsou uspořádána ve 2 × 3 dlaždice.  
  
 ![8 & č. 45; pomocí & č. 45; 9 matice rozdělené do 2 & č. 45; pomocí & č. 45; 3 dlaždice](../../parallel/amp/media/usingtilesmatrix.png "usingtilesmatrix")  
  
 Následující příklad zobrazí globální, dlaždice, a místní indexy tohoto rozložen formou dlaždic matice. `array_view` Objekt se vytvoří pomocí elementy typu `Description`. `Description` Obsahuje globální, dlaždice a místní indexy elementu v matici. Kód ve volání `parallel_for_each` nastaví hodnoty na globální, dlaždice a místní indexy jednotlivých prvků. Výstup zobrazuje hodnoty `Description` struktury.  
  
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
    COORD coord; coord.X = width; coord.Y = height;  
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);  
    SMALL_RECT* rect = new SMALL_RECT();  
    rect->Left = 0; rect->Top = 0; rect->Right = width; rect->Bottom = height;  
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);  
}  
  
// This method creates an 8x9 matrix of Description structures. In the call to parallel_for_each, the structure is updated   
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
  
 Hlavní pracovní v příkladu je v definici `array_view` objekt a volání `parallel_for_each`.  
  
1.  Vektor `Description` struktury se zkopíruje do 8 x 9 `array_view` objektu.  
  
2.  `parallel_for_each` Metoda je volána s `tiled_extent` objektu jako výpočetní doméně. `tiled_extent` Objekt se vytvoří při volání `extent::tile()` metodu `descriptions` proměnné. Parametry typu volání `extent::tile()`, `<2,3>`, zadejte, že jsou vytvořeny 2 × 3 dlaždice. Proto matice 8 x 9 je rozložen formou dlaždic do 12 dlaždice, čtyři řádky a tři sloupce.  
  
3.  `parallel_for_each` Metoda je volána pomocí `tiled_index<2,3>` objektu (`t_idx`) jako index. Parametry typu indexu (`t_idx`) musí odpovídat parametrům typ výpočetní doméně (`descriptions.extent.tile< 2, 3>()`).  
  
4.  Po provedení každé vlákno index `t_idx` vrátí informace, o které dlaždice vlákno se v (`tiled_index::tile` vlastnosti) a umístění vlákno v rámci dlaždice (`tiled_index::local` vlastnost).  
  
## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Dlaždice synchronizace – tile_static a tile_barrier::wait –  
 Předchozí příklad znázorňuje rozložení dlaždic a indexy, ale není sám o sobě velmi užitečné.  Dlaždice je užitečné, když jsou nedílnou součástí algoritmus a zneužití dlaždice `tile_static` proměnné. Vzhledem k tomu, že všechna vlákna v dlaždici mít přístup k `tile_static` proměnné, volání `tile_barrier::wait` slouží k synchronizaci přístup k `tile_static` proměnné. I když všechny podprocesy v dlaždici mají přístup k `tile_static` proměnné, neexistuje žádný zaručenou pořadí provádění vláken v dlaždici. Následující příklad ukazuje, jak používat `tile_static` proměnné a `tile_barrier::wait` metodu pro výpočet průměrná hodnota každou dlaždici. Zde jsou klíče k pochopení příkladu:  
  
1.  RawData je uložený v matici 8 x 8.  
  
2.  Velikost dlaždice je 2 x 2. Tím se vytvoří 4 x 4 mřížky dlaždic a průměry může být uložený v matice 4 x 4 pomocí `array` objektu. Nejsou k dispozici pouze omezený počet typů, které můžete zaznamenat odkazem v funkci AMP omezený. `array` Třída je jeden z nich.  
  
3.  Velikost matice a velikost vzorku jsou definované za použití `#define` příkazy, protože typ parametry, které chcete `array`, `array_view`, `extent`, a `tiled_index` musí být konstantní hodnoty. Můžete také použít `const int static` deklarace. Další výhodou je je jednoduchá, chcete-li změnit velikost vzorku pro výpočet průměrné dlaždice více než 4 x 4.  
  
4.  A `tile_static` 2 x 2 pole hodnot float je deklarovaný pro každou dlaždici. I když jsou deklaraci v kódové cestě pro každé vlákno, pouze jedno pole se vytvoří pro každou dlaždici v matici.  
  
5.  Je řádek kódu ke zkopírování hodnot v jednotlivých dlaždici `tile_static` pole. Pro každé vlákno po zkopírování hodnotu do pole, provádění ve vlákně zastaví z důvodu volání `tile_barrier::wait`.  
  
6.  Po dosažení všech vláken v dlaždici bariéry, lze vypočítat průměr. Vzhledem k tomu, že kód provede pro každé vlákno, není `if` příkaz pouze vypočítat průměr na jedno vlákno. Průměr je uložené v proměnné průměry. Bariéry je v podstatě konstruktor, který řídí výpočty pomocí dlaždice, podobně jako můžete použít `for` smyčky.  
  
7.  Data v `averages` proměnné, protože se jedná `array` objektu, musí se zkopírovat zpět na hostitele. Tento příklad používá operátor převodu vektoru.  
  
8.  V příkladu SAMPLESIZE, můžete změnit na 4 a kód provede správně bez další změny.  
  
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
 Může to být tempting k vytvoření `tile_static` proměnné s názvem `total` a zvýšit tuto proměnnou pro každé vlákno takto:  
  
```cpp  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);

 
```  
  
 První problém s tímto přístupem je, že `tile_static` proměnné nemůže mít inicializátory. Druhý problém je, že je na přiřazení časování `total`, protože všechny podprocesy v dlaždici mít přístup k proměnné seřazeny. Algoritmus, který má-li povolit pouze jedno vlákno k celkem v každé bariéry, jak ukazuje následující může programu. Toto řešení však není rozšiřitelný.  
  
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
  
## <a name="memory-fences"></a>Ochranné paměti  
 Existují dva druhy paměti přístupů, které musí být synchronizovány – globální paměť přístup a `tile_static` přístup do paměti. A `concurrency::array` objekt přiděluje jenom globální paměť. A `concurrency::array_view` odkazovat globální paměť `tile_static` paměti, nebo obojí, v závislosti na tom, jak byl zkonstruován.  Existují dva typy paměti, která musí být synchronizovány:  
  
-   globální paměť  
  
- `tile_static`  
  
 A *paměti ochranná* zajišťuje, že paměť přístupů, které jsou k dispozici pro jiná vlákna v dlaždici přístup z více vláken a že paměť přístupů jsou spouštěny v pořadí, v programu. Aby, kompilátory a procesory není změnit pořadí čtení a zápisy napříč ochranná. V C++ AMP ochranná paměti vytvořené volání jednu z těchto metod:  
  

- [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait): vytvoří ohraničení kolem obě globální a `tile_static` paměti.  
  
- [tile_barrier::wait_with_all_memory_fence – metoda](reference/tile-barrier-class.md#wait_with_all_memory_fence): vytvoří ohraničení kolem obě globální a `tile_static` paměti.  
  
- [tile_barrier::wait_with_global_memory_fence – metoda](reference/tile-barrier-class.md#wait_with_global_memory_fence): vytvoří ohraničení kolem pouze globální paměť.  
  
- [tile_barrier::wait_with_tile_static_memory_fence – metoda](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): vytvoří ohraničení kolem pouze `tile_static` paměti.  

  
 Volání metody konkrétní ochranná, které vyžadují může zvýšit výkon vaší aplikace. Typ bariéry ovlivňuje, jak kompilátor a hardware změnit jeho pořadí příkazy. Například pokud použijete ochranná globální paměť, se vztahuje jenom na globální paměti přístupů a proto může změnit pořadí kompilátor a hardwaru čte a zapisuje `tile_static` proměnné na dvou stranách ochranná.  
  
 V následujícím příkladu, bariéry synchronizuje zápisy do `tileValues`, `tile_static` proměnné. V tomto příkladu `tile_barrier::wait_with_tile_static_memory_fence` nazývá místo `tile_barrier::wait`.  
  
```cpp  
// Using a tile_static memory fence.  
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),  
 [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)   
{ *// Copy the values of the tile into a tile-sized array.  
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];  
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];  
 *// Wait for the tile-sized array to load before calculating the average.  
    t_idx.barrier.wait_with_tile_static_memory_fence();

 *// If you remove the if statement, then the calculation executes for every *// thread in the tile, and makes the same assignment to averages each time.  
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
  
## <a name="see-also"></a>Viz také  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile_static – klíčové slovo](../../cpp/tile-static-keyword.md)

