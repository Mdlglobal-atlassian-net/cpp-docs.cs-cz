---
title: retval | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6f17f44e520018f82dc82abe88427a2410d68e7
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606348"
---
# <a name="retval"></a>retval
Označí parametr, který přijímá návratovou hodnotu člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[retval]  
```  
  
## <a name="remarks"></a>Poznámky  
 **Retval** C++ atribut má stejné funkce jako [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) atribut MIDL.  
  
 **retval** musí být uvedena v posledním argumentu v deklaraci funkce.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [umožňujících vazbu](../windows/bindable.md) ukázkový používání **retval**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Rozhraní parametrů, metody rozhraní|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**out**|  
|**Neplatné atributy**|**in**|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   