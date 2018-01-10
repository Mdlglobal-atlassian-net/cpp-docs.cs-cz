---
title: Atributy (C + +/ CX) | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6dcd3818d21b644211891ae4779a6b9bf5074e6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-ccx"></a>Atributy (C + +/ CX)
Atribut je zvláštní druh ref třídu, která před lze v hranatých závorkách na prostředí Windows Runtime typy a metody k určení určitého chování při vytváření metadat. Několik předdefinovaných atributy – například [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)– běžně se používají v jazyce C + +/ CX kódu. Tento příklad ukazuje, jak je atribut použito pro třídu:  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>Vlastní atributy  
 Můžete také definovat vlastní atributy. Vlastní atributy musí splňovat tato pravidla prostředí Windows Runtime:  
  
-   Vlastní atributy může obsahovat pouze veřejná pole.  
  
-   Pole vlastních atributů může být inicializována při použití atributu na třídu.  
  
-   Pole může být jedním z těchto typů:  
  
    -   Int32 (int)  
  
    -   UInt32 (bez znaménka int)  
  
    -   bool  
  
    -   Platform::String ^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::type ^  
  
    -   Veřejný výčet tříd (zahrnuje výčty definovaný uživatelem)  
  
 Další příklad ukazuje, jak definovat vlastní atribut a inicializujte ho, pokud ji používáte.  
  
 [!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)