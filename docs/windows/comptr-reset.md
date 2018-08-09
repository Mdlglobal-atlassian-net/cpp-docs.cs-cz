---
title: ComPtr::Reset | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 74f26f520be276de863c612718de8520bffc1219
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649702"
---
# <a name="comptrreset"></a>ComPtr::Reset
Uvolní všechny odkazy pro ukazatele na rozhraní, které souvisí s tímto **ComPtr**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet odkazů vydání, pokud existuje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)