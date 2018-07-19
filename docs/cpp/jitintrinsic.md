---
title: jitintrinsic | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8b1c932f53651b8ad116139724348714b183506
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939387"
---
# <a name="jitintrinsic"></a>jitintrinsic
Označí funkci jako významnou pro 64bitový modul CLR (Common Language Runtime). Používáno pro určité funkce v knihovnách poskytnutých společností Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Poznámky  
 Direktiva `jitintrinsic` přidá k signatuře funkce klíčové slovo MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>).  
  
 Není doporučeno použití této funkce **__declspec** modifikátor, jako výsledky neočekávané situace může nastat.  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)