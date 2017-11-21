---
title: "Používání akcelerátoru a objektů accelerator_view | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 47355ea2c7db35b32c69e91bf8445efe7671ccce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Používání akcelerátoru a objektů accelerator_view
Můžete použít [akcelerátoru](../../parallel/amp/reference/accelerator-class.md) a [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) třídy k určení zařízení nebo emulátoru ke spuštění kódu C++ AMP v. Systém může mít několik zařízení nebo emulátorů, které se liší podle velikosti paměti, podpory sdílené paměti, podpora ladění nebo podporu dvojitou přesností. C++ Accelerated Massive Parallelism (C++ AMP) poskytuje rozhraní API, která vám pomůže zkontrolovat dostupné akcelerátorů, nastavit jako výchozí, zadejte více accelerator_views pro několik volání parallel_for_each – a provádět úlohy speciální ladění.  
  
## <a name="using-the-default-accelerator"></a>Pomocí výchozí akcelerátoru  
 Modul runtime C++ AMP vybere akcelerátor výchozí, pokud psaní kódu a vyberte některou. Modul runtime rozhodne akcelerátoru výchozí následujícím způsobem:  
  
1.  Pokud aplikace běží v režimu ladění, akcelerátor podporující ladění.  
  
2.  V opačném akcelerátoru, které je určené proměnnou prostředí CPPAMP_DEFAULT_ACCELERATOR, pokud je nastaveno.  
  
3.  V opačném – emulace zařízení.  
  
4.  Jinak zařízení, která má největší množství dostupné paměti.  
  
