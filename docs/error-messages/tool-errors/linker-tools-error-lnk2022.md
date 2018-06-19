---
title: Chyba linkerů Lnk2022 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7769bc28dc777ef8d7b82b91b9695356db05a682
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300885"
---
# <a name="linker-tools-error-lnk2022"></a>Chyba linkerů LNK2022  
  
> metadata operace se nezdařila (*HRESULT*): *error_message*  
  
Linkeru zjistil chybu při slučování metadat. Metadata chyby musí vyřešit propojení úspěšně.  
  
Jeden způsob, jak diagnostikovat potíže je spuštění **ildasm-tokeny** na soubory objektů nalézt typy, které mají tokeny uvedené v `error_message`a vyhledejte rozdíly.  V metadatech dva různé typy se stejným názvem není platný, i v případě, že právě LayoutType atributu se liší.  
  
Jeden důvodu LNK2022 je ve více souborech určených ke kompilaci, se stejným názvem, ale s konfliktními definice typu (například struktury) existuje, a při kompilaci s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  V takovém případě se ujistěte, že typ má stejné definice v souborech všech určených ke kompilaci.  Název typu, je uvedena ve `error_message`.  
  
Další možnou příčinou LNK2022 je při linkeru vyhledá soubor metadat v jiném umístění, než bylo zadáno pro kompilátor (s [#using](../../preprocessor/hash-using-directive-cpp.md) ). Ujistěte se, že soubor metadat (.dll nebo .netmodule) je ve stejném umístění, když uplyne linkeru, stejně, jako když byl předán kompilátoru.  
  
Při vytváření aplikace ATL použití makra `_ATL_MIXED` je vyžadována ve všech souborech určených ke kompilaci, pokud se používá alespoň v jedné.  
  
## <a name="example"></a>Příklad  
  
Následující příklad definuje typ prázdný.  
  
```cpp  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>Příklad  
  
Tento příklad ukazuje, že nemůže propojit dva soubory zdrojového kódu, které obsahují typy stejný název, ale jiné definice.  
  
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