---
title: Šablony referenčních tříd (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb322ae641a1821ed8434e0ea197acf752698e6
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592617"
---
# <a name="template-ref-classes-ccx"></a>Šablony referenčních tříd (C + +/ CX)
Šablony jazyka C++ nejsou publikované na metadata a proto nemůže mít veřejný nebo chráněný usnadnění ve svém programu. Standardní šablony jazyka C++ můžete samozřejmě používají interně ve svém programu. Kromě toho můžete definovat privátní ref class jako šablona a třídu ref explicitně specializovaný šablony lze deklarovat jako privátní člen třída public ref class.  
  
## <a name="authoring-ref-class-templates"></a>Vytváření šablon třídy ref  
 Následující příklad ukazuje, jak deklarovat soukromé ref class jako šablona a také jak deklarovat standardní šablony jazyka C++ a jak je deklarovat jako členy v třída public ref class. Všimněte si, že standardní šablony C++ může být specializovaná podle typu prostředí Windows Runtime, v tomto případě Platform::String ^.  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>Viz také  
 [Systém typů (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)