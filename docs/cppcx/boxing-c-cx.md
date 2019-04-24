---
title: Zabalení (C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 3c281229b509ef72d37400b2088a6663be1afe42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257957"
---
# <a name="boxing-ccx"></a>Zabalení (C++/CX)

*Zabalení* proměnné typu hodnoty jako například zahrnuje [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime)– nebo základní skalární typ. například `int`– v referenční třídě při proměnná je předána metodě, která přebírá [ Platform::Object ^](../cppcx/platform-object-class.md) jako jeho typ vstupu.

## <a name="passing-a-value-type-to-an-object-parameter"></a>Předání typu hodnoty na objekt ^ parametr

I když není nutné explicitně pole proměnnou umožní předat parametr metody typu [Platform::Object ^](../cppcx/platform-object-class.md), třeba při načtení hodnoty, které byly dříve zabalená explicitně přetypovat zpět do původního typu.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Pomocí Platform::ibox –\<T > pro podporu typů s možnou hodnotou Null

C# a Visual Basic podporují koncept typy s možnou hodnotou Null. V C++/CX, můžete použít `Platform::IBox<T>` typ zpřístupňují veřejných metod, které podporují parametry typu s možnou hodnotou Null. Následující příklad ukazuje C++/CX veřejnou metodu, která vrátí hodnotu null, když C# / / volající předává pro jeden z argumentů hodnotu null.

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

V jazyce C# XAML klienta můžete ho využívat takto:

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
[Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)
