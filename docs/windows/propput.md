---
title: propput | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propput
dev_langs:
- C++
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af96a6825c88fb479709b2b6138f3fe6286b8b17
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016808"
---
# <a name="propput"></a>propput
Určuje funkci, která nastavení vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[propput]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Propput** C++ atribut má stejné funkce jako [propput](http://msdn.microsoft.com/library/windows/desktop/aa367146) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **propput**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|`propget`, `propputref`|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propputref](../windows/propputref.md)