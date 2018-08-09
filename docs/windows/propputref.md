---
title: propputref | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72fa9523b850e5c7d76b587c37b181f21df25c0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013977"
---
# <a name="propputref"></a>propputref
Určuje vlastnost nastavení funkci, která používá odkaz namísto hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
[propputref]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Propputref** C++ atribut má stejné funkce jako [propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) atribut MIDL.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **propputref**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Metoda|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|`propget`, `propput`|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   