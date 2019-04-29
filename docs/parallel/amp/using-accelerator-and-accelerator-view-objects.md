---
title: Používání akcelerátoru a objektů accelerator_view
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 05ca53d075867fefa43f7471bb795040d075274e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405388"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Používání akcelerátoru a objektů accelerator_view

Můžete použít [akcelerátoru](../../parallel/amp/reference/accelerator-class.md) a [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) třídy a zadejte zařízení nebo emulátoru spustit vaše C++ kódu AMP na. Systém může mít několik zařízení nebo emulátorů, které se liší podle množství paměti, podpory sdílené paměti, podpory ladění nebo podpory dvojité přesnosti. C++Accelerated Massive Parallelism (C++ AMP) poskytuje rozhraní API, která vám umožní zkoumat všechny dostupné akcelerátory, nastavit jako výchozí, zadejte více accelerator_views pro více volání na parallel_for_each a provádění zvláštních úkolů ladění.

## <a name="using-the-default-accelerator"></a>Použití výchozího akcelerátoru

Modul runtime C++ AMP vybere výchozí akcelerátor, pokud napíšete kód pro výběr konkrétní skupinu. Modul runtime zvolí výchozí akcelerátor takto:

1. Pokud aplikace běží v režimu ladění, akcelerátor podporující ladění.

2. V opačném případě akcelerátor, který je zadaný proměnnou prostředí CPPAMP_DEFAULT_ACCELERATOR, pokud je nastavena.

3. Jinak – neemulované zařízení.

4. V opačném případě zařízení, které má největší velikost dostupné paměti.

5. V opačném případě zařízení, které není připojeno k zobrazení.

Kromě toho modul runtime určuje `access_type` z `access_type_auto` pro výchozí akcelerátor. To znamená, že výchozí akcelerátor používá sdílenou paměť, pokud je podporována, a pokud se ví, že jeho vlastnostech výkonu (šířka pásma a čekací doba) být stejný jako vyhrazená (nesdílená) paměť.

Podle výchozího akcelerátoru sestavením a přezkoumáním vlastnosti můžete určit vlastnosti výchozího akcelerátoru. Následující příklad kódu zobrazí cestu, množství paměti akcelerátoru, podporu sdílené paměti, podporu dvojité přesnosti a omezenou podporu dvojité přesnosti výchozího akcelerátoru.

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

### <a name="cppampdefaultaccelerator-environment-variable"></a>Proměnná prostředí CPPAMP_DEFAULT_ACCELERATOR

Můžete nastavit proměnnou prostředí CPPAMP_DEFAULT_ACCELERATOR k určení `accelerator::device_path` výchozího akcelerátoru. Cesta je závislá na hardwaru. Následující kód používá `accelerator::get_all` funkce k načtení seznamu dostupných akcelerátorů a poté zobrazí cestu a charakteristiku každého akcelerátoru.

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

