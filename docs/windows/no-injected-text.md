---
title: no_injected_text – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc0dcba6597b6b8a3b37c240bf1c4a58f30b6b23
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020340"
---
# <a name="noinjectedtext"></a>no_injected_text
Zabrání kompilátoru vkládání kódu v důsledku použití atributu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[ no_injected_text(  
   boolean  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *Logická* (volitelné)  
 **Hodnota TRUE** žádný kód vložený, chcete-li **false** umožňující kódu vložit. **Hodnota TRUE** je výchozí nastavení.  
  
## <a name="remarks"></a>Poznámky  
 Nejběžnější použití nástroje **no_injected_text –** atributů C++, je [/Fx](../build/reference/fx-merge-injected-code.md) – možnost kompilátoru, která vloží **no_injected_text –** atributu do souboru .mrg.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Kdekoli|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   