---
title: Serializace (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6efd56655cb5b262eab7d7f14c197e11466fb8bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)