Chcete-li vybrat akcelerátor, použijte `accelerator::get_all` metodu pro načtení seznamu dostupných akcelerátorů a poté vyberte jednu podle jeho vlastnosti. Tento příklad ukazuje, jak vybrat akcelerátor, který má nejvíce paměti:

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
> Jeden z akcelerátorů jsou vráceny pomocí `accelerator::get_all` je akcelerátor procesoru. Nelze spustit kód na akcelerátoru procesoru. Chcete-li filtrovat akcelerátor procesoru, porovnejte hodnotu [device_path](reference/accelerator-class.md#device_path) vlastnosti akcelerátoru, který je vrácen `accelerator::get_all` s hodnotou [accelerator::cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Další informace najdete v části "Speciální akcelerátory" v tomto článku.

## <a name="shared-memory"></a>Sdílená paměť

Sdílená paměť je paměť, která je přístupná pomocí procesoru a akcelerátoru. Využití sdílené paměti eliminuje nebo významně snižuje režijní náklady na kopírování dat mezi CPU a akcelerátorem. I když je paměť sdílená, se nedá přistupovat souběžně CPU a akcelerátorem a tím proto způsobí nedefinované chování. Vlastnost akcelerátoru [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) vrátí **true** Pokud akcelerátor podporuje sdílenou paměť a [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) příkazy property GET Výchozí hodnota [access_type](reference/concurrency-namespace-enums-amp.md#access_type) pro paměť přidělenou na `accelerator`– například **pole**s přidružené s `accelerator`, nebo `array_view` přistupováno z objektů `accelerator`.

Modul runtime C++ AMP automaticky zvolí nejvhodnější výchozí `access_type` pro každou `accelerator`, ale charakteristiky výkonu (šířka pásma a čekací doba) sdílené paměti mohou být horší, než ty, které akcelerátoru vyhrazené (nesdílené) paměti při čtení z procesoru, zápisu z procesoru, nebo obojí. Pokud sdílená paměť funguje stejně dobře jako vyhrazená paměť pro čtení a zápis z procesoru, modul runtime použije se výchozí `access_type_read_write`; v opačném případě modul runtime zvolí konzervativnější výchozí `access_type`a umožňuje aplikacím ho přepsat, pokud přístup k paměti výhody vzory jádra jeho výpočtu těží z jiného `access_type`.

Následující příklad kódu ukazuje, jak určit, zda výchozí akcelerátor podporuje sdílenou paměť a potom přepíše jeho výchozí typ přístupu a vytvoří `accelerator_view` z něj.

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

`accelerator_view` Vždy odráží `default_cpu_access_type` z `accelerator` je spojený, a poskytuje rozhraní pro přepsání nebo změnu jeho `access_type`.

## <a name="changing-the-default-accelerator"></a>Změna výchozího akcelerátoru

Můžete změnit výchozí akcelerátor voláním `accelerator::set_default` metody. Výchozí akcelerátor lze změnit pouze jednou za aplikace spuštění a můžete ho musí změnit před spuštěním jakéhokoli kódu na GPU. Jakákoli následná volání funkce změny akcelerátoru vrátí **false**. Pokud chcete použít jiný akcelerátor ve volání `parallel_for_each`, přečtěte si část "Použití více akcelerátorů" v tomto článku. Následující příklad kódu nastaví výchozí akcelerátor, který není emulován, není připojen k zobrazení a podporuje dvojitou přesnost.

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

- Můžete předat `accelerator_view` objekty k volání [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody.

- Můžete vytvořit **pole** pomocí zvláštního `accelerator_view` objektu. Modul runtime jazyka C + AMP vybere `accelerator_view` objekt ze zachyceného **pole** objektu ve výrazu lambda.

## <a name="special-accelerators"></a>Speciální akcelerátory

Umístění zařízení tří speciálních akcelerátorů jsou dostupná jako vlastnosti `accelerator` třídy:

- [Accelerator::direct3d_ref – datový člen](reference/accelerator-class.md#direct3d_ref): Tento jednovláknový akcelerátor používá software na procesoru pro emulaci obecné grafické karty. Používá se ve výchozím nastavení pro ladění, ale není užitečné ve výrobě, protože je pomalejší než hardwarové akcelerátory. Kromě toho je k dispozici pouze v rozhraní DirectX SDK a sady Windows SDK a je nepravděpodobné, že by být nainstalovaný na počítači zákazníka. Další informace najdete v tématu [ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code).

- [Accelerator::direct3d_warp – datový člen](reference/accelerator-class.md#direct3d_warp): Tento akcelerátor poskytuje záložní řešení pro provádění kódu jazyka C++ AMP na vícejádrových procesorech pomocí Streaming SIMD Extensions (SSE).

- [Accelerator::cpu_accelerator – datový člen](reference/accelerator-class.md#cpu_accelerator): Pomocí tohoto akcelerátoru nastavíte pracovní pole. Nedokáže spustit kód jazyka C++ AMP. Další informace najdete v tématu [pracovní pole v jazyce C++ AMP](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) Zveřejněte na paralelní programování v blogu nativního kódu.

## <a name="interoperability"></a>Interoperabilita

Runtime C++ AMP podporuje interoperabilitu mezi `accelerator_view` třídou a rozhraním Direct3D [rozhraní ID3D11Device](/windows/desktop/api/d3d11/nn-d3d11-id3d11device). [Create_accelerator_view –](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) přijímá metodu `IUnknown` rozhraní a vrátí `accelerator_view` objektu. [Get_device –](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) přijímá metodu `accelerator_view` objekt a vrátí `IUnknown` rozhraní.

## <a name="see-also"></a>Viz také:

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view – třída](../../parallel/amp/reference/accelerator-view-class.md)
