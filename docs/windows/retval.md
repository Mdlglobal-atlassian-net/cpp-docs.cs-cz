---
title: "retval – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.retval
dev_langs: C++
helpviewer_keywords: retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf7aa0cf8dd9767f603807ee18e23fe02d3446c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="retval"></a>retval
Označí parametr, který obdrží hodnotu vrácenou člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[retval]  
  
```  
  
## <a name="remarks"></a>Poznámky  
 **Retval** atribut C++ má stejné funkce jako [retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL atribut.  
  
 **retval –** musí být uvedena na poslední argument v deklaraci funkce.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [vazbu](../windows/bindable.md) pro ukázkové použití **retval**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Parametr rozhraní, rozhraní – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**out**|  
|**Neplatné atributy**|**in**|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy parametru](../windows/parameter-attributes.md)   
 [Atributy metody](../windows/method-attributes.md)   
