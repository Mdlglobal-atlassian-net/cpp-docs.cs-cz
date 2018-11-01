---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 202d5b23a5e2e8e673e3c220b9618cfe6cd4f0d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525603"
---
# <a name="embeddedidl"></a>embedded_idl

**Specifické pro C++**

Určuje, že knihovna typů je zapsána do souboru .tlh se zachovaným kódem atributem generován.

## <a name="syntax"></a>Syntaxe

```
embedded_idl[("param")]
```

### <a name="parameters"></a>Parametry

*Param*<br/>
Může být jedna ze dvou hodnot:

- **emitidl**: informace o typu naimportované z knihovny typelib bude k dispozici v generované projektu s atributy IDL.  Toto je výchozí nastavení a bude platit, pokud nezadáte parametr `embedded_idl`.

- **no_emitidl**: informace o typu naimportované z knihovny typelib nemusí být v generované projektu s atributy IDL.

## <a name="example"></a>Příklad

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

## <a name="remarks"></a>Poznámky

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)