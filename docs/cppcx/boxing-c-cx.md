---
title: ZabaleníC++(/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 90c5af31efc6523683227dbf54c85390bc98510a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740669"
---
# <a name="boxing-ccx"></a>ZabaleníC++(/CX)

*Zabalením* je zalomení proměnné typu hodnoty, jako je například [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime), nebo základní skalární `int`typ jako – v referenční třídě, když je proměnná předána metodě, která jako svůj vstupní typ používá [Platform:: Object ^.](../cppcx/platform-object-class.md) .

## <a name="passing-a-value-type-to-an-object-parameter"></a>Předání typu hodnoty do objektu ^ Parameter

I když nemusíte explicitně zadat proměnnou pro předání parametru metody typu [Platform:: Object ^](../cppcx/platform-object-class.md), musíte explicitně přetypovat zpět na původní typ při načtení hodnot, které byly dříve zabaleny.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Použití Platform:: iBox\<T > pro podporu typů hodnot s možnou hodnotou null

C#a Visual Basic podporují koncept typů s možnou hodnotou null. V C++/CX můžete použít `Platform::IBox<T>` typ k vystavení veřejných metod, které podporují parametry typu hodnoty s možnou hodnotou null. Následující příklad ukazuje veřejnou metodu C++/CX, která vrací hodnotu null v případě C# , že volající předává hodnotu null pro jeden z argumentů.

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

V klientovi C# XAML ho můžete využít takto:

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null
```

## <a name="see-also"></a>Viz také:

[Systém typů (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Přetypování (C++/CX)](../cppcx/casting-c-cx.md)<br/>
[Referenční zdroje k jazyku C++/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
