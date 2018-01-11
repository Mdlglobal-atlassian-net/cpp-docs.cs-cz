---
title: "Položka | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.entry
dev_langs: C++
helpviewer_keywords: entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ffd90ccdcce39ab73f1c1b550b466541dacf8a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="entry"></a>entry
V modulu určením vstupní bod v knihovně DLL Určuje exportované funkce nebo konstanta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ entry(  
   id  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 ID vstupního bodu.  
  
## <a name="remarks"></a>Poznámky  
 **Položka** atribut C++ má stejné funkce jako [položka](http://msdn.microsoft.com/library/windows/desktop/aa366815) MIDL atribut.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [idl_module –](../windows/idl-module.md) pro příklad použití **položka**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|`idl_module`atribut|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
