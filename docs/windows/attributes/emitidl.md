---
title: emitidl (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.emitidl
dev_langs:
- C++
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 520b9bf8d6a71593acd95ebaac98a72036fcabf2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070020"
---
# <a name="emitidl"></a>emitidl

Určuje, zda jsou všechny následné IDL – atributy zpracovat a umístí do generovaného souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
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
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)
