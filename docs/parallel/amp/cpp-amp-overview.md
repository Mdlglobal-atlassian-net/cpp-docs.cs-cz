---
title: "Přehled produktu C++ AMP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
caps.latest.revision: "60"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54823d53cfe6e83879db70dac7809a1b40217bd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-amp-overview"></a>Přehled produktu C++ AMP
C++ Accelerated Massive Parallelism (C++ AMP) zrychluje spuštění kódu C++ a využívají data paralelní hardwaru, jako jsou grafický procesor (GPU) na kartě diskrétní grafiky. Pomocí C++ AMP můžete kódu algoritmy vícerozměrných dat tak, aby spuštění lze urychlit pomocí paralelismus na heterogenní hardwaru. Programovací model C++ AMP zahrnuje vícerozměrná pole, indexování, přenos paměti, dlaždice a knihovnu matematické funkce. Rozšíření jazyka C++ AMP můžete použít k řízení, jak přesunout data z procesoru na grafický procesor a zpět, takže může zlepšit výkon.  
  
## <a name="system-requirements"></a>Požadavky na systém  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)], nebo[!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]  
  
-   Rozhraní DirectX 11 funkce úroveň 11.0 nebo novější hardwaru  
  
-   Pro ladění na emulátoru softwaru [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] nebo [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] je vyžadován. Pro ladění na hardware, je nutné nainstalovat ovladače grafické karty. Další informace najdete v tématu [ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code).  
  
## <a name="introduction"></a>Úvod  
 Následující dva příklady ilustrují primární součásti C++ AMP. Předpokládejme, že chcete přidat odpovídající elementy dvě jednorozměrná pole. Můžete například chtít přidat `{1, 2, 3, 4, 5}` a `{6, 7, 8, 9, 10}` získat `{7, 9, 11, 13, 15}`. Bez použití C++ AMP, může zapsat následující kód k přidání čísla a zobrazit výsledky.  
  
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
  
-   Data: Data se skládá ze tří polí. Všechny mají stejné pořadí (jeden) a délky (5).  
  
-   Iterace: První `for` smyčky poskytuje mechanismus pro iterace v rámci prvků v poli. Kód, který chcete provést výpočetní částky je součástí první `for` bloku.  
  
-   Index: `idx` proměnná přistupuje k jednotlivých prvků pole.  
  
 Používání modelu C++ AMP, můžete napsat kód následující místo.  
  
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
  
 Stejné základní prvky jsou přítomny, ale používají C++ AMP konstrukce:  
  
-   Data: Použijte pole v jazyce C++ vytvořit tři C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) objekty. Zadat čtyři hodnoty vytvořit `array_view` objektu: datových hodnot, pořadí, typ elementu a délka `array_view` objekt v Každá dimenze. Pořadí a typ jsou předány jako parametry typu. Data a délka jsou předány jako parametry konstruktor. V tomto příkladu je jednorozměrné pole C++, který je předán do konstruktoru. Pořadí a délka se používají k vytvoření pravoúhlému tvaru data v `array_view` objektu a hodnoty se používají k vyplnění pole data. Knihovna runtime také zahrnuje [array – třída](../../parallel/amp/reference/array-class.md), který má rozhraní, které vypadá takto: `array_view` třídy a je popsána dále v tomto článku.  
  
