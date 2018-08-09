---
title: UUID (atributy C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 07258b2f7416b0747be81075f4c037a6be54e7a6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647070"
---
# <a name="uuid-c-attributes"></a>uuid (atributy C++)
Určuje jedinečné ID pro třídu nebo rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ uuid(  
   "uuid"  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *uuid*  
 128-bit, jedinečný identifikátor.  
  
## <a name="remarks"></a>Poznámky  
 Pokud není zadán definici třídy nebo rozhraní **uuid** atribut C++ a kompilátor Visual C++ bude poskytovat jednu. Pokud zadáte **uuid**, musí obsahovat uvozovky.  
  
 Pokud nezadáte **uuid**, pak bude kompilátor generovat stejný identifikátor GUID pro rozhraní nebo třídy se stejným názvem v projektech různých atributů v počítači.  
  
 Uuidgen.exe nebo Guidgen.exe můžete použít ke generování vlastní jedinečné ID. (Chcete-li spustit některý z těchto nástrojů, klikněte na tlačítko **Start** a klikněte na tlačítko **spustit** v nabídce. Zadejte název požadované nástroje.)  
  
 Při použití v projektu, která ATL také nepoužívá, určení **uuid** atribut je stejné jako zadání [uuid](../cpp/uuid-cpp.md) **__declspec** modifikátor. Načíst **uuid** třídy, můžete použít [__uuidof](../cpp/uuidof-operator.md)  
  
## <a name="example"></a>Příklad  
 Najdete v článku [umožňujících vazbu](../windows/bindable.md) příklad ukázkový používání **uuid**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **struktura**, **rozhraní**, **sjednocení**, **výčtu**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [IDL – atributy](../windows/idl-attributes.md)   
 [Atributy rozhraní](../windows/interface-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   