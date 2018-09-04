---
title: 'Návod: Ladění aplikace C++ AMP | Dokumentace Microsoftu'
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
ms.openlocfilehash: 3a8c5affeaee73be7dd464ea44ea62db35257f7b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689753"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Návod: Ladění aplikace C++ AMP
Toto téma ukazuje, jak ladit aplikaci, která používá C++ Accelerated Massive Parallelism (C++ AMP) využít grafický procesor (GPU). Využívá paralelní snížení program, který shrnuje velkého pole celých čísel. Tento návod znázorňuje následující úlohy:  
  
- Spouští se ladicí program GPU.  
  
- Kontroluje se vlákna GPU v okně vlákna GPU.  
  
- Použití **paralelní zásobníky** okno současně zachovávají zásobníky volání z více vláken GPU.  
  
- Použití **paralelní sledování** okna zkontrolujte hodnoty jeden výraz napříč několika vlákny za stejnou dobu.  
  
- Nastavení příznaku, zamrzá, uvolnění a seskupení vlákna GPU.  
  
- Spuštění všech vláken dlaždice do určitého umístění v kódu.  
  
## <a name="prerequisites"></a>Požadavky  
 
Před zahájením tohoto návodu:  
  
- Čtení [přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
- Ujistěte se, že tento řádek jsou čísla zobrazena v textovém editoru. Další informace najdete v tématu [postupy: zobrazení čísel řádků v editoru](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).  
  
- Zajistěte, aby že se systémem Windows 8 nebo Windows Server 2012, v zájmu podpory ladění v softwarovém emulátoru.  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>K vytvoření ukázkového projektu  
  
1. Spusťte sadu Visual Studio.  
  
2. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
3. V části **nainstalováno** v podokně šablony vyberte **Visual C++**.  
  
4. Zvolte **Konzolová aplikace Win32**, typ `AMPMapReduce` v **název** pole a klikněte na tlačítko **OK** tlačítko.  
  
5. Zvolte **Další** tlačítko.  
  
6. Zrušte **Předkompilovaná hlavička** zaškrtněte políčko a klikněte na tlačítko **Dokončit** tlačítko.  
  
7. V **Průzkumníka řešení**, odstraňte stdafx.h targetver.h a stdafx.cpp z projektu.  
  
8. Otevřete AMPMapReduce.cpp a nahraďte jeho obsah následujícím kódem.  
  
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
  
9. V panelu nabídky zvolte **souboru** > **Uložit vše**.  
  
10. V **Průzkumníka řešení**, otevřete místní nabídku pro **AMPMapReduce**a klikněte na tlačítko **vlastnosti**.  
  
11. V **stránky vlastností** dialogovém okně **vlastnosti konfigurace**, zvolte **C/C++** > **předkompilované hlavičky**.  
  
12. Pro **předkompilovaných hlaviček** vlastnosti, vyberte **není použití předkompilovaných hlaviček**a klikněte na tlačítko **OK** tlačítko.  
  
13. V panelu nabídky zvolte **sestavení** > **sestavit řešení**.  
  
## <a name="debugging-the-cpu-code"></a>Ladění kódu procesoru  
 
V tomto postupu použijete místní ladicí program Windows abyste měli jistotu, že je správný kód procesoru v této aplikaci. Segment kódu procesoru v této aplikaci, která je obzvláště zajímavé `for` smyčky v `reduction_sum_gpu_kernel` funkce. Určuje založený na stromové architektuře paralelní redukci, který běží na GPU.  
  
### <a name="to-debug-the-cpu-code"></a>Chcete-li ladit kód procesoru  
  
1. V **Průzkumníka řešení**, otevřete místní nabídku pro **AMPMapReduce**a klikněte na tlačítko **vlastnosti**.  
  
2. V **stránky vlastností** dialogovém okně **vlastnosti konfigurace**, zvolte **ladění**. Ověřte, že **místní ladicí program Windows** výběru v **ladicí program ke spuštění** seznamu.  
  
3. Vraťte se **Editor kódu**.  
  
4. Nastavte zarážky na řádcích kódu je znázorněno na následujícím obrázku (přibližně 67 řádků řádek 70).  
  
     ![Procesor zarážky](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
Procesor zarážky  
  
5. V panelu nabídky zvolte **ladění** > **spustit ladění**.  
  
6. V **lokální** okna, podívejte se hodnotu `stride_size` dokud není dosaženo zarážky na řádku 70.  
  
7. V panelu nabídky zvolte **ladění** > **Zastavit ladění**.  
  
## <a name="debugging-the-gpu-code"></a>Ladění kódu GPU  
 
Tato část ukazuje, jak na ladění kódu GPU, což je kód obsažen v `sum_kernel_tiled` funkce. GPU kód vypočítá součet prvků celých čísel pro každý "blok" paralelně.  
  
### <a name="to-debug-the-gpu-code"></a>Ladění kódu GPU  
  
1. V **Průzkumníka řešení**, otevřete místní nabídku pro **AMPMapReduce**a klikněte na tlačítko **vlastnosti**.  
  
2. V **stránky vlastností** dialogovém okně **vlastnosti konfigurace**, zvolte **ladění**.  
  
3. V **ladicí program ke spuštění** seznamu vyberte **místní ladicí program Windows**.  
  
4. V **typ ladicího programu** seznamu, ověřte, že **automaticky** zaškrtnuto.

    **Automatické** je výchozí hodnota. Před Windows 10 **pouze GPU** je požadovaná hodnota místo **automaticky**.
  
5. Zvolte **OK** tlačítko.  
  
6. Nastavte zarážku na řádky 30, jak je znázorněno na následujícím obrázku.  
  
     ![Zarážky GPU](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
Zarážky GPU  
  
7. V panelu nabídky zvolte **ladění** > **spustit ladění**. Zarážky v kódu procesoru na řádcích 67 a 70 nebudou provedeny během ladění, protože tyto řádky kódu jsou spouštěny na CPU GPU.  
  
### <a name="to-use-the-gpu-threads-window"></a>K použití okna vláken GPU  
  
1. Chcete-li otevřít **vlákna GPU** okna na řádku nabídek zvolte **ladění** > **Windows** > **vlákna GPU**.  
  
     Stav vlákna GPU v si můžete prohlédnout **vlákna GPU** okno, které se zobrazí.  
  
2. Ukotvit **vlákna GPU** okno v dolní části sady Visual Studio. Zvolte **rozbalte přepínač vlákno** tlačítko zobrazíte textová pole a vlákno. **Vlákna GPU** okno zobrazuje celkový počet aktivních a blokovaná vlákna GPU, jak je znázorněno na následujícím obrázku.  
  
     ![Vlákna GPU – okno s 4 aktivní vlákna](../../parallel/amp/media/campc.png "campc")  
Okno vláken GPU  
  
     Existují 313 dlaždice přidělených pro tento výpočet. Každá dlaždice obsahuje 32 vláken. Protože místní ladění GPU na emulátoru softwaru dojde, existují čtyři aktivní vlákna GPU. Čtyři vlákna současného provádění pokynů a poté přesuňte společně do další instrukci.  
  
     V **vlákna GPU** okna, jsou čtyři vlákna GPU aktivní a zablokovaný 28 vlákna GPU [tile_barrier::wait](reference/tile-barrier-class.md#wait) příkaz definovaný na o řádku 21 (`t_idx.barrier.wait();`). Všechny 32 vláken GPU patří do první dlaždice `tile[0]`. Šipka odkazuje na řádek, který zahrnuje aktuální vlákno. Pokud chcete přepnout do jiného vlákna, použijte jednu z následujících metod:  

    - V řádku pro vlákno pro přepnutí do v **vlákna GPU** okno, otevřete místní nabídku a zvolte **přepnout na vlákno**. Pokud řádek představuje více než jedno vlákno, nebudete se přepnout na první vlákno podle souřadnice vlákna.  
  
    - Zadejte hodnoty pole a vlákno vlákna do příslušných textových polí a klikněte na tlačítko **přepínač vlákno** tlačítko.  
  
     **Zásobník volání** v okně se zobrazí zásobník volání aktuálního vlákna GPU.  
  
### <a name="to-use-the-parallel-stacks-window"></a>Použití okna paralelní zásobníky  
  
1. Chcete-li otevřít **paralelní zásobníky** okna na řádku nabídek zvolte **ladění** > **Windows** > **paralelní zásobníky**.  
  
     Můžete použít **paralelní zásobníky** okno současně kontrolovat rámce zásobníku z více vláken GPU.  
  
2. Ukotvit **paralelní zásobníky** okno v dolní části sady Visual Studio.  
  
3. Ujistěte se, že **vlákna** je vybrán v seznamu v levém horním rohu. Na následujícím obrázku **paralelní zásobníky** zobrazení zásobníku volání, zaměřuje vlákna GPU, které jste viděli v okně se zobrazí **vlákna GPU** okna.  
  
     ![Okno paralelních zásobníků s 4 aktivní vlákna](../../parallel/amp/media/campd.png "campd")  
Okno paralelních zásobníků  
  
     32 vláken se nepovedlo z `_kernel_stub` na příkaz lambda v `parallel_for_each` volání funkce a pak `sum_kernel_tiled` funkce, kde dochází k paralelní redukci. 28 mimo 32 vláken pokročila do [tile_barrier::wait](reference/tile-barrier-class.md#wait) příkazu a zůstat blokovaných na řádku 22, zatímco 4 vlákna zůstaly aktivní v `sum_kernel_tiled` funkce na řádku 30.  

     Můžete si prohlédnout vlastnosti vlákna GPU, které jsou k dispozici v **vlákna GPU** okna v bohaté datového tipu sady **paralelní zásobníky** okna. Chcete-li to provést, umístěte ukazatel myši na rámec zásobníku **sum_kernel_tiled**. Následující obrázek znázorňuje DataTip.  
  
     ![Datového tipu pro okna paralelní zásobníky](../../parallel/amp/media/campe.png "campe")  
Vlákna GPU datového tipu  
  
     Další informace o **paralelní zásobníky** okna, naleznete v tématu [použití okna paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
### <a name="to-use-the-parallel-watch-window"></a>Použití okna paralelního sledování  
  
1. Chcete-li otevřít **paralelní sledování** okna na řádku nabídek zvolte **ladění** > **Windows** > **paralelní sledování**  >  **Paralelní sledování 1**.  
  
     Můžete použít **paralelní sledování** okno pro kontrolu hodnot výrazu napříč více vlákny.  
  
2. Ukotvit **paralelního kukátka 1** okno do dolní části sady Visual Studio. Existují 32 řádky v tabulce **paralelní sledování** okna. Každý odpovídá GPU vlákno, které se zobrazovalo v okně vlákna GPU a **paralelní zásobníky** okna. Teď můžete zadat výrazy jehož hodnoty, které chcete kontrolovat napříč všech 32 vláken GPU.  
  
3. Vyberte **Přidat kukátko** záhlaví sloupce, zadejte `localIdx`a klikněte na tlačítko **Enter** klíč.  
  
4. Vyberte **Přidat kukátko** znovu záhlaví sloupců, typ `globalIdx`a klikněte na tlačítko **Enter** klíč.  
  
5. Vyberte **Přidat kukátko** znovu záhlaví sloupců, typ `localA[localIdx[0]]`a klikněte na tlačítko **Enter** klíč.  
  
     Výběrem příslušné záhlaví sloupce můžete řadit podle zadaného výrazu.  
  
     Vyberte **localA [localIdx [0]]** záhlaví sloupce seřadí hodnoty ve sloupci. Následující obrázek ukazuje výsledky řazení podle **localA [localIdx [0]]**.  
  
     ![Paralelního kukátka s seřazených výsledků](../../parallel/amp/media/campf.png "campf")  
 Výsledky řazení  
  
     Můžete exportovat obsah **paralelní sledování** okno do Excelu výběrem **Excel** tlačítko a pak zvolíte **otevřít v aplikaci Excel**. Pokud máte ve svém vývojovém počítači nainstalována aplikace Excel, tím se otevře, který obsahuje obsah Excelového listu.  
  
6. V pravém horním rohu **paralelní sledování** okna, je ovládací prvek filtru, který vám umožní filtrovat obsah pomocí logických operátorů. ENTER `localA[localIdx[0]] > 20000` text filtru ovládací prvek pole a klikněte na tlačítko **Enter** klíč.  
  
     V okně nyní obsahuje pouze vlákna, na kterém `localA[localIdx[0]]` hodnota je větší než 20000. Obsah je pořád seřazené podle `localA[localIdx[0]]` sloupec, který je řazení akce jste provedli dříve.  
  
## <a name="flagging-gpu-threads"></a>Nastavení příznaku vlákna GPU  
 
Můžete označit konkrétní vlákna GPU označením je **vlákna GPU** okně **paralelního sledování** okna nebo datového tipu v **paralelní zásobníky** okno. Pokud řádek v okně vlákna GPU obsahuje více než jedno vlákno, označíte tento řádek označí všechna vlákna, které jsou obsaženy v řádku.  
  
### <a name="to-flag-gpu-threads"></a>Příznak vlákna GPU  
  
1. Vyberte **[vlákno]** záhlaví sloupce v **paralelního kukátka 1** období seřadíte položky podle indexu dlaždice a index podprocesu.  
  
2. V panelu nabídky zvolte **ladění** > **pokračovat**, což způsobí, že čtyři vlákna, které bylo aktivních mohla pokračovat na další odbourejte překážky bránící (definované na řádku 32 AMPMapReduce.cpp).  
  
3. Výběrem symbolu příznak na levé straně řádek, který obsahuje čtyři vlákna, které jsou nyní aktivní.  
  
     Následující obrázek znázorňuje čtyři aktivní vlákna s příznakem v **vlákna GPU** okna.  
  
     ![Okno vláken GPU s vlákna s příznakem](../../parallel/amp/media/campg.png "campg")  
Aktivní vlákna v okně vlákna GPU  
  
     **Paralelní sledování** okno a datového tipu sady **paralelní zásobníky** okno obou označení vlákna s příznakem.  
  
4. Pokud chcete zaměřit na čtyři vlákna, které jste příznakem, můžete zobrazit v **vlákna GPU**, **paralelní sledování**, a **paralelní zásobníky** windows, pouze s příznakem vlákna.  
  
     Zvolte **zobrazit pouze s příznakem** tlačítko na jakémkoli systému windows nebo na **umístění ladění** nástrojů. Je vidět na následujícím obrázku **zobrazit pouze s příznakem** tlačítko **umístění ladění** nástrojů.  
  
     ![Panel nástrojů ladit umístění s ikonou zobrazit pouze označená příznakem](../../parallel/amp/media/camph.png "camph")  
**Zobrazit pouze s příznakem** tlačítko  
  
     Nyní **vlákna GPU**, **paralelní sledování**, a **paralelní zásobníky** windows zobrazit pouze vlákna s příznakem.  
  
## <a name="freezing-and-thawing-gpu-threads"></a>Zmrazení a uvolnění vlákna GPU  
 
Můžete ukotvit (Pozastavit) a uvolnit vlákna GPU (pokračovat) buď z **vlákna GPU** okno nebo **paralelní sledování** okna. Můžete zablokovat a odblokovat vlákna CPU stejným způsobem jako; informace najdete v tématu [postupy: použití okna vláken](/visualstudio/debugger/how-to-use-the-threads-window).  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>Zablokovat a odblokovat vlákna GPU  
  
1. Zvolte **zobrazit pouze s příznakem** tlačítko Zobrazit všechna vlákna.  
  
2. V panelu nabídky zvolte **ladění** > **pokračovat**.  
  
3. Otevřete místní nabídku pro aktivní řádek a pak zvolte **ukotvit**.  
  
     Na následující ilustraci **vlákna GPU** okno zobrazuje, že všechny čtyři vlákna jsou zmražená.  
  
     ![Vlákna GPU windows zobrazující zmrazené vlákna](../../parallel/amp/media/campk.png "campk")  
Zmrazené vlákna **vlákna GPU** okna  
  
     Podobně **paralelní sledování** okno zobrazuje, že všechny čtyři vlákna jsou zmražená.  
  
4. V panelu nabídky zvolte **ladění** > **pokračovat** umožňující další čtyři vlákna GPU průběhu posledních odbourejte překážky bránící na řádku 22 a dosáhnout zarážku na řádky 30. **Vlákna GPU** okno zobrazuje, čtyři dříve zmrazené vlákna zůstaly zamrznuté a v aktivním stavu.  
  
5. V panelu nabídky zvolte **ladění**, **pokračovat**.  
  
6. Z **paralelní sledování** okna, můžete také uvolnit osobu nebo více vláken GPU.  
  
### <a name="to-group-gpu-threads"></a>Do skupiny vláken GPU  
  
1. Na místní nabídku pro jednu z vlákna **vlákna GPU** okně zvolte **Group By**, **adresu**.  
  
     Vlákna **vlákna GPU** okna jsou seskupené podle adres. Adresa odpovídá podle pokynů ve zpětném překladu, ve kterém je každá skupina vlákna umístěna. na řádku 22 jsou vlákna 24 kde [tile_barrier::wait – metoda](reference/tile-barrier-class.md#wait) provádí. 12 vlákna jsou podle instrukce pro odbourejte překážky bránící na řádku 32. Čtyři tato vlákna s příznakem. Osm vlákna jsou na zarážku na řádky 30. Čtyři tato vlákna jsou zmražená. Následující obrázek znázorňuje seskupená vlákna **vlákna GPU** okna.  

     ![Vlákna GPU – okno s vlákny seskupené podle adres](../../parallel/amp/media/campl.png "campl")  
Seskupená vlákna **vlákna GPU** okna  
  
2. Můžete také provést **Group By** operace tak, že otevřete místní nabídku pro mřížky dat **paralelní sledování** okně Výběr **Group By**a následným výběrem možnosti v nabídce Položka, která odpovídá jak mají být seskupeny vlákna.  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>Spuštění všech vláken na konkrétní místo v kódu  
 
Spuštění všech vláken v daném bloku na řádek obsahující kurzor pomocí **spustit aktuální dlaždici do pozice kurzoru**.  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Ke spuštění všech vláken umístění označeny kurzor  
  
1. V místní nabídce pro zmrazené vlákna, zvolte **uvolnit**.  
  
2. V **Editor kódu**, umístěte kurzor na řádku 30.  
  
3. V místní nabídce pro **Editor kódu**, zvolte **spustit aktuální dlaždici ke kurzoru**.  
  
     24 vlákna, které byly dříve blokovány bariéře na řádku 21 pokročila řádek 32. To je ukázáno **vlákna GPU** okna.  
  
## <a name="see-also"></a>Viz také  
 
[Přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md)   
[Ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code)   
[Postupy: použití okna vláken GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
[Postupy: použití okna paralelního sledování](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
[Analýza kódu C++ AMP pomocí Vizualizéru souběžnosti](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)