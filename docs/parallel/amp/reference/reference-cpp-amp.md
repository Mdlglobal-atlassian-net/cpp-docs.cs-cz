---
title: Referenční dokumentace (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: a334c7873675183dc06abfc2fe51472190996bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351167"
---
# <a name="reference-c-amp"></a>Referenční dokumentace (C++ AMP)

Tato část obsahuje referenční informace pro modul runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
>  Standard jazyka C++ vyhrazuje použití identifikátorů, které začínají podtržítkem (`_`) znak, například pro implementaci knihoven. Nepoužívejte názvy začínající podtržítkem ve vašem kódu. Chování kódu elementy, jejichž názvy postupujte podle tohoto konvence není zaručeno a se může změnit v budoucích vydáních. Z těchto důvodů jsou takovéto prvky kódu z této dokumentace vynechány.

## <a name="in-this-section"></a>V tomto oddílu

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
Poskytuje třídy a funkce umožňují zrychlení kódu C++ na datově paralelním hardwaru.

[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)<br/>
Poskytuje funkce podporující spolupráci rozhraní D3D. Umožňuje bezproblémové použití zdrojů rozhraní D3D pro výpočty v kódu AMP a využívání prostředků vytvořených v knihovně AMP v kódu D3D bez nutnosti vytvářet nadbytečné pomocné kopie. C++ AMP můžete postupně urychlovat provádění výpočetně náročných oddílů DirectX aplikace a použít rozhraní D3D API nad daty vytvořenými výpočty AMP.

[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)<br/>
Funkce v `fast_math` oboru názvů nejsou kompatibilní s normou C99. Jsou k dispozici pouze jednoduchou přesnost verze jednotlivých funkcí. Tyto funkce používají vnitřní funkce rozhraní DirectX, které jsou rychlejší než odpovídající funkce v `precise_math` obor názvů a nevyžadují rozšířenou podporu dvojité přesnosti v akcelerátoru, ale jsou méně přesné. Existují dvě verze jednotlivých funkcí pro kompatibilitu na úrovni zdroje s kódem C99; obě verze přebírají a vracejí hodnoty s jednoduchou přesností.

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)<br/>
Poskytuje typy a funkce, které jsou navržené pro grafické programování.

[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)<br/>
Funkce v `precise_math` obor názvů jsou kompatibilní s normou C99. Verze jednoduchou a dvojitou přesností jednotlivých funkcí jsou zahrnuty. Tyto funkce – to zahrnuje funkce jednoduchou přesností, vyžadují rozšířenou podporu dvojité přesnosti v akcelerátoru.

## <a name="related-sections"></a>Související oddíly

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++ AMP zrychlí provádění kódu jazyka C++ využitím hardwaru paralelizovaného pro data, která je běžně přítomen jako grafický procesor (GPU) na samostatné grafické kartě.
