---
title: /Zc:alignedNew (c ++ 17 přepsání zarovnaný přidělení) | Microsoft Docs
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:alignedNew
dev_langs:
- C++
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
author: corob-msft
ms.author: corob
ms.openlocfilehash: 5f9527d63a9843bd4df90520e5b4759126d72fe1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378381"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (c ++ 17 přepsání zarovnaný přidělení)

Povolení podpory pro C ++ 17 přepsání zarovnán **nové**, dynamické přidělování paměti zarovnán na hranicích větší než výchozí hodnota pro maximální velikost standardní zarovnaný typu, **maximální\_zarovnat\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Poznámky

Visual Studio verze 15,5 umožňuje kompilátoru a podpora knihovny pro C ++ 17 standardní přepsání zarovnaný dynamické přidělování paměti. Když **/Zc:alignedNew** je zadána možnost, dynamické přidělování jako `new Example;` respektuje zarovnání *příklad* i když je větší než `max_align_t`, největší zarovnání vyžaduje se pro libovolného základní typu. Pokud je již více než zaručit původní operátorem zarovnání přidělené typu **nové**, k dispozici jako hodnotu předdefinovaná makra  **\_ \_STDCPP\_výchozí \_Nový\_zarovnání\_\_**, příkaz `new Example;` výsledkem volání `::operator new(size_t)` stejně jako ve C ++ 14. Pokud je větší než zarovnání  **\_ \_STDCPP\_výchozí\_nový\_zarovnání\_\_**, místo toho získává implementace paměť pomocí `::operator new(size_t, align_val_t)`. Podobně odstranění přepsání zarovnaný typů vyvolá `::operator delete(void*, align_val_t)` nebo velikosti odstranit podpis `::operator delete(void*, size_t, align_val_t)`.

**/Zc:alignedNew** možnost je dostupná jenom při [/std: c ++ 17](std-specify-language-standard-version.md) nebo [/std: c ++ nejnovější](std-specify-language-standard-version.md) je povoleno. V části **/std: c ++ 17** nebo **/std: c ++ nejnovější**, **/Zc:alignedNew** je ve výchozím nastavení povolené tak, aby odpovídala ISO standardu C ++ 17. Pokud jediný důvodu implementovat operátor **nové** a **odstranit** je podpora přepsání zarovnaný přidělení, může tento kód v C ++ 17 režimu už nepotřebujete. Chcete-li tuto možnost vypnout a vrátit se k C ++ 14 chování **nové** a **odstranit** při **/std::c ++ 17** nebo **/std: c ++ nejnovější** není zadaný, Zadejte **/Zc:alignedNew-**. Pokud implementujete operátor **nové** a **odstranit** , ale nejste připravení implementovat přepsání zarovnaný operátor **nové** a **odstranit** přetížení, které mají `align_val_t` parametr, použijte **/Zc:alignedNew-** možnost zabránit generování standardní knihovna a kompilátor volá přepsání zarovnaný přetížení. [/ Projektovou-](permissive-standards-conformance.md) možnost nezmění výchozí nastavení **/Zc:alignedNew**.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak operátor **nové** a operátor **odstranit** chovají při **/Zc:alignedNew** je možnost nastavena.

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

Tento výstup je typický pro 32-bit sestavení. Ukazatele, které hodnoty se liší podle kde vaše aplikace běží v paměti.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Informace o problémech shoda v jazyce Visual C++ najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc:alignedNew** nebo **/Zc:alignedNew-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)  
