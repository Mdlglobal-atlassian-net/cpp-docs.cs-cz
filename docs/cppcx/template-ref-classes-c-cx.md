---
title: "Třídy šablon ref (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b8bb720ef9275f9023cf15986f011573f4c510b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="template-ref-classes-ccx"></a>Třídy šablon ref (C + +/ CX)
Šablonami C++ nejsou vydané ve službě metadata a proto nemůže mít veřejných nebo chráněného usnadnění v programu. Standardní C++ šablony můžete použít samozřejmě interně v programu. Kromě toho můžete definovat třídu privátní ref jako šablona a třídu ref explicitně specializované šablony můžou deklarovat jako soukromý člen v třídě veřejné ref.  
  
## <a name="authoring-ref-class-templates"></a>Vytváření šablon ref – třída  
 Následující příklad ukazuje, jak deklarovat třídu privátní ref jako šablona a také jak deklarovat standardní šablona C++ a jak deklarovat je i jako členy do veřejného ref třídy. Všimněte si, že může být standardní šablona C++ specializuje pomocí prostředí Windows Runtime typu, v tomto případě Platform::String ^.  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)