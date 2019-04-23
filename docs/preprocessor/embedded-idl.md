---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: c46924d2757d01a934c21a70f23e6556f6a10fd3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034086"
---
# <a name="embeddedidl"></a>embedded_idl

**Specifické pro C++**

Určuje, že knihovna typů je zapsána do souboru .tlh se zachovaným kódem atributem generován.

## <a name="syntax"></a>Syntaxe

```
embedded_idl[("param")]
```

### <a name="parameters"></a>Parametry

*param*<br/>
Může být jedna ze dvou hodnot:

- **emitidl**: Informace o typu naimportované z knihovny typelib bude k dispozici v generované projektu s atributy IDL.  Toto je výchozí nastavení a bude platit, pokud nezadáte parametr `embedded_idl`.

- **no_emitidl**: Informace o typu naimportované z knihovny typelib nebudou k dispozici v generované projektu s atributy IDL.

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

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)