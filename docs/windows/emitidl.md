---
title: emitidl | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 4c52b905420dcb576705d63be7d7bdce27c5eea6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015240"
---
# <a name="emitidl"></a>emitidl
Určuje, zda jsou všechny následné IDL – atributy zpracovat a umístí do generovaného souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>Parametry  
*Stav*  
Jednu z těchto hodnot: `true`, `false`, `forced`, `restricted`, `push`, nebo `pop`.  
  
-   Pokud `true`, atributy IDL kategorie v souboru zdrojového kódu jsou umístěny v souboru generovaného IDL. Toto je výchozí nastavení pro **emitidl**.  
  
-   Pokud `false`, atributy IDL kategorie v souboru zdrojového kódu nejsou umístěny v souboru generovaného IDL.  
  
-   Pokud `restricted`, umožňuje IDL – atributy, které se v souboru bez [modulu](../windows/module-cpp.md) atribut. Kompilátor negeneruje souboru IDL.  
  
-   Pokud `forced`, přepíše následné `restricted` atribut, který vyžaduje soubor mít `module` atribut, pokud existují IDL – atributy v souboru.  
  
-   `push` Umožňuje uložit aktuální **emitidl** nastavení na interní **emitidl** zásobníku, a `pop` umožňuje nastavit **emitidl** na libovolné hodnoty je v horní části vnitřní **emitidl** zásobníku.  
  
`defaultimports=`*Logická* \(volitelné)  
-   Pokud *logická* je **true**, docobj.idl se importují do generovaného souboru. Navíc pokud souboru IDL se stejným názvem jako. h: soubor, který jste `#include` do zdrojových kód nachází ve stejném adresáři jako soubor hlaviček, pak generovaného souboru obsahuje příkaz import pro tento soubor .idl.  
  
-   Pokud *logická* je **false**, docobj.idl není importován do generovaného souboru. Musíte explicitně importujete soubory .idl s [importovat](../windows/import.md).  
  
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
  
Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
[Atributy kompilátoru](../windows/compiler-attributes.md)   
[Samostatné atributy](../windows/stand-alone-attributes.md)   
[Ukázky atributů](http://msdn.microsoft.com/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)