---
title: idl_quote (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168026"
---
# <a name="idl_quote"></a>idl_quote

Umožňuje použít konstrukce IDL, které nejsou podporovány v aktuální verzi vizuálu C++ a předávat je do generovaného souboru. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Parametry

*textové*<br/>
Název atributu, který zamýšlíte, C++ aby kompilátor společnosti Microsoft předával do generovaného souboru IDL bez vrácení chyby kompilátoru.

## <a name="remarks"></a>Poznámky

Pokud je atribut **idl_quote** C++ použit jako samostatný atribut (se středníkem po pravé závorce), pak je *text* umístěn do sloučeného souboru IDL, jak je. Pokud se pro symbol používá **idl_quote** , *text* je umístěn v rámci bloku atributu pro daný symbol.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak lze zadat nepodporovaný atribut (pomocí **v**, který je podporován) a jak definovat a použít nedefinovanou konstruktor. idl:

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

Tento kód způsobuje `MYFLOT` a `MYDUB` a *textovou* položku, která se má umístit do generovaného souboru IDL. Parametr *Name* vynutí umístění *textu* před cokoli, co odkazuje na *název* ve vygenerovaném souboru IDL. Parametr *závislosti* vynutí, aby byly definice seznamu závislostí umístěny před *textem* v generovaném souboru IDL.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)
