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
ms.openlocfilehash: f0b114089567de06a71f15b69c556e08d1e4e9c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404077"
---
# <a name="jitintrinsic"></a>jitintrinsic
Označí funkci jako významnou pro 64bitový modul CLR (Common Language Runtime). Používáno pro určité funkce v knihovnách poskytnutých společností Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Poznámky  
 **jitintrinsic** přidá klíčové slovo MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) k signatuře funkce.  
  
 Není doporučeno použití této funkce **__declspec** modifikátor, jako výsledky neočekávané situace může nastat.  
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)