-   Iterace: [parallel_for_each – funkce (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) poskytuje mechanismus pro iterace v rámci datové prvky, nebo *výpočetní domény*. V tomto příkladu je zadána výpočetní doméně `sum.extent`. Kód, který chcete spustit, je součástí výrazu lambda, nebo *funkce jádra*. `restrict(amp)` Znamená, že je použit pouze podmnožinu jazyka C++, které můžou urychlit C++ AMP.  
  
-   Index: [index – třída](../../parallel/amp/reference/index-class.md) proměnnou, `idx`, je deklarovaný s pořadí jednoho tak, aby odpovídala pořadí `array_view` objektu. Pomocí index dostanete jednotlivé prvky `array_view` objekty.  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>Tvarování a indexování dat: index a rozsahu  
 Musí definovat hodnoty data a deklarovat tvaru dat, ještě před spuštěním kódu jádra. Všechna data je definován jako pole (obdélníkovou) a definujete poli, aby obsahovalo všechny pořadí (počet dimenzí). Data mohou být jakékoli velikosti v žádném z dimenzí.  
  
### <a name="index-class"></a>index – třída  
 [Index – třída](../../parallel/amp/reference/index-class.md) Určuje umístění v `array` nebo `array_view` objekt zapouzdřením posun z tohoto počátku v Každá dimenze do jednoho objektu. Při přístupu k umístění, do pole, předáte `index` objekt indexování operátor `[]`, místo seznam indexy celé číslo. Máte přístup k elementů v Každá dimenze pomocí [array:: Operator() – operátor](reference/array-class.md#operator_call) nebo [array_view:: Operator() – operátor](reference/array-view-class.md#operator_call).  
  
 Následující příklad vytvoří jednorozměrné index, který určuje třetí element jednorozměrné `array_view` objektu. Index se používá k vytištění třetí element v `array_view` objektu. Výstup je 3.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";    
// Output: 3  
```  
  
 Následující příklad vytvoří dvourozměrná index, který určuje element kde řádek = 1 a sloupec = 2 v dvourozměrná `array_view` objektu. První parametr `index` konstruktor je komponenta řádek, a druhý parametr je sloupec součástí. Výstup je 6.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);  
  
index<2> idx(1, 2);  
  
std::cout <<a[idx] << "\n";    
// Output: 6  
```  
  
 Následující příklad vytvoří prostorový index, který určuje element kde hloubka = 0, řádek = 1 a sloupec = 3 v trojrozměrné `array_view` objektu. Všimněte si, že první parametr je komponentu hloubku, druhý parametr je komponentu řádek a třetí parametr je sloupec součástí. Výstup je 8.  
  
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
 [Extent – třída](../../parallel/amp/reference/extent-class.md) určuje délce dat v každém dimenze `array` nebo `array_view` objektu. Můžete vytvořit rozsah a použít k vytvoření `array` nebo `array_view` objektu. Můžete také načíst rozsah existující `array` nebo `array_view` objektu. Následující příklad vypíše délka rozsah v každé dimenze `array_view` objektu.  
  
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
  
 Následující příklad vytvoří `array_view` dimensions objekt, který má stejný jako objekt v předchozím příkladu, ale tento příklad používá `extent` místo použití explicitní parametrů v objektu `array_view` konstruktor.  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Přesun dat do akcelerátor: pole a array_view  
 Dva kontejnery data používá k přesunu dat do akcelerátor jsou definovány v knihovně modulu runtime. Jsou [array – třída](../../parallel/amp/reference/array-class.md) a [array_view – třída](../../parallel/amp/reference/array-view-class.md). `array` Třídy je třída kontejneru, která vytvoří kopii dat hloubkové, když se objekt. `array_view` Třída představuje obálkovou třídu, která zkopíruje data, když funkce jádra přistupuje k datům. Když na zdrojového zařízení je potřeba data data se zkopírují zpět.  
  
### <a name="array-class"></a>array – třída  
 Když `array` vytvoření objektu, se vytvoří hloubkové kopie dat na akcelerátor Pokud použijete konstruktor, který zahrnuje ukazatel na datovou sadu. Funkce jádra upravením kopie na akcelerátor. Po dokončení provádění jádra funkce musíte zkopírovat data zpět na strukturu datového zdroje. Následující příklad vynásobí každý prvek v vektor 10. Po dokončení funkce jádra `vector conversion operator` se používá ke zkopírování dat zpět do objektu vektoru.  
  
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
 `array_view` Má skoro stejný členy, jako `array` třídy, ale základní chování není stejný. Data předána `array_view` konstruktor není na GPU replikované, jako je v `array` konstruktor. Místo toho ale data se zkopírují do akcelerátor při provedení funkce jádra. Proto pokud vytvoříte dva `array_view` objekty, které používají stejná data i `array_view` objekty odkazovat na stejné místo paměti. Když to uděláte, budete muset synchronizovat všechny vícevláknové přístup. Hlavní výhodou použití `array_view` třída je, že data jsou přesouvána pouze v případě, že je nutné.  
  
### <a name="comparison-of-array-and-arrayview"></a>Porovnání pole a array_view  
 Následující tabulka shrnuje podobnost a rozdíly mezi `array` a `array_view` třídy.  
  
|Popis|array – třída|array_view – třída|  
|-----------------|-----------------|-----------------------|  
|Pokud je určen pořadí|V době kompilace.|V době kompilace.|  
|Pokud je určen rozsahu|V době běhu.|V době běhu.|  
|Obrazec|Obdélníkový.|Obdélníkový.|  
|Úložiště dat|Je kontejner data.|Je obálku data.|  
|Kopírovat|Explicitní a hloubkové kopírování v definici.|Implicitní kopie při přístupu podle funkce jádra.|  
|Načítání dat|Zkopírováním dat pole zpět do objektu na vlákno procesoru.|Přímý přístup z `array_view` objektu nebo pomocí volání [array_view::synchronize – metoda](reference/array-view-class.md#synchronize) Chcete-li pokračovat, přístup k datům na původní kontejneru.|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>Sdílené paměti u pole a array_view  
 Sdílené paměti je paměť, která je přístupná procesoru a akcelerátorem. Použití sdílené paměti eliminuje nebo výrazně snižuje zatížení sady kopírování dat mezi procesoru a akcelerátorem. I když je sdílená paměť, jej nelze získat přístup, souběžně procesoru a akcelerátorem, a to způsobí tak, že nedefinované chování.  
  
 `array`objekty slouží k určení jemně odstupňovanou kontrolu nad použití sdílené paměti, pokud ji podporuje přidružené akcelerátoru. Jestli akcelerátor podporuje sdílené paměti je dáno akcelerátoru [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) vlastnost, která vrací `true` případě, že podporuje sdílené paměti. Pokud je podporováno sdílené paměti, výchozí [access_type – výčet](reference/concurrency-namespace-enums-amp.md#access_type) paměti je dáno přidělení na akcelerátor `default_cpu_access_type` vlastnost. Ve výchozím nastavení `array` a `array_view` trvat objekty na stejné `access_type` jako primární přidružené `accelerator`.  
  
 Nastavením [Array::cpu_access_type data – datový člen](reference/array-class.md#cpu_access_type) vlastnost `array` explicitně, které můžou podrobné cvičení řídit přes jak sdílené paměti se používá, tak, aby můžete optimalizovat aplikace pro výkon hardwaru vlastnosti, na základě způsobů přístupu k paměti z jeho výpočetní jádra. `array_view` Odráží stejné `cpu_access_type` jako `array` , k němuž se; nebo, pokud array_view je vytvořený bez zdroje dat, jeho `access_type` odráží prostředí, ve kterém nejprve způsobuje, že se přidělit úložiště. To znamená, pokud nejprve je přístupný pro hostitele (CPU), pak se chová jako kdyby byly vytvořeny přes procesoru zdroj dat a sdílených složek `access_type` z `accelerator_view` přidružený k podle zachycení; ale pokud je první přistupují `accelerator_view`, pak se chová jako by šlo vytvořit přes `array` vytvořen, na který `accelerator_view` a sdílených složek `array`na `access_type`.  
  
 Následující příklad kódu ukazuje, jak určit, zda akcelerátoru výchozí podporuje sdílené paměti a poté vytvoří několik polí, které mají různé cpu_access_type konfigurace.  
  
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
  
## <a name="executing-code-over-data-parallelforeach"></a>Provádění kódu přes Data: parallel_for_each –  
 [Parallel_for_each –](reference/concurrency-namespace-functions-amp.md#parallel_for_each) funkce definuje kód, který chcete spustit na akcelerátoru s daty v `array` nebo `array_view` objektu. Vezměte v úvahu následující kód z zavedení tohoto tématu.  
  
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
  
 `parallel_for_each` Metoda přebírá dva argumenty, výpočetní domény a výrazu lambda.  
  
 *Výpočetní domény* je `extent` objekt nebo `tiled_extent` objekt, který definuje sadu vláken vytvořit pro paralelní zpracování. Jedno vlákno se vygeneruje pro každý prvek ve výpočetní doméně. V takovém případě `extent` objekt jednorozměrné a má pět elementy. Proto jsou spuštěny pět vláken.  
  
 *Výrazu lambda* definuje kód pro spuštění na každé vlákno. V klauzuli zachycení `[=]`, určuje, že tělo výrazu lambda podle hodnoty, které jsou v tomto případě má přístup k proměnné všechny zaznamenané `a`, `b`, a `sum`. V tomto příkladu se vytvoří seznam parametrů jednorozměrné `index` proměnné s názvem `idx`. Hodnota `idx[0]` je 0 v první vlákno a zvýší o 1 v každé další vlákno. `restrict(amp)` Znamená, že je použit pouze podmnožinu jazyka C++, které můžou urychlit C++ AMP.  Omezení na funkce, které mají omezit modifikátor jsou popsané v [omezení (C++ AMP)](../../cpp/restrict-cpp-amp.md). Další informace najdete v tématu, [syntaxe výrazu Lambda](../../cpp/lambda-expression-syntax.md).  
  
 Výrazu lambda může obsahovat kód pro spuštění nebo ho můžete volat funkci samostatné jádra. Musí obsahovat funkci jádra `restrict(amp)` modifikátor. Následující příklad je ekvivalentní předchozí příklad, ale zavolá funkci samostatné jádra.  
  
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
  
## <a name="accelerating-code-tiles-and-barriers"></a>Urychlovacího kód: Dlaždice a překážek  

 Pomocí dlaždice, můžete získat další akcelerace. Dlaždice rozdělí vláken na stejné obdélníková podmnožiny nebo *dlaždice*. Můžete určit velikost příslušné dlaždice na základě datové sady a algoritmus, který je implementován. Pro každé vlákno, které máte přístup *globální* umístění datový prvek relativně k celé `array` nebo `array_view` a přístup k *místní* umístění relativně k dlaždici. Pomocí hodnoty místní index usnadňuje kódu, protože nemusíte psát kód, který převede hodnoty indexu z globálního na místní. Chcete-li použít dlaždice, volejte [Extent::Tile – metoda](reference/extent-class.md#tile) ve výpočetní doméně v `parallel_for_each` metoda a použití [tiled_index](../../parallel/amp/reference/tiled-index-class.md) objekt ve výrazu lambda.  
  
 V typické aplikace elementů v dlaždici souvisejí s nějakým způsobem a má kód pro přístup k a udržování přehledu o hodnoty mezi dlaždice. Použití [tile_static – klíčové slovo](../../cpp/tile-static-keyword.md) – klíčové slovo a [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait) toho chcete dosáhnout. Proměnné, která se má `tile_static` – klíčové slovo má obor napříč celou dlaždice a instance proměnné se vytvoří pro každou dlaždici. Je nutné zajistit synchronizaci vláken dlaždice přístup k proměnné. [Tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait) zastaví provádění aktuální vlákno, dokud všechna vlákna v dlaždici dosáhli volání `tile_barrier::wait`. Proto můžete shromažďujete hodnoty mezi dlaždici pomocí `tile_static` proměnné. Poté můžete dokončit všechny výpočty, které vyžadují přístup do všech hodnot.  

  
 Následující diagram představuje dvourozměrná řadu vzorkování data, která jsou uspořádána ve dlaždice.  
  
 ![Index hodnoty v vedle sebe rozsah](../../parallel/amp/media/camptiledgridexample.png "camptiledgridexample")  
  
 Následující příklad kódu používá vzorkování data z předchozí diagram. Kód nahradí každé hodnoty v dlaždici podle průměr hodnot v dlaždici.  
  
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
  
## <a name="math-libraries"></a>Knihovny Math  
 C++ AMP zahrnuje dvě matematické knihovny. Dvojitá přesnost knihovny v nástroji [Concurrency::precise_math – Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md) poskytuje podporu pro funkce dvojitou přesností. Také poskytuje podporu pro funkce s jednoduchou přesností, i když je stále potřebná podpora dvojitou přesností na hardware. Je v souladu s [C99 specifikace (ISO/IEC 9899)](http://go.microsoft.com/fwlink/linkid=225887). Akcelerátor musí podporovat a úplného dvojitou přesností. Můžete určit, jestli nemá kontrolou hodnotu [Accelerator::supports_double_precision – datový člen](reference/accelerator-class.md#supports_double_precision). Knihovny math rychlé v [Concurrency::fast_math – Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md), obsahuje další sadu matematické funkce. Tyto funkce, které podporují pouze `float` operandy, provést rychleji, ale nejsou jako přesné jako v knihovně matematické dvojitou přesností. Funkce jsou součástí \<amp_math.h > hlavičkový soubor a všechny jsou deklarovány s `restrict(amp)`. Funkce v \<cmath – > soubor hlaviček importují do obou `fast_math` a `precise_math` obory názvů. `restrict` – Klíčové slovo se používá k rozlišení \<cmath – > C++ AMP a verze. Následující kód vypočítá logaritmus základu 10, rychlé metodou, každou hodnotu, která je ve výpočetní doméně.  

  
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
            logs[idx] = concurrency::fast_math::log10(logs[idx]);  
        }  
    );  
  
    for (int i = 0; i < 6; i++) {  
        std::cout << logs[i] << "\n";  
    }  
}  
  
```  
  
## <a name="graphics-library"></a>Knihovna grafiky  
 C++ AMP obsahuje grafiky knihovnu, která je určená pro Zrychlený programováním grafiky. Tato knihovna se používá pouze v zařízeních, která podporují nativní grafické funkce. Metody jsou v [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md) a jsou součástí \<amp_graphics.h > soubor hlaviček. Klíčové komponenty knihovny grafiky jsou:  
  
- [Texture – třída](../../parallel/amp/reference/texture-class.md): texture třídu můžete použít k vytvoření textury z paměti nebo ze souboru. Textury podobat pole, protože obsahují data, a se podobají kontejnery ve standardní knihovně C++ s ohledem na přiřazení a vytváření kopie. Další informace najdete v tématu [kontejnery standardní knihovny C++](../../standard-library/stl-containers.md). Parametry šablony `texture` třídy jsou typ elementu a pořadí. Pořadí může být 1, 2 nebo 3. Typ elementu může být jeden z typů krátké vektoru, které jsou popsány dále v tomto článku.  
  
- [writeonly_texture_view – třída](../../parallel/amp/reference/writeonly-texture-view-class.md): poskytuje přístup jen pro zápis k žádné texture.  
  
- [Krátké knihovna vektoru](http://msdn.microsoft.com/en-us/4c4f5bed-c396-493b-a238-c347563f645f): definuje sadu typů krátké vektoru o délce 2, 3 a 4, které jsou založeny na `int`, `uint`, `float`, `double`, [norm](../../parallel/amp/reference/norm-class.md), nebo [unorm](../../parallel/amp/reference/unorm-class.md).  
  
## <a name="includewin8appnamelongbuildincludeswin8appnamelongmdmd-apps"></a>[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]Aplikace  
 Stejně jako jiné knihovny jazyka C++ použijete C++ AMP v vaší [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Tyto články popisují, jak zahrnout kódu C++ AMP v aplikacích vytvořené pomocí C++, C#, Visual Basic nebo JavaScript:  
  
- [Používání modelu C++ AMP v aplikacích pro Windows Store](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [Návod: Vytvoření základní komponenty prostředí Windows Runtime v jazyce C++ a volání z jazyka JavaScript](http://go.microsoft.com/fwlink/p/linkid=249077)  
  
- [Bing Maps Optimalizátor cesty, aplikace Windows Store v JavaScript a C++](http://go.microsoft.com/fwlink/p/linkid=249078)  
  
- [Jak používat C++ AMP z C# s použitím prostředí Windows Runtime](http://go.microsoft.com/fwlink/p/linkid=249080)  
  
- [Jak používat C++ AMP z jazyka C#](http://go.microsoft.com/fwlink/p/linkid=249081)  
  
- [Volání nativních funkcí ze spravovaného kódu](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP a vizualizér souběžnosti  
 Vizualizér souběžnosti zahrnuje podporu pro analýzu výkonu C++ AMP kódu. Tyto články popisují tyto funkce:  
  
- [Graf aktivity GPU](/visualstudio/profiling/gpu-activity-graph)  
  
- [Aktivita GPU (stránkování)](/visualstudio/profiling/gpu-activity-paging)  
  
- [Aktivita GPU (Tento proces)](/visualstudio/profiling/gpu-activity-this-process)  
  
- [Aktivita GPU (jiné procesy)](/visualstudio/profiling/gpu-activity-other-processes)  
  
- [Kanály (zobrazení vláken)](/visualstudio/profiling/channels-threads-view)  
  
- [Analýza kódu C++ AMP s vizualizér souběžnosti](http://go.microsoft.com/fwlink/linkid=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>Doporučení výkonu  
 MODULUS a dělení celých čísel bez znaménka mají výrazně lepší výkon než numerického zbytku a dělení podepsaná celá čísla. Doporučujeme použít bez znaménka celá čísla, pokud je to možné.  
  
## <a name="see-also"></a>Viz také  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Syntaxe výrazu lambda](../../cpp/lambda-expression-syntax.md)   
 [Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [Paralelní programování v blogu nativního kódu](http://go.microsoft.com/fwlink/p/linkid=238472)
