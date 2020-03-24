---
title: Chyba sestavení projektu PRJ0025
ms.date: 08/27/2018
f1_keywords:
- PRJ0025
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
ms.openlocfilehash: 30445a3abc2a6ad05c983448f57ed5b93df6e61f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192351"
---
# <a name="project-build-error-prj0025"></a>Chyba sestavení projektu PRJ0025

> Dávkový soubor '*File*' obsahuje obsah v kódování Unicode, který nelze přeložit na znakovou stránku ANSI uživatele.
>
> *Obsah UNICODE souboru*

Systém projektu našel v pravidle vlastního buildu nebo v události sestavení obsah Unicode, který nelze správně přeložit na aktuální znakovou stránku ANSI uživatele.

Řešením této chyby je aktualizovat obsah pravidla sestavení nebo události sestavení pro použití ANSI nebo pro instalaci znakové stránky do počítače a nastavit jej jako výchozí systém.

Další informace o vlastních krocích sestavení a událostech sestavení naleznete v tématu [porozumění vlastním krokům sestavení a událostem sestavení](../../build/understanding-custom-build-steps-and-build-events.md).
