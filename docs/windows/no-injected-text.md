---
title: "no_injected_text – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.no_injected_text
dev_langs: C++
helpviewer_keywords: no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7856da95c8bd7563d66fc901bdac1f2a931b7384
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="noinjectedtext"></a>no_injected_text
Kompilátor brání vložení kódu v důsledku použití atributu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ no_injected_text(  
   boolean  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 `boolean`(volitelné)  
 **Hodnota TRUE,** žádný kód vložili, chcete-li **false** umožňující kód vložit. **Hodnota TRUE,** je výchozí.  
  
## <a name="remarks"></a>Poznámky  
 Nejběžnější použití **no_injected_text –** C++ atribut je [/Fx](../build/reference/fx-merge-injected-code.md) – možnost kompilátoru, která vloží **no_injected_text –** atribut do souboru .mrg.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Odkudkoli|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy kompilátoru](../windows/compiler-attributes.md)   
