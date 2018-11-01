---
title: Upozornění sestavení projektu PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: b0fceff05ffe35515965b7e0a880c8b4c941b07e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583206"
---
# <a name="project-build-warning-prj0041"></a>Upozornění sestavení projektu PRJ0041

Nelze najít chybějící závislost 'závislosti' pro soubor 'file'. Projektu stále možné sestavit, ale může se jevit jako zastaralý dokud tento soubor není nalezen.

Soubor (soubor prostředků nebo.idl/.odl souboru, například obsažené příkazu zahrnout, který systém projektu nebylo možné přeložit.

Protože systém projektu nezpracovává příkazy preprocesoru (například #if), nemusí být problematický příkaz ve skutečnosti součástí sestavení.

Pokud chcete vyřešit toto upozornění, odstraňte všechny nepotřebné kód v souborech .rc nebo přidejte zástupné soubory odpovídající název.