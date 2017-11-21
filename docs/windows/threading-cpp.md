---
title: "dělení na vlákna (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.threading
dev_langs: C++
helpviewer_keywords: threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c85287a590dfa9cf3c931ce358dca8b303f4737a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|**Platí pro**|**Třída**,`struct`|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|**Třída typu coclass**|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [COM – atributy](../windows/com-attributes.md)   
 [TypeDef, Enum, Union a Struct – atributy](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
 [Podpora více vláken ve starším kódu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutrální Apartment](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
