---
title: Závažná chyba C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: 6a802928315126b72397ba6e8cc61b66f46deb41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202837"
---
# <a name="fatal-error-c1900"></a>Závažná chyba C1900

> Il – Neshoda mezi '*tool1*' verze '*Číslo1*' a '*Tool2*' verze '*číslo2*'

Nástroje spuštěné v různých průchodech kompilátoru se neshodují. *Číslo1* a *číslo2* odkazují na data souborů. Například v metodě Pass 1 se spustí front-end kompilátoru (C1. dll) a v Pass 2 se spustí back-end kompilátoru (C2. dll). Data souborů se musí shodovat.

Chcete-li tento problém vyřešit, zajistěte, aby byly všechny aktualizace aplikovány na aplikaci Visual Studio. Pokud potíže potrvají, opravte nebo přeinstalujte sadu Visual Studio pomocí **programů a funkcí** v Ovládacích panelech systému Windows.
