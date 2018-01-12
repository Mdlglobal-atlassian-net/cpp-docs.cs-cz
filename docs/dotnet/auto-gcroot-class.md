---
title: "auto_gcroot – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs: C++
helpviewer_keywords: auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bb203193d1568056c631d90a2e1f5b1cf1d00e5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="autogcroot-class"></a>auto_gcroot – třída
Správa automatického prostředků (jako je [auto_ptr – třída](../standard-library/auto-ptr-class.md)) které lze použít pro vložení do nativního typu virtuální popisovač.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_element_type`  
 Spravovaný typ, který má být vložen.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [auto_gcroot –](../dotnet/auto-gcroot.md)   
 [auto_gcroot – členové](../dotnet/auto-gcroot-members.md)   
 [Postupy: deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle – třída](../dotnet/auto-handle-class.md)