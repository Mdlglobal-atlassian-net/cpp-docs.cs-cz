---
title: "emitidl – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.emitidl
dev_langs:
- C++
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55fc74eef3d2ead7312f7dca46f20c3a1ed7ba91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="emitidl"></a>emitidl
Určuje, zda jsou všechny následné IDL – atributy zpracovat a uložena v souboru generovaného IDL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>Parametry  
*Stav*  
Jednu z těchto hodnot: **true**, **false**, **vynutit**, **s omezeným přístupem**, **nabízené**, nebo **pop**.  
  
-   Pokud **true**, všechny kategorie IDL – atributy v souboru zdrojového kódu jsou umístěny v souboru generovaného IDL. Toto je výchozí nastavení pro **emitidl –**.  
  
-   Pokud **false**, všechny kategorie IDL – atributy v souboru zdrojového kódu nejsou uloženy do souboru generovaného IDL.  
  
-   Pokud **s omezeným přístupem**, umožňuje IDL – atributy v souboru bez [modulu](../windows/module-cpp.md) atribut. Kompilátor negeneruje souboru IDL.  
  
-   Pokud **vynutit**, přepsání následné **s omezeným přístupem** atribut, který vyžaduje soubor, který chcete mít **modulu** atribut v případě, že existují IDL atributy v souboru.  
  
-   **nabízená** umožňuje uložit aktuální **emitidl –** nastavení interní **emitidl –** zásobník a **pop** umožňuje nastavíte **emitidl –**na jakémkoli hodnota je v horní části interní **emitidl –** zásobníku.  
  
`defaultimports=`*Logická hodnota* \(volitelné)  
-   Pokud *boolean* je **true**, docobj.idl je importovat do generovaného .idl souboru. Navíc pokud souboru IDL se stejným názvem jako .h soubor, který `#include` do zdrojových kód najít ve stejném adresáři jako soubor h a potom soubor generovaný .idl obsahuje příkaz import pro tento soubor .idl.  
  
-   Pokud *boolean* je **false**, docobj.idl není importován do generovaného .idl souboru. Je nutné explicitně naimportovat soubory .idl s [importovat](../windows/import.md).  
  
## <a name="remarks"></a>Poznámky  
Po **emitidl –** C++ atribut se vyskytuje v souboru se zdrojovým kódem, kategorie IDL – atributy, které jsou umístěny v souboru generovaného IDL. Pokud je žádné **emitidl –** výstup do souboru generovaného IDL jsou atribut IDL – atributy v souboru se zdrojovým kódem.  
  
Je možné, že více **emitidl –** atributů v souboru zdrojového kódu. Pokud `[emitidl(false)];` se vyskytuje v souboru bez následné `[emitidl(true)];`, pak se do souboru generovaného .idl zpracovávají žádné atributy.  
  
Pokaždé, když kompilátor narazí do nového souboru **emitidl –** implicitně nastavena na **true**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
[Atributy kompilátoru](../windows/compiler-attributes.md)   
[Samostatné atributy](../windows/stand-alone-attributes.md)   
[Ukázky atributů](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)