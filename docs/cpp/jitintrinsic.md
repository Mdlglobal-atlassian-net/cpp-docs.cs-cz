---
title: jitintrinsic | Microsoft Docs
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
ms.openlocfilehash: 71cd88882ea104275e4c1a43ccf05494a859d303
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418751"
---
# <a name="jitintrinsic"></a>jitintrinsic
Označí funkci jako významnou pro 64bitový modul CLR (Common Language Runtime). Používáno pro určité funkce v knihovnách poskytnutých společností Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Poznámky  
 Direktiva `jitintrinsic` přidá k signatuře funkce klíčové slovo MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>).  
  
 Použití tohoto modifikátoru `__declspec` není doporučeno, protože může dojít k neočekávaným výsledkům.  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)