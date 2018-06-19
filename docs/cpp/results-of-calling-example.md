---
title: Příklad výsledků volání | Microsoft Docs
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
ms.openlocfilehash: 5cc5d5f96b5ffabd5397f26b6ff1372232fe0cd6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421416"
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
  
## <a name="cdecl"></a>__cdecl  
 Název funkce dekorované C je "_MyFunc."  
  
 ![Konvence volání CDECL](../cpp/media/vc37i01.gif "vc37I01")  
Konvence volání __cdecl  
  
## <a name="stdcall-and-thiscall"></a>__stdcall a thiscall  
 C dekorované název (`__stdcall`) je "_MyFunc@20." Název C++ dekorované je vlastní.  
  
 ![&#95;&#95;stdcall a konvence volání thiscall](../cpp/media/vc37i02.gif "vc37I02")  
__Stdcall a thiscall – konvence volání  
  
## <a name="fastcall"></a>__fastcall  
 C dekorované název (`__fastcall`) je "@MyFunc@20." Název C++ dekorované je vlastní.  
  
 ![Konvence pro volání &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
Konvence volání __fastcall  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)