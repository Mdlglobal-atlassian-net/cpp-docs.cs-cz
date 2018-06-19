---
title: Referenční dokumentace (C++ AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c39528bf3b1e6c9235e4b2daabcd8bbddd0d52f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685889"
---
# <a name="reference-c-amp"></a>Referenční dokumentace (C++ AMP)
Tato část obsahuje referenční informace pro modul runtime C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Standardní jazyka C++ rezerv použití identifikátorů, které začínají podtržítkem (`_`) znak pro implementace například knihovny. Nepoužívejte názvy počínaje podtržítkem ve vašem kódu. Uvolní chování kódu elementy, jejichž názvy následují touto konvencí se nezaručuje a v budoucnu se mohou změnit. Z těchto důvodů jsou tyto elementy kódu vynechaný této dokumentace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)  
 Poskytuje třídy a funkce, které umožňují akcelerace kódu C++ na paralelní hardwaru data.  
  
 [Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)  
 Poskytuje funkce, které podporují D3D interoperability. Umožňuje bezproblémové použití D3D prostředků pro výpočet v kódu AMP a využívat prostředky vytvořené v AMP v kódu D3D bez vytvoření zprostředkující redundantní kopie. C++ AMP můžete přírůstkově urychlit části náročné DirectX aplikací a použít rozhraní API D3D na dat vytvářených z AMP výpočty.  
  
 [Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)  
 Funkce `fast_math` nejsou kompatibilní se standardem C99 oboru názvů. Pouze jednoduchou přesností verze jednotlivé funkce jsou k dispozici. Vnitřní funkce DirectX, které jsou rychlejší než odpovídající funkce v použít tyto funkce `precise_math` obor názvů a nevyžadují rozšířené podpory dvojitou přesností na akcelerátor, ale je méně přesné. Existují dvě verze jednotlivé funkce pro zdroj úroveň kompatibility s kódem C99; obě verze trvat a návratové hodnoty jednoduchou přesností.  
  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)  
 Poskytuje typy a funkce, které jsou určené pro programováním grafiky.  
  
 [Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)  
 Funkce `precise_math` obor názvů jsou C99 kompatibilní. Jednoduchou přesností a dvojitou přesností verzích jednotlivé funkce jsou zahrnuty. Tyto funkce – to zahrnuje funkce jednoduchou přesností – vyžadují rozšířené podpory dvojitou přesností na akcelerátor.  
  
## <a name="related-sections"></a>Související oddíly  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C++ AMP zrychluje provádění kódu C++ a využívají data paralelní hardware, který se obvykle nachází jako grafický procesor (GPU) na kartě diskrétní grafiky.