5.  Jinak zařízení, který není připojen k zobrazení.  
  
 Kromě toho modul runtime určuje `access_type` z `access_type_auto` pro výchozí akcelerátoru. To znamená, že výchozí akcelerátoru používá sdílené paměti, pokud ji podporuje, a pokud se ví, že jeho výkonové charakteristiky (šířky pásma a latence) být stejný jako vyhrazené paměti (nesdílené).  
  
 Vlastnosti akcelerátoru výchozí můžete určit vytváření výchozím akcelerátoru a Prozkoumáním jeho vlastnosti. Následující příklad kódu vytiskne cesty, množství paměti akcelerátoru, podpory sdílené paměti, podporu dvojitou přesností a omezená podpora Dvojitá přesnost akcelerátoru výchozí.  
  
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
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Proměnné prostředí CPPAMP_DEFAULT_ACCELERATOR  
 Můžete nastavit proměnnou prostředí CPPAMP_DEFAULT_ACCELERATOR a určit, `accelerator::device_path` akcelerátoru výchozí. Cesta je závislé na hardwaru. Následující kód používá `accelerator::get_all` funkce pro načtení seznamu dostupných akcelerátorů a potom zobrazí vlastnosti každého akcelerátoru a cesta.  
  
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
 Pokud chcete vybrat akcelerátor, použijte `accelerator::get_all` metodu pro načtení seznamu dostupných akcelerátorů a pak vyberte jeden podle jeho vlastnosti. Tento příklad ukazuje, jak vybrat akcelerátoru, který má nejvíce paměti:  
  
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
>  Jeden z akcelerátorů, které se vrátí pomocí `accelerator::get_all` je akcelerátor procesoru. Kód nelze spustit na akcelerátoru procesoru. Filtrovat akcelerátoru procesoru, porovnat hodnotu [device_path –](reference/accelerator-class.md#device_path) vlastnost akcelerátoru, který je vrácen `accelerator::get_all` s hodnotou [Accelerator::cpu_accelerator –](reference/accelerator-class.md#cpu_accelerator). Další informace najdete v části "Speciální akcelerátorů" v tomto článku.  
  
## <a name="shared-memory"></a>Sdílené paměti  
 Sdílené paměti je paměť, která je přístupná procesoru a akcelerátorem. Použití sdílené paměti eliminuje nebo výrazně snižuje zatížení sady kopírování dat mezi procesoru a akcelerátorem. I když je sdílená paměť, jej nelze získat přístup, souběžně procesoru a akcelerátorem, a to způsobí tak, že nedefinované chování. Vlastnosti akcelerátoru [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) vrátí `true` Pokud akcelerátor podporuje sdílené paměti a [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) vlastnost získá výchozí [access_type](reference/concurrency-namespace-enums-amp.md#access_type) paměti přidělené na `accelerator`– například `array`s přidružené `accelerator`, nebo `array_view` objekty na `accelerator`. 
  
 Modul runtime C++ AMP automaticky vybere nejlepší výchozí `access_type` pro každou `accelerator`, ale může být při čtení zhoršení než ty, které paměti vyhrazené akcelerátoru (nesdílené) výkonové charakteristiky (šířky pásma a latence) sdílené paměti z procesoru, zápis z procesoru, nebo obojí. Pokud sdílené paměti provede i vyhrazené paměti pro čtení a zápis z procesoru, modul runtime výchozí `access_type_read_write`, jinak hodnota modulu runtime zvolí více konzervativní výchozí `access_type`a umožňuje aplikaci přepsat, pokud přístup do paměti vzory jeho výpočetní jádra těžit z jiné `access_type`.  
  
 Následující příklad kódu ukazuje, jak určit, zda akcelerátoru výchozí podporuje sdílené paměti a pak přepsání jeho výchozí typ přístupu a vytvoří `accelerator_view` z něj.  
  
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
  
 `accelerator_view` Vždy odráží `default_cpu_access_type` z `accelerator` přidružené, a poskytuje žádné rozhraní k přepsání nebo změnit jeho `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Změna výchozí akcelerátoru  
 Můžete změnit výchozí akcelerátoru voláním `accelerator::set_default` metoda. Pouze jednou za aplikace spuštění a musí ho změnit před provedením jakékoli kódu na GPU, můžete změnit výchozí akcelerátoru. Žádné další funkce volání změnit akcelerátor vrací `false`. Pokud chcete použít jiný akcelerátoru v volání `parallel_for_each`, přečtěte si části "Použití více akcelerátorů" v tomto článku. Následující příklad kódu nastaví výchozí akcelerátoru ten, který není emulovaných, není připojen k zobrazení a podporuje dvojitou přesností.  
  
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
 Existují dva způsoby, jak používat více akcelerátorů ve vaší aplikaci:  

-   Můžete předat `accelerator_view` objekty, které se volání [parallel_for_each –](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metoda.  
  
-   Můžete vytvořit `array` pomocí konkrétní `accelerator_view` objektu. Modul runtime C + AMP vyzvedne, až bude `accelerator_view` objekt z zaznamenané `array` objekt ve výrazu lambda.  
  
## <a name="special-accelerators"></a>Speciální akcelerátorů  
 Je k dispozici jako vlastnosti zařízení cest tři speciální akcelerátorů `accelerator` třídy:  
  
- [Accelerator::direct3d_ref – datový člen](reference/accelerator-class.md#direct3d_ref): Tento jednovláknové akcelerátoru pomocí softwaru na procesoru emulovat obecné grafické karty. Použije se ve výchozím nastavení pro ladění, ale není užitečné v produkčním prostředí, protože je nižší než akcelerátorů hardwaru. Kromě toho je k dispozici pouze v DirectX SDK a sadu Windows SDK a je pravděpodobně být nainstalovány na počítače zákazníků. Další informace najdete v tématu [ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code).  
  
- [Accelerator::direct3d_warp – datový člen](reference/accelerator-class.md#direct3d_warp): Tento accelerator poskytuje záložní řešení pro spouštění kódu C++ AMP v vícejádrovými procesory, které používají Streaming SIMD Extensions (SSE).  
  
- [Accelerator::cpu_accelerator – datový člen](reference/accelerator-class.md#cpu_accelerator): můžete použít tento akcelerátoru pro nastavení pracovní pole. Kód C++ AMP ji nelze spustit. Další informace najdete v tématu [pracovní pole v C++ AMP](http://go.microsoft.com/fwlink/p/LinkId=248485) můžete zveřejnit na paralelní programování v blogu nativního kódu.  
  
## <a name="interoperability"></a>Interoperabilita  
 Modul runtime C++ AMP podporuje spolupráci mezi `accelerator_view` třídy a Direct3D – [ID3D11Device rozhraní](http://go.microsoft.com/fwlink/p/LinkId=248488). [Create_accelerator_view –](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) metoda trvá `IUnknown` rozhraní a vrátí `accelerator_view` objektu. [Get_device](http://msdn.microsoft.com/en-us/8194125e-8396-4d62-aa8a-65831dea8439) metoda trvá `accelerator_view` objekt a vrátí `IUknown` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Ladění kódu GPU](/visualstudio/debugger/debugging-gpu-code)   
 [accelerator_view – třída](../../parallel/amp/reference/accelerator-view-class.md)
