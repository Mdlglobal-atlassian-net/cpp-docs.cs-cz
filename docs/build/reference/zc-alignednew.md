---
title: /Zc:alignedNew (přidělení nadměrného zarovnání C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 041f62bbbf5f7a2750960d21d1534cf6daf4b874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335688"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (přidělení nadměrného zarovnání C++17)

Povolit podporu pro C ++ 17 over-aligned **nové**, dynamické přidělení paměti zarovnané na hranice větší než výchozí pro maximální velikosti standardní zarovnaný typ, **max\_align\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignedNew**\[-]

## <a name="remarks"></a>Poznámky

Kompilátor a knihovna MSVC podporují standardní přetížení dynamické paměti C++17. Když **je zadána možnost /Zc:alignedNew,** `new Example;` dynamické přidělení, například respektuje zarovnání `max_align_t` *Příklad* i v případě, že je větší než , největší zarovnání požadované pro všechny základní typ. Pokud zarovnání přiděleného typu není větší než zarovnání zaručené původním **operátorem new**, které je k `new Example;` dispozici jako hodnota `::operator new(size_t)` předdefinovaného makra ** \_ \_STDCPP\_DEFAULT\_NEW\_ALIGNMENT\_**, výsledkem příkazu je volání stejně jako v jazyce C++14. Pokud zarovnání je větší než `::operator new(size_t, align_val_t)` ** \_ \_STDCPP\_default\_new\_alignment\_**, implementace místo toho získá paměť pomocí . Podobně odstranění přerovnaných typů vyvolá `::operator delete(void*, align_val_t)` nebo velký podpis `::operator delete(void*, size_t, align_val_t)`odstranění .

Možnost **/Zc:alignedNew** je k dispozici pouze v případě, že je povolena [možnost /std:c++17](std-specify-language-standard-version.md) nebo [/std:c++latest.](std-specify-language-standard-version.md) Pod **/std:c++17** nebo **/std:c++latest**, **/Zc:alignedNew** je ve výchozím nastavení povolen a vyhovuje standardu ISO C++17. Pokud jediný důvod, proč implementovat operátor **new** a **odstranit** je pro podporu přerovnaných přidělení, můžete již potřebovat tento kód v režimu C ++ 17. Chcete-li tuto možnost vypnout a vrátit se k chování **nového** jazyka C++14 a **odstranit** při použití **parametru /std::c++17** nebo **/std:c++latest**, zadejte **/Zc:alignedNew-**. Pokud implementujete operátor **new** a **odstranit,** ale nejste připraveni implementovat přerovnaný operátor **new** a **odstranit** přetížení, které mají `align_val_t` parametr, použijte **/Zc:alignedNew-** možnost zabránit kompilátoru a standardní knihovny z generování volání over-aligned přetížení. Možnost [/tolerantní-](permissive-standards-conformance.md) nezmění výchozí nastavení **/Zc:alignedNew**.

Podpora **/Zc:alignedNew** je k dispozici od visual studia 2017 verze 15.5.

## <a name="example"></a>Příklad

Tato ukázka ukazuje, jak operátor **new** a **operátor delete** chovat při **/Zc:alignedNew** možnost je nastavena.

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

Tento výstup je typický pro 32bitová sestavení. Hodnoty ukazatele se liší v závislosti na tom, kde je aplikace spuštěna v paměti.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Informace o problémech s kondenzací v jazyce Visual C++ naleznete [v tématu Nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku **vlastností Vlastnosti** > konfigurace**C/C++** > **.**

1. Upravte vlastnost **Další volby** tak, aby **zahrnovala parametr /Zc:alignedNew** nebo **/Zc:alignedNew-** a pak zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](zc-conformance.md)
