---
title: Upozornění sestavení projektu PRJ0041 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7677c5718783065f64e52f98f7ddbed76e905d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038136"
---
# <a name="project-build-warning-prj0041"></a>Upozornění sestavení projektu PRJ0041

Nelze najít chybějící závislost 'závislosti' pro soubor 'file'. Projektu stále možné sestavit, ale může se jevit jako zastaralý dokud tento soubor není nalezen.

Soubor (soubor prostředků nebo.idl/.odl souboru, například obsažené příkazu zahrnout, který systém projektu nebylo možné přeložit.

Protože systém projektu nezpracovává příkazy preprocesoru (například #if), nemusí být problematický příkaz ve skutečnosti součástí sestavení.

Pokud chcete vyřešit toto upozornění, odstraňte všechny nepotřebné kód v souborech .rc nebo přidejte zástupné soubory odpovídající název.