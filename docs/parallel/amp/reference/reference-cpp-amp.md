---
title: Referenční dokumentace (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: ff7c2b0894a2fa3de7674a72bc93dd3f781398b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126406"
---
# <a name="reference-c-amp"></a>Referenční dokumentace (C++ AMP)

Tato část obsahuje referenční informace pro modul C++ runtime urychleného obrovských paralelismuC++ (amp).

> [!NOTE]
> Standard C++ jazyka vyhrazuje použití identifikátorů, které začínají znakem podtržítka (`_`) pro implementace, jako jsou knihovny. Nepoužívejte názvy začínající podtržítkem ve vašem kódu. Chování prvků kódu, jejichž názvy následují podle této konvence, není zaručeno a v budoucích verzích se může změnit. Z těchto důvodů jsou tyto prvky kódu z této dokumentace vynechány.

## <a name="in-this-section"></a>V tomto oddílu

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
Poskytuje třídy a funkce, které umožňují zrychlení C++ kódu na datovém paralelním hardwaru.

[Concurrency::direct3d – obor názvů](concurrency-direct3d-namespace.md)<br/>
Poskytuje funkce, které podporují interoperabilitu rozhraní D3D. Umožňuje bezproblémové použití prostředků D3D k výpočtům v kódu AMP a používání prostředků vytvořených v AMP v kódu D3D bez vytváření redundantních pomocných kopií. Pomocí C++ amp můžete postupně zrychlit výpočetní a náročné oddíly aplikací rozhraní DirectX a použít rozhraní D3D API pro data vytvořená z výpočtů amp.

[Concurrency::fast_math – obor názvů](concurrency-fast-math-namespace.md)<br/>
Funkce v oboru názvů `fast_math` nejsou kompatibilní s C99. K dispozici jsou pouze verze s jednoduchou přesností jednotlivých funkcí. Tyto funkce používají vnitřní funkce rozhraní DirectX, které jsou rychlejší než odpovídající funkce v oboru názvů `precise_math` a nevyžadují rozšířenou podporu s dvojitou přesností v akcelerátoru, ale jsou méně přesné. Existují dvě verze každé funkce pro kompatibilitu na úrovni zdroje s C99 kódem. obě verze přebírají a vracejí hodnoty s jednoduchou přesností.

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)<br/>
Poskytuje typy a funkce navržené pro grafické programování.

[Concurrency::precise_math – obor názvů](concurrency-precise-math-namespace.md)<br/>
Funkce v oboru názvů `precise_math` C99 kompatibilní. Součástí jsou i verze s jednoduchou přesností a dvojitou přesností jednotlivých funkcí. Tyto funkce – to zahrnuje funkce s jednoduchou přesností – vyžaduje rozšířenou podporu dvojité přesnosti v akcelerátoru.

## <a name="related-sections"></a>Související oddíly

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++AMP zrychlí provádění C++ kódu využitím hardwaru, který je běžně přítomen jako grafický procesor (GPU) na samostatné grafické kartě.
