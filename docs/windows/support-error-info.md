---
title: support_error_info – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.support_error_info
dev_langs:
- C++
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c366a379d15e50aabdc3c2157f57f85b6b5b33b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="supporterrorinfo"></a>support_error_info
Implementuje podporu pro vrácení podrobné chyby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ support_error_info(  
   error_interface=uuid  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 **error_interface**  
 Identifikátor implementace rozhraní **IErrorInfo**.  
  
## <a name="remarks"></a>Poznámky  
 **Support_error_info –** C++ atribut implementuje podporu pro vrácení podrobné, kontextové chyb, kterými cílový objekt do klienta. Pro objekt pro podporu chyby, metody **IErrorInfo** rozhraní musí být implementována objektem. Další informace najdete v tématu [podpora IDispatch a IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md).  
  
 Přidá tento atribut [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) jako základní třída pro cílový objekt. Výsledkem je výchozí implementaci třídy **ISupportErrorInfo** a je možné použít při jednom rozhraní generuje chyby na objekt.  
  
## <a name="example"></a>Příklad  
 Následující kód přidá výchozí podporu **ISupportErrorInfo** rozhraní k `CMyClass` objektu.  
  
```  
// cpp_attr_ref_support_error_info.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="mymod")];  
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]  
__interface IMyErrors  
{  
};  
  
[ coclass, support_error_info("IMyErrors"),  
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]  
class CMyClass  
{  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**class**|  
|**Opakovatelných**|Ano|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
