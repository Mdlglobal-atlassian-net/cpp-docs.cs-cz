---
title: Používání modelu C++ AMP v aplikacích pro UWP
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 31fede0a2419e56d53cb16521b08067dac5facc6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272656"
---
# <a name="using-c-amp-in-uwp-apps"></a>Používání modelu C++ AMP v aplikacích pro UWP

C++ AMP (C++ Accelerated Massive Parallelism) můžete použít v aplikaci pro univerzální platformu Windows (UPW) provádět výpočty na GPU (Graphic Processing Unit) nebo jiných počítačových akcelerátorech. Nicméně C++ AMP neposkytuje rozhraní API pro práci přímo s typy prostředí Windows Runtime a modulu Windows Runtime nenabízí obal pro C++ AMP. Při použití typů Windows Runtime ve vašem kódu – včetně těch, které jste sami vytvořili, je nutné je převést na typy, které jsou kompatibilní s C++ AMP.

## <a name="performance-considerations"></a>Důležité informace o výkonu

Pokud používáte rozšíření součásti Visual C++ C + +/ CX k vytvoření aplikace pro univerzální platformu Windows (UPW), doporučujeme používat typy prostý staré dat (POD) spolu se souvislým úložištěm – například `std::vector` nebo pole stylu C – pro data, která bude použít s C++ AMP. To může pomoci dosáhnout vyššího výkonu než pomocí typů bez POD nebo kontejnerů RT systému Windows, protože k dojít k žádnému zařazování.

V jádře C++ AMP pro přístup k datům, která je uložena tímto způsobem pouze zabalte `std::vector` nebo pole úložiště `concurrency::array_view` a potom použijte zobrazení pole ve `concurrency::parallel_for_each` smyčka:

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

Při práci s rozhraními API Windows Runtime můžete chtít použít C++ AMP na data, která je uložená v kontejneru Windows Runtime, jako `Platform::Array<T>^` nebo v komplexních datových typech, jako jsou třídy nebo struktury, které jsou deklarovány s použitím **ref** klíčové slovo nebo **hodnotu** – klíčové slovo. V takových situacích je nutné provést další úkony a zpřístupnit data C++ AMP.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::Array\<T > ^, kde T je typ POD

Pokud se setkáte `Platform::Array<T>^` a T je typ POD, můžete přístup k jeho základnímu úložišti stačí použít `get` členské funkce:

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

Pokud T není POD typ, použijte techniku, která je popsaná v následující části dat s C++ AMP.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Typy modulu Windows Runtime: třídy deklarované s použitím klíčových slov ref a value

C++ AMP nepodporuje komplexní datové typy. Jedná se o typy bez POD a všechny typy, které jsou deklarovány pomocí **ref** – klíčové slovo nebo **hodnotu** – klíčové slovo. Pokud je použit nepodporovaný typ v `restrict(amp)` kontextu, Chyba kompilace je vygenerována.

Pokud narazíte na nepodporovaný typ, můžete kopírovat zajímavé části data do `concurrency::array` objektu. Kromě zpřístupnění dat pro použití C++ AMP využívat, můžete tento postup ručního kopírování také zvýšit výkon, maximalizací lokality dat a zajištěním, že se data, která se nepoužije zkopírována na akcelerátor. Další výkon lze zvýšit pomocí *pracovního pole*, což je zvláštní forma `concurrency::array` poskytující nápovědu k modulu runtime AMP, která pole by měla být optimalizováno pro častý přenos mezi ním a jinými poli na určený akcelerátor.

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

## <a name="see-also"></a>Viz také:

[Vytvoření první aplikace pro UPW pomocí jazyka C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[Vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
