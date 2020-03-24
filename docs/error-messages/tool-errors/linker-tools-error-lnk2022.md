---
title: Chyba linkerů LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: d30dad6f8ad146ff467eb4eaf32b21dd6950d25f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194639"
---
# <a name="linker-tools-error-lnk2022"></a>Chyba linkerů LNK2022

> operace metadat se nezdařila (*HRESULT*): *ERROR_MESSAGE*

Linker zjistil chybu při slučování metadat. Aby bylo možné úspěšně propojit chyby metadat, je nutné je vyřešit.

Jedním ze způsobů, jak tento problém diagnostikovat, je spustit **Ildasm tokeny** na soubory objektů a najít, které typy mají tokeny uvedené v `error_message`a vyhledat rozdíly.  V metadatech jsou dva různé typy se stejným názvem neplatné, i když se atribut Just LayoutType liší.

Jedním z důvodů pro LINKERŮ LNK2022 je, že typ (například struktura) existuje ve více compilands se stejným názvem, ale s konfliktními definicemi a při kompilaci s možností [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  V takovém případě se ujistěte, že typ má stejnou definici ve všech compilands.  Název typu je uveden v `error_message`.

Další možnou příčinou pro LINKERŮ LNK2022 je, že linker najde soubor metadat v jiném umístění, než byl zadán kompilátoru (s [#using](../../preprocessor/hash-using-directive-cpp.md) ). Ujistěte se, že soubor metadat (. dll nebo. netmodule) je ve stejném umístění při předání do linkeru, jak byl předán do kompilátoru.

Při sestavování aplikace ATL je použití `_ATL_MIXED` makra požadováno ve všech compilands, pokud je použito alespoň v jednom.

## <a name="example"></a>Příklad

Následující příklad definuje prázdný typ.

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>Příklad

Tento příklad ukazuje, že nelze propojit dva soubory zdrojového kódu, které obsahují typy se stejným názvem, ale různé definice.

Následující ukázka generuje LINKERŮ LNK2022.

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```
