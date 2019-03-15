---
title: /Zc:alignedNew (c ++ 17 nadbytečně zarovnané přidělení)
ms.date: 02/28/2018
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: e0d850d54611579288b81a334af4abdfab6e411c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820335"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (c ++ 17 nadbytečně zarovnané přidělení)

Povolit podporu pro C ++ 17 nadbytečně zarovnané **nové**, dynamické přidělování paměti zarovnány na hranice větší než je výchozí maximální velikost standardní zarovnaný typu, **maximální\_zarovnat\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Poznámky

Visual Studio verze 15.5 umožňuje kompilátoru a podpora knihovny pro C ++ 17 standardní nadbytečně zarovnané dynamické přidělování paměti. Když **/Zc:alignedNew** je zadána možnost dynamického přidělování, jako `new Example;` respektuje zarovnání *příklad* i když je větší než `max_align_t`, největšímu zarovnání vyžaduje se pro všechny základní typ. Pokud je zarovnání přiděleného typu nesmí být větší než který zaručeno, že původní operátorem **nové**, která je dostupná jako hodnotu předdefinované makro  **\_ \_STDCPP\_výchozí \_Nový\_zarovnání\_\_**, příkaz `new Example;` výsledkem volání `::operator new(size_t)` stejně jako v C ++ 14. Pokud je větší než zarovnání  **\_ \_STDCPP\_výchozí\_nový\_zarovnání\_\_**, místo toho získává implementaci paměť pomocí `::operator new(size_t, align_val_t)`. Podobně, vyvolá odstranění nadbytečně zarovnané typy `::operator delete(void*, align_val_t)` nebo velikosti odstranit podpis `::operator delete(void*, size_t, align_val_t)`.

**/Zc:alignedNew** možnost je dostupná jenom při [/std: c ++ 17](std-specify-language-standard-version.md) nebo [/std: c ++ nejnovější](std-specify-language-standard-version.md) je povolená. V části **/std: c ++ 17** nebo **/std: c ++ nejnovější**, **/Zc:alignedNew** je ve výchozím nastavení povolené, tak, aby odpovídal ISO standardu C ++ 17. Pokud pouze z důvodu můžete implementovat operátor **nové** a **odstranit** je podpora nadbytečně zarovnané přidělení, už je nutné tento kód v C ++ 17 režimu. Tuto možnost vypnout a vrátit v C ++ 14 chování **nové** a **odstranit** při **/std::c ++ 17** nebo **/std: c ++ nejnovější** není zadána, Zadejte **/Zc:alignedNew-**. Pokud se rozhodnete implementovat operátor **nové** a **odstranit** , ale nejste připraveni k implementaci nadbytečně zarovnané operátor **nové** a **odstranit** přetížení, které mají `align_val_t` parametrů, použijte **/Zc:alignedNew-** volá možnost zabránit generuje kompilátor a standardní knihovna pro nadbytečně zarovnané přetížení. [/ Permissive-](permissive-standards-conformance.md) možnost nezmění výchozí nastavení **/Zc:alignedNew**.

## <a name="example"></a>Příklad

Tato ukázka předvádí, jak operátor **nové** a operátor **odstranit** chovat, když **/Zc:alignedNew** je možnost nastavená.

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

Tímto výstupem je typický pro 32bitová sestavení. Ukazatel, který se hodnoty liší založené na němž je aplikace spuštěna v paměti.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc:alignedNew** nebo **/Zc:alignedNew-** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
