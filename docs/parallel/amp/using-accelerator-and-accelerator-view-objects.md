---
title: Používání akcelerátoru a objektů accelerator_view
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 80d9c26f636cc736f90eacddea07a8fc31caff93
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512882"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>Používání akcelerátoru a objektů accelerator_view

Třídy akcelerátoru a [](../../parallel/amp/reference/accelerator-class.md) [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) můžete použít k určení zařízení nebo emulátoru, na kterém chcete C++ kód amp spustit. Systém může mít několik zařízení nebo emulátorů, které se liší podle množství paměti, podpory sdílené paměti, podpory ladění nebo podpory pro dvojitou přesnost. C++Akcelerované obrovský paralelismus (C++ amp) poskytuje rozhraní API, která můžete použít k prohlédnutí dostupných akcelerátorů, nastavit jako výchozí, zadat více accelerator_views pro více volání do parallel_for_each a provádět speciální úlohy ladění.

## <a name="using-the-default-accelerator"></a>Použití výchozího akcelerátoru

Modul C++ amp runtime vybere výchozí akcelerátor, pokud nepíšete kód pro výběr konkrétního. Modul runtime zvolí výchozí akcelerátor následujícím způsobem:

1. Pokud aplikace běží v režimu ladění, akcelerátor, který podporuje ladění.

2. V opačném případě akcelerátor, který je určen proměnnou prostředí CPPAMP_DEFAULT_ACCELERATOR, pokud je nastaven.

3. Jinak zařízení, které není emulované.

4. V opačném případě zařízení, které má největší velikost dostupné paměti.

5. V opačném případě zařízení, které není k zobrazení připojeno.

Kromě toho modul runtime určuje `access_type` `access_type_auto` pro výchozí akcelerátor. To znamená, že výchozí akcelerátor používá sdílenou paměť, pokud je podporovaná, a pokud je známá jeho Charakteristika výkonu (šířka pásma a latence), která je stejná jako vyhrazená (nesdílená) paměť.

Můžete určit vlastnosti výchozího akcelerátoru tím, že vytvoříte výchozí akcelerátor a prozkoumáte jeho vlastnosti. Následující příklad kódu vytiskne cestu, velikost paměti akcelerátoru, podporu sdílené paměti, podporu dvojité přesnosti a omezené podpory dvojitých přesností výchozího akcelerátoru.

```cpp
void default_properties() {
    accelerator default_acc;
    std::wcout << default_acc.device_path << "\n";
    std::wcout << default_acc.dedicated_memory << "\n";
    std::wcout << (accs[i].supports_cpu_shared_memory ?
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";
    std::wcout << (accs[i].supports_double_precision ?
        "double precision: true" : "double precision: false") << "\n";
    std::wcout << (accs[i].supports_limited_double_precision ?
        "limited double precision: true" : "limited double precision: false") << "\n";
}
```

### <a name="cppamp_default_accelerator-environment-variable"></a>Proměnná prostředí CPPAMP_DEFAULT_ACCELERATOR

Proměnnou prostředí CPPAMP_DEFAULT_ACCELERATOR můžete nastavit tak, aby určovala `accelerator::device_path` výchozí akcelerátor. Cesta je závislá na hardwaru. Následující kód používá `accelerator::get_all` funkci k načtení seznamu dostupných akcelerátorů a následně zobrazuje cestu a vlastnosti jednotlivých akcelerátorů.

```cpp
void list_all_accelerators()
{
    std::vector<accelerator> accs = accelerator::get_all();

    for (int i = 0; i <accs.size(); i++) {
        std::wcout << accs[i].device_path << "\n";
        std::wcout << accs[i].dedicated_memory << "\n";
        std::wcout << (accs[i].supports_cpu_shared_memory ?
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";
        std::wcout << (accs[i].supports_double_precision ?
            "double precision: true" : "double precision: false") << "\n";
        std::wcout << (accs[i].supports_limited_double_precision ?
            "limited double precision: true" : "limited double precision: false") << "\n";
    }
}
```

## <a name="selecting-an-accelerator"></a>Výběr akcelerátoru

Chcete-li vybrat akcelerátor, použijte `accelerator::get_all` metodu pro načtení seznamu dostupných akcelerátorů a pak vyberte jednu z nich na základě jejích vlastností. Tento příklad ukazuje, jak vybrat akcelerátor, který má nejvíce paměti:

```cpp
void pick_with_most_memory()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];

    for (int i = 0; i <accs.size(); i++) {
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {
            acc_chosen = accs[i];
        }
    }

    std::wcout << "The accelerator with the most memory is "
        << acc_chosen.device_path << "\n"
        << acc_chosen.dedicated_memory << ".\n";
}
```

