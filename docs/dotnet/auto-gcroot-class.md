---
title: auto_gcroot – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: da63d58136d61bbea75daa90ac01cee5b44ac86d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039098"
---
# <a name="autogcroot-class"></a>auto_gcroot – třída
Správa automatického prostředků (jako [auto_ptr – třída](../standard-library/auto-ptr-class.md)) který slouží k vložení virtuální popisovač do nativního typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>Parametry  
*_element_type*<br/>
Spravovaný typ má být vložen.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr –  
  
## <a name="see-also"></a>Viz také  
 [auto_gcroot –](../dotnet/auto-gcroot.md)   
 [auto_gcroot – členové](../dotnet/auto-gcroot-members.md)   
 [Postupy: deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle – třída](../dotnet/auto-handle-class.md)