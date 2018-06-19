---
title: dělení na vlákna (C++) | Microsoft Docs
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
ms.openlocfilehash: f21ea8c16b4e09a5ad1845a10797be00f91b0d8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891321"
---
# <a name="threading-c"></a>threading (C++)
Určuje model vláken pro objekt COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 ***model*** (volitelné)  
 Jedna z následujících modely vláken:  
  
-   **Apartment** (dělení objektu apartment)  
  
-   **neutrální** (součásti rozhraní .NET Framework bez uživatelského rozhraní)  
  
-   **jeden** (jednoduché vlákna)  
  
-   **volné** (bez dělení na vlákna)  
  
-   **obě** (apartment a volných vláken)  
  
 Výchozí hodnota je **apartment**.  
  
## <a name="remarks"></a>Poznámky  
 **Dělení na vlákna** atribut C++ v souboru generovaného IDL nezobrazí, ale se použije k implementaci objektu COM.  
  
 V projekty knihovny ATL Pokud [třída typu coclass](../windows/coclass.md) atribut je přítomen, model vláken určeného *modelu* se předá jako parametr šablony k [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) – třída , vložená **třída typu coclass** atribut.  
  
 **Dělení na vlákna** atribut také chrání přístup k [event_source –](../windows/event-source.md).  
  
## <a name="example"></a>Příklad  
 Najdete v článku [licenci](../windows/licensed.md) příklad pro ukázkové použití **dělení na vlákna**.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Podpora více vláken ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutrální Apartment](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
