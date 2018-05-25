---
title: 'Návod: Ladění aplikace C++ AMP | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf80276b5434804651bcc4507397e9479f6e494
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Návod: Ladění aplikace C++ AMP
Toto téma ukazuje, jak ladit aplikaci, která používá C++ Accelerated Massive Parallelism (C++ AMP) využívat výhod grafický procesor (GPU). Využívá paralelní snížení program, který shrnuje velké pole celých čísel. Tento návod znázorňuje následující úlohy:  
  
-   Spuštění ladicího programu GPU.  
  
-   Probíhá kontrola vláken GPU v okna vláken GPU.  
  
-   Použití okna paralelní zásobníky současně sledovat zásobníky volání více vláken GPU.  
  
-   Použití okna paralelního sledování kontrola hodnoty jeden výraz napříč více vláken ve stejnou dobu.  
  
-   Označování, zmrazení, uvolnění a seskupení vláken GPU.  
  
-   Provádění všechna vlákna tohoto dlaždice do určitého umístění v kódu.  
  
## <a name="prerequisites"></a>Požadavky  
 Než začnete Tento názorný postup:  
  
-   Čtení [přehled produktu C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Ujistěte se, že řádku čísla se zobrazí v textovém editoru. Další informace najdete v tématu [postupy: zobrazení čísel řádků v editoru](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).  
  
-   Ujistěte se, zda jsou spuštěny [!INCLUDE[win8](../../build/reference/includes/win8_md.md)] nebo [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] pro podporu ladění na emulátoru softwaru.  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>K vytvoření ukázkového projektu  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
3.  V části **nainstalovaná** v podokně šablon vyberte **Visual C++**.  
  
4.  Zvolte **Konzolová aplikace Win32**, typ `AMPMapReduce` v **název** pole a potom vyberte **OK** tlačítko.  
  
5.  Vyberte **Další** tlačítko.  
  
6.  Vymazat **předkompilované hlavičky** zaškrtněte políčko a potom vyberte **Dokončit** tlačítko.  
  
7.  V **Průzkumníku**, odstranit stdafx.h, targetver.h a stdafx.cpp z projektu.  
  
8.  Otevřete AMPMapReduce.cpp a nahraďte jeho obsah následujícím kódem.  
  
 ```cpp  
    // AMPMapReduce.cpp defines the entry point for the program.  
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.   
  
    #include <stdio.h>  
    #include <tchar.h>  
    #include <amp.h>  
  
    const int BLOCK_DIM = 32;  
  
    using namespace concurrency;  
  
    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)  
    {  
        tile_static int localA[BLOCK_DIM];  
  
        index<1> globalIdx = t_idx.global * stride_size;  
        index<1> localIdx = t_idx.local;  
  
        localA[localIdx[0]] =  A[globalIdx];  
  
        t_idx.barrier.wait();  
  
        // Aggregate all elements in one tile into the first element.  
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)   
        {  
            if (localIdx[0] < i)   
            {  
  
                localA[localIdx[0]] += localA[localIdx[0] + i];  
            }  
  
            t_idx.barrier.wait();  
        }  
  
        if (localIdx[0] == 0)  
        {  
            A[globalIdx] = localA[0];  
        }  
    }  
  
    int size_after_padding(int n)  
    {  
        // The extent might have to be slightly bigger than num_stride to   
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.  
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)  
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;  
    }  
  
    int reduction_sum_gpu_kernel(array<int, 1> input)   
    {  
        int len = input.extent[0];  
  
        //Tree-based reduction control that uses the CPU.  
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)   
        {  
            // Number of useful values in the array, given the current  
            // stride size.  
            int num_strides = len / stride_size;    
  
            extent<1> e(size_after_padding(num_strides));  
  
            // The sum kernel that uses the GPU.  
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)  
            {  
                sum_kernel_tiled(idx, input, stride_size);  
            });  
        }  
  
        array_view<int, 1> output = input.section(extent<1>(1));  
        return output[0];  
    }  
  
    int cpu_sum(const std::vector<int> &arr) {  
        int sum = 0;  
        for (size_t i = 0; i < arr.size(); i++) {  
            sum += arr[i];  
        }  
        return sum;  
    }  
  
    std::vector<int> rand_vector(unsigned int size) {  
        srand(2011);  
  
        std::vector<int> vec(size);  
        for (size_t i = 0; i < size; i++) {  
            vec[i] = rand();  
        }  
        return vec;  
    }  
  
    array<int, 1> vector_to_array(const std::vector<int> &vec) {  
        array<int, 1> arr(vec.size());  
        copy(vec.begin(), vec.end(), arr);  
        return arr;  
    }  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
        std::vector<int> vec = rand_vector(10000);  
        array<int, 1> arr = vector_to_array(vec);  
  
        int expected = cpu_sum(vec);  
        int actual = reduction_sum_gpu_kernel(arr);  
  
        bool passed = (expected == actual);  
        if (!passed) {  
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);  
        }  
        printf("sum: %s\n", passed  "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
 ```  
  
9. Na řádku nabídek zvolte **soubor**, **Uložit vše**.  
  
10. V **Průzkumníku řešení**, otevřete místní nabídku pro **AMPMapReduce**a potom zvolte **vlastnosti**.  
  
11. V **stránky vlastností** dialogovém **vlastnosti konfigurace**, zvolte **C/C++**, **předkompilovaných hlaviček**.  
  
12. Pro **předkompilovaných hlaviček** vlastnosti, vyberte **není použití předkompilovaných hlaviček**a potom zvolte **OK** tlačítko.  
  
13. Na řádku nabídek zvolte **sestavení**, **sestavit řešení**.  
  
## <a name="debugging-the-cpu-code"></a>Ladění kódu procesoru  
 V tomto postupu budete používat místní ladicí program systému Windows a ujistěte se, zda je správný kód procesoru v této aplikaci. Segment kódu procesoru v této aplikaci, která je zajímavé hlavně `for` smyčky v `reduction_sum_gpu_kernel` funkce. Určuje, na základě stromu paralelní snížení, který se spouští na GPU.  
  
### <a name="to-debug-the-cpu-code"></a>Pokud chcete ladit kód procesoru  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro **AMPMapReduce**a potom zvolte **vlastnosti**.  
  
2.  V **stránky vlastností** dialogovém **vlastnosti konfigurace**, zvolte **ladění**. Ověřte, že **místní ladicí program Windows** vybrán **ladicí program ke spuštění** seznamu.  
  
3.  Vrátit do editoru kódu.  
  
4.  Nastavte zarážky na řádky kódu vidět na následujícím obrázku (přibližně řádky 67 řádku 70).  
  
     ![Procesor zarážky](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
Procesor zarážky  
  
5.  Na řádku nabídek zvolte **ladění**, **spustit ladění**.  
  
6.  V **místní hodnoty –** okně sledovat hodnota `stride_size` dokud nebude dosaženo zarážek na řádku 70.  
  
7.  Na řádku nabídek zvolte **ladění**, **Zastavte ladění**.  
  
## <a name="debugging-the-gpu-code"></a>Ladění kódu GPU  
 V této části ukazuje, jak k ladění kódu GPU, což je kód obsažené v `sum_kernel_tiled` funkce. Kódu GPU vypočítá součet celých čísel pro každý "blok" paralelně.  
  
### <a name="to-debug-the-gpu-code"></a>Ladění kódu GPU  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro **AMPMapReduce**a potom zvolte **vlastnosti**.  
  
2.  V **stránky vlastností** dialogovém **vlastnosti konfigurace**, zvolte **ladění**.  
  
3.  V **ladicí program ke spuštění** seznamu, vyberte **místní ladicí program Windows**.  
  
4.  V **ladicí program typu** seznamu, ověřte, že **automaticky** je vybrána.

    **Automatické** je výchozí hodnota. Před Windows 10 **GPU pouze** je požadovaná hodnota místo **automaticky**.
  
5.  Vyberte **OK** tlačítko.  
  
6.  Nastavte zarážky v řádku 30, jak je znázorněno na následujícím obrázku.  
  
     ![Grafický procesor zarážky](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
Grafický procesor zarážek  
  
7.  Na řádku nabídek zvolte **ladění**, **spustit ladění**. Zarážky v kódu procesoru na řádcích 67 a 70 nebudou provedeny během GPU ladění, protože tyto řádky kódu jsou spouštěny na procesoru.  
  
### <a name="to-use-the-gpu-threads-window"></a>K použití okna vláken GPU  
  
1.  Otevření okna vláken GPU v řádku nabídek zvolte **ladění**, **Windows**, **vláken GPU**.  
  
     Si můžete prohlédnout stav vláken GPU v okna vláken GPU, který se zobrazí.  
  
2.  Ukotvení okna vláken GPU v dolní části sady Visual Studio. Vyberte **rozbalte přepínač vlákno** tlačítko pro zobrazení textového pole dlaždice a přístup z více vláken. Okna vláken GPU zobrazuje celkový počet vláken GPU aktivní i blokované, jak je znázorněno na následujícím obrázku.  
  
     ![Vlákna GPU – okno s 4 aktivních podprocesů](../../parallel/amp/media/campc.png "campc")  
Vlákna GPU – okno  
  
     Existují 313 dlaždice přidělené pro tento výpočet. Každou dlaždici obsahuje 32 vláken. Protože místní ladění GPU proběhne softwaru emulátoru, existují čtyři active vláken GPU. Čtyři vláken současně provést podle pokynů a pak přesunout společně k další instrukce.  
  
     V případě okna vláken GPU existují aktivní čtyři vláken GPU a 28 vláken GPU blokováno v [tile_barrier::wait –](reference/tile-barrier-class.md#wait) příkaz definované v o řádku 21 (`t_idx.barrier.wait();`). Všechny 32 vláken GPU patří do první dlaždice `tile[0]`. Šipka odkazuje na řádek, který obsahuje aktuální vlákno. Chcete-li přepnout na jiné vlákno, použijte jednu z následujících metod:  

  
    -   V řádku pro vlákno přejdete do okna vláken GPU otevřete místní nabídku a vyberte **přepnout na vlákno**. Pokud řádek představuje více než jedno vlákno, se změní první vlákno podle souřadnice přístup z více vláken.  
  
    -   Zadejte hodnoty dlaždice a vlákno podprocesu v příslušných textových polí a potom vyberte **přepínač vlákno** tlačítko.  
  
     Okno zásobník volání zobrazí zásobník volání aktuálního vlákna GPU.  
  
### <a name="to-use-the-parallel-stacks-window"></a>Použití okna paralelní zásobníky  
  
1.  Chcete-li otevřít okno Paralelní zásobníky v řádku nabídek zvolte **ladění**, **Windows**, **paralelní zásobníky**.  
  
     Okna paralelní zásobníky můžete současně kontrolovat rámce zásobníku více vláken GPU.  
  
2.  Ukotvení okna paralelní zásobníky v dolní části sady Visual Studio.  
  
3.  Ujistěte se, že **vláken** je vybrán v seznamu v levém horním rohu. Na následujícím obrázku ukazuje okna paralelní zásobníky zásobník volání zaměřuje zobrazení vláken GPU, které jste viděli v okna vláken GPU.  
  
     ![Okno Paralelní zásobníky s 4 aktivních podprocesů](../../parallel/amp/media/campd.png "campd")  
Okno Paralelní zásobníky  
  
     32 vláken se z `_kernel_stub` k příkazu lambda v `parallel_for_each` volání funkce a potom `sum_kernel_tiled` funkce, kde dochází k paralelní snížení. do mají zvýšily 28 mimo 32 vláken [tile_barrier::wait –](reference/tile-barrier-class.md#wait) příkaz a zůstanou blokované na řádku 22, zatímco jiná 4 vlákna zůstala aktivní v `sum_kernel_tiled` funkce na řádku 30.  

  
     Vlastnosti vlákna GPU, které jsou k dispozici v okna vláken GPU v bohaté popis dat okna paralelní zásobníky si můžete prohlédnout. Chcete-li to provést, umístěte ukazatel myši na rámec zásobníku **sum_kernel_tiled**. Následující obrázek znázorňuje popis dat.  
  
     ![Popis dat pro okna paralelní zásobníky](../../parallel/amp/media/campe.png "campe")  
Vlákna GPU popis dat  
  
     Další informace o okna paralelní zásobníky najdete v tématu [použití okna paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
### <a name="to-use-the-parallel-watch-window"></a>Použití okna paralelního sledování  
  
1.  Otevření okna paralelního sledování v řádku nabídek zvolte **ladění**, **Windows**, **paralelního sledování**, **paralelní sledování 1**.  
  
     Okna paralelního sledování můžete zkontrolovat hodnoty výrazu napříč více vláken.  
  
2.  Okno ukotvení paralelní 1 sledovat v dolní části sady Visual Studio. Existují 32 řádky v tabulce okna paralelního sledování. Každý odpovídá, se nacházely okna vláken GPU a okna paralelní zásobníky vlákna GPU. Teď můžete zadat výrazy jehož hodnoty, které chcete zkontrolovat mezi všechny 32 vláken GPU.  
  
3.  Vyberte **Přidat kukátko** záhlaví sloupce, zadejte `localIdx`a potom vyberte klávesu Enter.  
  
4.  Vyberte **Přidat kukátko** znovu záhlaví sloupce, typ `globalIdx`a potom vyberte klávesu Enter.  
  
5.  Vyberte **Přidat kukátko** znovu záhlaví sloupce, typ `localA[localIdx[0]]`a potom vyberte klávesu Enter.  
  
     Můžete řadit podle zadaného výrazu výběrem jeho odpovídající záhlaví sloupce.  
  
     Vyberte **localA [localIdx [0]]** záhlaví sloupce seřadí hodnoty ve sloupci. Následující obrázek znázorňuje výsledky řazení podle **localA [localIdx [0]]**.  
  
     ![Paralelní kukátko – okno s výsledky seřazené](../../parallel/amp/media/campf.png "campf")  
 Řazení výsledků  
  
     Obsah okna paralelního sledování můžete exportovat do Excelu zvolením tlačítka aplikace Excel a pak vyberete **otevřít v aplikaci Excel**. Pokud máte ve svém vývojovém počítači nainstalovanou aplikaci Excel, otevře se listu aplikace Excel, který obsahuje obsah.  
  
6.  V pravém horním rohu okna paralelního sledování je ovládací prvek filtru, který můžete použít k filtrování obsahu pomocí logických výrazů. Zadejte `localA[localIdx[0]] > 20000` v textu ovládací prvek filtru pole a zvolte klávesu Enter.  
  
     Okno teď obsahuje pouze vláken, na kterém `localA[localIdx[0]]` hodnota je větší než 20000. Obsah je stále seřazené podle `localA[localIdx[0]]` sloupec, který je řazení akcí, které jste provedli dříve.  
  
## <a name="flagging-gpu-threads"></a>Označování vláken GPU  
 Můžete označit konkrétní vláken GPU označíte příznakem je v okna vláken GPU, okna paralelního sledování nebo popis dat v okna paralelní zásobníky. Pokud v řádku v okna vláken GPU obsahuje více než jedno vlákno, tento řádek označování příznaky všechna vlákna, které jsou obsaženy v řádku.  
  
### <a name="to-flag-gpu-threads"></a>Chcete-li příznak vláken GPU  
  
1.  Vyberte **[vlákno]** záhlaví sloupce v okně paralelní sledování 1 seřadit podle dlaždice a indexem přístup z více vláken.  
  
2.  Na řádku nabídek zvolte **ladění**, **pokračovat**, což způsobí, že čtyři vláken, byly active pokroku na další bariéry (definovanou v řádku 32 AMPMapReduce.cpp).  
  
3.  Zvolte symbol příznak na levé straně na řádek, který obsahuje čtyři vláken, které jsou nyní aktivní.  
  
     Následující obrázek znázorňuje čtyři active označení vlákna v okna vláken GPU.  
  
     ![Vlákna GPU – okno s označení vlákna](../../parallel/amp/media/campg.png "campg")  
Aktivních vláken v okna vláken GPU  
  
     Okna paralelního sledování a popis dat okna paralelní zásobníky obou indikovat označení vlákna.  
  
4.  Pokud se chcete zaměřit na čtyři vláken, které jste příznakem, můžete zobrazit v vláken GPU, paralelní sledování a Paralelní zásobníky windows pouze označení vlákna.  
  
     Zvolte příznakem jenom zobrazit tlačítko na žádném systému windows nebo na **ladění umístění** panelu nástrojů. Následující obrázek znázorňuje tlačítko příznakem jenom zobrazit na **ladění umístění** panelu nástrojů.  
  
     ![Ladění umístění panelu nástrojů zobrazí pouze označené ikonou](../../parallel/amp/media/camph.png "camph")  
Zobrazit pouze příznakem tlačítko  
  
     Okna vláken GPU paralelního sledování a Paralelní zásobníky nyní zobrazí pouze označení vlákna.  
  
## <a name="freezing-and-thawing-gpu-threads"></a>Zmrazení a uvolnění vláken GPU  
 Lze ukotvit (Pozastavit) a uvolnění vláken GPU (pokračovat) z okna vláken GPU nebo okna paralelního sledování. Lze ukotvit a uvolnění procesoru vláken stejným způsobem jako; informace najdete v tématu [postupy: použití okna vláken](/visualstudio/debugger/how-to-use-the-threads-window).  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>Freeze – a odblokování vláken GPU  
  
1.  Vyberte **příznakem jenom zobrazit** tlačítko zobrazíte všechna vlákna.  
  
2.  Na řádku nabídek zvolte **ladění**, **pokračovat**.  
  
3.  Otevřete místní nabídku pro aktivní řádek a potom zvolte **Freeze**.  
  
     Na následujícím obrázku okna vláken GPU ukazuje, že všechny čtyři vláken zmrazené.  
  
     ![Vlákna GPU windows zobrazující ukotvené vláken](../../parallel/amp/media/campk.png "campk")  
Ukotvené vláken v okna vláken GPU  
  
     Podobně okna paralelního sledování ukazuje, že všechny čtyři vláken zmrazené.  
  
4.  Na řádku nabídek zvolte **ladění**, **pokračovat** umožňující další čtyři vláken GPU průběhu po bariéry na řádku 22 a dosáhnout zarážek na řádku 30. Okna vláken GPU zobrazuje, zda zůstává zachována čtyři dříve ukotvené vláken ukotvené a v aktivním stavu.  
  
5.  Na řádku nabídek zvolte **ladění**, **pokračovat**.  
  
6.  Z okna paralelního sledování můžete také uvolnit jednotlivcům nebo více vláken GPU.  
  
### <a name="to-group-gpu-threads"></a>Do skupiny vláken GPU  
  
1.  V místní nabídce pro jednu z vláken v **vláken GPU** okně zvolte **Group By**, **adresu**.  
  
     Vláken v okna vláken GPU jsou seskupené podle adres. Adresa odpovídá instrukce v zpětný překlad, kde se nachází každou skupinu vláken. 24 vláken jsou na řádku 22 kde [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait) se spustí. 12 vláken jsou u instrukce pro bariéry na řádku 32. Jsou označeny čtyři tyto vláken. Vlákna osm jsou u zarážky na řádku 30. Čtyři tyto vláken zmrazené. Následující obrázek znázorňuje seskupené vláken v okna vláken GPU.  

  
     ![Vlákna GPU – okno s vlákny seskupené podle adresy](../../parallel/amp/media/campl.png "campl")  
Seskupené vláken v okna vláken GPU  
  
2.  Můžete také provést **Group By** operaci otevřením místní nabídku pro data mřížky okna paralelního sledování výběr **Group By**a pak vyberete položku nabídky, která odpovídá způsob k seskupení vláken.  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>Spuštění všechna vlákna do určitého umístění v kódu  
 Spustit všechna vlákna v dané dlaždici na řádek, který obsahuje kurzor pomocí **spustit aktuální dlaždice pro kurzor**.  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Aby se spouštěly všechna vlákna umístění označena kurzoru  
  
1.  V místní nabídce pro ukotvené vlákna, zvolte **odblokování**.  
  
2.  V editoru kódu, umístěte kurzor v řádku 30.  
  
3.  V místní nabídce pro editoru kódu, zvolte **spustit aktuální dlaždice pro kurzor**.  
  
     24 vláken, které byly dříve blokováno v bariéry na řádku 21 mít zvýšily na řádek 32. To je ukázáno v **vláken GPU** okno.  
  
## <a name="see-also"></a>Viz také  
 [Přehled produktu C++ AMP](../../parallel/amp/cpp-amp-overview.md)   
 [Ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code)   
 [Postupy: použití okna vláken GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
 [Postupy: použití okna paralelního sledování](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
 [Analýza kódu C++ AMP s vizualizér souběžnosti](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

