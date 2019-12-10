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
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988405"
---
# <a name="serialization-ccli"></a>Serializace (C++/CLI)

Serializace (proces uložení stavu objektu nebo člena na trvalé médium) spravovaných tříd (včetně jednotlivých polí nebo vlastností) je podporována třídami <xref:System.SerializableAttribute> a <xref:System.NonSerializedAttribute>.

## <a name="remarks"></a>Poznámky

Použijte vlastní atribut **SerializableAttribute** pro spravovanou třídu k serializaci celé třídy nebo použijte pouze pro konkrétní pole nebo vlastnosti k serializaci částí spravované třídy. Použijte vlastní atribut **NonSerializedAttribute** k vyloučení polí nebo vlastností spravované třídy z serializace.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

V následujícím příkladu je třída `MyClass` (a vlastnost `m_nCount`) označena jako serializovatelný. Vlastnost `m_nData` však není serializována tak, jak je určena **Neserializovaným** vlastním atributem:

### <a name="code"></a>Kód

```cpp
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

Všimněte si, že oba atributy mohou být odkazovány pomocí jejich "krátkého" názvu "(**serializovatelný** a **neserializovaný**). To je podrobněji vysvětleno v tématu [použití atributů](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Viz také:

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
