---
title: RDX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.rdx
dev_langs: C++
helpviewer_keywords: rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d3384547f1c7648504137004ce90d0c0f41cda77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rdx"></a>rdx
Klíč registru vytvoří nebo upraví existující klíč registru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Název klíče, který se vytvořit nebo otevřít.  
  
 `valuename`(volitelné)  
 Určuje pole hodnoty nastavení. Pokud hodnota pole s tímto názvem již neexistuje v klíči, se přidá.  
  
 *regtype*  
 Typ klíče registru, který chcete přidat. Může být jedna z následujících: **text**, **dword**, **binární**, nebo `CString`.  
  
## <a name="remarks"></a>Poznámky  
 **Rdx** C++ atribut vytvoří nebo upraví existující klíč registru pro komponenty modelu COM. Atribut přidá BEGIN_RDX_MAP makro do objektu, který implementuje cílového člena. `RegistryDataExchange`, funkce Vložit v důsledku makro BEGIN_RDX_MAP lze použít k přenosu dat mezi registru a datové členy  
  
 Tento atribut lze použít ve spojení s [třída typu coclass](../windows/coclass.md), [progid](../windows/progid.md), nebo [vi_progid –](../windows/vi-progid.md) atributy nebo další atributy, které znamená jednu z těchto.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída** nebo `struct` člena|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Příklad  
 Následující kód přidá klíč registru s názvem MyValue systému popisující součást CMyClass COM.  
  
```  
// cpp_attr_ref_rdx.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
  
[module (name="MyLib")];  
  
class CMyClass {  
public:  
   CMyClass() {  
      strcpy_s(m_sz, "SomeValue");  
   }  
  
   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]   
   char m_sz[256];  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [registration_script –](../windows/registration-script.md)   
