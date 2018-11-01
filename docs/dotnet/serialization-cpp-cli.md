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
ms.openlocfilehash: 74810328d654787be46794a31d857eb3fd0731ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478140"
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

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)