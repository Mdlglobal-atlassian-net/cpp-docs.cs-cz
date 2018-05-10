---
title: UUID (atributy C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e56793855b278e0631c39ebfcdc51669a001a24b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="uuid-c-attributes"></a>uuid (atributy C++)
Určuje jedinečné ID pro třídy nebo rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *uuid*  
 128-bit, jedinečný identifikátor.  
  
## <a name="remarks"></a>Poznámky  
 Pokud definice třídy nebo rozhraní neurčuje `uuid` atribut C++ a pak Visual C++ compiler bude poskytovat jeden. Pokud zadáte `uuid`, je nutné zahrnout uvozovky.  
  
 Pokud nezadáte `uuid`, bude kompilátor generovat stejný identifikátor GUID pro rozhraní nebo třídy se stejným názvem v projektech jiný atribut na počítači.  
  
 Uuidgen.exe nebo Guidgen.exe můžete použít ke generování vlastní jedinečné ID. (Chcete-li spustit některý z těchto nástrojů, klikněte na tlačítko **spustit** a klikněte na tlačítko **spustit** v nabídce. Pak zadejte název požadované nástroje.)  
  
 Při použití v projektu, který také nepoužívá ATL, určení `uuid` atribut je stejné jako zadání [uuid](../cpp/uuid-cpp.md) __declspec – modifikátor. Načíst `uuid` třídy, můžete použít [__uuidof –](../cpp/uuidof-operator.md)  
  
## <a name="example"></a>Příklad  
 Najdete v článku [vazbu](../windows/bindable.md) příklad pro ukázkové použití `uuid`.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`, `interface`, **– typ union**, `enum`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
