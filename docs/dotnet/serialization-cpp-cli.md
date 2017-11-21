---
title: Serializace (C + +/ CLI) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57ec673e945d0db14ce8fee0d477d7aeb2a9e238
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="serialization-ccli"></a>Serializace (C++/CLI)
Serializace (proces ukládání stavu objektu nebo člena do trvalého média) spravovaných tříd (včetně jednotlivých polí nebo vlastnosti) se nepodporuje <xref:System.SerializableAttribute> a <xref:System.NonSerializedAttribute> třídy.  
  
## <a name="remarks"></a>Poznámky  
 Použít **SerializableAttribute** vlastní atribut spravovanou třídu k serializaci celou třídu nebo jenom ke konkrétním pole nebo vlastnosti k serializaci částí spravované třídy. Použití **NonSerializedAttribute** vlastní atribut pole nebo vlastnosti spravované třídy z serializována.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu třída `MyClass` (a vlastnost `m_nCount`) je označena jako serializovatelný. Ale `m_nData` vlastnost není serializovat jako indikován **NonSerialized** vlastních atributů:  
  
### <a name="code"></a>Kód  
  
```  
// serialization_and_mcpp.cpp  
// compile with: /LD /clr  
using namespace System;  
  
[ Serializable ]  
public ref class MyClass {  
public:  
   int m_nCount;  
private:  
   [ NonSerialized ]  
   int m_nData;  
};  
```  
  
### <a name="comments"></a>Komentáře  
 Všimněte si, že oba atributy lze odkazovat pomocí jejich "krátkého názvu" (**Serializable** a **NonSerialized**). To se vysvětluje dále v [použití atributů](/dotnet/standard/attributes/applying-attributes).  
  
## <a name="see-also"></a>Viz také  
 [.NET – programování s C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)