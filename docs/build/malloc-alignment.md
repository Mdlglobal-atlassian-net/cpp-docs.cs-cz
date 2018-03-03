---
title: "malloc – zarovnání | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d9acaf1c8912e1b563bb5d05ae600d1430049e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="malloc-alignment"></a>malloc – zarovnání
[malloc –](../c-runtime-library/reference/malloc.md) záruku, že se k vrácení paměti, která vhodným způsobem je zarovnán pro ukládání libovolný objekt, který má základní zarovnání a který může přizpůsobit množství paměti, který je přidělen. A *základní zarovnání* je zarovnání, která je menší než nebo rovna největší zarovnání, která je podporována implementací bez specifikace zarovnání. (V jazyce Visual C++, to je vyžadované pro zarovnání `double`, nebo 8 bajtů. V kódu, která je cílena 64bitové platformy je 16 bajtů.) Například by být zarovnána přidělení čtyř bajtů na hranici, která podporuje všechny čtyři bajtů nebo menší objekt.  
  
 Visual C++ umožňuje typy, které mají *rozšířené zarovnání*, která se také označují jako *přepsání zarovnán* typy. Například typy SSE [__m128](../cpp/m128.md) a `__m256`a typy, které jsou deklarovány s použitím `__declspec(align( n ))` kde `n` je větší než 8, rozšířili zarovnání. Zarovnání paměti na hranici, který je vhodný pro objekt, který vyžaduje rozšířené zarovnání není zaručena podle `malloc`. Chcete-li přidělit paměť pro přepsání zarovnaný typy, použijte [_aligned_malloc –](../c-runtime-library/reference/aligned-malloc.md) a související funkce.  
  
## <a name="see-also"></a>Viz také  
 [Použití zásobníku](../build/stack-usage.md)   
 [Zarovnat](../cpp/align-cpp.md)   
 [__declspec](../cpp/declspec.md)