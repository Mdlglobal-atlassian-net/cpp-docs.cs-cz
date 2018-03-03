---
title: "Příklad výsledků volání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eaa47af17e46f51ef92cc15b8d2275b2ed8e05f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="results-of-calling-example"></a>Příklad výsledků volání
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
  
## <a name="cdecl"></a>__cdecl  
 Název funkce dekorované C je "_MyFunc."  
  
 ![Konvence volání CDECL](../cpp/media/vc37i01.gif "vc37I01")  
Konvence volání __cdecl  
  
## <a name="stdcall-and-thiscall"></a>__stdcall a thiscall  
 C dekorované název (`__stdcall`) je "_MyFunc@20." Název C++ dekorované je vlastní.  
  
 ![&#95; &#95; stdcall a konvence volání thiscall](../cpp/media/vc37i02.gif "vc37I02")  
__Stdcall a thiscall – konvence volání  
  
## <a name="fastcall"></a>__fastcall  
 C dekorované název (`__fastcall`) je "@MyFunc@20." Název C++ dekorované je vlastní.  
  
 ![Konvence volání pro &#95; &#95; fastcall](../cpp/media/vc37i03.gif "vc37I03")  
Konvence volání __fastcall  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Příklad volání: prototyp a volání funkce](../cpp/calling-example-function-prototype-and-call.md)