---
title: Chyba sestavení projektu PRJ0024 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0024
dev_langs:
- C++
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb539a5f1ee5f1aa5f9d828d93fa6d0dc8690c22
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215595"
---
# <a name="project-build-error-prj0024"></a>Chyba sestavení projektu PRJ0024

> Cestu kódovanou sadou Unicode '*cesta*se nepodařilo přeložit na uživatelovu ANSI znakovou stránku.

*cesta* je původní verze Unicode řetězec cesty. Této chybě může dojít v případech, ve kterých je cestu kódovanou sadou Unicode, který nelze přeložit přímo na ANSI pro aktuální systémová znaková stránka.

K této chybě může dojít, pokud pracujete s projektem, který byl vyvinut v systému pomocí znakovou stránku, která není ve vašem počítači.

Řešením této chyby je aktualizovat cestu použití ANSI textu nebo k instalaci na znakovou stránku ve vašem počítači a nastavte jej jako výchozí systémové hodnoty.