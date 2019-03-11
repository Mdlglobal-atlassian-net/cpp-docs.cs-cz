---
title: Serializace (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: 794a71ae9a146b691ba6a4377a7fdf2c3ddd3501
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741386"
---
# <a name="serialization-ccli"></a>Serializace (C++/CLI)

Serializace (proces ukládání stavu objektu nebo člen na trvalé médium) spravovaných tříd (včetně jednotlivá pole nebo vlastnosti) je podporován <xref:System.SerializableAttribute> a <xref:System.NonSerializedAttribute> třídy.

## <a name="remarks"></a>Poznámky

Použít **SerializableAttribute** vlastního atributu na spravovanou třídu k serializaci celá třída nebo použít pouze na konkrétní pole nebo vlastnosti, které chcete serializovat částí spravované třídy. Použití **NonSerializedAttribute** vlastního atributu na pole nebo vlastnosti spravovanou třídu z serializována.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

V následujícím příkladu třída `MyClass` (a vlastnost `m_nCount`) je označen jako serializovatelný. Ale `m_nData` vlastnost se neserializuje je uvedené **NonSerialized** vlastního atributu:

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

Všimněte si, že oba atributy můžete odkazovat pomocí jejich "krátký název" (**Serializable** a **NonSerialized**). To je vysvětleno dále v [použití atributů](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Viz také:

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
