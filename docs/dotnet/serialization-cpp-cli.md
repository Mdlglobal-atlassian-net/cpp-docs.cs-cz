---
title: Serializace (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f4a410da74c37ee722c04f21e2cde906b9d061d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164557"
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