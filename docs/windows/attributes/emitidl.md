---
title: emitidl (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 6c4055e0f14bced1e5047fc502a4bf274126f804
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031631"
---
# <a name="emitidl"></a>emitidl

Určuje, zda jsou všechny následné IDL – atributy zpracovat a umístí do generovaného souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Parametry

*state*<br/>
Jednu z těchto hodnot: `true`, `false`, `forced`, `restricted`, `push`, nebo `pop`.

- Pokud `true`, atributy IDL kategorie v souboru zdrojového kódu jsou umístěny v souboru generovaného IDL. Toto je výchozí nastavení pro **emitidl**.

- Pokud `false`, atributy IDL kategorie v souboru zdrojového kódu nejsou umístěny v souboru generovaného IDL.

- Pokud `restricted`, umožňuje IDL – atributy, které se v souboru bez [modulu](module-cpp.md) atribut. Kompilátor negeneruje souboru IDL.

- Pokud `forced`, přepíše následné `restricted` atribut, který vyžaduje soubor mít `module` atribut, pokud existují IDL – atributy v souboru.

- `push` Umožňuje uložit aktuální **emitidl** nastavení na interní **emitidl** zásobníku, a `pop` umožňuje nastavit **emitidl** na libovolné hodnoty je v horní části vnitřní **emitidl** zásobníku.

`defaultimports=`*Logická* \(volitelné)

- Pokud *logická* je **true**, docobj.idl se importují do generovaného souboru. Navíc pokud souboru IDL se stejným názvem jako. h: soubor, který jste `#include` do zdrojových kód nachází ve stejném adresáři jako soubor hlaviček, pak generovaného souboru obsahuje příkaz import pro tento soubor .idl.

- Pokud *logická* je **false**, docobj.idl není importován do generovaného souboru. Musíte explicitně importujete soubory .idl s [importovat](import.md).

## <a name="remarks"></a>Poznámky

Po **emitidl** C++ atribut dochází v souboru zdrojového kódu, atributy IDL kategorií jsou umístěny v souboru generovaného IDL. Pokud není žádný **emitidl** atribut IDL – atributy v souboru zdrojového kódu se zobrazují v souboru generovaného IDL.

Je možné mít více **emitidl** atributy v souboru zdrojového kódu. Pokud `[emitidl(false)];` dochází v souboru bez následné `[emitidl(true)];`, pak žádné atributy jsou zpracovány do souboru generovaného IDL.

Pokaždé, když kompilátor narazí nový soubor **emitidl** implicitně nastavena na **true**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)
