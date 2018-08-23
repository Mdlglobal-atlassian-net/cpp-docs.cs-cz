---
title: Atributy (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7db8d6c527842cd3784623002fba001a4174c1fc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601135"
---
# <a name="attributes-ccx"></a>Atributy (C + +/ CX)
Atribut je zvláštním druhem třídy ref class, která můžou před do hranatých závorek pro typy Windows Runtime a metody k určení určitého chování, k vytvoření metadat. Několik předdefinovaných atributů, například [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)– se běžně používají v jazyce C + +/ CX kódu. Tento příklad ukazuje, jak je atribut aplikován na třídu:  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>Vlastní atributy  
 Můžete také definovat vlastní atributy. Vlastní atributy musí splňovat tato pravidla modulu Windows Runtime:  
  
-   Vlastní atributy může obsahovat jenom veřejné položky.  
  
-   Pole vlastních atributů může být inicializována, když je atribut aplikován na třídu.  
  
-   Pole může být jeden z těchto typů:  
  
    -   datový typ Int32 (int).  
  
    -   UInt32 (unsigned int).  
  
    -   bool  
  
    -   Platform::String ^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::type – ^  
  
    -   Veřejný výčet tříd (včetně výčtů definovaný uživatelem)  
  
 Následující příklad ukazuje, jak definovat vlastní atribut, kterou následně inicializujete při jeho použití.  
  
 [!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)