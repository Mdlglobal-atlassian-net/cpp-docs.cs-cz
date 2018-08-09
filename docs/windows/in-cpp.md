---
title: v aplikaci (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.in
dev_langs:
- C++
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8522b3af527267706a2e2697b88049a38b0f092f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017188"
---
# <a name="in-c"></a>in (C++)
Označuje, že je parametr předat z volající procedury do volané procedury.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[in]  
```  
  
## <a name="remarks"></a>Poznámky  
 **v** C++ atribut má stejné funkce jako [v](http://msdn.microsoft.com/library/windows/desktop/aa367051) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Zobrazit [umožňujících vazbu](../windows/bindable.md) příklad, jak používat **v**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní parametrů, metody rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|**retval**|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [Výchozí hodnota](../windows/defaultvalue.md)   
 [ID](../windows/id.md)   
 [out](../windows/out-cpp.md)   