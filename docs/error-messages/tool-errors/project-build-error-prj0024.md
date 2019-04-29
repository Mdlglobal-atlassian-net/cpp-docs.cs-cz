---
title: Chyba sestavení projektu PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: 645b898bdffcc6d7b397c25eb3c41cea25cb361f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384099"
---
# <a name="project-build-error-prj0024"></a>Chyba sestavení projektu PRJ0024

> Cestu kódovanou sadou Unicode '*cesta*se nepodařilo přeložit na uživatelovu ANSI znakovou stránku.

*cesta* je původní verze Unicode řetězec cesty. Této chybě může dojít v případech, ve kterých je cestu kódovanou sadou Unicode, který nelze přeložit přímo na ANSI pro aktuální systémová znaková stránka.

K této chybě může dojít, pokud pracujete s projektem, který byl vyvinut v systému pomocí znakovou stránku, která není ve vašem počítači.

Řešením této chyby je aktualizovat cestu použití ANSI textu nebo k instalaci na znakovou stránku ve vašem počítači a nastavte jej jako výchozí systémové hodnoty.