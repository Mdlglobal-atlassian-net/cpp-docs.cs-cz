---
title: 'Návod: Ladění aplikace C++ amp'
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 0c9fb5588cfd44c83d8fe72c7c4aede0fedab672
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69631589"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Návod: Ladění aplikace C++ amp

Toto téma ukazuje, jak ladit aplikaci, která používá C++ akcelerované paralelismuy (C++ amp) k využití výhod grafického procesoru (GPU). Používá program s paralelním omezením, který sečte velké pole celých čísel. Tento návod znázorňuje následující úlohy:

- Spouští se ladicí program GPU.

- Kontrola vláken GPU v okně vláken GPU.

- Použití okna **paralelní zásobníky** k současnému sledování zásobníků volání více vláken GPU.

- Pomocí okna **paralelní kukátko** můžete kontrolovat hodnoty jednoho výrazu v několika vláknech současně.

- Označování, zamrznutí, rozmrazování a seskupení vláken GPU.

- Spouštění všech vláken dlaždice do konkrétního umístění v kódu.

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod:

- Přečtěte si [ C++ přehled amp](../../parallel/amp/cpp-amp-overview.md).

- Ujistěte se, že v textovém editoru jsou zobrazena čísla řádků. Další informace najdete v tématu [jak: Zobrazení čísel řádků v editoru](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)

- Ujistěte se, že používáte aspoň Windows 8 nebo Windows Server 2012 pro podporu ladění v emulátoru softwaru. 

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>K vytvoření ukázkového projektu

Pokyny k vytvoření projektu se liší v závislosti na verzi sady Visual Studio, kterou používáte. Ujistěte se, že máte v levé horní části této stránky zvolenou správnou verzi.

::: moniker range="vs-2019"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>Vytvoření ukázkového projektu v aplikaci Visual Studio 2019

1. Na panelu nabídek vyberte možnost **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**. 

1. Z filtrovaného seznamu typů projektů zvolte Konzolová **aplikace** a pak zvolte **Další**. Na další stránce `AMPMapReduce` do pole **název** zadejte název projektu a v případě potřeby zadejte umístění projektu.

   ![Pojmenovat projekt](../../build/media/mathclient-project-name-2019.png "Pojmenovat projekt")

1. Pro vytvoření projektu klienta klikněte na tlačítko **vytvořit** .

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>Vytvoření ukázkového projektu v aplikaci Visual Studio 2017 nebo Visual Studio 2015

1. Spusťte Visual Studio.

1. Na panelu nabídek vyberte **soubor** > **Nový** > **projekt**.

1. V části **nainstalováno** v podokně šablony vyberte **možnost C++Visual** .

1. Zvolte **Konzolová aplikace Win32**, `AMPMapReduce` do pole **název** zadejte a pak klikněte na tlačítko **OK** .

1. Zvolte **Další** tlačítko.

1. Zrušte zaškrtnutí políčka **Předkompilovaná hlavička** a pak klikněte na tlačítko **Dokončit** .

1. V **Průzkumník řešení**z projektu odstraňte *stdafx. h*, *targetver. h*a *stdafx. cpp* .

::: moniker-end

Generace

8. Otevřete AMPMapReduce. cpp a nahraďte jeho obsah následujícím kódem.

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

9. V řádku nabídek vyberte **soubor** > **Uložit vše**.

10. V **Průzkumník řešení**otevřete místní nabídku pro **AMPMapReduce**a pak zvolte **vlastnosti**.

11. V dialogovém okně **stránky vlastností** v části **Vlastnosti konfigurace**vyberte možnost **C/C++**  > předkompilované hlavičky.

12. Pro vlastnost **předkompilované hlavičky** vyberte **Nepoužívat předkompilované hlavičky**a pak klikněte na tlačítko **OK** .

13. Na řádku nabídek klikněte na **sestavit** > sestavení**řešení**.

## <a name="debugging-the-cpu-code"></a>Ladění kódu CPU

