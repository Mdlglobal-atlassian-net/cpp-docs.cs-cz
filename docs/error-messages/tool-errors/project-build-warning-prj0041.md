---
title: Upozornění sestavení projektu PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191926"
---
# <a name="project-build-warning-prj0041"></a>Upozornění sestavení projektu PRJ0041

Nelze najít chybějící závislost ' Dependency ' pro soubor ' file '. Projekt se může stále sestavit, ale může se i nadále zobrazovat bez aktuálního stavu, dokud se tento soubor nenajde.

Soubor (soubor prostředků nebo soubor. idl/. odl jako příklad obsahuje příkaz include, který systém projektu nemohl vyřešit.

Vzhledem k tomu, že systém projektu nezpracovává příkazy preprocesoru (například #if), problematický příkaz nemusí být ve skutečnosti součástí sestavení.

Chcete-li vyřešit toto upozornění, odstraňte veškerý nepotřebný kód v souborech. RC nebo přidejte zástupné soubory příslušného názvu.
