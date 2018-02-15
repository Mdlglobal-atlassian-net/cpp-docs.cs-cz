---
title: "Používání modelu C++ AMP v aplikacích pro UPW | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 481ea5918e7572375fdafd9ba489da34730fef84
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="using-c-amp-in-uwp-apps"></a>Používání modelu C++ AMP v aplikacích pro UPW
C++ AMP (C++ Accelerated Massive Parallelism) ve vaší aplikaci pro univerzální platformu Windows (UWP) slouží k provádění výpočtů na grafický procesor (grafiky zpracování Unit) nebo jiné výpočetní akcelerátorů. Ale C++ AMP neposkytuje rozhraní API pro práci přímo s typy prostředí Windows Runtime a prostředí Windows Runtime neposkytuje obálku pro C++ AMP. Při použití prostředí Windows Runtime typy ve vašem kódu – včetně těch, které jste sami vytvořili, je nutné je převést na typy, které jsou kompatibilní s C++ AMP.  
  
## <a name="performance-considerations"></a>Důležité informace o výkonu  
 Pokud používáte [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) k vytvoření aplikace pro univerzální platformu Windows (UWP), doporučujeme použít typy prostý starý dat (POD) společně s souvislý úložiště – například `std::vector` nebo pole stylu jazyka C – pro data, která bude použita s C++ AMP. Můžete dosáhnout vyšší výkon než pomocí jiných POD typy nebo Windows RT kontejnerů, protože žádné zařazování má proběhnout.  
  
 V C++ AMP jádra, pro přístup k datům, uložená tímto způsobem právě zabalení `std::vector` nebo pole úložiště v `concurrency::array_view` a potom pomocí zobrazení pole v `concurrency::parallel_for_each` smyčka:  
  
```cpp  
// simple vector addition example  
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);
  
concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);
  
av2.discard_data();
  
concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)  
    {  
        av2[idx] = av0[idx] + av1[idx];  
    });
```  
  
## <a name="marshaling-windows-runtime-types"></a>Zařazování typů modulu Windows Runtime  
 Při práci s rozhraními API Windows Runtime, můžete chtít použít C++ AMP na data, která je uložená v prostředí Windows Runtime kontejneru, jako `Platform::Array<T>^` nebo komplexními datovými typy, jako jsou třídy nebo struktury, které jsou deklarovány s použitím `ref` – klíčové slovo nebo `value`</C4>–klíčovéslovo. V těchto situacích máte nějakou práci navíc ke zpřístupnění dat C++ AMP.  
  
### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::Array\<T > ^, kde T představuje typ POD  
 Když narazíte `Platform::Array<T>^` a T představuje typ POD, máte přístup k jeho základní úložiště jenom pomocí `get` – členská funkce:  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```  
  
 Pokud T není POD typem, použijte pro používání data C++ AMP technika, který je popsán v následující části.  
  
### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Typy modulu Windows Runtime: třídy deklarované s použitím klíčových slov ref a value  
 C++ AMP nepodporuje komplexními datovými typy. To zahrnuje bez POD typy a všechny typy, které jsou deklarovány s použitím `ref` – klíčové slovo nebo `value` – klíčové slovo. Pokud se používá nepodporovaný typ `restrict(amp)` se vygeneruje kontext chyby kompilace.  
  
 Pokud narazíte na nepodporovaný typ, můžete zkopírovat zajímavé části svých dat do `concurrency::array` objektu. Kromě vytváření data k dispozici pro C++ AMP využívat, můžete tento postup ručního kopírování také zvýšit výkon, tím se maximalizuje polohu dat a zajistíte, že data, která se nepoužijí není zkopírovány do akcelerátor. Další výkon lze zvýšit pomocí *pracovní pole*, což je speciální formu `concurrency::array` poskytuje nápovědu pro modul runtime AMP, který pole by mělo být optimalizované pro časté přenos mezi nimi a ostatní pole na Zadaný akcelerátoru.  
  
```cpp  
// pixel_color.h  
ref class pixel_color sealed  
{  
public: 
    pixel_color(Platform::String^ color_name, int red, int green, int blue)   
    {  
        name = color_name;  
        r = red;  
        g = green;  
        b = blue;  
    }  
 
    property Platform::String^ name;   
    property int r;  
    property int g;  
    property int b;  
};  
  
// Some other file  
  
std::vector<pixel_color^> pixels (256);
  
for (pixel_color ^pixel : pixels)   
{  
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}  
  
// Create the accelerators  
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);
  
// Create the staging arrays  
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
  
// Extract data from the complex array of structs into staging arrays.  
concurrency::parallel_for(0, 256, [&](int i)  
    {   
        red_vec[i] = pixels[i]->r;  
        blue_vec[i] = pixels[i]->b;  
    });
  
// Array views are still used to copy data to the accelerator  
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);
  
// Change all pixels from blue to red.  
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)  
    {  
        av_red[idx] = 255;  
        av_blue[idx] = 0;  
    });
```  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření první aplikace UWP s použitím jazyka C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)   
 [Vytváření Windows Runtime komponent v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)

