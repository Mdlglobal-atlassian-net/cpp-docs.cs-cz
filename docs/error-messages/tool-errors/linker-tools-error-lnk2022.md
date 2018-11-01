---
title: Chyba linkerů LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: e55202274c5ec3982f784ad6cdf074a5a99e922f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491387"
---
# <a name="linker-tools-error-lnk2022"></a>Chyba linkerů LNK2022

> operace s metadaty selhala (*HRESULT*): *error_message*

Linker došlo k chybě při slučování metadat. Chyby metadat musí být přeloženy na odkaz úspěšně.

Jedním ze způsobů pro diagnostiku tohoto problému je ke spuštění **ildasm-tokeny** na objekt soubory, které chcete najít typy, které mají tokeny uveden v `error_message`a vyhledejte rozdíly.  V metadatech dva různé typy se stejným názvem není platný, i v případě, že se liší jenom atribut LayoutType.

Jeden z důvodu LNK2022 je ve více souborech určených ke kompilaci, se stejným názvem, ale s konfliktní definice typu (jako je například struktura) existuje, a při kompilaci s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  V takovém případě Ujistěte se, že typ má stejné definici ve všech souborech určených ke kompilaci.  Název typu je uveden v `error_message`.

Další možnou příčinou LNK2022 je, pokud linker zjistí soubor metadat v jiném umístění než bylo zadáno pro kompilátor (s [#using](../../preprocessor/hash-using-directive-cpp.md) ). Ujistěte se, že soubor metadat (.dll nebo .netmodule) je ve stejném umístění, pokud je předán linkeru, stejně, jako když byla předána do kompilátor.

Při sestavování aplikace ATL, použijte makro `_ATL_MIXED` vyžaduje ve všech souborech určených ke kompilaci, pokud se používá v alespoň jednom.

## <a name="example"></a>Příklad

Následující příklad definuje typ prázdný.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>Příklad

Tento příklad ukazuje, že nelze propojit dva soubory zdrojového kódu, které obsahují typy stejným názvem, ale různé definice.

Následující ukázka generuje LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```