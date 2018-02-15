---
title: "Zabalení (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24fcd5b24d03b70901c0216c46211d2bdc935f21
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="boxing-ccx"></a>Zabalení (C + +/ CX)
*Zabalení* je typ proměnné hodnotu zabalení, jako [Windows::Foundation::DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)– nebo základní skalárního typu jako `int`– v třídě ref, když je proměnná předána metodu, která přebírá [ Platform::Object ^](../cppcx/platform-object-class.md) jako typ vstupu.  
  
## <a name="passing-a-value-type-to-an-object-parameter"></a>Předání typu hodnoty do objektu ^ parametr  
 I když není nutné explicitně pole proměnnou, do které předat parametru metody typu [Platform::Object ^](../cppcx/platform-object-class.md), budete muset explicitně převést zpět na původní typ při načtení hodnoty, které jste do dříve pole.  
  
 [!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]  
  
### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Pomocí Platform::IBox\<T > pro podporu typy hodnot s povolenou hodnotou Null  
 C# a Visual Basic podporují koncept typy hodnot s povolenou hodnotou Null. V jazyce C + +/ CX, můžete použít `Platform::IBox<T>` typ vystavit veřejné metody, které podporují parametry typu hodnot hodnotu Null. Následující příklad ukazuje C + +/ CX veřejná metoda, která vrátí hodnotu null, pokud volající C# předá hodnotu null pro jeden z argumentů.  
  
 [!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]  
  
 V klientovi C# XAML můžete ho využívají takto:  
  
```  
  
// C# client code  
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();  
    int? a = null;  
    int? b = 5;  
    var result = obj.Multiply(a,b); //result = null  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Přetypování (C + +/ CX)](../cppcx/casting-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)