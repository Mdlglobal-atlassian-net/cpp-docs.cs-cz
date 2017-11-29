---
title: ComPtr::Reset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1227a2d8c38fd26b82e09d58326cc3790a4e7b14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comptrreset"></a>ComPtr::Reset
Uvolní všechny odkazy pro ukazatele na rozhraní, které souvisí s Tento ComPtr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet odkazů na vydání, pokud existuje.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)