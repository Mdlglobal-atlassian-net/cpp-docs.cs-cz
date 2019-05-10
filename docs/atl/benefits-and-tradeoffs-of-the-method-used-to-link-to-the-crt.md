---
title: Výhody a nevýhody metody použité k připojení k CRT
ms.date: 05/06/2019
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
ms.openlocfilehash: b2e504de91cea9fef6e9acb0fc851bc2cc271e97
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221276"
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Výhody a nevýhody metody použité k připojení k CRT

Váš projekt můžete propojit s CRT dynamicky nebo staticky. Následující tabulka popisuje výhody a nevýhody, které jsou součástí zvolíte, jakou metodu použít.

|Metoda|Výhody|Kompromis|
|------------|-------------|--------------|
|Staticky připojení k CRT<br /><br /> (**Knihovny prostředí Runtime** nastavena na **Single-threaded**)|CRT knihovny DLL není vyžadováno v systému, ve kterém se spustí na obrázku.|Přibližně 25 tisíc spuštění kódu se přidá do bitové kopie, podstatně čímž zvětšují její velikost.|
|Dynamické propojování CRT<br /><br /> (**Knihovny prostředí Runtime** nastavena na **vícevláknové**)|Svou image nevyžaduje, aby spouštěcí kód CRT, tak, aby byl mnohem menší.|CRT knihovny DLL musí být spuštěná image systému.|

Téma [připojení k CRT v projektu knihovny ATL](../atl/linking-to-the-crt-in-your-atl-project.md) popisuje, jak vybrat způsob, ve které chcete propojit s CRT.

## <a name="see-also"></a>Viz také:

[Programování s použitím knihovny ATL a běhového kódu jazyka C](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Knihovny DLL a chování běhové knihovny v jazyce Visual C++](../build/run-time-library-behavior.md)<br/>
[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
