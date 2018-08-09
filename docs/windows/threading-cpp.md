---
title: Práce s vlákny (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e0e8b13a74c5b232e2662f80fc1cc8f80a1ffc9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652998"
---
# <a name="threading-c"></a>threading (C++)
Určuje model vláken pro objekt modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ threading(  
   model=enumeration  
) ]  
```  
  
### <a name="parameters"></a>Parametry  
 *model* (volitelné)  
 Jeden z následujících modely dělení na vlákna:  
  
-   `apartment` (podprocesový model apartment)  
  
-   `neutral` (Součásti rozhraní .NET framework bez uživatelského rozhraní)  
  
-   `single` (jednoduché dělení na vlákna)  
  
-   `free` (bez vláken)  
  
-   `both` (objektu apartment a volných vláken)  
  
 Výchozí hodnota je `apartment`.  
  
## <a name="remarks"></a>Poznámky  
 **Dělení na vlákna** C++ atribut se nezobrazují v souboru IDL vygenerovaný, ale budou použity v implementaci váš objekt modelu COM.  
  
 V projektech ATL Pokud [coclass](../windows/coclass.md) atribut je také k dispozici, model vláken určené *modelu* je předán jako parametr šablony [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) třídy , Vložit `coclass` atribut.  
  
 **Dělení na vlákna** atribut také chrání přístup k [event_source](../windows/event-source.md).  
  
## <a name="example"></a>Příklad  
 Najdete v článku [licenci](../windows/licensed.md) příklad ukázkový používání **dělení na vlákna**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, **– struktura**|  
|**Opakovatelné**|Ne|  
|**Vyžadované atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Com – atributy](../windows/com-attributes.md)   
 [– TypeDef, Enum, Union a struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atributy třídy](../windows/class-attributes.md)   
 [Podpora multithreadingu ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutrální bytů](http://msdn.microsoft.com/library/windows/desktop/ms681813)   