V tomto postupu použijete místní ladicí program systému Windows k ujištění, že kód CPU v této aplikaci je správný. Segment kódu CPU v této aplikaci, který je obzvláště zajímavý, je `for` smyčka `reduction_sum_gpu_kernel` ve funkci. Řídí paralelní snižování na základě stromové struktury, které se spouští na GPU.

### <a name="to-debug-the-cpu-code"></a>Ladění kódu CPU

1. V **Průzkumník řešení**otevřete místní nabídku pro **AMPMapReduce**a pak zvolte **vlastnosti**.

2. V dialogovém okně **stránky vlastností** v části **Vlastnosti konfigurace**vyberte možnost **ladění**. Ověřte, že je v **ladicím programu pro spuštění** v seznamu vybraná možnost **místní ladicí program Windows** .

3. Vraťte se do **editoru kódu**.

4. Nastavte zarážky na řádcích kódu, které jsou znázorněny na následujícím obrázku (přibližně řádky 67 řádek 70).

   ![Zarážky procesoru](../../parallel/amp/media/campcpubreakpoints.png "Zarážky procesoru") <br/>
   Zarážky procesoru

5. Na panelu nabídek vyberte **ladit** > **Spustit ladění**.

6. V okně **místní** hodnoty Sledujte hodnotu `stride_size` , dokud se nedosáhne zarážky na řádku 70.

7. Na řádku nabídek klikněte na položku **ladit** > **Zastavit ladění**.

## <a name="debugging-the-gpu-code"></a>Ladění kódu GPU

V této části se dozvíte, jak ladit kód GPU, což je kód obsažený `sum_kernel_tiled` ve funkci. Kód GPU vypočítá součet celých čísel pro každý blok paralelně.

### <a name="to-debug-the-gpu-code"></a>Ladění kódu GPU

1. V **Průzkumník řešení**otevřete místní nabídku pro **AMPMapReduce**a pak zvolte **vlastnosti**.

2. V dialogovém okně **stránky vlastností** v části **Vlastnosti konfigurace**vyberte možnost **ladění**.

3. V seznamu **Spustit ladicí program** vyberte **místní ladicí program systému Windows**.

4. V seznamu **Typ ladicího programu** ověřte, zda je vybrána možnost **automaticky** .

    Výchozí hodnota je **auto** . Před Windows 10 je **grafický procesor jenom** požadovaná hodnota místo **auto**.

5. Zvolte **OK** tlačítko.

6. Nastavte zarážku na řádku 30, jak je znázorněno na následujícím obrázku.

   ![Zarážky GPU](../../parallel/amp/media/campgpubreakpoints.png "Zarážky GPU") <br/>
   Zarážka GPU

7. Na panelu nabídek vyberte **ladit** > **Spustit ladění**. Zarážky v kódu CPU na řádcích 67 a 70 nejsou spouštěny během ladění GPU, protože tyto řádky kódu jsou spouštěny na procesoru.

### <a name="to-use-the-gpu-threads-window"></a>Použití okna vlákna GPU

1. Chcete-li otevřít okno **vlákna GPU** , v panelu nabídek vyberte možnost **ladit** > **vlákna GPU** **systému Windows** > .

   Můžete zkontrolovat stav vláken GPU v zobrazeném okně **vlákna GPU** .

