---
title: Namespace Platform::metadata | Microsoft Docs
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::Metadata
dev_langs: C++
helpviewer_keywords: Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce300956045c0a111deef6d514d1699bea8d794b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="platformmetadata-namespace"></a>Namespace Platform::metadata
Tento obor názvů obsahuje atributy, které upravují deklarace typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
namespace Platform {  
   namespace Metadata {  
}}  
```  
  
### <a name="members"></a>Členové  
 I když tento obor názvů je určený pro interní použití, prohlížeče zobrazí následující členy tento obor názvů.  
  
|Název|Poznámka|  
|----------|------------|  
|Atribut|Základní třídu pro atributy.|  
|[Platform::Metadata::DefaultMemberAttribute – atribut](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|Určuje upřednostňovaný funkce k vyvolání mezi několik možných přetížených funkcí.|  
|[Atribut Platform::metadata::FlagsAttribute](../cppcx/platform-metadata-flagsattribute-attribute.md)příznaky|Deklaruje výčet jako výčet bitových polí.<br /><br /> Následující příklad ukazuje, jak se má použít `Flags` atribut výčet.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|  
|[Platform::metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|Zajišťuje, že privátní ref třída má název třídy platný runtime.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Platform`  
  
### <a name="requirements"></a>Požadavky  
 **Metadata:** platform.winmd  
  
 **Namespace:** Platform::Metadata  
  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](platform-namespace-c-cx.md)