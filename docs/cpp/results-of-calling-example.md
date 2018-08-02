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
ms.openlocfilehash: 9c49457aecb93b16ffb294f88e4f6643826492e2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465688"
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
  
## <a name="cdecl"></a>__cdecl  
 Název upravený funkce jazyka C je "_MyFunc."  
  
 ![Konvenci volání CDECL](../cpp/media/vc37i01.gif "vc37I01")  
**__Cdecl** konvence volání  
  
## <a name="stdcall-and-thiscall"></a>__stdcall a thiscall  
 Dekorovaného názvu C (**__stdcall**) je "_MyFunc@20." Název C++ dekorovaných je speciální.  
  
 ![&#95;&#95;stdcall čárky a konvence volání thiscall](../cpp/media/vc37i02.gif "vc37I02")  
__Stdcall a konvence volání thiscall  
  
## <a name="fastcall"></a>__fastcall  
 Dekorovaného názvu C (**__fastcall**) je "@MyFunc@20." Název C++ dekorovaných je speciální.  
  
 ![Konvence pro volání &#95; &#95;fastcall](../cpp/media/vc37i03.gif "vc37I03")  
Konvence volání __fastcall  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)