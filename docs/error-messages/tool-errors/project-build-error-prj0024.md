---
title: Chyba sestavení projektu PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: bcfdcce54618acca0e22daa54e95083cf3ee9d50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192611"
---
# <a name="project-build-error-prj0024"></a>Chyba sestavení projektu PRJ0024

> Cestu k sadě*Unicode Path nelze*přeložit na znakovou stránku ANSI uživatele.

*cesta* je původní verze Unicode řetězce cesty. K této chybě může dojít v případech, kdy je k dispozici cesta Unicode, kterou nelze přímo přeložit do ANSI pro aktuální znakovou stránku systému.

K této chybě může dojít, pokud pracujete s projektem, který byl vytvořen v systému pomocí znakové stránky, která není ve vašem počítači.

Řešením této chyby je aktualizovat cestu k používání textu ANSI nebo nainstalovat znakovou stránku do počítače a nastavit ji jako výchozí systém.
