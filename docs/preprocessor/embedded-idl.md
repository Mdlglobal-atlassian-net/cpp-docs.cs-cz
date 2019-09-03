---
title: importovat atribut embedded_idl
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216324"
---
# <a name="embedded_idl-import-attribute"></a>importovat atribut embedded_idl

**C++Konkrétní**

Určuje, zda je knihovna typů zapsána `.tlh` do souboru s zachovaným kódem generovaným atributem.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **embedded_idl** [ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>Parametry

**emitidl**\
Informace o typu importované z *knihovny typů* jsou k dispozici v IDL generovaném pro projekt s atributy. Toto chování je výchozí a je platné, pokud nezadáte parametr do `embedded_idl`.

**"no_emitidl"** \
Informace o typu importované z *knihovny typů* nejsou přítomny v IDL generovaném pro projekt s atributy.

## <a name="example"></a>Příklad

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
