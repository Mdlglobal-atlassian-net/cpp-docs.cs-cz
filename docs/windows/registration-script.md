---
title: registration_script – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.registration_script
dev_langs:
- C++
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4385dd12fccafb154a637dd5260764667d3887a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="registrationscript"></a>registration_script
Spustí skript zadanou vlastní registraci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ registration_script(   
   script   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Skript*  
 Úplná cesta k souboru vlastní registrace skript (.). Hodnota **žádné**, jako například `script = "none"`, označuje, že coclass nemá žádné požadavky na registraci.  
  
## <a name="remarks"></a>Poznámky  
 **Registration_script –** C++ atribut provede vlastní registrace skript určeného **skriptu**. Pokud tento atribut nezadá, použije se soubor standardní .rgs (obsahující informace o registraci komponenty). Další informace o .rgs souborů najdete v tématu [ATL komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md).  
  
 Tento atribut vyžaduje, aby [třída typu coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atribut (nebo jiný atribut, který zahrnuje jednu z těchto) také použít stejného elementu.  
  
## <a name="example"></a>Příklad  
 Následující kód určuje, že součást má skript registru s názvem cpp_attr_ref_registration_script.rgs.  
  
```  
// cpp_attr_ref_registration_script.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="REG")];  
  
[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]  
__interface IFace {};  
  
// requires "cpp_attr_ref_registration_script.rgs"  
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist  
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),  
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]  
class CMyClass:public IFace {};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Jeden nebo více z následujících: **třída typu coclass**, **progid**, nebo **vi_progid –**.|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [rdx](../windows/rdx.md)   