2. Ukotvěte okno **vlákna GPU** v dolní části sady Visual Studio. Chcete-li zobrazit textová pole dlaždice a vlákno, klikněte na tlačítko **Rozbalit přepínač vlákna** . Okno **vlákna GPU** zobrazuje celkový počet aktivních a blokovaných vláken GPU, jak je znázorněno na následujícím obrázku.

   ![Okno vláken GPU se 4 aktivními vlákny](../../parallel/amp/media/campc.png "Okno vláken GPU se 4 aktivními vlákny") <br/>
   Okno vláken GPU

   Pro tento výpočet jsou přiřazeny 313 dlaždice. Každá dlaždice obsahuje 32 vláken. Vzhledem k tomu, že dojde k místnímu ladění GPU na emulátoru softwaru, existují čtyři aktivní vlákna GPU. Čtyři vlákna provádějí tyto pokyny současně a pak se vzájemně přesunou k další instrukci.

   V okně **vlákna GPU** jsou aktivní čtyři vlákna GPU a 28 vláken GPU se zablokovala v příkazu [tile_barrier:: wait](reference/tile-barrier-class.md#wait) , který je definován na řádku 21`t_idx.barrier.wait();`(). Všechna 32 vláken GPU patří do první dlaždice `tile[0]`. Šipka odkazuje na řádek, který obsahuje aktuální vlákno. Chcete-li přepnout na jiné vlákno, použijte jednu z následujících metod:

    - V řádku vlákna, na které chcete přejít v okně **vlákna GPU** otevřete místní nabídku a vyberte možnost **Přepnout do vlákna**. Pokud řádek představuje více než jedno vlákno, přejdete do prvního vlákna podle souřadnic vlákna.

    - Do příslušných textových polí zadejte dlaždice a hodnoty vlákna vlákna a pak klikněte na tlačítko **Přepnout vlákno** .

   Okno **zásobník volání** zobrazuje zásobník volání aktuálního vlákna GPU.

### <a name="to-use-the-parallel-stacks-window"></a>Použití okna Paralelní zásobníky

1. Chcete-li otevřít okno **paralelní zásobníky** , v panelu nabídek vyberte možnost **ladit** > **paralelní zásobníky** **systému Windows** > .

   Okno **paralelní zásobníky** můžete použít k současné kontrole snímků zásobníku více vláken GPU.

2. Ukotvěte okno **paralelní zásobníky** v dolní části sady Visual Studio.

3. Ujistěte se, že je v seznamu v levém horním rohu vybraná možnost **vlákna** . Na následujícím obrázku okno **paralelní zásobníky** zobrazuje prioritní zobrazení zásobníku volání GPU, které jste viděli v okně **vláken GPU** .

   ![Okno paralelní zásobníky se čtyřmi aktivními vlákny](../../parallel/amp/media/campd.png "Okno paralelní zásobníky se čtyřmi aktivními vlákny") <br/>
   Okno paralelní zásobníky

   32 vláken `_kernel_stub` do příkazu lambda `parallel_for_each` ve `sum_kernel_tiled` volání funkce a následně do funkce, kde dojde k paralelnímu zmenšení. 28 z vláken 32 bylo dokončeno na příkaz [tile_barrier:: wait](reference/tile-barrier-class.md#wait) a zůstane blokované na řádku 22, zatímco ostatní 4 vlákna zůstávají aktivní ve `sum_kernel_tiled` funkci na řádku 30.

   Můžete zkontrolovat vlastnosti vlákna GPU, které jsou k dispozici v okně **vlákna GPU** v bohatém DataTip okna **paralelní zásobníky** . Chcete-li to provést, umístěte ukazatel myši na rámec zásobníku **sum_kernel_tiled**. Na následujícím obrázku je znázorněno DataTip.

   ![Okno DataTip pro paralelní zásobníky](../../parallel/amp/media/campe.png "Okno DataTip pro paralelní zásobníky") <br/>
   DataTip vlákna GPU

   Další informace o okně **paralelní zásobníky** najdete v tématu [použití okna Paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="to-use-the-parallel-watch-window"></a>Použití paralelního okno Kukátko

1. Chcete-li otevřít okno **paralelní kukátko** , v panelu nabídek vyberte možnost **ladit** > **Windows** > **paralelní sledování** > **paralelní sledování 1**.

   Můžete použít okno **paralelní kukátko** pro kontrolu hodnot výrazu ve více vláknech.

2. Ukotvěte okno **paralelní kukátko 1** k dolnímu okraji sady Visual Studio. V tabulce okna **paralelního kukátka** jsou 32 řádky. Každý odpovídá vláknu GPU, který se zobrazil v okně vlákna GPU a v okně **paralelní zásobníky** . Nyní můžete zadat výrazy, jejichž hodnoty chcete kontrolovat v rámci všech 32 vláken GPU.

3. Vyberte záhlaví sloupce **Přidat kukátko** , zadejte `localIdx`a pak stiskněte klávesu **ENTER** .

4. Znovu vyberte záhlaví sloupce **Přidat kukátko** , zadejte `globalIdx`a potom zvolte klávesu **ENTER** .

5. Znovu vyberte záhlaví sloupce **Přidat kukátko** , zadejte `localA[localIdx[0]]`a potom zvolte klávesu **ENTER** .

   Můžete řadit podle zadaného výrazu výběrem odpovídajícího záhlaví sloupce.

   Vyberte záhlaví sloupce **Local-[localIdx [0]]** pro řazení sloupce. Následující ilustrace znázorňuje výsledky řazení podle **lokální hodnoty [localIdx [0]]** .

   ![Paralelní okno kukátko s seřazenými výsledky](../../parallel/amp/media/campf.png "Paralelní okno kukátko s seřazenými výsledky") <br/>
   Výsledky řazení

   Obsah můžete exportovat v okně **paralelní kukátko** do aplikace Excel tak, že kliknete na tlačítko **Excel** a pak zvolíte možnost **otevřít v aplikaci Excel**. Pokud máte ve vývojovém počítači nainstalovaný Excel, otevře se excelový list, který obsahuje obsah.

6. V pravém horním rohu okna **paralelní kukátko** je ovládací prvek filtru, který můžete použít k filtrování obsahu pomocí logických výrazů. Do `localA[localIdx[0]] > 20000` textového pole Filtr zadejte a potom zvolte klávesu **ENTER** .

   Okno nyní obsahuje pouze vlákna, na kterých `localA[localIdx[0]]` je hodnota větší než 20000. Obsah je stále seřazen podle `localA[localIdx[0]]` sloupce, což je akce řazení, kterou jste provedli dříve.

## <a name="flagging-gpu-threads"></a>Označení vláken GPU

Konkrétní vlákna GPU můžete označit příznakem v okně **vlákna GPU** , v okně **paralelní kukátko** nebo v DataTip v okně **paralelní zásobníky** . Pokud řádek v okně vláken GPU obsahuje více než jedno vlákno, označí tento řádek všechna vlákna, která jsou obsažena na řádku.

### <a name="to-flag-gpu-threads"></a>Označení vláken GPU

1. V okně **paralelní kukátko 1** vyberte záhlaví sloupce **[Thread]** , které chcete seřadit podle indexu dlaždic a indexu vlákna.

2. Na panelu nabídek vyberte možnost**pokračovat**v **ladění** > , což způsobí, že čtyři vlákna, která byla aktivní pro průběh další bariéry (definované na řádku 32 AMPMapReduce. cpp).

3. Na levé straně řádku, který obsahuje čtyři aktuálně aktivní vlákna, vyberte symbol označení.

   Následující obrázek znázorňuje čtyři aktivní vlákna označená příznakem v okně **vláken GPU** .

   ![Okno vláken GPU s vlákny s příznakem](../../parallel/amp/media/campg.png "Okno vláken GPU s vlákny s příznakem") <br/>
   Aktivní vlákna v okně vláken GPU

   Okno **paralelního sledování** a DataTip okna **paralelní zásobníky** označují vlákna označená příznakem.

4. Pokud se chcete zaměřit na čtyři vlákna, která jste označili příznakem, můžete se rozhodnout zobrazit v oknech **vlákna GPU**, **paralelní sledování**a **paralelní zásobníky** pouze vlákna s příznakem.

   V libovolném z oken nebo na panelu nástrojů **umístění ladění** vyberte tlačítko **Zobrazit pouze označené příznakem** . Následující ilustrace znázorňuje tlačítko **Zobrazit pouze s příznakem** na panelu nástrojů **umístění ladění** .

   ![Panel nástrojů umístění ladění s ikonou zobrazit jenom ikonu s příznakem](../../parallel/amp/media/camph.png "Panel nástrojů umístění ladění s ikonou zobrazit jenom ikonu s příznakem") <br/>
   **Zobrazit tlačítko pouze s příznakem**

   Okna **GPU**, **paralelní sledování**a **paralelní zásobníky** teď zobrazují pouze vlákna označená příznakem.

## <a name="freezing-and-thawing-gpu-threads"></a>Mrznutí a rozmrazení vláken GPU

Vlákna GPU můžete zablokovat (pozastavit) a uvolnit (obnovit) z okna **vlákna GPU** nebo okna **paralelního sledování** . Můžete zablokovat a rozmrazit vlákna procesoru stejným způsobem; informace naleznete v tématu [How to: Použijte okno](/visualstudio/debugger/how-to-use-the-threads-window)vlákna.

### <a name="to-freeze-and-thaw-gpu-threads"></a>Zablokování a odmrazení vláken GPU

1. Kliknutím na tlačítko **Zobrazit pouze s příznakem** zobrazíte všechna vlákna.

2. Na panelu nabídek vyberte možnost**pokračovat**v **ladění** > .

3. Otevřete místní nabídku pro aktivní řádek a pak zvolte možnost **ukotvit**.

   Následující obrázek okna **vlákna GPU** ukazuje, že jsou zmrazena všechna čtyři vlákna.

   ![Vlákna GPU okna zobrazující zmrazená vlákna](../../parallel/amp/media/campk.png "Vlákna GPU okna zobrazující zmrazená vlákna") <br/>
   Zmrazená vlákna v okně **vláken GPU**

   Podobně okno **paralelní kukátko** ukazuje, že jsou zmrazena všechna čtyři vlákna.

4. Na panelu nabídek vyberte možnost **ladit** > **pokračovat** a umožněte, aby další čtyři vlákna GPU probíhala po bariérě na řádku 22 a aby se dosáhlo zarážky na řádku 30. Okno **vlákna GPU** ukazuje, že čtyři dříve zmrazená vlákna zůstala zmrazená a v aktivním stavu.

5. Na řádku nabídek klikněte na položku **ladit**, **pokračovat**.

6. V okně **paralelní kukátko** můžete také odblokovat jednotlivá vlákna nebo více vláken GPU.

### <a name="to-group-gpu-threads"></a>Seskupení vláken GPU

1. V místní nabídce pro jedno z podprocesů v okně **vlákna GPU** vyberte **Seskupit podle**, **adresa**.

   Vlákna v okně **vláken GPU** se seskupují podle adres. Adresa odpovídá instrukci v zpětném překladu, kde je umístěna každá skupina vláken. 24 vláken na řádku 22, kde je spuštěna [Metoda tile_barrier:: wait](reference/tile-barrier-class.md#wait) . 12 vláken je v pokynech pro bariéru na řádku 32. Čtyři z těchto vláken jsou označena příznakem. Osm vláken na zarážce na řádku 30. Čtyři z těchto vláken jsou zmrazeny. Následující ilustrace znázorňuje seskupená vlákna v okně **vláken GPU** .

   ![Okno vláken GPU s vlákny seskupenými podle adresy](../../parallel/amp/media/campl.png "Okno vláken GPU s vlákny seskupenými podle adresy") <br/>
   Seskupená vlákna v okně **vláken GPU**

2. Operaci **Seskupit podle** můžete také provést tak, že otevřete místní nabídku pro datovou mřížku okna **paralelní sledování** , zvolíte možnost **Seskupit podle**a pak zvolíte položku nabídky, která odpovídá způsobu, jakým chcete seskupit vlákna.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>Spuštění všech vláken do konkrétního umístění v kódu

Všechna vlákna v dané dlaždici se spouštějí na řádek, který obsahuje kurzor pomocí **kurzoru spustit aktuální dlaždici**.

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Spuštění všech vláken do umístění označeného kurzorem

1. V místní nabídce pro zmrazená vlákna klikněte na možnost **rozmrazit**.

2. V **editoru kódu**umístěte kurzor na řádek 30.

3. V místní nabídce **editoru kódu**vyberte možnost **Spustit aktuální dlaždici a umístěte kurzor**.

   24 vláken, která byla dříve blokovaná na bariérě na řádku 21, probíhala na řádku 32. To se zobrazuje v okně **vlákna GPU** .

## <a name="see-also"></a>Viz také:

[Přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md)<br/>
[Ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[Postupy: Použití okna vláken GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[Postupy: Použití okna Paralelní sledování](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[Analýza C++ kódu amp pomocí Vizualizátor souběžnosti](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