> [!NOTE]
> Jedním z akcelerátorů, které vrací `accelerator::get_all` , je akcelerátor procesoru. V akcelerátoru procesoru nelze spustit kód. Pokud chcete vyfiltrovat akcelerátor procesoru, porovnejte hodnotu vlastnosti [device_path](reference/accelerator-class.md#device_path) akcelerátoru, který je vrácený `accelerator::get_all` hodnotou akcelerátoru: [: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Další informace najdete v části speciální akcelerátory v tomto článku.

## <a name="shared-memory"></a>Sdílená paměť

Sdílená paměť je paměť, ke které je možné použít procesor i akcelerátor. Použití sdílené paměti eliminuje nebo významně snižuje nároky na kopírování dat mezi CPU a akcelerátorem. I když je paměť sdílená, nelze k ní současně přistupovat pomocí procesoru i akcelerátoru, což způsobí nedefinované chování. Vlastnost akcelerátoru [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) vrací **hodnotu true** , pokud akcelerátor podporuje sdílenou paměť a vlastnost [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) Získá výchozí [access_type](reference/concurrency-namespace-enums-amp.md#access_type) pro přidělenou paměť na `accelerator`– například **pole**s `accelerator`přidružené k objektům nebo `array_view` k objektům přidaným `accelerator`na.

Modul C++ runtime amp automaticky zvolí nejvhodnější výchozí hodnotu `access_type` pro každý `accelerator`, ale charakteristiky výkonu (šířka pásma a latence) sdílené paměti mohou být horší než vyhrazená (nesdílená) paměť akcelerátoru, když čtení z procesoru, zápis z procesoru nebo obojí. Je- `access_type_read_write`li sdílená paměť využívána i vyhrazenou pamětí pro čtení a zápis z procesoru, je výchozí hodnota modulu runtime; v opačném případě modul `access_type`runtime zvolí více konzervativních výchozích hodnot a umožní aplikaci její přepsání v případě přístupu k paměti. vzorce jejich výpočetních jader využívají jiné `access_type`výhody.

Následující příklad kódu ukazuje, jak určit, zda výchozí akcelerátor podporuje sdílenou paměť, a pak přepíše svůj výchozí typ přístupu a vytvoří `accelerator_view` z něj.

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
    acc.set_default_cpu_access_type(access_type_read_write);

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view reflects the default_cpu_access_type of the
    // accelerator it’s associated with.
    accelerator_view acc_v = acc.default_view;
}
```

`accelerator_view` Vždy odráží`accelerator` , ke kterému je přidruženo, a neposkytuje žádné rozhraní k přepsání nebo změně jeho `access_type`. `default_cpu_access_type`

## <a name="changing-the-default-accelerator"></a>Změna výchozího akcelerátoru

Můžete změnit výchozí akcelerátor voláním `accelerator::set_default` metody. Výchozí akcelerátor můžete změnit jenom jednou za spuštění aplikace a musíte ho změnit předtím, než se v GPU spustí nějaký kód. Jakákoli následná volání funkce pro změnu akcelerátoru vrátí **hodnotu false**. Pokud chcete použít jiný akcelerátor při volání `parallel_for_each`, přečtěte si část použití více akcelerátorů v tomto článku. Následující příklad kódu nastaví výchozí akcelerátor na jeden, který není Emulovaný, není připojen k zobrazení a podporuje dvojitou přesnost.

```cpp
bool pick_accelerator()
{
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;

    auto result = std::find_if(accs.begin(), accs.end(),
        [] (const accelerator& acc) {
            return !acc.is_emulated &&
                acc.supports_double_precision &&
                !acc.has_display;
        });

    if (result != accs.end()) {
        chosen_one = *(result);
    }

    std::wcout <<chosen_one.description <<std::endl;
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;
}
```

## <a name="using-multiple-accelerators"></a>Použití více akcelerátorů

Existují dva způsoby použití více akcelerátorů v aplikaci:

- Můžete předat `accelerator_view` objekty voláním metody [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .

- Objekt **pole** lze vytvořit pomocí určitého `accelerator_view` objektu. Modul runtime C + amp vybere `accelerator_view` objekt z zachyceného objektu **Array** ve výrazu lambda.

## <a name="special-accelerators"></a>Speciální akcelerátory

Cesty zařízení tří speciálních akcelerátorů jsou k dispozici jako vlastnosti `accelerator` třídy:

- [akcelerátor::D datový člen irect3d_ref](reference/accelerator-class.md#direct3d_ref): Tento akcelerátor s jedním vláknem používá software na CPU k emulaci generické grafické karty. Používá se ve výchozím nastavení pro ladění, ale není užitečné v produkčním prostředí, protože je pomalejší než hardwarové akcelerátory. Navíc je k dispozici pouze v sadě DirectX SDK a Windows SDK a pravděpodobně nebude nainstalována na počítače vašich zákazníků. Další informace najdete v tématu [ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code).

- [akcelerátor::D datový člen irect3d_warp](reference/accelerator-class.md#direct3d_warp): Tento akcelerátor poskytuje záložní řešení pro spouštění C++ kódu amp na vícejádrových procesorech, které používají streaming SIMD Extensions (SSE).

- [Accelerator:: cpu_accelerator – datový člen](reference/accelerator-class.md#cpu_accelerator): Tento akcelerátor můžete použít pro nastavení pracovních polí. Nelze spustit C++ kód amp. Další informace najdete v tématu [pracovní pole v C++ amp](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) post na paralelním programování v blogu nativního kódu.

## <a name="interoperability"></a>Interoperabilita

Modul C++ runtime amp podporuje interoperabilitu mezi `accelerator_view` třídou a rozhraním Direct3D [ID3D11Device](/windows/win32/api/d3d11/nn-d3d11-id3d11device). Metoda [Create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) přebírá `IUnknown` `accelerator_view` rozhraní a vrací objekt. Metoda [Get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) přebírá `accelerator_view` `IUnknown` objekt a vrací rozhraní.

## <a name="see-also"></a>Viz také:

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view – třída](../../parallel/amp/reference/accelerator-view-class.md)
