---
title: Příklad výsledků volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- examples [C++], results of calling
- results, thiscall call
- results, __fastcall keyword call
- results, __cdecl call
- results, __stdcall call
ms.assetid: aa70a7cb-ba1d-4aa6-bd0a-ba783da2e642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e7b022925e22f021a2ddad1b3b9ef52924b25a3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939104"
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
  
## <a name="cdecl"></a>__cdecl  
 Název upravený funkce jazyka C je "_MyFunc."  
  
 ![Konvenci volání CDECL](../cpp/media/vc37i01.gif "vc37I01")  
Konvenci volání __cdecl  
  
## <a name="stdcall-and-thiscall"></a>__stdcall a thiscall  
 Dekorovaného názvu C (**__stdcall**) je "_MyFunc@20." Název C++ dekorovaných je speciální.  
  
 ![&#95;&#95;stdcall čárky a konvence volání thiscall](../cpp/media/vc37i02.gif "vc37I02")  
__Stdcall a konvence volání thiscall  
  
## <a name="fastcall"></a>__fastcall  
 Dekorovaného názvu C (**__fastcall**) je "@MyFunc@20." Název C++ dekorovaných je speciální.  
  
 ![Konvence pro volání &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
Konvence volání __fastcall  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)